# 1.6 Lua实战

这里提供一些小练习，可以让你进一步了解Lua在TerraCraft的应用，以及游戏引擎为Lua支持的特性。

## 面向对象与跨文件导入

游戏引擎为lua支持了面向对象开发的功能，在通常的开发模式中，我们一般把lua文件的代码用一个类封装起来，并在lua文件最后一行返回该类本身。这样我们在外部文件导入lua文件的时候可以直接得到文件对应的类。同时，引擎为lua类支持了面向对象的继承功能，子类可以继承父类，以此实现更灵活的开发。

通过如下实战，你可以更清晰地了解面向对象和跨文件导入的一般写法。

在你的Mod主文件夹内创建一个子文件夹，命名为`TestFolder`，里面新建3个文件：`TestAnimal.lua`和`TestDog.lua`和`TestCat.lua`。把下面代码复制粘贴到对应文件：

#### TestAnimal.lua

```
local TestAnimal = class("TestAnimal")

function TestAnimal:__init(name)
    self.name = name
end

function TestAnimal:Say()
    print("animal saying")
end

return TestAnimal
```

#### TestDog.lua

```
local TestDog = class("TestDog", require("TestAnimal"))

function TestDog:__init(age)
    TestDog.super.__init("SuperBigDog")
    self.age = age
end

function TestDog:Say()
    TestDog.super.Say(self)
    print("Woof! My age is", self.age)
end

return TestDog
```

#### TestCat.lua

```
local TestCat = class("TestCat", require("TestAnimal"))

function TestCat:__init()
    TestCat.super.__init("SuperSmallCat")
end

function TestCat:Say()
    TestCat.super.Say(self)
    print("Meow!")
end

return TestCat
```

我们在文件夹里面，创建了一个基类TestAnimal，并编写了两个子类描述这表示猫和狗两个类。

在init.lua中，我们在CommonProxy的构造函数中，把猫和狗两个类进行实例化，并希望猫和狗能够得到函数Say的结果：

```
function CommonProxy:__init()
    local TestCat = require("TestFolder.TestCat")
    local TestDog = require("TestFolder.TestDog")
    local cat = TestCat.new()
    local dog = TestDog.new(3)
    cat:Say()
    dog:Say()
end
```

跨文件导入的包名路径是支持以当前文件所在文件夹作为相对路径来编写的。在TestCat和TestDog导入TestAnimal的时候，由于他们都在同一个文件夹内，因此可以直接写lua文件名。而在init.lua导入TestCat和TestDog的时候，因为这两个文件相对于init.lua文件还隔了个TestFolder文件夹，因此需要多写TestFolder这个包名。如果希望导入上层的lua文件，你需要明确从Mod根目录开始的所有包名路径。

## 热更新实战

游戏引擎为Mod开发流程引入了一个重要功能：热更新。你可以实时地修改你的Mod代码并马上能在游戏内看到最新效果，而不需要重启游戏。这可以极大提高AI开发和UI开发的效率。

我们从一个实战开始。假设一个策划想让你在游戏每帧打印1到50累加的结果，在init.lua中你可以这么写：

```
function CommonProxy:update()
    local res = 0
    for i = 1, 50 do
        res = res + i
    end
    print("sum of 1 to 50:", res)
end
```

进入游戏，你会发现在每一个游戏帧，控制台会一直输出1到50累加的结果：

（TODO截图）

然后，这个策划突然间想让你把之前的需求改成每帧打印1到100的结果，你可以把刚刚写好的代码修改成如下代码：

```
function CommonProxy:update()
    local res = 0
    for i = 1, 100 do
        res = res + i
    end
    print("sum of 1 to 100:", res)
end
```

但是你仅仅只是改动了一个小的需求，自然不想关闭游戏重开来测试这个新需求。你只需要按下F5键，游戏引擎会自动将立即更新并应用最新的代码，每帧控制台输出也会变成输出1到100的结果。

（TODO截图）

了解热更新的特性后，您可以实现边开发边测试，实现开发效率最大化。









