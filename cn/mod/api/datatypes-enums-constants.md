# 数据类型、枚举类型

本篇描述的数据类型、枚举类型在所有的文件均可用。

## 数据类型（Data Types）

### JSON

| 静态函数 | 返回值 | 描述 |
| :--- | :---: | :--- |
| Json:new\_local\(\) | Attack | 返回一个JSON对象。 |

| 函数 | 返回值 | 描述 |
| :--- | :---: | :--- |
| Json:SetInt\(string key, int value\) | void | 写入字符串键和整数值。 |
| Json:SetInt\(int value\) | void | 写入整数。 |
| Json:SetDouble\(string key, double value\) | void | 写入字符串键和浮点数值。 |
| Json:SetDouble\(double value\) | void | 写入浮点数值。 |
| Json:SetBoolean\(string key, bool value\) | void | 写入字符串键和布尔值。 |
| Json:SetBoolean\(bool value\) | void | 写入布尔值。 |
| Json:SetString\(string key, string value\) | void | 写入字符串键和字符串值。 |
| Json:SetString\(string value\) | void | 写入字符串值。 |
|  |  |  |
|  |  |  |
|  |  |  |
|  |  |  |
| Json:GetInt\(string key\) | int | 由字符串键读取整数值，若键值对不存在或值非整数类型，总是返回0。 |
| Json:GetInt\(\) | int | 读取整数值，若不存在或非整数类型，总是返回0。 |
| Json:GetDouble\(string key\) | double | 由字符串键读取浮点数值，若键值对不存在或值非浮点数类型，总是返回0.0。 |
| Json:GetDouble\(\) | double | 由读取浮点数值，若不存在或非浮点数类型，总是返回0.0。 |
| Json:GetBoolean\(string key\) | bool | 由字符串键读取布尔值，若键值对不存在或值非布尔类型，总是返回false。 |
| Json:GetBoolean\(\) | bool | 由读取布尔值，若不存在或非布尔类型，总是返回false。 |
| Json:GetString\(string key\) | string | 由字符串键读取字符串值，若键值对不存在或值非字符串类型，总是返回空字符串。 |
| Json:GetString\(\) | string | 由读取字符串值，若不存在或非字符串类型，总是返回空字符串。 |
|  |  |  |
|  |  |  |
|  |  |  |

### ArrayList&lt;T&gt;

TerraCraft内置的动态数组。

| 属性 | 类型 | 描述 |
| :--- | :---: | :--- |
| ArrayList.length | int | **【只读】**数组长度。 |

| 函数 | 返回值 | 描述 |
| :--- | :---: | :--- |
| ArrayList:GetLength\(\) | int | 返回数组长度。 |
| ArrayList\[index\] | T | 读取或写入指定下标的数组元素。index有效区间为\[1, 可用数量\]。 |

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

| 属性 | 类型 | 描述 |
| :--- | :---: | :--- |
| ExData.xxx | 由xxx的具体类型决定 | 读写拓展数据。 |
| ExData.xxx\[n\] | 由xxx的具体类型决定 | 读写拓展数据数组。 |

| 函数 | 返回值 | 描述 |
| :--- | :---: | :--- |
| ExData:DataOf\(string dataSetName\) | bool | 判断当前数据是否拥有指定数据集。 |

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

表示一个点。

| 属性 | 类型 | 描述 |
| :--- | :---: | :--- |
| Point.x | double | 点的横坐标。 |
| Point.y | double | 点的纵坐标。 |

### Rectangle

表示一个轴对齐矩形。

| 属性 | 类型 | 描述 |
| :--- | :---: | :--- |
| Rectangle.x | int | 矩形左上角横坐标。 |
| Rectangle.y | int | 矩形左上角纵坐标。 |
| Rectangle.width | int | 矩形宽度。 |
| Rectangle.height | int | 矩形高度。 |

| 函数 | 返回值 | 描述 |
| :--- | :---: | :--- |
| Rectangle:Set\(int x, int y, int width, int height\) | void | 设置新的矩形。 |

### SpriteEx

绘制拓展信息，决定绘制的相关参数。

| 属性 | 类型 | 描述 |
| :--- | :--- | :--- |
| SpriteEx.scaleRateX | float | 贴图绘制时横向缩放尺寸。（默认为1.0） |
| SpriteEx.scaleRateY | float | 贴图绘制时纵向缩放尺寸。（默认为1.0） |
| SpriteEx.rotateX | float | 贴图的旋转中心点X。（若绘制对象为实体，默认为实体中心，否则默认为0.0） |
| SpriteEx.rotateY | float | 贴图的旋转中心点Y。（若绘制对象为实体，默认为实体中心，否则默认为0.0） |
| SpriteEx.angle | float | 贴图绘制时的旋转角度。（默认为0.0） |
| SpriteEx.flipHorizontal | bool | 贴图绘制时是否水平翻转。（默认为false） |
| SpriteEx.flipVertical | bool | 贴图绘制时是否竖直翻转。（默认为false） |

