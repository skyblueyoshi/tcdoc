# MOD入门——JSON数据表

在这一章中，您将了解JSON**数据表**的概念。事实上在整个Mod开发流程中，我们需要按照规定的模板格式编写JSON数据表，依靠游戏内置的大量功能模板来实现大部分功能。如果内置模板功能仍然无法满足自己的想法，则可以编写Lua脚本实现更复杂的逻辑。

如果您未接触过JSON，我们建议先提前学习JSON的规范化编写，之后再阅读本教程。

对于接下来的每一个章节，我们会先介绍入门方法，之后再介绍进阶方法。如果您希望制作一个简单小巧的Mod，只阅读入门级教程即可。如果您希望制作功能更强大、画面更炫酷的Mod，可以继续阅读进阶教程。

## 1、JSON数据表（JSON DataTable）

Mod对于所有对象均采用**JSON数据表**的形式进行初始化。数据表内部所有的名称使用空间均为Mod所在的私有空间，而不是使用全局空间。如果想要进行Mod之间的联动，需要指向其他Mod的对象，请使用`其他Mod的命名空间:名称`。举个例子：

> 假设当前加载了命名空间为happy\_days和coco\_world的两个模组，happy\_days模组有一个叫做cat\_bullet的物品，coco\_world模组希望与happy\_days模组进行联动，设计了一把枪械叫做dog\_gun，希望用happy\_days的cat\_bullet作为弹药。  
> 那么在coco\_world数据表的dog\_gun中写入的弹药物品应为happy\_days:cat\_bullet。如果直接写cat\_bullet只会在原版物品和当前模组物品中查找这个名称，找不到就直接报错。

如果Mod私有空间中的对象名称跟TerraCraft原版名称相同，则实际指向Mod的这个对象，而不是TerraCraft原版的对象。如果想指向TerraCraft原版的对象，请使用`tc:名称`。还是举个例子：

> 假设当前希望编写一个模组，将9个原版泥土合成1个钻石，而当前模组已经出现了命名为dirt的物品。如果直接使用dirt，那么会采用模组的dirt来合成钻石。而如果使用tc:dirt，则会采用原版的泥土合成钻石。

## 2、TerraCraftForge的数据表注册机制

在编写第一个数据表之前，您需要简单地了解一下数据表是干什么用的。TCF在加载所有模组时会自动对数据表的每个对象进行**注册（Register）**，之后每个对象会得到游戏内动态生成的唯一数字ID，这个数字ID在整个游戏运行时是不会发生改变的。_这个知识点在Lua脚本教程中会用到哦0w0。_

## 3、数据表编写

如果你想要编写一个数据表，我们建议在`/mods/terracraft`中寻找相对于的数据表，并仿照这个数据表的格式进行编写。

同时您应该按照严格格式的数据表规范进行编写，参阅[模组数据表文档](../datatable/)。注意，数据表严格采用JSON格式填写，并且并不支持注释。

