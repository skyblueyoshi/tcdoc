# 地图API

## 地图通用模块（MapUtils）

### 通用常量

| 常量 | 类型 | 值 | 描述 |
| :--- | :---: | :---: | :--- |
| MapUtils._UNDERGROUND\_LINE_ | int | 416 | 地表层与地下层分界格纵坐标。 |
| MapUtils._NETHER\_LINE_ | int | 2450 | 地下层与地狱层分界格纵坐标。 |
| MapUtils._NETHER\_CAVE\_LINE_ | int | 2560 | 地狱层大型洞穴分界格纵坐标。 |

### 通用函数

#### 查询地图相关函数

这些函数在客户端和服务端均有效。

| 函数 | 返回值 | 描述 |
| :--- | :---: | :--- |
| MapUtils.IsValid\(int xi, int yi\) | bool | 判断指定格子是否有效，即所在区块是否存在。 |
| MapUtils.IsAreaValid\(int xi, int yi, int width, int height\) | bool | 判断矩形区域内所有格子是否都有效，即矩形区域覆盖的区块是否全部存在。 |
| MapUtils.IsSolid\(int xi, int yi\) | bool | 判断指定格子是否为实心前景。 若格子所在区块不存在，总是返回false。 |

#### 修改地图相关函数

这些函数在服务端均有效，在客户端不会进行有效操作。

| 函数 | 返回值 | 描述 |
| :--- | :---: | :--- |
| MapUtils.SetFront\(int xi, int yi, int blockID\) | void |  |

#### 

#### 不安全的函数（Unsafe Functions）

已弃用。

