# 抛射物API

## 钩子函数（抛射物脚本：contents/projectile\_ai/...）

### void Init\(\)

```lua
function Init()
    
end
```

抛射物生成时调用一次该函数。

### void Update\(\)

```lua
function Update()
    
end
```

抛射物每帧运行时调用，您可以在该函数内编写运动等逻辑。

### void PreUpdate\(\)

```lua
function ReadyUpdate()
    
end
```

抛射物每帧运行`Update()`函数前调用。通常用于在使用AI重用后在原逻辑前插入新逻辑。

### void PostUpdate\(\)

```lua
function PostUpdate()
    
end
```

抛射物每帧运行`Update()`函数后调用。通常用于在使用AI重用后追加逻辑。

### void OnDraw\(\)

```lua
function OnDraw()
    
end
```

抛射物每帧绘制前调用，在该函数内编写自定义绘制属性。不使用该钩子函数时采取默认处理方式。

### void OnKilled\(\)

```lua
function OnKilled()
    
end
```

抛射物死亡时调用一次该函数。

### void ModifyHitNpc\(Npc npc, Attack hitAttack\)

```lua
function ModifyHitNpc(npc, hitAttack)
    
end
```

抛射物击中Npc前调用该函数，通常用于修改`hitAttack`来实现攻击数据自定义。

* `npc`为被击中的NPC对象。
* `hitAttack`为攻击属性（见[Attack数据类型](type.md#attack)）。

### void OnHitNpc\(Npc npc, Attack hitAttack\)

```lua
function OnHitNpc(npc, hitAttack)
    
end
```

抛射物击中Npc时调用该函数。

* `npc`为被击中的NPC对象。
* `hitAttack`为攻击属性。

### void ModifyHitPlayer\(Player player, Attack hitAttack\)

```lua
function ModifyHitPlayer(player, hitAttack)
    
end
```

抛射物击中玩家前调用该函数，通常用于修改`hitAttack`来实现攻击数据自定义。

* `player`为被击中的玩家对象。
* `hitAttack`为攻击属性。

### void OnHitPlayer\(Player player, Attack hitAttack\)

```lua
function OnHitPlayer(player, hitAttack)
    
end
```

抛射物击中玩家时调用该函数。

* `player`为被击中的玩家对象。
* `hitAttack`为攻击属性。

### void OnTileCollide\(double oldSpeedX, double oldSpeedY\)

```lua
function OnTileCollide()
    
end
```

抛射物击中实心图块时调用该函数。

* `oldSpeedX`和`oldSpeedY`表示击中实心图块前一帧的横向和纵向速度。

## 抛射物通用模块（ProjectileUtils）

| 函数 | 返回值 | 描述 |
| :--- | :---: | :--- |
| ProjectileUtils.Create\(int id, double centerX, double centerY, double speedX = 0.0, double speedY = 0.0, Attack attack = Attack:new\(0, 0, 0\)\) | Projectile | 创建一个抛射物实体，返回创建好的抛射物实体。 `id`：抛射物ID。`centerX`和`centerY`：创建抛射物的中心点。`speedX`和`speedY`：初始运动速度。`Attack`：抛射物的基础攻击力。 |
| ProjectileUtils.CreateFromPlayer\(Player playerOwner, int id, double centerX, double centerY, double speedX = 0.0, double speedY = 0.0, Attack attack = Attack:new\(0, 0, 0\)\) | Projectile | 创建一个以指定玩家为拥有者的抛射物实体，返回创建好的抛射物实体。 |
| ProjectileUtils.CreateFromNpc\(Npc npcOwner, int id, double centerX, double centerY, double speedX = 0.0, double speedY = 0.0, Attack attack = Attack:new\(0, 0, 0\)\) | Projectile | 创建一个以指定NPC为拥有者的抛射物实体，返回创建好的抛射物实体。 |
| ProjectileUtils.SearchByRect\(double x, double y, int width, int height\) | ArrayList&lt;Projectile&gt; | 返回包含于指定矩形区域内部的所有抛射物列表。 |
| ProjectileUtils.SearchByCircle\(double centerX, double centerY, int radius\) | ArrayList&lt;Projectile&gt; | 返回包含于指定圆形区域内部的所有抛射物列表。 |
| ProjectileUtils.SearchNearestProjectile\(double centerX, double centerY, int radius, bool noCrossTiles = false\) | Projectile/nil | 搜索在指定圆形区域内部距离圆心最近的抛射物，返回该抛射物。若结果不存在，返回nil。`noCrossTiles`表示是否排除中心到圆心的连线被图格遮挡的抛射物。 |

## 抛射物类（Projectile Class，继承自Entity Class）

**抛射物（Projectile）**类表示具有抛射物基本信息的实体类。通常用于表示弓箭、子弹、弹幕等实体对象。

在编写抛射物AI脚本时，**self表示当前正在操作的抛射物类**。

### 父类

该类的父类为[Entity类](entity.md#shi-ti-lei-entity-class)。可直接使用该父类的类成员属性与类成员函数。

### 类成员属性

| 属性 | 类型 | 描述 |
| :--- | :---: | :--- |
| Projectile.id | int | **【只读】**当前抛射物的动态ID。 |
| Projectile.baseAttack | Attack | 当前抛射物的基础攻击属性。一般由创建时给定。 |
| Projectile.targetTime | int | 当前抛射物的目标时间。一般由创建时给定，通常用于实现达到目标时间后触发相关逻辑。 |
| Projectile.isCheckNpc | bool | 当前抛射物是否作用于NPC。一般由创建时指定，默认为false，决定是否碰撞、伤害NPC。 |
| Projectile.isCheckPlayer | bool | 当前抛射物是否作用于玩家。一般由创建时指定，默认为false，决定是否碰撞、伤害玩家。 |
| Projectile.maxSpeed | double | **【只读】**当前抛射物最大移动速度。 |
| Projectile.hots\[4\] | Point | **【只读】**当前抛射物的热固定点。允许读取最多4个热固定点。 |
| Projectile.state | int | 抛射物当前在简单有限状态机中的状态。 |
| Projectile.stateTimer | int | 抛射物的状态机计时器。 |
| Projectile.modData | ExData | 抛射物当前模组自定义模组数据。 |

### 类成员函数

| 函数 | 返回值 | 描述 |
| :--- | :---: | :--- |
| Projectile:Kill\(\) | void | 清除当前抛射物对象。 |
| Projectile:GetPlayerOwner\(\) | Player/nil | 若当前抛射物的玩家拥有者存在且存活，返回该玩家对象，否则返回nil。 |
| Projectile:GetNpcOwner\(\) | Npc/nil | 若当前抛射物的NPC拥有者存在且存活，返回该NPC对象，否则返回nil。 |
| Projectile:GetPlayerTarget\(\) | Player/nil | 若当前抛射物的玩家锁定目标存在且存活，返回该玩家对象，否则返回nil。 |
| Projectile:GetNpcTarget\(\) | Npc/nil | 若当前抛射物的NPC锁定目标存在且存活，返回该NPC对象，否则返回nil。 |
| Projectile:SetPlayerTarget\(Player player\) | void | 设定当前抛射物的玩家锁定目标。 |
| Projectile:SetNpcTarget\(Npc npc\) | void | 设定当前抛射物的NPC锁定目标。 |

