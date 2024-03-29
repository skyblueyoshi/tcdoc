# Data Types and Enums

本篇描述的数据类型、枚举类型在所有的文件均可用。

## Data Types

### ObjectRef（抽象类）

维护指定类型对象的引用。

继承该抽象类的子类：BlockEntityRef。

| 属性            |     类型     | 描述                                                                    |
| ------------- | :--------: | --------------------------------------------------------------------- |
| ObjectRef.ref | Object/nil | <p>读取时返回被引用的对象，若对象不存在则返回nil。</p><p>写入时将对象的引用覆盖到当前引用，写入nil表示写入空引用。</p> |

#### 案例

例如，在如下范例中，`self.modData.blockEntityRef`表示方块实体引用。`blockEntity2`表示某个方块实体对象。

```lua
local br = self.modData.blockEntityRef        -- Get the reference of block entity
local blockEntity = br.ref        -- Get the block entity from reference
if blockEntity ~= nil then
    -- do something
end
br.ref = blockEntity2        -- Set the reference point to blockEntity2
local blockEntity3 = br.ref        -- blockEntity3 is the same object blockEntity2
br.ref = nil        -- Set the renference point to nothing
local blockEntity4 = br.ref        -- blockEntity4 is nil
```

### ArrayList\<T>

TerraCraft内置的动态数组。

| 属性               |  类型 | 描述            |
| ---------------- | :-: | ------------- |
| ArrayList.length | int | **【只读】**数组长度。 |

| 函数                    | 返回值 | 描述                                   |
| --------------------- | :-: | ------------------------------------ |
| ArrayList:GetLength() | int | 返回数组长度。                              |
| ArrayList\[index]     |  T  | 读取或写入指定下标的数组元素。index有效区间为\[1, 可用数量]。 |

#### 遍历方案

```lua
for i = 1, arrayList.length do
    local element = arrayList[i]
    -- do something on this element
end
```

### ExData

拓展数据。在TerraCraft模组中拥有两种拓展数据。

**局部拓展数据（ModData）**为当前使用该数据的对象独有，整个游戏中该对象只拥有一个局部拓展数据。

**全局拓展数据（GlobalData）**为同一类对象均拥有的属性，整个游戏中该对象拥有所有模组的全局拓展数据。

| 属性             |      类型     | 描述        |
| -------------- | :---------: | --------- |
| ExData.xxx     | 由xxx的具体类型决定 | 读写拓展数据。   |
| ExData.xxx\[n] | 由xxx的具体类型决定 | 读写拓展数据数组。 |

| 函数                                |  返回值 | 描述               |
| --------------------------------- | :--: | ---------------- |
| ExData:DataOf(string dataSetName) | bool | 判断当前数据是否拥有指定数据集。 |

#### 案例

1. 某个模组的NPC拥有`GlobalData`，数据为`bool isCold`和`int coldTime`。
2. `npc1`拥有`ModData`，数据为`int timer`和`double targetAngle`。
3. `npc2`拥有`ModData`，数据为`int magicLevel`。
4. `npc3`没有`ModData`。

如下是访问这些数据的范例：

```lua
-- access global data of npc1
local globalData1 = npc1:GetGlobalData()
globalData1.isCold = true
globalData1.coldTime = 32

-- access mod data of npc1
local modData1 = npc1:GetModData()
modData1.timer = modData1.timer + 1
modData1.targetAngle = Utils.PI

-- access global data of npc2
local globalData2 = npc2:GetGlobalData()
globalData2.isCold = false
globalData2.coldTime = 0

-- access mod data of npc2
local modData2 = npc2:GetModData()
modData2.magicLevel = 2

-- access global data of npc3
local globalData3 = npc3:GetGlobalData()
globalData3.isCold = not globalData3.isCold

-- cannot access mod data of npc3
local modData3 = npc3:GetModData()
-- modData3 is nil, cannot read or write data
```

### Point

Represents a point.

| Member  |  Type  | Description                    |
| ------- | :----: | ------------------------------ |
| Point.x | double | The x coordinate of the point. |
| Point.y | double | The y coordinate of the point. |

### Rectangle

Represents an axis-aligned rectangle.

