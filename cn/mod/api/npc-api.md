# NPC API

NPC在TerraCraft中泛指除了玩家之外的所有生物，如动物、敌怪、村民、BOSS等。

## 钩子函数

请在**NPCAI**脚本中使用这些钩子函数。

#### void Init\(\)

```lua
function Init()
    --init current npc here
end
```

NPC生成时调用一次该函数。

#### void Update\(\)

```lua
function Update()
    --update every game loop
end
```

NPC抛射物每帧运行时调用，您可以在该函数内编写运动等逻辑。

#### void PreUpdate\(\)

```lua
function ReadyUpdate()
    --update every game loop
end
```

NPC抛射物每帧运行`Update()`函数前调用。通常用于在使用AI重用后在原逻辑前插入新逻辑。

#### void PostUpdate\(\)

```lua
function PostUpdate()
    --update every game loop
end
```

NPC每帧运行`Update()`函数后调用。通常用于在使用AI重用后追加逻辑。

#### void OnDraw\(\)

```lua
function OnDraw()
    --change the sprite parameters before drawing every game loop
end
```

NPC每帧绘制前调用，在该函数内编写自定义绘制属性。不使用该钩子函数时采取默认处理方式。

#### void OnKilled\(\)

```lua
function OnKilled()
    --do something when npc is killed
end
```

NPC死亡时调用一次该函数。

#### void OnTileCollide\(double oldSpeedX, double oldSpeedY\)

```lua
function OnTileCollide()
    --do something when npc hit tiles
end
```

NPC与图块碰撞时调用该函数。

* `oldSpeedX`和`oldSpeedY`表示击中实心图块前一帧的横向和纵向速度。

## NPC通用模块（NpcUtils）

| 函数 | 返回值 | 描述 |
| :--- | :---: | :--- |
| NpcUtils.Create\(int id, double x, double y, double speedX = 0.0, double speedY = 0.0\) | Npc | 在指定位置创建一个NPC，返回创建好的NPC实体。 `id`：NPC的ID。`x`和`y`：创建NPC的坐标。`speedX`和`speedY`：初始运动速度。 |
| NpcUtils.SearchByRect\(double x, double y, int width, int height\) | ArrayList&lt;Npc&gt; | 返回包含于指定矩形区域内部的所有NPC列表。 |
| NpcUtils.SearchByCircle\(double centerX, double centerY, int radius\) | ArrayList&lt;Npc&gt; | 返回包含于指定圆形区域内部的所有NPC列表。 |
| NpcUtils.SearchNearestNpc\(double centerX, double centerY, int radius, bool noCrossTiles = false\) | Npc/nil | 搜索在指定圆形区域内部距离圆心最近的NPC，返回该NPC。若结果不存在，返回nil。noCrossTiles表示是否排除中心到圆心的连线被图格遮挡的NPC。 |
| NpcUtils.SearchNearestEnemy\(double centerX, double centerY, int radius, bool noCrossTiles = false\) | Npc/nil | 搜索在指定圆形区域内部距离圆心最近的敌对NPC，返回该NPC。若结果不存在，返回nil。noCrossTiles表示是否排除中心到圆心的连线被图格遮挡的NPC。 |

## NPC类（Npc Class）

**NPC**类表示具有生物基本信息的非玩家实体类。

在编写NPC AI脚本时，**self表示当前正在操作的NPC类**。

### 父类

该类的父类为[Entity类](entity.md#shi-ti-lei-entity-class)。可直接使用该父类的类成员属性与类成员函数。

### 类成员属性



### 类成员函数

| 函数 | 返回值 | 描述 |
| :--- | :---: | :--- |
| Npc:AddBuff\(int buffID, int buffTime\) | void | 为当前NPC添加一个状态效果。若原状态效果存在，以最长时间为新状态效果的持续时间。 |
| Npc:RemoveBuff\(int buffID\) | void | 移除一个状态效果。 |
| Npc:RemoveAllBuff\(\) | void | 移除全部状态效果。 |
| Npc:HasBuff\(int buffID\) | bool | 返回NPC是否拥有指定状态效果。 |
| Npc:HasAnyBuff\(\) | bool | 返回NPC是否存在状态效果。 |



