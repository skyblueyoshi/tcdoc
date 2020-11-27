# 数据类型、枚举类型

本篇描述的数据类型、枚举类型在所有的文件均可用。

## 数据类型（Data Types）

### ArrayList&lt;T&gt;

TerraCraft内置的动态数组。

| 函数 | 返回值 | 描述 |
| :--- | :---: | :--- |
| ArrayList:GetLength\(\) | int | 返回数组长度。 |
| ArrayList\[index\] | T | 读取或写入指定下标的数组元素。index有效区间为\[1, 可用数量\]。 |

#### 遍历方案

```lua
for i = 1, arrayList:GetLength() do
    local element = arrayList[i]
    -- do something on this element
end
```

### UserVar&lt;T&gt;

用户自定义数据，用于在脚本中实现自定义变量。`T`可以为`int`类型或者`double`类型，可用16个数据。

| 函数 | 返回值 | 描述 |
| :--- | :---: | :--- |
| UserVar\[index\] | T | 读取或写入指定下标index的用户自定义数据。index有效区间为\[1, 16\]。 |

#### 使用例

```lua
self.ivar[1] = 123
self.ivar[4] = 456
self.ivar[6] = self.ivar[1]
self.dvar[1] = 1.0
self.dvar[4] = self.dvar[4] + 1.0
```

### Flags

用户自定义布尔值数据，用于在脚本中实现自定义布尔值变量。可用64个数据。

| 函数 | 返回值 | 描述 |
| :--- | :---: | :--- |
| Flags\[index\] | bool | 读取或写入指定下标index的用户自定义布尔值数据。index有效区间为\[1, 64\]。 |

#### 使用例

```lua
self.flags[1] = true
self.flags[2] = false
self.flags[3] = self.flags[1]
if (self.flags[3]) then
    -- do something
end
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

### SpriteEx

绘制拓展信息，决定绘制的相关参数。

| 属性 | 类型 | 描述 |
| :--- | :--- | :--- |
| SpriteEx.scaleRateX | float | 贴图绘制时横向缩放尺寸。（默认为1.0） |
| SpriteEx.scaleRateY | float | 贴图绘制时纵向缩放尺寸。（默认为1.0） |
| SpriteEx.rotateX | float | 贴图的旋转中心点X。（若绘制对象为实体，默认为实体中心） |
| SpriteEx.rotateY | float | 贴图的旋转中心点Y。（若绘制对象为实体，默认为实体中心） |
| SpriteEx.angle | float | 贴图绘制时的旋转角度。（默认为0.0） |
| SpriteEx.flipHorizontal | bool | 贴图绘制时是否水平翻转。（默认为false） |
| SpriteEx.flipVertical | bool | 贴图绘制时是否竖直翻转。（默认为false） |

### Hitbox

表示一个碰撞箱。若`angle`属性为0，表示轴对齐碰撞箱（AABB）。否则表示一个绕中心点旋转的碰撞箱。

| 属性 | 类型 | 描述 |
| :--- | :---: | :--- |
| Hitbox.x | double | 碰撞箱在旋转角度为0时左上角横坐标。 |
| Hitbox.y | double | 碰撞箱在旋转角度为0时左上角纵坐标。 |
| Hitbox.width | int | 碰撞箱的宽度。 |
| Hitbox.height | int | 碰撞箱的高度。 |
| Hitbox.angle | double | 若碰撞箱可以旋转，表示碰撞箱的旋转角度。 |

| 函数 | 返回值 | 描述 |
| :--- | :---: | :--- |
| Hitbox:Overlap\(Hitbox other\) | bool | 返回当前碰撞箱与另一个碰撞箱是否重叠。 |
| Hitbox:OverlapAABB\(Hitbox other\) | bool | 返回当前轴对齐矩形与另一个轴对齐矩形是否重叠。 |

### Attack

表示一个攻击属性。包括攻击值、击退值、暴击率三个属性。

| 属性 | 类型 | 描述 |
| :--- | :---: | :--- |
| Attack.attack | int | 攻击值。 |
| Attack.knockBack | int | 攻击的击退值。 |
| Attack.crit | int | 攻击的百分暴击率。1-100表示1-100%的概率产生双倍暴击伤害，大于100表示总是产生双倍暴击伤害，小于1表示不产生双柏暴击伤害。 |

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