| Member           | Type | Description                                                 |
| ---------------- | :--: | ----------------------------------------------------------- |
| Rectangle.x      |  int | The x coordinate of the upper left corner of the rectangle. |
| Rectangle.y      |  int | The y coordinate of the upper left corner of the rectangle. |
| Rectangle.width  |  int | The width of the rectangle.                                 |
| Rectangle.height |  int | The height of the rectangle.                                |

| Function                                           | Returns | Description          |
| -------------------------------------------------- | :-----: | -------------------- |
| Rectangle:Set(int x, int y, int width, int height) |   void  | Set a new rectangle. |

### SpriteEx

Sprite extension information, has the relevant parameters of drawing.

| Member                  | Type  | Description                                                                                                                                             |
| ----------------------- | ----- | ------------------------------------------------------------------------------------------------------------------------------------------------------- |
| SpriteEx.scaleRateX     | float | \[ default `1.0` ] The horizontal zoom size when the sprite is drawn.                                                                                   |
| SpriteEx.scaleRateY     | float | \[ default `1.0` ] The vertical zoom size when the sprite is drawn.                                                                                     |
| SpriteEx.rotateX        | float | The center point X of the sprite's rotation. If the drawing object is an entity, the default is the center of the entity, otherwise the default is 0.0. |
| SpriteEx.rotateY        | float | The center point Y of the sprite's rotation. If the drawing object is an entity, the default is the center of the entity, otherwise the default is 0.0. |
| SpriteEx.angle          | float | \[ default `0.0` ] The rotation angle when the sprite is drawn.                                                                                         |
| SpriteEx.flipHorizontal | bool  | \[ default `false` ] Whether to flip horizontally when the sprite is drawn.                                                                             |
| SpriteEx.flipVertical   | bool  | \[ default `false` ] Whether to flip vertically when the sprite is drawn.                                                                               |

| Function              | Returns | Description       |
| --------------------- | :-----: | ----------------- |
| SpriteEx:SetDefault() |   void  | Restore Defaults. |

### Hitbox

Represents a collision box. If the `angle` attribute is 0, it means axis aligned collision box (AABB). Otherwise, it represents a collision box rotating around the center point.

| Member         |  Type  | Description                                                                                             |
| -------------- | :----: | ------------------------------------------------------------------------------------------------------- |
| Hitbox.x       | double | The x coordinate of the upper left corner of the hitbox when the rotation angle is 0.                   |
| Hitbox.y       | double | The y coordinate of the upper left corner of the hitbox when the rotation angle is 0.                   |
| Hitbox.width   |   int  | The width of the hitbox.                                                                                |
| Hitbox.height  |   int  | The height of the hitbox.                                                                               |
| Hitbox.centerX | double | **\[ Read-only ]** Returns the center x coordinate of the hitbox.                                       |
| Hitbox.centerY | double | **\[ Read-only ]** Returns the center y coordinate of the hitbox.                                       |
| Hitbox.angle   | double | **\[ Read-only ]** Returns the rotation angle of the collision box if the collision box can be rotated. |

| Function                         | Returns | Description                                                                                      |
| -------------------------------- | :-----: | ------------------------------------------------------------------------------------------------ |
| Hitbox:Overlap(Hitbox other)     |   bool  | Returns whether the current hitbox overlaps with another hitbox.                                 |
| Hitbox:OverlapAABB(Hitbox other) |   bool  | Returns whether the current axis-aligned rectangle overlaps with another axis-aligned rectangle. |

### Attack

表示一个攻击属性。

| 属性               |  类型 | 描述                                                                |
| ---------------- | :-: | ----------------------------------------------------------------- |
| Attack.attack    | int | 攻击值。                                                              |
| Attack.knockBack | int | 攻击的击退值。                                                           |
| Attack.crit      | int | 攻击的百分暴击率。1-100表示1-100%的概率产生双倍暴击伤害，大于100表示总是产生双倍暴击伤害，小于1表示不产生暴击伤害。 |

| 静态函数                                                   |   返回值  | 描述            |
| ------------------------------------------------------ | :----: | ------------- |
| Attack:new\_local(int attack, int knockBack, int crit) | Attack | 返回一个Attack对象。 |

### Defense

表示一个防御属性。

