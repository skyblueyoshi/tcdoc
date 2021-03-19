# 1.3 配置模组环境

## 创建第一个模组

在游戏主目录的devmods文件夹内创建一个文件夹作为将要开发Mod的项目文件夹，文件夹名称任意取名。

> _注：本教程以“ExampleMod”为例子，在devmods文件夹内创建"ExampleMod"文件夹，请按自己想要开发的模组名称给文件夹命名。_

创建如下文件，并在该JSON文件中填写你的Mod项目的基本信息：

> ExampleMod/tcmod.json

```sql
{
  "modid": "exmod",
  "displayName": "ExampleMod",
  "description": "A journey ends and a new story begins.",
  "version": "1.0.0.0",
  "tcVersion": "Indev 1.1",
  "authorList": [ "BlueYoshi", "KfcMario" ],
  "credits": "Anything you want to thank.",
  "useSaver": true
}
```

| 属性 | 类型 | 默认 | 描述 |
| :--- | :--- | :--- | :--- |
| modid | 字符串 | 必填 | 当前模组的命名空间ID，模组包的唯一标识符，模组发布后不可再修改。见下面关于命名空间的概念解释。只能由小写字母、数字、下划线组成 |
| displayName | 字符串 | 必填 | 游戏中对玩家可见的模组名称 |
| description | 字符串 | 空 | 游戏中对玩家可见的模组描述 |
| version | 字符串 | 必填 | 模组版本号，每次更新模组时需要更新该版本号，版本号必须为4个数字并以英文点号分隔，并且更新版本时数字应该依次累加 |
| tcVersion | 字符串 | 必填 | TerraCraft游戏本体的版本号，请准确填写以便存档版本检测 |
| authorList | 数组 | 必填 | 开发当前模组的作者名称，可以设置多个作者名称 |
| credits | 字符串 | 空 | 感谢信息 |
| useSaver | 布尔值 | false | 模组是否使用存档，一般填true |

## 命名空间

命名空间（`modid`，又称作`namespace`）是当前模组在整个模组包的唯一标识符。如果在所有加载的模组中出现了两个或多个命名空间相同的模组，这两个模组会发生冲突导致模组包加载失败。因此在命名`modid`时请尽可能选择一个不容易发生冲突的命名空间。TerraCraft原版的命名空间为`tc`或者`空`。

命名空间的重要作用是确保所有的对象（比如方块、物品、NPC、抛射物、特效等）的名称在全局空间中是独一无二的，每个对象在全局空间的唯一名称是`命名空间:名称`。通过如下简单的例子来理解：

> 假设当前加载了命名空间为happy\_days和coco\_world的两个模组，两个模组都有一个叫做dirt的方块，那么在全局空间中：  
> （1）dirt和tc:dirt均表示TerraCraft原版的泥土方块  
> （2）happy\_days:dirt表示happy\_days模组的泥土方块  
> （3）coco\_world:dirt表示coco\_world模组的泥土方块

对于原版的所有对象，它们在全局空间的唯一名称是`名称`或者`tc:名称`，请注意区别。

## 中文乱码问题

请将所有JSON文件保存为`UTF8`格式，否则在游戏运行过程中可能会出现乱码问题。

