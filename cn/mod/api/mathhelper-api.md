# 数学与几何API

模块名称：MathHelper

## 数学常量

| 常量 | 返回值 | 描述 |
| :--- | :--- | :--- |
| MathHelper.E | double | 自然常数 |
| MathHelper.LOG2E | double | 以 2 为底 e 的对数 |
| MathHelper.LOG10E | double | 以 10 为底 e 的对数 |
| MathHelper.PI | double | 圆周率 |
| MathHelper.TWO\_PI | double | 圆周率 x 2 |
| MathHelper.PI\_OVER\_2 | double | 圆周率 / 2 |
| MathHelper.PI\_OVER\_4 | double | 圆周率 / 4 |

## 随机数

<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x51FD;&#x6570;</th>
      <th style="text-align:center">&#x8FD4;&#x56DE;&#x503C;</th>
      <th style="text-align:left">&#x63CF;&#x8FF0;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">MathHelper.RandInt(int n)</td>
      <td style="text-align:center">int</td>
      <td style="text-align:left">&#x82E5;n&#x5927;&#x4E8E;0&#xFF0C;&#x8FD4;&#x56DE;[0, n)&#x7684;&#x968F;&#x673A;&#x6574;&#x6570;&#xFF0C;&#x5426;&#x5219;&#x8FD4;&#x56DE;0&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">MathHelper.RandIntArea(int begin, int len)</td>
      <td style="text-align:center">int</td>
      <td style="text-align:left">&#x82E5;len&#x5927;&#x4E8E;0&#xFF0C;&#x8FD4;&#x56DE;[begin, begin + len)&#x7684;&#x968F;&#x673A;&#x6574;&#x6570;&#xFF0C;&#x5426;&#x5219;&#x8FD4;&#x56DE;begin&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">MathHelper.RandDouble(double value)</td>
      <td style="text-align:center">double</td>
      <td style="text-align:left">&#x82E5;value&#x5927;&#x4E8E;0&#xFF0C;&#x8FD4;&#x56DE;[0, value)&#x7684;&#x968F;&#x673A;&#x6D6E;&#x70B9;&#x6570;&#xFF0C;&#x5426;&#x5219;&#x8FD4;&#x56DE;0&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">MathHelper.RandDoubleArea(double begin, double len)</td>
      <td style="text-align:center">double</td>
      <td style="text-align:left">&#x82E5;len&#x5927;&#x4E8E;0&#xFF0C;&#x8FD4;&#x56DE;[begin, begin + len)&#x7684;&#x968F;&#x673A;&#x6D6E;&#x70B9;&#x6570;&#xFF0C;&#x5426;&#x5219;&#x8FD4;&#x56DE;begin&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">MathHelper.RandSym(double value)</td>
      <td style="text-align:center">double</td>
      <td style="text-align:left">&#x8FD4;&#x56DE;(-value, value)&#x7684;&#x968F;&#x673A;&#x6D6E;&#x70B9;&#x6570;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">MathHelper.RandTry(int n)</td>
      <td style="text-align:center">bool</td>
      <td style="text-align:left">
        <p>&#x5F53;n&#x4E3A;&#x6B63;&#x6570;&#x65F6;1/n&#x6982;&#x7387;&#x8FD4;&#x56DE;true&#xFF0C;&#x5426;&#x5219;&#x59CB;&#x7EC8;&#x8FD4;&#x56DE;false&#x3002;</p>
        <p><code>&#x4F8B;1&#xFF1A;ut.randTry(3)&#x6709;1/3&#x6982;&#x7387;&#x8FD4;&#x56DE;true&#x3002;</code>
        </p>
        <p><code>&#x4F8B;2&#xFF1A;ut.randTry(2)&#x6709;&#x4E00;&#x534A;&#x6982;&#x7387;&#x8FD4;&#x56DE;true&#x3002;</code>
        </p>
      </td>
    </tr>
  </tbody>
</table>

## 数学运算与模型

