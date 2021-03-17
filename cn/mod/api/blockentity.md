# 方块实体API

## 钩子函数

请在**方块实体**脚本中使用这些钩子函数。**方块实体的所有钩子函数都只在服务端运行。**

### void Update\(\)

```lua
function Update()
    
end
```

**【仅服务端调用】**方块实体在服务端每个事件帧运行时调用。注意，过多且过于复杂的方块实体更新函数可能会导致服务端发生卡顿，应简化设计该函数。

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

