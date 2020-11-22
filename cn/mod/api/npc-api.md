# NPC API

## NPC通用模块（NpcUtils）

| 函数 | 返回值 | 描述 |
| :--- | :---: | :--- |
| NpcUtils.SearchByRect\(double x, double y, int width, int height\) | ArrayList&lt;Npc&gt; | 返回包含于指定矩形区域内部的所有NPC列表。 |
| NpcUtils.SearchByCircle\(double centerX, double centerY, int radius\) | ArrayList&lt;Npc&gt; | 返回包含于指定圆形区域内部的所有NPC列表。 |
| NpcUtils.SearchNearestNpc\(double centerX, double centerY, int radius, bool noCrossTiles = false\) | Npc/nil | 搜索在指定圆形区域内部距离圆心最近的NPC，返回该NPC。若结果不存在，返回nil。noCrossTiles表示是否排除中心到圆心的连线被图格遮挡的NPC。 |
| NpcUtils.SearchNearestEnemy\(double centerX, double centerY, int radius, bool noCrossTiles = false\) | Npc/nil | 搜索在指定圆形区域内部距离圆心最近的敌对NPC，返回该NPC。若结果不存在，返回nil。noCrossTiles表示是否排除中心到圆心的连线被图格遮挡的NPC。 |

## NPC类（Npc Class）

**NPC**类表示具有生物基本信息的非玩家实体类。

在编写NPC AI脚本时，**self表示当前正在操作的NPC类**。

### 父类

该类的父类为[Entity类](entity.md#shi-ti-lei-entity-class)。可直接使用该父类的类成员属性与类成员函数。