<table>
  <thead>
    <tr>
      <th style="text-align:left">API</th>
      <th style="text-align:left">&#x8FD4;&#x56DE;&#x503C;</th>
      <th style="text-align:left">&#x63CF;&#x8FF0;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">MathHelper.PositiveMod(int a, int b)</td>
      <td style="text-align:left">int</td>
      <td style="text-align:left">
        <p>&#x8FD4;&#x56DE;a&#x4E0E;b&#x6C42;&#x4F59;&#x7684;&#x975E;&#x8D1F;&#x6570;&#x7ED3;&#x679C;&#x3002;</p>
        <p><code>&#x4F8B;1&#xFF1A;ut.positiveMod(5, 3)&#x8FD4;&#x56DE;2&#x3002;</code>
        </p>
        <p><code>&#x4F8B;2&#xFF1A;ut.positiveMod(-5, 3)&#x8FD4;&#x56DE;1&#x3002;</code>
        </p>
        <p><a href="mathhelper-api.md#int-ut-positivemod-int-a-int-b">&#x6E90;&#x7801;&#x53C2;&#x8003;</a>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">MathHelper.FloorDivide(int a, int b)</td>
      <td style="text-align:left">int</td>
      <td style="text-align:left">
        <p>&#x82E5;b&#x975E;0&#xFF0C;&#x8FD4;&#x56DE;a&#x5411;&#x4E0B;&#x53D6;&#x6574;&#x6574;&#x9664;b&#x7684;&#x7ED3;&#x679C;&#xFF0C;&#x5426;&#x5219;&#x8FD4;&#x56DE;0&#x3002;</p>
        <p><code>&#x4F8B;1&#xFF1A;ut.floorDivide(10, 3)&#x8FD4;&#x56DE;3&#x3002;</code>
        </p>
        <p><code>&#x4F8B;2&#xFF1A;ut.floorDivide(-4, 3)&#x8FD4;&#x56DE;-2&#x3002;</code>
        </p>
        <p><a href="mathhelper-api.md#int-ut-floordivide-int-a-int-b">&#x6E90;&#x7801;&#x53C2;&#x8003;</a>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">MathHelper.SinValue(int phase, int period, int begin = 0)</td>
      <td style="text-align:left">double</td>
      <td style="text-align:left">
        <p>&#x8FD4;&#x56DE;&#x4EE5;period&#x4E3A;&#x5468;&#x671F;&#x3001;&#x4EE5;begin&#x4E3A;&#x521D;&#x76F8;&#x4F4D;&#x7684;&#x6B63;&#x5F26;&#x6CE2;&#x5728;&#x76F8;&#x4F4D;phase&#x7684;&#x503C;&#x3002;</p>
        <p><a href="mathhelper-api.md#double-ut-sinvalue-int-phase-int-period-int-begin">&#x6E90;&#x7801;&#x53C2;&#x8003;</a>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">MathHelper.CosValue(int phase, int period, int begin = 0)</td>
      <td style="text-align:left">double</td>
      <td style="text-align:left">
        <p>&#x8FD4;&#x56DE;&#x4EE5;period&#x4E3A;&#x5468;&#x671F;&#x3001;&#x4EE5;begin&#x4E3A;&#x521D;&#x76F8;&#x4F4D;&#x7684;&#x4F59;&#x5F26;&#x6CE2;&#x5728;&#x76F8;&#x4F4D;phase&#x7684;&#x503C;&#x3002;</p>
        <p><a href="mathhelper-api.md#double-ut-cosvalue-int-phase-int-period-int-begin">&#x6E90;&#x7801;&#x53C2;&#x8003;</a>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">MathHelper.ToTargetValue(double start, double target, double step)</td>
      <td
      style="text-align:left">double</td>
        <td style="text-align:left">
          <p>&#x8FD4;&#x56DE;start&#x503C;&#x5F80;target&#x503C;&#x65B9;&#x5411;&#x79FB;&#x52A8;step&#x957F;&#x5EA6;&#x7684;&#x7ED3;&#x679C;&#xFF0C;&#x82E5;&#x5230;&#x8FBE;target&#x503C;&#xFF0C;&#x5219;&#x8FD4;&#x56DE;target&#x503C;&#x3002;
            <br
            /><code>&#x4F8B;1&#xFF1A;ut.toTargetValue(1, 10, 5)&#x8FD4;&#x56DE;6&#x3002;<br />&#x4F8B;2&#xFF1A;ut.toTargetValue(6, 10, 5)&#x8FD4;&#x56DE;10&#x3002;</code>
          </p>
          <p><a href="mathhelper-api.md#double-ut-totargetvalue-double-start-double-target-double-step">&#x6E90;&#x7801;&#x53C2;&#x8003;</a>
          </p>
        </td>
    </tr>
  </tbody>
</table>

## 二维空间几何

