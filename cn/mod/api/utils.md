# 通用API

## 通用模块（Utils）

### 全局常量

#### 脚本环境常量

| 常量            |    类型   |  值  | 描述                                                                                                   |
| ------------- | :-----: | :-: | ---------------------------------------------------------------------------------------------------- |
| Utils.netMode | NetMode | 见描述 | <p>若当前脚本为服务端环境，值为<code>NET_MODE_SERVER</code>。</p><p>若当前脚本为客户端环境，值为<code>NET_MODE_CLIENT</code>。</p> |

#### 数学常量

| 常量                  |   类型   |      值     | 描述            |
| ------------------- | :----: | :--------: | ------------- |
| Utils._E_           | double | 2.71828175 | 自然常数          |
| Utils._LOG2E_       | double |  1.442695  | 以 2 为底 e 的对数  |
| Utils._LOG10E_      | double |  0.4342945 | 以 10 为底 e 的对数 |
| Utils._PI_          | double | 3.14159274 | 圆周率           |
| Utils._TWO\_PI_     | double | 6.28318548 | 圆周率 x 2       |
| Utils._PI\_OVER\_2_ | double | 1.57079637 | 圆周率 / 2       |
| Utils._PI\_OVER\_4_ | double |  0.7853982 | 圆周率 / 4       |

### 随机数

| 函数                                             |   返回值  | 描述                                                                                                                                           |
| ---------------------------------------------- | :----: | -------------------------------------------------------------------------------------------------------------------------------------------- |
| Utils.RandInt(int n)                           |   int  | 若n大于0，返回\[0, n)的随机整数，否则返回0。                                                                                                                  |
| Utils.RandIntArea(int begin, int len)          |   int  | 若len大于0，返回\[begin, begin + len)的随机整数，否则返回begin。                                                                                              |
| Utils.RandDouble(double value)                 | double | 若value大于0，返回\[0, value)的随机浮点数，否则返回0。                                                                                                         |
| Utils.RandDoubleArea(double begin, double len) | double | 若len大于0，返回\[begin, begin + len)的随机浮点数，否则返回begin。                                                                                             |
| Utils.RandSym(double value)                    | double | 返回(-value, value)的随机浮点数。                                                                                                                     |
| Utils.RandTry(int n)                           |  bool  | <p>当n为正数时1/n概率返回true，否则始终返回false。</p><p><code>例1：Utils.RandTry(3)有1/3概率返回true。</code></p><p><code>例2：Utils.RandTry(2)有一半概率返回true。</code></p> |

### 数学运算与模型

| 函数                                                            |   返回值  | 描述                                                                                                                                                                     |
| ------------------------------------------------------------- | :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Utils.Cell(double a)                                          |   int  | 返回实际横/纵坐标对应的格子横/纵坐标。注意每个格子为16像素，实际结果为除以16后向下取整。                                                                                                                        |
| Utils.PositiveMod(int a, int b)                               |   int  | <p>返回a与b求余的非负数结果。</p><p><code>例1：Utils.PositiveMod(5, 3)返回2。</code></p><p><code>例2：Utils.PositiveMod(-5, 3)返回1。</code></p>                                             |
| Utils.FloorDivide(int a, int b)                               |   int  | <p>若b非0，返回a向下取整整除b的结果，否则返回0。</p><p><code>例1：Utils.FloorDivide(10, 3)返回3。</code></p><p><code>例2：Utils.FloorDivide(-4, 3)返回-2。</code></p>                                |
| Utils.SinValue(int phase, int period, int begin = 0)          | double | 返回以period为周期、以begin为初相位的正弦波在相位phase的值。                                                                                                                                 |
| Utils.CosValue(int phase, int period, int begin = 0)          | double | 返回以period为周期、以begin为初相位的余弦波在相位phase的值。                                                                                                                                 |
| Utils.ToTargetValue(double start, double target, double step) | double | <p>返回start值往target值方向移动step长度的结果，若到达target值，则返回target值。<br><code>例1：Utils.ToTargetValue(1, 10, 5)返回6。</code><br><code>例2：Utils.ToTargetValue(6, 10, 5)返回10。</code></p> |

### 二维空间几何

| 函数                                                                                            |       返回值      | 描述                                                                                                                          |
| --------------------------------------------------------------------------------------------- | :------------: | --------------------------------------------------------------------------------------------------------------------------- |
| Utils.GetPointsDistance(double x1, double y1, double x2, double y2)                           |     double     | <p>返回点(x1, y1)到点(x2, y2)的距离。</p><p><code>例：Utils.GetPointsDistance(1.0,0.0,4.0,4.0)返回5.0。</code></p>                        |
| Utils.GetDistance(double x, double y)                                                         |     double     | <p>返回点(x, y)到原点(0, 0)的距离。</p><p><code>例：Utils.GetDistance(3.0, 4.0)返回5.0。</code></p>                                        |
| Utils.GetPointSegmentDistance(double x, double y, double x1, double y1, double x2, double y2) |     double     | 返回点(x, y)到以点(x1, y1)和点(x2, y2)为两端点的线段的距离。                                                                                   |
| Utils.GetAngle(double x, double y)                                                            |     double     | <p>返回向量(x, y)与横坐标的夹角。</p><p><code>例1：Utils.GetAngle(1, 1)返回π/4。</code></p><p><code>例2：Utils.GetAngle(0, 1)返回π/2。</code></p> |
| Utils.FixAngle(double angle)                                                                  |     double     | 将角度按2π周期增加或减少，返回最终限定在区间(-π, π]内的结果。                                                                                         |
| Utils.GetXYFromPolar(double length, double angle)                                             | double, double | 将极坐标转换为直角坐标，返回横坐标和纵坐标。                                                                                                      |
| Utils.RotateXY(double x, double y, double angle)                                              | double, double | 将点(x, y)绕原点旋转指定角度，返回旋转后的横坐标和纵坐标。                                                                                            |

