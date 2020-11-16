# 抛射物API

抛射物（Projectile）是一类实体，继承自实体（Entity）类，可以使用entity类的成员属性和函数，同时可以使用自己的成员属性和函数。在编写抛射物的Lua文件中，请直接使用self来表示当前正在操作的抛射物。

## 钩子函数

### Init\(\)

抛射物生成时调用一次该函数。

### Update\(tickTime\)

抛射物每帧运行时调用，tickTime为当前抛射物实际生存时间（帧）。

### Kill\(tickTime\)

抛射物死亡时调用一次该函数，tickTime为当前抛射物实际生存时间（帧）。

### OnHitNpc\(target, attack\)

抛射物击中Npc时调用该函数。target为被击中的Npc，attack为攻击数值。

### OnHitPlayer\(target, attack\)

抛射物击中玩家时调用该函数。target为被击中的玩家，attack为攻击数值。

### OnTileCollide\(oldSpeedX, oldSpeedY\)

抛射物击中实心图块时调用该函数。oldSpeedX和oldSpeedY表示击中实心图块前一帧的横向和纵向速度。



