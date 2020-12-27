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

### void UpdateScreen\(int xi, int yi\)

```lua
function UpdateScreen(xi, yi)
    
end
```

当前方块在客户端的屏幕内时执行。

* `xi`表示当前方块所在格子横坐标。
* `yi`表示当前方块所在格子纵坐标。

### void RenderFurniture\(int xi, int yi, SpriteRenderer spriteRenderer, int tickTime\)

```lua
function RenderFurniture(int xi, int yi, spriteRenderer, tickTime)
    
end
```

当前家具在客户端被绘制时调用该函数，用来决定家具的绘制方式。

* `xi`表示当前方块所在格子横坐标。
* `yi`表示当前方块所在格子纵坐标。
* `spriteRenderer`表示精灵渲染器。
* `tickTime`表示客户端全局渲染时间。

### void PreRenderFurniture\(int xi, int yi, SpriteRenderer spriteRenderer, int tickTime\)

```lua
function PreRenderFurniture(int xi, int yi, spriteRenderer, tickTime)
    
end
```

绘制当前家具前调用该函数，用来在绘制家具前绘制自定义内容。

### void PostRenderFurniture\(int xi, int yi, SpriteRenderer spriteRenderer, int tickTime\)

```lua
function PostRenderFurniture(int xi, int yi, spriteRenderer, tickTime)
    
end
```

绘制完当前家具后调用该函数，用来在绘制家具后绘制自定义内容。

