# 1.4 认识模组路径

参考**devmods/terracraft**的文件管理方式，您可以根据模组需求在你的模组文件夹中创建这些文件夹和内部对应文件。

* _**data**_：编写杂项配置表。
* _**contents**_：存放游戏元素和对应配置表。
  * _**advancements**_：存放进度。
  * _**blocks**_：存放方块。
  * _**block\_presets**_：存放方块预设。
  * _**boimes**_：存放生物群系。
    * _**surfaces**_：存放地表生物群系。
    * _**undergrounds**_：存放洞穴生物群系。
    * _**nethers**_：存放地狱生物群系。
  * _**buffs**_：存放状态效果。
  * _**buildings**_：存放建筑。
  * _**commands**_：存放指令。
  * _**effects**_：存放特效。
  * _**effect\_ai**_：存放特效AI。
  * _**enchantments**_：存放附魔。
  * _**items**_：存放物品。
  * _**item\_ai**_：存放物品逻辑。
  * _**liquids**_：存放流体。
  * _**npcs**_：存放NPC。
  * _**npc\_ai**_：存放NPC的AI。
  * _**projectiles**_：存放抛射物。
  * _**projectile\_ai**_：存放抛射物AI。
  * _**recipes**_：存放配方。
  * _**recipe\_config**_：存放万能配方表。
  * _**mod\_textures**_：存放自定义贴图。
  * _**skeletons**_：存放骨骼模型。
  * _**shaders**_：存放着色器。
  * _**skins**_：存放皮肤。
  * _**spawns**_：存放NPC生成表。
  * _**trees**_：存放树。
* _**languages**_：存放语言文件。
* _**scripts**_：存放全局脚本模块。
* _**sounds**_：存放音效文件。

一般情况下，我们在_**contents**_文件夹进行模组开放。_**contents**_所有子文件夹内可以随意自定义文件目录结构。

