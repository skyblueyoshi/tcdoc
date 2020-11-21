# 数据类型、枚举、全局量

本篇描述的数据类型、枚举类型和全局变量在所有的文件均可用。

## 数据类型（Data Types）

### Hitbox

表示一个碰撞箱。若`angle`属性为0，表示轴对齐碰撞箱（AABB）。否则表示一个绕中心点旋转的碰撞箱。

| 属性 | 类型 | 描述 |
| :--- | :--- | :--- |
| Hitbox.x | double | 碰撞箱在旋转角度为0时左上角横坐标。 |
| Hitbox.y | double | 碰撞箱在旋转角度为0时左上角纵坐标。 |
| Hitbox.width | int | 碰撞箱的宽度。 |
| Hitbox.height | int | 碰撞箱的高度。 |
| Hitbox.angle | double | 若碰撞箱可以旋转，表示碰撞箱的旋转角度。 |

| 函数 | 返回值 | 描述 |
| :--- | :--- | :--- |
| Hitbox:Overlap\(Hitbox other\) | bool | 返回当前碰撞箱与另一个碰撞箱是否重叠。 |
| Hitbox:OverlapAABB\(Hitbox other\) | bool | 返回当前轴对齐矩形与另一个轴对齐矩形是否重叠。 |

### Attack

表示一个攻击属性。包括攻击值、击退值、暴击率三个属性。

| 属性 | 类型 | 描述 |
| :--- | :--- | :--- |
| Attack.attack | int | 攻击值。 |
| Attack.knockBack | int | 攻击的击退值。 |
| Attack.crit | int | 攻击的百分暴击率。1-100表示1-100%的概率产生双倍暴击伤害，大于100表示总是产生双倍暴击伤害，小于1表示不产生双柏暴击伤害。 |

### EntityKey

表示一个实体在对应实体类型中的唯一键值。

### UserVar&lt;T&gt;

用户自定义数据，用于在脚本中实现自定义变量。`T`可以为`int`类型或者`double`类型。您可以通过如下使用例了解该数据类型的用法。

| 函数 | 返回值 | 描述 |
| :--- | :--- | :--- |
| UserVar:Apply\(int n\) | void | 申请指定可用数量的用户自定义数据。申请时会清空原数据，并将全部数据置为0，请仅在初始化时使用。 |
| UserVar\[index\] | T | 读取或写入指定下标index的用户自定义数据。index有效区间为\[1, 可用数量\]。使用自定义数据前必须申请可用数量。 |

#### 使用例

```lua
-- This is a projectile script

function Init()
    self.ivar:Apply(4) -- Apply 4 integer values
    self.dvar:Apply(2) -- Apply 2 double values
    self.ivar[1] = 123
    self.ivar[2] = 456
    self.ivar[3] = self.ivar[1]
    self.ivar[4] = 789
    self.dvar[1] = 1.0
    self.dvar[2] = 2.0
end

function Update()
    self.ivar[2] = self.ivar[1]
    self.dvar[2] = self.dvar[2] + 1.0
end
```

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
| `NET_MODE_SERVER` | 当前脚本为服务端环境。 |
| `NET_MODE_CLIENT` | 当前脚本为客户端环境。 |

### Shape

描述形状类型。

| 枚举值 | 描述 |
| :--- | :--- |
| SHAPE\_BOX | 碰撞箱形状为轴对齐矩形。 |
| SHAPE\_ROTATE\_BOX | 碰撞箱形状为旋转矩形。 |

## 全局常量（Global Constants）

<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x5E38;&#x91CF;&#x540D;</th>
      <th style="text-align:left">&#x5E38;&#x91CF;&#x503C;</th>
      <th style="text-align:left">&#x63CF;&#x8FF0;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">netMode</td>
      <td style="text-align:left">&#x89C1;&#x63CF;&#x8FF0;</td>
      <td style="text-align:left">
        <p>&#x82E5;&#x5F53;&#x524D;&#x811A;&#x672C;&#x4E3A;&#x670D;&#x52A1;&#x7AEF;&#x73AF;&#x5883;&#xFF0C;&#x503C;&#x4E3A;<code>NET_MODE_SERVER</code>&#x3002;</p>
        <p>&#x82E5;&#x5F53;&#x524D;&#x811A;&#x672C;&#x4E3A;&#x5BA2;&#x6237;&#x7AEF;&#x73AF;&#x5883;&#xFF0C;&#x503C;&#x4E3A;<code>NET_MODE_CLIENT</code>&#x3002;</p>
      </td>
    </tr>
  </tbody>
</table>



