# 抛射物API

## 钩子函数

请在抛射物AI脚本中使用这些钩子函数。

### void Init\(\)

```lua
function Init()
    --init current projectile here
end
```

抛射物生成时调用一次该函数。

### void Update\(int tickTime\)

```lua
function Update(tickTime)
    --update every game loop
end
```

抛射物每帧运行时调用，您可以在该函数内编写运动等逻辑。

* `tickTime`为总生存时间（帧）。

### void PreUpdate\(int tickTime\)

```lua
function ReadyUpdate(tickTime)
    --update every game loop
end
```

抛射物每帧运行`Update(tickTime)`函数前调用。通常用于在使用AI重用后在原逻辑前插入新逻辑。

* `tickTime`为总生存时间（帧）。

### void PostUpdate\(int tickTime\)

```lua
function PostUpdate(tickTime)
    --update every game loop
end
```

抛射物每帧运行`Update(tickTime)`函数后调用。通常用于在使用AI重用后追加逻辑。

* `tickTime`为总生存时间（帧）。

### void OnDraw\(int tickTime\)

```lua
function OnDraw(tickTime)
    --change the sprite parameters before drawing every game loop
end
```

抛射物每帧绘制前调用，在该函数内编写自定义绘制属性。不使用该钩子函数时采取默认处理方式。

* `tickTime`为总生存时间（帧）。

### void OnKilled\(int tickTime\)

```lua
function OnKilled(tickTime)
    --do something when projectile is killed
end
```

抛射物死亡时调用一次该函数。

* `tickTime`为总生存时间（帧）。

### void ModifyHitNpc\(Npc npc, Attack hitAttack\)

```lua
function ModifyHitNpc(npc, hitAttack)
    --modify this attack value when projectile hit a npc
end
```

抛射物击中Npc前调用该函数，通常用于修改`hitAttack`来实现攻击数据自定义。

* `npc`为被击中的NPC对象。
* `hitAttack`为攻击属性（见[Attack数据类型](datatypes-enums-constants.md#attack)）。

### void OnHitNpc\(Npc npc, Attack hitAttack\)

```lua
function OnHitNpc(npc, hitAttack)
    --do something when projectile hit a npc
end
```

抛射物击中Npc时调用该函数。

* `npc`为被击中的NPC对象。
* `hitAttack`为攻击属性。

### void ModifyHitPlayer\(Player player, Attack hitAttack\)

```lua
function ModifyHitPlayer(player, hitAttack)
    --modify this attack value projectile hit a player
end
```

抛射物击中玩家前调用该函数，通常用于修改`hitAttack`来实现攻击数据自定义。

* `player`为被击中的玩家对象。
* `hitAttack`为攻击属性。

### void OnHitPlayer\(Player player, Attack hitAttack\)

```lua
function OnHitPlayer(player, hitAttack)
    --do something when projectile hit a player
end
```

抛射物击中玩家时调用该函数。

* `player`为被击中的玩家对象。
* `hitAttack`为攻击属性。

### void OnTileCollide\(double oldSpeedX, double oldSpeedY\)

```lua
function OnTileCollide(oldSpeedX, oldSpeedY)
    --do something when projectile hit tiles
end
```

抛射物击中实心图块时调用该函数。

* `oldSpeedX`和`oldSpeedY`表示击中实心图块前一帧的横向和纵向速度。

## 抛射物类（Projectile Class）

**抛射物（Projectile）**类表示具有抛射物基本信息的实体类。通常用于表示弓箭、子弹、弹幕等实体对象。

在编写抛射物AI脚本时，**self表示当前正在操作的抛射物类**。

### 父类

该类的父类为[Entity类](entity.md#shi-ti-lei-entity-class)。可直接使用该父类的类成员属性与类成员函数。

### 类成员属性



### 类成员函数

| 函数 | 返回值 | 描述 |
| :--- | :---: | :--- |
| Projectile:Kill\(\) | void | 清除当前抛射物对象。 |
| Projectile:GetPlayerOwner\(\) | Player/nil | 若当前抛射物的玩家拥有者存在且存活，返回该玩家对象，否则返回nil。 |
| Projectile:GetNpcOwner\(\) | Npc/nil | 若当前抛射物的NPC拥有着存在且存活，返回该NPC对象，否则返回nil。 |
| Projectile:GetPlayerTarget\(\) | Player/nil | 若当前抛射物的玩家锁定目标存在且存活，返回该玩家对象，否则返回nil。 |
| Projectile:GetNpcTarget\(\) | Npc/nil | 若当前抛射物的NPC锁定目标存在且存活，返回该NPC对象，否则返回nil。 |
| Projectile:SetPlayerTarget\(Player player\) | void | 设定当前抛射物的玩家锁定目标。 |
| Projectile:SetNpcTarget\(Npc npc\) | void | 设定当前抛射物的NPC锁定目标。 |

