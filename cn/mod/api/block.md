# 方块API

## 钩子函数（方块预设脚本：contents/block\_presets/...）

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

### void OnRandomTick\(int xi, int yi\)

```lua
function OnRandomTick(xi, yi)
    
end
```

**【仅服务端调用】**当前方块在服务端被随机刻选中时执行。

* `xi`表示当前方块所在格子横坐标。
* `yi`表示当前方块所在格子纵坐标。

### void OnPlaced\(int xi, int yi, PlaceParameter placeParameter\)

```lua
function OnPlaced(xi, yi, placeParameter)
    
end
```

**【仅服务端调用】**当前方块在服务端被放置时执行。

* `xi`表示当前方块所在格子横坐标。
* `yi`表示当前方块所在格子纵坐标。
* `placeParameter`表示放置方块附加的信息参数。

### void OnDestroy\(int xi, int yi, DestroyParameter destroyParameter\)

```lua
function OnDestroy(xi, yi, destroyParameter)
    
end
```

**【仅服务端调用】**当前方块在服务端被破坏前执行。

* `xi`表示当前方块所在格子横坐标。
* `yi`表示当前方块所在格子纵坐标。
* `destroyParameter`表示破坏方块附加的信息参数。

### void OnClicked\(int xi, int yi, ClickParameter clickParameter\)

```lua
function OnClicked(xi, yi, clickParameter)
    
end
```

**【仅服务端调用】**当前方块在服务端被玩家右键点击时执行。

* `xi`表示当前方块所在格子横坐标。
* `yi`表示当前方块所在格子纵坐标。
* `placeParameter`表示右键点击方块附加的信息参数。

### void OnSignal\(int xi, int yi, bool isActivated\)

```lua
function OnSignal(xi, yi, isActivated)
    
end
```

**【仅服务端调用】**当前方块在服务端被红石信号触发时执行。

* `xi`表示当前方块所在格子横坐标。
* `yi`表示当前方块所在格子纵坐标。
* `isActivated`表示红石信号是否为激活信号，若为否，表示反激活信号。

### void UpdateScreen\(int xi, int yi\)

```lua
function UpdateScreen(xi, yi)
    
end
```

**【仅客户端调用】**当前方块在客户端的屏幕内时执行。

* `xi`表示当前方块所在格子横坐标。
* `yi`表示当前方块所在格子纵坐标。

### void RenderFurniture\(int xi, int yi, int tickTime\)

```lua
function RenderFurniture(int xi, int yi, tickTime)
    
end
```

**【仅客户端调用】**当前家具在客户端被绘制时调用该函数，用来决定家具的绘制方式。

* `xi`表示当前方块所在格子横坐标。
* `yi`表示当前方块所在格子纵坐标。
* `tickTime`表示客户端全局渲染时间。

### void PreRenderFurniture\(int xi, int yi, int tickTime\)

```lua
function PreRenderFurniture(int xi, int yi, tickTime)
    
end
```

**【仅客户端调用】**允许在绘制家具前绘制自定义内容。

### void PostRenderFurniture\(int xi, int yi, int tickTime\)

```lua
function PostRenderFurniture(int xi, int yi, tickTime)
    
end
```

**【仅客户端调用】**允许在绘制家具后绘制自定义内容。

## 方块通用模块（BlockUtils）

#### 数值函数

| 函数 | 返回值 | 描述 |
| :--- | :---: | :--- |
| Block.GetGroupID\(int blockID\) | int | 返回指定方块ID的方块组ID。 |
| Block.GetSubGroupID\(int blockID\) | int | 返回指定方块ID的方块子组ID。 |