| 属性                        |  类型 | 描述      |
| ------------------------- | :-: | ------- |
| Defense.defense           | int | 防御值。    |
| Defense.blastDefense      | int | 爆炸防御值。  |
| Defense.flameDefense      | int | 火焰防御值。  |
| Defense.projectileDefense | int | 抛掷物防御值。 |
| Defense.breathDefense     | int | 呼吸防御值。  |
| Defense.fallDefense       | int | 摔落防御值。  |
| Defense.knockBackDefense  | int | 击退防御值。  |

### EntityKey

表示一个实体在对应实体类型中的唯一键值。

### Color

Represents a color with four channels of alpha (transparency), red, green, and blue.

| Member      | Type | Description                                                               |
| ----------- | :--: | ------------------------------------------------------------------------- |
| Color.alpha |  int | **\[ Read-only ]** Transparent channel value, valid interval is \[0,255]. |
| Color.red   |  int | **\[ Read-only ]** Red channel value, valid interval is \[0,255].         |
| Color.green |  int | **\[ Read-only ]** Green channel value, valid interval is \[0,255].       |
| Color.blue  |  int | **\[ Read-only ]** Blue channel value, valid interval is \[0,255].        |

| Function                                           | Returns | Description           |
| -------------------------------------------------- | :-----: | --------------------- |
| Color:Set(int alpha, int red, int green, int blue) |   void  | Set new color.        |
| Color:Set(DefaultColor defaultColor)               |   void  | Set color by default. |

### PlaceParameter

放置方块的参数类型。

| 属性                      |     类型    | 描述             |
| ----------------------- | :-------: | -------------- |
| PlaceParameter.placeDir | Direction | **【只读】**放置的朝向。 |

### ClickParameter

点击方块的参数类型。

| 属性                       |     类型    | 描述                 |
| ------------------------ | :-------: | ------------------ |
| ClickParameter.playerRef | PlayerRef | **【只读】**发生点击的玩家引用。 |

### DestroyParameter

破坏方块的参数类型。

| 属性                         |  类型  | 描述                   |
| -------------------------- | :--: | -------------------- |
| DestroyParameter.boom      | bool | **【只读】**是否为由爆炸产生的破坏。 |
| DestroyParameter.silkTouch |  int | **【只读】**破坏时精准采集等级。   |
| DestroyParameter.fortune   |  int | **【只读】**破坏时时运等级。     |

## Enums

注意，这里的枚举值直接当作全局常量使用，且枚举类型的变量只能使用对应枚举值。例如：

```lua
if npc.shape == SHAPE_ROTATE_BOX then
    --do something
end
```

### NetMode

Describe the runtime environment is the client or server.&#x20;

_**Note that the client and built-in server are running at the same time in single mode.**_

| Enum                | Description                        |
| ------------------- | ---------------------------------- |
| _NET\_MODE\_SERVER_ | The runtime environment is server. |
| _NET\_MODE\_CLIENT_ | The runtime environment is client. |

### Direction

Represents what the direction is.

| Enum                | Description |
| ------------------- | ----------- |
| _DIRECTION\_LEFT_   | Left.       |
| _DIRECTION\_TOP_    | Top.        |
| _DIRECTION\_BOTTOM_ | Bottom.     |
| _DIRECTION\_RIGHT_  | Right.      |

### Shape

Represents a shape.

| Enum                 | Description                                           |
| -------------------- | ----------------------------------------------------- |
| _SHAPE\_BOX_         | The shape of the hitbox is an axis-aligned rectangle. |
| _SHAPE\_ROTATE\_BOX_ | The shape of the hitbox is a rotating rectangle.      |

### ItemType

描述物品类型。

| 枚举值                       | 描述        |
| ------------------------- | --------- |
| _ITEM\_TYPE\_NONE_        | 无物品。      |
| _ITEM\_TYPE\_BLOCKS_      | 方块类型物品。   |
| _ITEM\_TYPE\_TOOLS_       | 工具类型物品。   |
| _ITEM\_TYPE\_MATERIALS_   | 材料类型物品。   |
| _ITEM\_TYPE\_WIRES_       | 红石电线类型物品。 |
| _ITEM\_TYPE\_PROJECTILES_ | 抛射物类型物品。  |
| _ITEM\_TYPE\_CHESTS_      | 容器类型物品。   |

### ToolType

描述工具类型。

