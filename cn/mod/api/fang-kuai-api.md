# 方块API

## 钩子函数

请在**方块预设（Block Preset）**脚本中使用这些钩子函数。

### void Init\(int xi, int yi, Player player, Direction collisionDirection\)

```lua
function OnCollidePlayer(xi, yi, player, collisionDirection)
    
end
```

玩家与当前方块发生碰撞时执行该函数。

* `xi`表示当前方块所在格子横坐标。
* `yi`表示当前方块所在格子纵坐标。
* `player`表示与当前方块碰撞的玩家。
* `collisionDirection`表示方块被碰撞面的朝向。

