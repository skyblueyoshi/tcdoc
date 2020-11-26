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

用户自定义数据，用于在脚本中实现自定义变量。`T`可以为`int`类型或者`double`类型，可用64个数据。

| 函数 | 返回值 | 描述 |
| :--- | :---: | :--- |
| UserVar\[index\] | T | 读取或写入指定下标index的用户自定义数据。index有效区间为\[1, 64\]。 |

#### 使用例

```lua
-- This is a projectile script

function Init()
    self.ivar[1] = 123
    self.ivar[4] = 456
    self.ivar[6] = self.ivar[1]
    self.dvar[1] = 1.0
end

function Update()
    self.ivar[2] = self.ivar[1]
    self.dvar[4] = self.dvar[4] + 1.0
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
| NET\_MODE\_SERVER | 当前脚本为服务端环境。 |
| NET\_MODE\_CLIENT | 当前脚本为客户端环境。 |

### Shape

描述形状类型。

| 枚举值 | 描述 |
| :--- | :--- |
| SHAPE\_BOX | 碰撞箱形状为轴对齐矩形。 |
| SHAPE\_ROTATE\_BOX | 碰撞箱形状为旋转矩形。 |

### ItemType

描述物品类型。

| 枚举值 | 描述 |
| :--- | :--- |
| ITEM\_TYPE\_NONE | 无物品。 |
| ITEM\_TYPE\_BLOCKS | 方块类型物品。 |
| ITEM\_TYPE\_TOOLS | 工具类型物品。 |
| ITEM\_TYPE\_MATERIALS | 材料类型物品。 |
| ITEM\_TYPE\_WIRES | 红石电线类型物品。 |
| ITEM\_TYPE\_PROJECTILES | 抛射物类型物品。 |
| ITEM\_TYPE\_CHESTS | 容器类型物品。 |

### DefaultColor

描述默认颜色。

| 枚举值 | 描述 |
| :--- | :--- |
| COLOR\_BLACK | 黑色。ARGB=\(255, 0, 0, 0\) |
| COLOR\_WHITE | 白色。ARGB=\(255, 2555, 255, 255\) |
| COLOR\_GRAY | 灰色。ARGB=\(255, 128, 128, 128\) |
| COLOR\_RED | 红色。ARGB=\(255, 255, 0, 0\) |
| COLOR\_GREEN | 绿色。ARGB=\(255, 0, 255, 0\) |
| COLOR\_BLUE | 蓝色。ARGB=\(255, 0, 0, 255\) |
| COLOR\_YELLOW | 黄色。ARGB=\(255, 255, 255, 0\) |

