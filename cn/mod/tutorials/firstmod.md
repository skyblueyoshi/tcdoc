# 创建第一个Mod

## 0、TerraCraftForge \(TCF\)

什么是TerraCraftForge？TerraCraftForge是一个从Indev版本开始TerraCraft本体自带的模组包工具，自动帮助模组玩家导入模组包信息，处理模组的依赖以及存档兼容性问题，并给模组开发者提供便利的开发体验。

## 1、创建你的Mod工程

在游戏主目录的mods文件夹内创建一个文件夹作为将要开发Mod的项目文件夹，文件夹名称任意取名。

> _注：本教程以“MyFirstMod”为例子，在mods文件夹内创建"MyFirstMod"文件夹，请按自己想要开发的模组名称给文件夹命名。_

创建如下文件，并在该JSON文件中填写你的Mod项目的基本信息：

> MyFirstMod/tcmod.json

```text
{
  "modid": "my_first_mod",
  "displayName": "MyFirstMod",
  "description": "A journey ends and a new story begins.",
  "version": "1.0.0.0",
  "tcVersion": "Indev 0.1",
  "authorList": [ "BlueYoshi", "KfcMario" ],
  "credits": "Anything you want to thank."
}
```

| 属性 | 默认 | 描述 |
| :--- | :--- | :--- |
| modid | 必填 | 当前模组的命名空间ID，模组包的唯一标识符，模组发布后不可再修改。见下面关于命名空间的概念解释。只能由小写字母、数字、下划线组成 |
| displayName | 必填 | 游戏中对玩家可见的模组名称， |
| description | 空 | 游戏中对玩家可见的模组描述 |
| version | 必填 | 模组版本号，每次更新模组时需要更新该版本号，版本号必须为4个数字并以英文点号分隔，并且更新版本时数字应该依次累加，以便于Forge自动检测每个存档对应的版本信息并提供兼容处理 |
| tcVersion | 必填 | TerraCraft游戏本体的版本号，请准确填写以便TCF进行存档的版本检测 |
| authorList | 必填 | 开发当前模组的作者名称，可以设置多个作者名称 |
| credits | 空 | 感谢信息 |

### 命名空间

命名空间（`modid`，又称作`namespace`）是当前模组在整个模组包的唯一标识符。如果在所有加载的模组中出现了两个或多个命名空间相同的模组，这两个模组会发生冲突导致模组包加载失败。因此在命名`modid`时请尽可能选择一个不容易发生冲突的命名空间。TerraCraft原版的命名空间为`tc`或者`空`。

命名空间的重要作用是确保所有的对象（比如方块、物品、NPC、抛射物、特效等）的名称在全局空间中是独一无二的，每个对象在全局空间的唯一名称是`命名空间:名称`。通过如下简单的例子来理解：

> 假设当前加载了命名空间为happy\_days和coco\_world的两个模组，两个模组都有一个叫做dirt的方块，那么在全局空间中：  
> （1）dirt和tc:dirt均表示TerraCraft原版的泥土方块  
> （2）happy\_days:dirt表示happy\_days模组的泥土方块  
> （3）coco\_world:dirt表示coco\_world模组的泥土方块

对于原版的所有对象，它们在全局空间的唯一名称是`名称`或者`tc:名称`，请注意区别。

### 中文乱码问题

请将Mod中所有JSON文件保存为`UTF8 无签名`格式，否则在游戏运行过程中可能会出现乱码问题。这是因为`UTF8 无签名`为目前游戏对于JSON文件解码的格式，用于解决全球化的字符问题。

## 2、文件管理

参考/mods/terracraft的文件管理方式，您可以根据模组需求在项目主文件夹中创建这些文件夹和内部的文件：

* textures：存放贴图文件的地方，请使用png作为贴图文件格式
* blocks：存放方块相关信息
  * blocks.json：方块数据表
  * covers.json：方块覆盖对象数据表
  * ores.json：矿脉数据表
  * plants.json：植物数据表
* items：存放物品相关信息
  * items.json：物品数据表
  * groups.json：物品组的数据信息
* npcs：存放NPC相关信息
  * npcs.json：NPC数据表
  * npcAIs.json：NPC的AI数据表
  * XXX.lua：NPC指定AI的处理脚本
* effects：存放特效相关信息
* projectiles：存放抛射物的模组数据和代码
* buffs：存放状态效果的模组数据和代码
* enchantments：存放附魔的模组数据和代码
* liquids：存放流体的模组数据和代码
* recipes：存放配方的模组数据和代码
* skins：存放皮肤的模组数据和代码
* trees：存放树的模组数据和代码
* ui：存放用户图形界面的模组数据和代码

