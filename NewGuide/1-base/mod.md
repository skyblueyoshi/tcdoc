# 1.4 Mod架构

在模组文件夹中，您需要最少构建出这些文件：

TODO

## 构建tcmod.json

在Mod文件夹里新建一个空文件，命名为`tcmod.json`，该文件负责配置Mod的基本信息，包括显示名称，id，版本号等等。

* modid：模组的唯一标识，命名约定只能由小写字母和数字已经下划线组成。modid用于区分您的模组和其他不同的模组。
* displayName：模组的显示名称，用于在模组列表、物品详情等界面显示您的模组名。
* version：模组版本号，约定为数字.数字.数字.数字，用于游戏检测模组版本。
* tcVersion：模组最小支持的TC版本。
* authorList：作者名称列表。
* credits：一些想说的话。

## 构建contents文件夹

TODO（可能不需要）

## 构建init.lua

在您的Mod文件夹的主目录下中创建`init.lua`，并把下面这段代码复制粘贴到你的init.lua里。

```lua
local CommonProxy = class("CommonProxy")
function CommonProxy:__init()
    -- TODO
end

function CommonProxy:registerProxy()
    -- TODO
end

function CommonProxy:init()
    -- TODO
end

function CommonProxy:start()
    -- TODO
end

function CommonProxy:preUpdate()
    -- TODO
end

function CommonProxy:update()
    -- TODO
end

function CommonProxy:postUpdate()
    -- TODO
end

function CommonProxy:exit()
    -- TODO
end

local ClientProxy = class("ClientProxy", CommonProxy)

function ClientProxy:__init()
    ClientProxy.super.__init(self)
    -- TODO
end

function ClientProxy:registerProxy()
    ClientProxy.super.registerProxy(self)
    -- TODO
end

function ClientProxy:init()
    ClientProxy.super.init(self)
    -- TODO
end

function ClientProxy:start()
    ClientProxy.super.start(self)
    -- TODO
end

function ClientProxy:preUpdate()
    ClientProxy.super.preUpdate(self)
    -- TODO
end

function ClientProxy:update()
    ClientProxy.super.update(self)
    -- TODO
end

function ClientProxy:postUpdate()
    ClientProxy.super.postUpdate(self)
    -- TODO
end

function ClientProxy:render()
    -- TODO
end

function ClientProxy:exit()
    ClientProxy.super.exit(self)
    -- TODO
end

local ServerProxy = class("ServerProxy", CommonProxy)

function ServerProxy:__init()
    ServerProxy.super.__init(self)
    -- TODO
end

function ServerProxy:registerProxy()
    ServerProxy.super.registerProxy(self)
    -- TODO
end

function ServerProxy:init()
    ServerProxy.super.init(self)
    -- TODO
end

function ServerProxy:start()
    ServerProxy.super.start(self)
    -- TODO
end

function ServerProxy:preUpdate()
    ServerProxy.super.preUpdate(self)
    -- TODO
end

function ServerProxy:update()
    ServerProxy.super.update(self)
    -- TODO
end

function ServerProxy:postUpdate()
    ServerProxy.super.postUpdate(self)
    -- TODO
end

function ServerProxy:exit()
    ServerProxy.super.exit(self)
    -- TODO
end

local ModProxy = class("ModProxy")

function ModProxy:__init()
    self.m_proxy = nil
    if NetMode.current == NetMode.Server then
        self.m_proxy = ServerProxy.new()
    else
        self.m_proxy = ClientProxy.new()
    end
    self.m_proxy:registerProxy()
end

function ModProxy:init()
    self.m_proxy:init()
end

function ModProxy:start()
    self.m_proxy:start()
end

function ModProxy:preUpdate()
    self.m_proxy:preUpdate()
end

function ModProxy:update()
    self.m_proxy:update()
end

function ModProxy:postUpdate()
    self.m_proxy:postUpdate()
end

function ModProxy:render()
    if NetMode.current == NetMode.Client then
        self.m_proxy:render()
    end
end

function ModProxy:exit()
    self.m_proxy:exit()
end

return ModProxy
```

`init.lua`是整个模组参与游戏生命周期的入口，游戏会在客户端和服务端中生成从该文件表示的类对象，并使用该类对象参与整个游戏进程。

* 客户端/服务端初始化时，将实例化这个`ModProxy`对象，执行其中的`__init`方法（类构造函数）
* 客户端/服务端准备开始循环时，先执行`ModProxy`的的`init`方法，后执行`start`方法。
* 客户端/服务端在主循环每帧开始前，执行`ModProxy`的`preUpdate`方法。在主循环逻辑中，每帧执行`update`方法。在每帧结束时，执行`postUpdate`方法。
* 客户端在每个渲染帧时，执行`ModProxy`的`render`方法。
* 客户端/服务端退出游戏时，执行`ModProxy`的`exit`方法。

一般来说，`Modproxy`的`__init`里编写其他底层注册相关代码，`init`编写ui等初始化代码，`start`写与主循环相关的初始代码，`update/preUpdate/postUpdate`写每帧会执行的代码，`exit`写游戏结束时相关结束逻辑和内存释放代码。

## 什么是代理

为什么这里会有那么多的Proxy？在TerraCraft里，游戏分为客户端线程和服务端线程并行执行。即使是单人模式，游戏同样内置了一个服务端线程。客户端线程和服务端线程之间通过TCP网络协议进行数据交流（在单人模式中使用内网TCP）。而对于纯服务器程序，游戏只会运行服务端线程而不会运行客户端线程。在游戏进行过程中，客户端线程和服务端线程都会共同通过ModProxy执行代码。

我们可以直接使用`NetMode.current`为`NetMode.Client`或者`NetMode.Server`来判断当前代码的运行线程是客户端还是服务端。

由于客户端和服务端有许多代码是可以共用的，因此我们引入了一个`CommonProxy`类，来处理客户端和服务端的通用部分，并使用`ClientProxy`和`ServerProxy`继承`CommonProxy`来专门处理客户端和服务端不同的逻辑部分。

## 小试牛刀

1. 在服务端开始时，打印hello server。

答案：（TODO）

（2）在客户端线程中在控制台每帧打印hello client loop，在服务端线程中每帧打印hello server loop。

答案：（TODO）