<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x51FD;&#x6570;</th>
      <th style="text-align:left">&#x8FD4;&#x56DE;&#x503C;</th>
      <th style="text-align:left">&#x63CF;&#x8FF0;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">MathHelper.GetPointsDistance(double x1, double y1, double x2, double y2)</td>
      <td
      style="text-align:left">double</td>
        <td style="text-align:left">
          <p>&#x8FD4;&#x56DE;&#x70B9;(x1, y1)&#x5230;&#x70B9;(x2, y2)&#x7684;&#x8DDD;&#x79BB;&#x3002;</p>
          <p><code>&#x4F8B;&#xFF1A;ut.getPointsDistance(1.0,0.0,4.0,4.0)&#x8FD4;&#x56DE;5.0&#x3002;</code>
          </p>
          <p><a href="mathhelper-api.md#double-ut-getpointsdistance-double-x-1-double-y-1-double-x-2-double-y-2">&#x6E90;&#x7801;&#x53C2;&#x8003;</a>
          </p>
        </td>
    </tr>
    <tr>
      <td style="text-align:left">MathHelper.GetDistance(double x, double y)</td>
      <td style="text-align:left">double</td>
      <td style="text-align:left">
        <p>&#x8FD4;&#x56DE;&#x70B9;(x, y)&#x5230;&#x539F;&#x70B9;(0, 0)&#x7684;&#x8DDD;&#x79BB;&#x3002;</p>
        <p><code>&#x4F8B;&#xFF1A;ut.getDistance(3.0, 4.0)&#x8FD4;&#x56DE;5.0&#x3002;</code>
        </p>
        <p><a href="mathhelper-api.md#double-ut-getdistance-double-x-double-y">&#x6E90;&#x7801;&#x53C2;&#x8003;</a>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">MathHelper.GetPointSegmentDistance(double x, double y, double x1, double
        y1, double x2, double y2)</td>
      <td style="text-align:left">double</td>
      <td style="text-align:left">
        <p>&#x8FD4;&#x56DE;&#x70B9;(x, y)&#x5230;&#x4EE5;&#x70B9;(x1, y1)&#x548C;&#x70B9;(x2,
          y2)&#x4E3A;&#x4E24;&#x7AEF;&#x70B9;&#x7684;&#x7EBF;&#x6BB5;&#x7684;&#x8DDD;&#x79BB;&#x3002;</p>
        <p><a href="mathhelper-api.md#double-ut-getdistance-double-x-double-y">&#x6E90;&#x7801;&#x53C2;&#x8003;</a>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">MathHelper.GetAngle(double x, double y)</td>
      <td style="text-align:left">double</td>
      <td style="text-align:left">
        <p>&#x8FD4;&#x56DE;&#x5411;&#x91CF;(x, y)&#x4E0E;&#x6A2A;&#x5750;&#x6807;&#x7684;&#x5939;&#x89D2;&#x3002;</p>
        <p><code>&#x4F8B;1&#xFF1A;ut.getAngle(1, 1)&#x8FD4;&#x56DE;&#x3C0;/4&#x3002;</code>
        </p>
        <p><code>&#x4F8B;2&#xFF1A;ut.getAngle(0, 1)&#x8FD4;&#x56DE;&#x3C0;/2&#x3002;</code>
        </p>
        <p><a href="mathhelper-api.md#double-ut-getangle-double-x-double-y">&#x6E90;&#x7801;&#x53C2;&#x8003;</a>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">MathHelper.FixAngle(double angle)</td>
      <td style="text-align:left">double</td>
      <td style="text-align:left">
        <p>&#x5C06;&#x89D2;&#x5EA6;&#x6309;2&#x3C0;&#x5468;&#x671F;&#x589E;&#x52A0;&#x6216;&#x51CF;&#x5C11;&#xFF0C;&#x8FD4;&#x56DE;&#x6700;&#x7EC8;&#x9650;&#x5B9A;&#x5728;&#x533A;&#x95F4;(-&#x3C0;,
          &#x3C0;]&#x5185;&#x7684;&#x7ED3;&#x679C;&#x3002;</p>
        <p><a href="mathhelper-api.md#double-ut-fixangle-double-angle">&#x6E90;&#x7801;&#x53C2;&#x8003;</a>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">MathHelper.SlowSpeed2D(double spx, double spy, double dec)</td>
      <td style="text-align:left">double, double</td>
      <td style="text-align:left">
        <p>&#x5C06;&#x4E00;&#x4E2A;&#x4E8C;&#x7EF4;&#x901F;&#x5EA6;(spx, spy)&#x4EE5;&#x6052;&#x5B9A;&#x901F;&#x5EA6;(dec)&#x964D;&#x4F4E;&#xFF0C;&#x8FD4;&#x56DE;&#x65B0;&#x7684;&#x6A2A;&#x901F;&#x5EA6;&#x548C;&#x7EB5;&#x901F;&#x5EA6;&#x3002;</p>
        <p><a href="mathhelper-api.md#void-ut-slowspeed-2-d-double-and-spx-double-and-spy-double-dec">&#x6E90;&#x7801;&#x53C2;&#x8003;</a>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">MathHelper.SlowSpeed1D(double speed, double dec)</td>
      <td style="text-align:left">double</td>
      <td style="text-align:left">
        <p>&#x5C06;&#x4E00;&#x4E2A;&#x901F;&#x5EA6;&#x4EE5;&#x6052;&#x5B9A;&#x901F;&#x5EA6;(dec)&#x964D;&#x4F4E;&#xFF0C;&#x8FD4;&#x56DE;&#x65B0;&#x7684;&#x901F;&#x5EA6;&#x3002;</p>
        <p><a href="mathhelper-api.md#void-ut-slowspeed-2-d-double-and-spx-double-and-spy-double-dec">&#x6E90;&#x7801;&#x53C2;&#x8003;</a>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">MathHelper.GetXYFromPolar(double length, double angle)</td>
      <td style="text-align:left">double, double</td>
      <td style="text-align:left">
        <p>&#x5C06;&#x6781;&#x5750;&#x6807;&#x8F6C;&#x6362;&#x4E3A;&#x76F4;&#x89D2;&#x5750;&#x6807;&#xFF0C;&#x8FD4;&#x56DE;&#x6A2A;&#x5750;&#x6807;&#x548C;&#x7EB5;&#x5750;&#x6807;&#x3002;</p>
        <p><a href="mathhelper-api.md#void-ut-getxyfrompolar-double-and-x-double-and-y-double-length-double-angle">&#x6E90;&#x7801;&#x53C2;&#x8003;</a>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">MathHelper.RotateXY(double x, double y, double angle)</td>
      <td style="text-align:left">double, double</td>
      <td style="text-align:left">
        <p>&#x5C06;&#x70B9;(x, y)&#x7ED5;&#x539F;&#x70B9;&#x65CB;&#x8F6C;&#x6307;&#x5B9A;&#x89D2;&#x5EA6;&#xFF0C;&#x8FD4;&#x56DE;&#x65CB;&#x8F6C;&#x540E;&#x7684;&#x6A2A;&#x5750;&#x6807;&#x548C;&#x7EB5;&#x5750;&#x6807;&#x3002;</p>
        <p><a href="mathhelper-api.md#void-ut-rotatexy-double-and-x-double-and-y-double-angle">&#x6E90;&#x7801;&#x53C2;&#x8003;</a>
        </p>
      </td>
    </tr>
  </tbody>
