# 方块API

## 钩子函数

请在**方块预设（Block Preset）**脚本中使用这些钩子函数。

### void OnPlayerCollide\(int xi, int yi, Player player, Direction collisionDirection\)

```lua
function OnPlayerCollide(xi, yi, player, collisionDirection)
    
end
```

玩家与当前方块发生碰撞时执行该函数。

* `xi`表示当前方块所在格子横坐标。
* `yi`表示当前方块所在格子纵坐标。
* `player`表示与当前方块碰撞的玩家。

### void OnPlayerOverlap\(int xi, int yi, Player player\)

```lua
function OnPlayerOverlap(xi, yi, player)
    
end
```

玩家与当前方块发生重叠时执行该函数。

* `xi`表示当前方块所在格子横坐标。
* `yi`表示当前方块所在格子纵坐标。
* `player`表示与当前方块重叠的玩家。



