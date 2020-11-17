# 抛射物API

抛射物（Projectile）是一类实体，继承自实体（Entity）类，可以使用entity类的成员属性和函数，同时可以使用自己的成员属性和函数。在编写抛射物的Lua文件中，请直接使用self来表示当前正在操作的抛射物。

## 钩子函数

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

抛射物每帧运行时调用，tickTime为当前抛射物实际生存时间（帧）。

### void OnKilled\(int tickTime\)

```lua
function OnKilled(tickTime)
    --do something when projectile is killed
end
```

抛射物死亡时调用一次该函数，tickTime为当前抛射物实际生存时间（帧）。

### void OnHitNpc\(Npc target, Attack attack\)

```lua
function OnHitNpc(target, attack)
    --do something when projectile hit a npc
end
```

抛射物击中Npc时调用该函数。target为被击中的Npc，attack为攻击数值。

### void OnHitPlayer\(Player target, Attack attack\)

```lua
function OnHitPlayer(target, attack)
    --do something when projectile hit a player
end
```

抛射物击中玩家时调用该函数。target为被击中的玩家，attack为攻击数值。

### void OnTileCollide\(double oldSpeedX, double oldSpeedY\)

```lua
function OnTileCollide(oldSpeedX, oldSpeedY)
    --do something when projectile hit tiles
end
```

抛射物击中实心图块时调用该函数。oldSpeedX和oldSpeedY表示击中实心图块前一帧的横向和纵向速度。