| 函数 | 返回值 | 描述 |
| :--- | :---: | :--- |
| SpriteEx:SetDefault\(\) | void | 恢复默认值。 |

### Hitbox

表示一个碰撞箱。若`angle`属性为0，表示轴对齐碰撞箱（AABB）。否则表示一个绕中心点旋转的碰撞箱。

| 属性 | 类型 | 描述 |
| :--- | :---: | :--- |
| Hitbox.x | double | 碰撞箱在旋转角度为0时左上角横坐标。 |
| Hitbox.y | double | 碰撞箱在旋转角度为0时左上角纵坐标。 |
| Hitbox.width | int | 碰撞箱的宽度。 |
| Hitbox.height | int | 碰撞箱的高度。 |
| Hitbox.centerX | double | **【只读】**碰撞箱中心点的横坐标。 |
| Hitbox.centerY | double | **【只读】**碰撞箱中心点的纵坐标。 |
| Hitbox.angle | double | 若碰撞箱可以旋转，表示碰撞箱的旋转角度。 |

| 函数 | 返回值 | 描述 |
| :--- | :---: | :--- |
| Hitbox:Overlap\(Hitbox other\) | bool | 返回当前碰撞箱与另一个碰撞箱是否重叠。 |
| Hitbox:OverlapAABB\(Hitbox other\) | bool | 返回当前轴对齐矩形与另一个轴对齐矩形是否重叠。 |

### Attack

表示一个攻击属性。

| 属性 | 类型 | 描述 |
| :--- | :---: | :--- |
| Attack.attack | int | 攻击值。 |
| Attack.knockBack | int | 攻击的击退值。 |
| Attack.crit | int | 攻击的百分暴击率。1-100表示1-100%的概率产生双倍暴击伤害，大于100表示总是产生双倍暴击伤害，小于1表示不产生暴击伤害。 |

| 静态函数 | 返回值 | 描述 |
| :--- | :---: | :--- |
| Attack:new\_local\(int attack, int knockBack, int crit\) | Attack | 返回一个Attack对象。 |

### Defense

表示一个防御属性。

| 属性 | 类型 | 描述 |
| :--- | :---: | :--- |
| Defense.defense | int | 防御值。 |
| Defense.blastDefense | int | 爆炸防御值。 |
| Defense.flameDefense | int | 火焰防御值。 |
| Defense.projectileDefense | int | 抛掷物防御值。 |
| Defense.breathDefense | int | 呼吸防御值。 |
| Defense.fallDefense | int | 摔落防御值。 |
| Defense.knockBackDefense | int | 击退防御值。 |

### EntityKey

表示一个实体在对应实体类型中的唯一键值。

### Color

表示一个具有Alpha（透明度）、Red、Green、Blue四个通道的颜色。每个通道有效值为\[0, 255\]。

通道分量属性均只读，请通过Set函数来设置颜色的值。

| 属性 | 类型 | 描述 |
| :--- | :---: | :--- |
| Color.alpha | int | **【只读】**透明通道分量。 |
| Color.red | int | **【只读】**红色通道分量。 |
| Color.green | int | **【只读】**绿色通道分量。 |
| Color.blue | int | **【只读】**蓝色通道分量。 |

| 函数 | 返回值 | 描述 |
| :--- | :---: | :--- |
| Color:Set\(int alpha, int red, int green, int blue\) | void | 设置新的颜色。 |
| Color:Set\(DefaultColor defaultColor\) | void | 设置为指定默认颜色。 |

## 枚举类型（Enums）

注意，这里的枚举值直接当作全局常量使用，且枚举类型的变量只能使用对应枚举值。例如：

```lua
if npc.shape == SHAPE_ROTATE_BOX then
    --do something
end
```

### NetMode

描述当前脚本为客户端或者服务端。注意单人模式下客户端和内置服务端是同时运行的。

| 枚举值 | 描述 |
| :--- | :--- |
| _NET\_MODE\_SERVER_ | 当前脚本为服务端环境。 |
| _NET\_MODE\_CLIENT_ | 当前脚本为客户端环境。 |

### Direction

描述方向。

| 枚举值 | 描述 |
| :--- | :--- |
| _DIRECTION\_LEFT_ | 左边。 |
| _DIRECTION\_TOP_ | 上面。 |
| _DIRECTION\_BOTTOM_ | 下面。 |
| _DIRECTION\_RIGHT_ | 右边。 |

### Shape

描述形状类型。

| 枚举值 | 描述 |
| :--- | :--- |
| _SHAPE\_BOX_ | 碰撞箱形状为轴对齐矩形。 |
| _SHAPE\_ROTATE\_BOX_ | 碰撞箱形状为旋转矩形。 |

### ItemType

描述物品类型。

