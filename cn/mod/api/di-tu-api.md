# 地图API

## 地图通用模块（MapUtils）

### 通用常量

| 常量 | 类型 | 值 | 描述 |
| :--- | :---: | :---: | :--- |
| MapUtils._UNDERGROUND\_LINE_ | int | 416 | 地表层与地下层分界格纵坐标。 |
| MapUtils._NETHER\_LINE_ | int | 2450 | 地下层与地狱层分界格纵坐标。 |
| MapUtils._NETHER\_CAVE\_LINE_ | int | 2560 | 地狱层大型洞穴分界格纵坐标。 |

### 通用函数

| 函数 | 返回值 | 描述 |
| :--- | :---: | :--- |
| MapUtils.IsValid\(int xi, int yi\) | bool | 判断指定格子是否有效，即所在区块是否存在。 |
| MapUtils.IsAreaValid\(int xi, int yi, int width, int height\) | bool | 判断矩形区域内所有格子是否都有效，即矩形区域覆盖的区块是否全部存在。 |
| MapUtils.IsSolid\(int xi, int yi\) | bool | 判断指定格子是否为实心前景。 若格子所在区块不存在，总是返回false。 |

#### 不安全的函数（Unsafe Functions）

如下函数都不会进行区块的存在性检测。

在使用这些函数之前，必须使用IsValid或者IsAreaValid来证明格子所在区块死存在的。

| 函数 | 返回值 | 描述 |
| :--- | :---: | :--- |
| MapUtils.IsSolidUnsafe\(int xi, int yi\) | bool | IsSolid函数的不安全版本。 |