### 简单物理运动

| 函数                                                                                                 |       返回值      | 描述                                               |
| -------------------------------------------------------------------------------------------------- | :------------: | ------------------------------------------------ |
| Utils.SlowSpeed2D(double speedX, double speedY, double dec)                                        | double, double | 将一个二维速度(speedX, speedY)以恒定速度(dec)降低，返回新的横速度和纵速度。 |
| Utils.SlowSpeed1D(double speed, double dec)                                                        |     double     | 将一个速度以恒定速度(dec)降低，返回新的速度。                        |
| Utils.ForceSpeed2D(double speedX, double speedY, double force, double forceAngle, double maxSpeed) | double, double | 将一个二维速度(speedX, speedY)进行受力，返回新的横速度和纵速度。         |



## 源码参考

源码均以C++伪代码的形式展示，你可以通过这些源码来理解API的具体功能。

#### int Utils.PositiveMod(int a, int b)

```cpp
int c = a % b;
if (c < 0) c += b;
return c;
```

#### int Utils.FloorDivide(int a, int b)

```cpp
return a / b - ((a < 0 && a % b != 0) ? 1 : 0);
```

#### double Utils.GetPointsDistance(double x1, double y1, double x2, double y2)

```cpp
return sqrt(pow((x1)-(x2), 2) + pow((y1)-(y2), 2));
```

#### double Utils.GetDistance(double x, double y)

```cpp
return sqrt(pow(x, 2) + pow(y, 2));
```

#### double Utils.GetPointSegmentDistance(double x, double y, double x1, double y1, double x2, double y2)

```cpp
double cross = (x2 - x1) * (x - x1) + (y2 - y1) * (y - y1);
if (cross <= 0) return sqrt((x - x1) * (x - x1) + (y - y1) * (y - y1));

double d2 = (x2 - x1) * (x2 - x1) + (y2 - y1) * (y2 - y1);
if (cross >= d2) return sqrt((x - x2) * (x - x2) + (y - y2) * (y - y2));

double r = cross / d2;
double px = x1 + (x2 - x1) * r;
double py = y1 + (y2 - y1) * r;
return sqrt((x - px) * (x - px) + (py - y) * (py - y));
```

#### double Utils.GetAngle(double x, double y)

```cpp
return atan2(y, x);
```

#### double Utils.FixAngle(double angle)

```cpp
if (angle >= PI) angle -= 2 * PI * ceil((angle - PI) / (2 * PI));
else if (angle < -PI) angle += 2 * PI * ceil((-angle - PI) / (2 * PI));
return angle;
```

#### double Utils.SinValue(int phase, int period, int begin)

```cpp
return sin(begin + 2 * PI * float(phase % period) / period);
```

#### double Utils.CosValue(int phase, int period, int begin)

```cpp
return cos(begin + 2 * PI * float(phase % period) / period);
```

#### double Utils.ToTargetValue(double start, double target, double step)

```cpp
if (fabs(start - target) < step) start = target;
else if (start > target) start -= step;
else start += step;
return start;
```

#### void Utils.GetXYFromPolar(double & x, double & y, double length, double angle)

```cpp
x = length * cos(angle);
y = length * sin(angle);
```

#### void Utils.RotateXY(double & x, double & y, double angle)

```cpp
double dx = x, dy = y;
x = dx * cos(angle) - dy * sin(angle);
y = dx * sin(angle) + dy * cos(angle);
```

#### void Utils.SlowSpeed2D(double & spx, double & spy, double dec)

```cpp
double moveAngle = ut.getAngle(spx, spy);
spx = ut.toTargetValue(spx, 0, cos(moveAngle)*dec);
spy = ut.toTargetValue(spy, 0, sin(moveAngle)*dec);
```

#### double Utils.SlowSpeed1D(double speed, double dec)

```cpp
return ut.toTargetValue(speed, 0, dec);
```

#### void ForceSpeed2D(double & spx, double & spy, double force, double forceAngle, double maxSpeed)

```cpp
double forceX = force * cos(forceAngle);
double forceY = force * sin(forceAngle);
spx += forceX;
spy += forceY;
double moveAngle = GetAngle(spx, spy);
double maxSpx = maxSpeed * cos(moveAngle);
double maxSpy = maxSpeed * sin(moveAngle);

if (maxSpx >= 0) {
	if (spx > maxSpx) spx = maxSpx;
}
else {
	if (spx < maxSpx) spx = maxSpx;
}
if (maxSpy >= 0) {
	if (spy > maxSpy) spy = maxSpy;
}
else {
	if (spy < maxSpy) spy = maxSpy;
}
```