| 枚举值 | 描述 |
| :--- | :--- |
| _ITEM\_TYPE\_NONE_ | 无物品。 |
| _ITEM\_TYPE\_BLOCKS_ | 方块类型物品。 |
| _ITEM\_TYPE\_TOOLS_ | 工具类型物品。 |
| _ITEM\_TYPE\_MATERIALS_ | 材料类型物品。 |
| _ITEM\_TYPE\_WIRES_ | 红石电线类型物品。 |
| _ITEM\_TYPE\_PROJECTILES_ | 抛射物类型物品。 |
| _ITEM\_TYPE\_CHESTS_ | 容器类型物品。 |

### ToolType

描述工具类型。

| 枚举值 | 描述 |
| :--- | :--- |
| _TOOL\_TYPE\_NONE_ | 无有效工具类型。 |
| _TOOL\_TYPE\_AXE_ | 斧头。 |
| _TOOL\_TYPE\_PICKAXE_ | 镐子。 |
| _TOOL\_TYPE\_SWORD_ | 剑。 |
| _TOOL\_TYPE\_BOW_ | 弓/枪械。 |
| _TOOL\_TYPE\_HELMET_ | 头盔。 |
| _TOOL\_TYPE\_CHESTPLATE_ | 胸甲。 |
| _TOOL\_TYPE\_LEGGINGS_ | 裤腿。 |
| _TOOL\_TYPE\_BOOK_ | 书本。 |
| _TOOL\_TYPE\_SHEARS_ | 剪刀。 |
| _TOOL\_TYPE\_HOE_ | 锄。 |
| _TOOL\_TYPE\_WIRE\_CUTTER_ | 剪线钳。 |
| _TOOL\_TYPE\_DRILL_ | 钻头。 |
| _TOOL\_TYPE\_SAW_ | 锯子。 |
| _TOOL\_TYPE\_STAFF_ | 法杖。 |

### NpcType

描述NPC类型。

| 枚举值 | 描述 |
| :--- | :--- |
| _NPC\_TYPE\_NORMAL_ | 普通NPC。 |
| _NPC\_TYPE\_ANIMAL_ | 动物类NPC。 |
| _NPC\_TYPE\_VILLAGER_ | 村民类NPC。 |
| _NPC\_TYPE\_ARTHROPODS_ | 节肢类NPC。 |
| _NPC\_TYPE\_SMITE_ | 亡灵类NPC。 |
| _NPC\_TYPE\_BOSS_ | BOSS类NPC。 |

### DefaultColor

描述默认颜色。

| 枚举值 | 描述 |
| :--- | :--- |
| _COLOR\_BLACK_ | 黑色。ARGB=\(255, 0, 0, 0\) |
| _COLOR\_WHITE_ | 白色。ARGB=\(255, 2555, 255, 255\) |
| _COLOR\_GRAY_ | 灰色。ARGB=\(255, 128, 128, 128\) |
| _COLOR\_RED_ | 红色。ARGB=\(255, 255, 0, 0\) |
| _COLOR\_GREEN_ | 绿色。ARGB=\(255, 0, 255, 0\) |
| _COLOR\_BLUE_ | 蓝色。ARGB=\(255, 0, 0, 255\) |
| _COLOR\_YELLOW_ | 黄色。ARGB=\(255, 255, 255, 0\) |

### LightingState

描述客户端光照状态。

| 枚举值 | 描述 |
| :--- | :--- |
| _LIGHTING\_STATE\_NORMAL_ | 普通光照状态。 |
| _LIGHTING\_STATE\_NIGHT\_VISION_ | 夜视光照状态。 |
| _LIGHTING\_STATE\_BLINDNESS_ | 失明光照状态。 |

### DeathReason

描述玩家的死亡原因。

| 枚举值 | 描述 |
| :--- | :--- |
| _DEATH\_REASON\_UNKNOWN_ | 未知原因死亡。 |
| _DEATH\_REASON\_SUICIDE_ | 自杀。 |
| _DEATH\_REASON\_FALL_ | 摔死。 |
| _DEATH\_REASON\_DROWN_ | 淹死。 |
| _DEATH\_REASON\_BOOM_ | 炸死。 |
| _DEATH\_REASON\_BURN_ | 烧死。 |
| _DEATH\_REASON\_LAVA_ | 在岩浆中游泳。 |
| _DEATH\_REASON\_STARVE_ | 饿死。 |
| _DEATH\_REASON\_BUFF_ | 状态效果作用而死。 |
| _DEATH\_REASON\_POISON_ | 毒死。 |

### GameMode

描述玩家或地图的游戏模式。

| 枚举值 | 描述 |
| :--- | :--- |
| _GAME\_MODE\_SURVIVAL_ | 生存模式。 |
| _GAME\_MODE\_CREATIVE_ | 创造模式。 |
| _GAME\_MODE\_ADVANTURE_ | 冒险模式。 |

### OP

描述玩家的权限等级。

| 枚举值 | 描述 |
| :--- | :--- |
| _OP\_ANY_ | 任何人。 |
| _OP\_ADMIN_ | 管理员。 |
| _OP\_MASTER_ | 游戏拥有者（服主）。 |
| _OP\_DEVELOPER_ | 开发者。 |



