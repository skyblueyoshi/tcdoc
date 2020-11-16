# 数据类型、枚举类型和全局常量

本篇描述的数据类型、枚举类型和全局变量在所有的文件均可用。

## 数据类型（Data Types）

### Hitbox

| 成员参数名 | 类型 | 描述 |
| :--- | :--- | :--- |
| Hitbox.x | double | 碰撞箱在旋转角度为0时左上角横坐标。 |
| Hitbox.y | double | 碰撞箱在旋转角度为0时左上角纵坐标。 |
| Hitbox.width | int | 碰撞箱的宽度。 |
| Hitbox.height | int | 碰撞箱的高度。 |
| Hitbox.angle | double | 若碰撞箱可以旋转，表示碰撞箱的旋转角度。 |

## 

## 枚举类型（Enums）

注意，这里的枚举值直接当作全局常量使用，且枚举类型的变量只能使用对应枚举值。例如：

```lua
if npc.shape == SHAPE_ROTATE_BOX then
    --do something
end
```

### Shape

| 枚举值 | 描述 |
| :--- | :--- |
| SHAPE\_BOX | 碰撞箱形状为轴对齐矩形 |
| SHAPE\_ROTATE\_BOX | 碰撞箱形状为旋转矩形 |

## 全局常量（Global Constants）

| 常量名 | 描述 |
| :--- | :--- |
|  |  |