| 枚举值                        | 描述       |
| -------------------------- | -------- |
| _TOOL\_TYPE\_NONE_         | 无有效工具类型。 |
| _TOOL\_TYPE\_AXE_          | 斧头。      |
| _TOOL\_TYPE\_PICKAXE_      | 镐子。      |
| _TOOL\_TYPE\_SWORD_        | 剑。       |
| _TOOL\_TYPE\_BOW_          | 弓/枪械。    |
| _TOOL\_TYPE\_HELMET_       | 头盔。      |
| _TOOL\_TYPE\_CHESTPLATE_   | 胸甲。      |
| _TOOL\_TYPE\_LEGGINGS_     | 裤腿。      |
| _TOOL\_TYPE\_BOOK_         | 书本。      |
| _TOOL\_TYPE\_SHEARS_       | 剪刀。      |
| _TOOL\_TYPE\_HOE_          | 锄。       |
| _TOOL\_TYPE\_WIRE\_CUTTER_ | 剪线钳。     |
| _TOOL\_TYPE\_DRILL_        | 钻头。      |
| _TOOL\_TYPE\_SAW_          | 锯子。      |
| _TOOL\_TYPE\_STAFF_        | 法杖。      |

### NpcType

描述NPC类型。

| 枚举值                     | 描述        |
| ----------------------- | --------- |
| _NPC\_TYPE\_NORMAL_     | 普通NPC。    |
| _NPC\_TYPE\_ANIMAL_     | 动物类NPC。   |
| _NPC\_TYPE\_VILLAGER_   | 村民类NPC。   |
| _NPC\_TYPE\_ARTHROPODS_ | 节肢类NPC。   |
| _NPC\_TYPE\_SMITE_      | 亡灵类NPC。   |
| _NPC\_TYPE\_BOSS_       | BOSS类NPC。 |

### DefaultColor

Represents default color.

| Enum            | Description               |
| --------------- | ------------------------- |
| _COLOR\_BLACK_  | ARGB=(255, 0, 0, 0)       |
| _COLOR\_WHITE_  | ARGB=(255, 255, 255, 255) |
| _COLOR\_GRAY_   | ARGB=(255, 128, 128, 128) |
| _COLOR\_RED_    | ARGB=(255, 255, 0, 0)     |
| _COLOR\_GREEN_  | ARGB=(255, 0, 255, 0)     |
| _COLOR\_BLUE_   | ARGB=(255, 0, 0, 255)     |
| _COLOR\_YELLOW_ | ARGB=(255, 255, 255, 0)   |

### LightingState

描述客户端光照状态。

| 枚举值                              | 描述      |
| -------------------------------- | ------- |
| _LIGHTING\_STATE\_NORMAL_        | 普通光照状态。 |
| _LIGHTING\_STATE\_NIGHT\_VISION_ | 夜视光照状态。 |
| _LIGHTING\_STATE\_BLINDNESS_     | 失明光照状态。 |

### DeathReason

描述玩家的死亡原因。

| 枚举值                      | 描述        |
| ------------------------ | --------- |
| _DEATH\_REASON\_UNKNOWN_ | 未知原因死亡。   |
| _DEATH\_REASON\_SUICIDE_ | 自杀。       |
| _DEATH\_REASON\_FALL_    | 摔死。       |
| _DEATH\_REASON\_DROWN_   | 淹死。       |
| _DEATH\_REASON\_BOOM_    | 炸死。       |
| _DEATH\_REASON\_BURN_    | 烧死。       |
| _DEATH\_REASON\_LAVA_    | 在岩浆中游泳。   |
| _DEATH\_REASON\_STARVE_  | 饿死。       |
| _DEATH\_REASON\_BUFF_    | 状态效果作用而死。 |
| _DEATH\_REASON\_POISON_  | 毒死。       |

### GameMode

描述玩家或地图的游戏模式。

| 枚举值                     | 描述    |
| ----------------------- | ----- |
| _GAME\_MODE\_SURVIVAL_  | 生存模式。 |
| _GAME\_MODE\_CREATIVE_  | 创造模式。 |
| _GAME\_MODE\_ADVANTURE_ | 冒险模式。 |

### OP

描述玩家的权限等级。

| 枚举值             | 描述         |
| --------------- | ---------- |
| _OP\_ANY_       | 任何人。       |
| _OP\_ADMIN_     | 管理员。       |
| _OP\_MASTER_    | 游戏拥有者（服主）。 |
| _OP\_DEVELOPER_ | 开发者。       |

