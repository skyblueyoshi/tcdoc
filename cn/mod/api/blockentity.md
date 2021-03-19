# 方块实体API

## 钩子函数（方块实体脚本：contents/block\_entities/...）

### void OnPlaced\(PlaceParameter placeParameter\)

```lua
function OnPlaced(placeParameter)
    
end
```

**【仅服务端调用】**方块实体在服务端被初次放置时调用。

* `placeParameter`表示放置时传递的放置参数类型。

### void OnDestroy\(DestroyParameter DestroyParameter\)

```lua
function OnDestroy(destroyParameter)
    
end
```

**【仅服务端调用】**方块实体在服务端被破坏时调用。

* `destroyParameter`表示发生破坏时传递的破坏参数类型。

### void Update\(\)

```lua
function Update()
    
end
```

**【仅服务端调用】**方块实体在服务端每个事件帧运行时调用。注意，过多且过于复杂的方块实体更新函数可能会导致服务端发生卡顿，应简化设计该函数。

### void OnRandomTick\(\)

```lua
function OnRandomTick()
    
end
```

**【仅服务端调用】**方块实体在服务端触发随机刻时调用。

### void WriteToJson\(Json json\)

```lua
function WriteToJson(json)
    
end
```

**【仅服务端调用】**方块实体在服务端中把自身保存到JSON存档时调用。

* `json`表示将要被写入的JSON。

### void ReadFromJson\(Json json\)

```lua
function ReadFromJson(json)
    
end
```

**【仅服务端调用】**方块实体在服务端中读取JSON存档到自身时调用。

* `json`表示将要被读取的JSON。

