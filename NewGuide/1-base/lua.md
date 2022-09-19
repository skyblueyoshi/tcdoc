# 1.3 认识Lua

Lua是一门语法简单、运行高效的动态脚本语言，被广泛应用于手游开发领域。本游戏的模组开发将主要使用Lua作为编程语言。\


## Lua快速入门

https://learnxinyminutes.com/docs/zh-cn/lua-cn/XXX

## 菜鸟教程

https://www.runoob.com/lua/lua-tutorial.html

## 一般编程约定

源码统一使用UTF-8进行编码，为了防止出现乱码，请在编码的时候注意Pycharm右下角的编码格式为UTF-8。

* 变量：小驼峰命名法
* 类名、函数名：大驼峰命名法
* 私有成员、私有成员函数：下划线开头
* 共有成员、共有成员函数：无下划线开头
* 常量：全大写并用下划线分隔单词

PS：由于项目开发历史原因问题，许多函数名并非完全采用大驼峰命名法，如引擎API则统一为小驼峰命名法，您在开发时可以根据习惯遵循使用大/小驼峰命名法。

```lua
local testValue = 1

local TestClass = class("TestClass")
function TestClass:__init()
    self._privateValue = 1
    self.publicValue = 2
end
function TestClass:_RunPrivateFunction()
end
function TestClass:RunPublicFunction()
end

local TEST_CONSTANT = 123
```

## 新增Lua特性

在原有Lua基础语法之上，游戏引擎提供了这些新的Lua特性。

### 面向对象编程（OOP）

游戏引擎为Lua加入了面向对象语法，方便我们使用面向对象思想进行游戏开发。

* 使用class(类名,\[父类])来创建一个类，若指定父类，则创建该父类的子类。
* 使用function 类名:\_\_init(\[参数列表])来定义该类的构造函数。
* 使用类名.super.函数名(self, \[参数列表])来访问父类函数。

```lua
-- 定义Animal类
local Animal = class("Animal")

-- 定义Animal类的构造函数
function Animal:__init(soundName)
	self._soundName = soundName
end

function Animal:Act()
    PlaySound(self._soundName)
end

-- 定义Dog类，继承自Animal类
local Dog = class("Dog", Animal)

-- 定义Dog类的构造函数，注意内部一定要执行父类的构造函数
function Dog:__init()
    Dog.super.__init("Bark")
end

function Dog:Act()
    Dog.super.Act(self)
end

-- 定义Bird类，继承自Animal类
local Bird = class("Bird", Animal)
function Bird:__init()
    Bird.super.__init("Sing")
end

function Bird:Act()
    Bird.super.Act(self)
    self:_Fly()
end

function Bird:_Fly()
    -- 鸟类飞行
end

```

### 热更新

热更新是指游戏在运行时无需重启即可快速应用您修改后的最新代码。您可以在游戏运行时修改您的模组代码，之后按F5得到模组代码修改后的效果。

注意：热更新仅仅更新函数体和函数内的变量，对于已经存在于内存中的数据不会进行更新。因此，对于代码中全局维护的数据发生了变化，您需要重启游戏才能来应用该变化。

### 错误定位

当Lua脚本运行出错时，引擎将弹出错误警告窗口并将错误堆栈输出到日志。您可以根据堆栈信息定位出错原因。

### 打印日志

引擎将print函数作为模组的日志输出函数，print不仅将把信息显示在控制台中，还会把信息记录到日志里，便于日后查看日志。

print还支持这些特性：

* print支持打印部分API接口的内部信息。
* print支持打印lua的表。
* print支持在同一行日志中打印多个信息，使用逗号分割print的参数即可。

### 跨文件导入

你可以使用require("lua路径")来导入你的代码文件。lua路径支持使用当前目录下相对路径，以及使用当前模组目录下的绝对路径。如果需要跨模组导入文件，则需要在lua路径最前面加入模组前缀。

### JSON序列化和反序列化

JsonUtil是引擎的JSON格式序列化库，可以使用JsonUtil.toJson将lua表序列化为标准JSON字符串，也可以使用JsonUtil.fromJson将一个标准JSON字符串反序列化为lua表。使用该序列化库可以实现将lua的任意表通过协议进行传输，或者实现加载及保存存档。