</table>



## 源码参考

源码均以C++伪代码的形式展示，你可以通过这些源码来理解API的具体功能。

### int MathHelper.PositiveMod\(int a, int b\)

```cpp
int c = a % b;
if (c < 0) c += b;
return c;
```

### int MathHelper.FloorDivide\(int a, int b\)

```cpp
return a / b - ((a < 0 && a % b != 0) ? 1 : 0);
```

### double MathHelper.GetPointsDistance\(double x1, double y1, double x2, double y2\)

```cpp
return sqrt(pow((x1)-(x2), 2) + pow((y1)-(y2), 2));
```

### double MathHelper.GetDistance\(double x, double y\)

```cpp
return sqrt(pow(x, 2) + pow(y, 2));
```

### double MathHelper.GetPointSegmentDistance\(double x, double y, double x1, double y1, double x2, double y2\)

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

### double MathHelper.GetAngle\(double x, double y\)

```cpp
return atan2(y, x);
```

### double MathHelper.FixAngle\(double angle\)

```cpp
if (angle >= PI) angle -= 2 * PI * ceil((angle - PI) / (2 * PI));
else if (angle < -PI) angle += 2 * PI * ceil((-angle - PI) / (2 * PI));
return angle;
```

### double MathHelper.SinValue\(int phase, int period, int begin\)

```cpp
return sin(begin + 2 * PI * float(phase % period) / period);
```

### double MathHelper.CosValue\(int phase, int period, int begin\)

```cpp
return cos(begin + 2 * PI * float(phase % period) / period);
```

### double MathHelper.ToTargetValue\(double start, double target, double step\)

```cpp
if (fabs(start - target) < step) start = target;
else if (start > target) start -= step;
else start += step;
return start;
```

### void MathHelper.SlowSpeed2D\(double & spx, double & spy, double dec\)

```cpp
double moveAngle = ut.getAngle(spx, spy);
spx = ut.toTargetValue(spx, 0, cos(moveAngle)*dec);
spy = ut.toTargetValue(spy, 0, sin(moveAngle)*dec);
```

### double MathHelper.SlowSpeed1D\(double speed, double dec\)

```cpp
return ut.toTargetValue(speed, 0, dec);
```

### void MathHelper.GetXYFromPolar\(double & x, double & y, double length, double angle\)

```cpp
x = length * cos(angle);
y = length * sin(angle);
```

### void MathHelper.RotateXY\(double & x, double & y, double angle\)

```cpp
double dx = x, dy = y;
x = dx * cos(angle) - dy * sin(angle);
y = dx * sin(angle) + dy * cos(angle);
```


