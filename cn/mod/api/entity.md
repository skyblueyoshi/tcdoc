# 实体API

全局表名称：entity

## 实体坐标与图形

如下是获取和控制实体图形的API。

<table>
  <thead>
    <tr>
      <th style="text-align:left">API</th>
      <th style="text-align:center">&#x8FD4;&#x56DE;&#x503C;</th>
      <th style="text-align:left">&#x63CF;&#x8FF0;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">entity.x()</td>
      <td style="text-align:center">double</td>
      <td style="text-align:left">&#x8FD4;&#x56DE;&#x5B9E;&#x4F53;&#x5DE6;&#x4E0A;&#x89D2;&#x6A2A;&#x5750;&#x6807;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">entity.y()</td>
      <td style="text-align:center">double</td>
      <td style="text-align:left">&#x8FD4;&#x56DE;&#x5B9E;&#x4F53;&#x5DE6;&#x4E0A;&#x89D2;&#x7EB5;&#x5750;&#x6807;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">entity.setX(double x)</td>
      <td style="text-align:center">void</td>
      <td style="text-align:left">&#x8BBE;&#x7F6E;&#x5B9E;&#x4F53;&#x5DE6;&#x4E0A;&#x89D2;&#x6A2A;&#x5750;&#x6807;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">entity.setY(double y)</td>
      <td style="text-align:center">void</td>
      <td style="text-align:left">&#x8BBE;&#x7F6E;&#x5B9E;&#x4F53;&#x5DE6;&#x4E0A;&#x89D2;&#x7EB5;&#x5750;&#x6807;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">entity.speedX()</td>
      <td style="text-align:center">double</td>
      <td style="text-align:left">&#x8FD4;&#x56DE;&#x5B9E;&#x4F53;&#x6A2A;&#x5411;&#x901F;&#x5EA6;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">entity.speedY()</td>
      <td style="text-align:center">double</td>
      <td style="text-align:left">&#x8FD4;&#x56DE;&#x5B9E;&#x4F53;&#x7EB5;&#x5411;&#x901F;&#x5EA6;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">entity.setSpeedX(double spx)</td>
      <td style="text-align:center">void</td>
      <td style="text-align:left">&#x8BBE;&#x7F6E;&#x5B9E;&#x4F53;&#x6A2A;&#x5411;&#x901F;&#x5EA6;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">entity.setSpeedY(double spy)</td>
      <td style="text-align:center">void</td>
      <td style="text-align:left">&#x8BBE;&#x7F6E;&#x5B9E;&#x4F53;&#x7EB5;&#x5411;&#x901F;&#x5EA6;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">entity.width()</td>
      <td style="text-align:center">int</td>
      <td style="text-align:left">&#x8FD4;&#x56DE;&#x5B9E;&#x4F53;&#x78B0;&#x649E;&#x7BB1;&#x5BBD;&#x5EA6;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">entity.height()</td>
      <td style="text-align:center">int</td>
      <td style="text-align:left">&#x8FD4;&#x56DE;&#x5B9E;&#x4F53;&#x78B0;&#x649E;&#x7BB1;&#x9AD8;&#x5EA6;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">entity.centerX()</td>
      <td style="text-align:center">double</td>
      <td style="text-align:left">&#x8FD4;&#x56DE;&#x5B9E;&#x4F53;&#x6B63;&#x4E2D;&#x95F4;&#x6A2A;&#x5750;&#x6807;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">entity.centerY()</td>
      <td style="text-align:center">double</td>
      <td style="text-align:left">&#x8FD4;&#x56DE;&#x5B9E;&#x4F53;&#x6B63;&#x4E2D;&#x95F4;&#x7EB5;&#x5750;&#x6807;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">entity.rightX()</td>
      <td style="text-align:center">double</td>
      <td style="text-align:left">&#x8FD4;&#x56DE;&#x5B9E;&#x4F53;&#x6700;&#x53F3;&#x4FA7;&#x6A2A;&#x5750;&#x6807;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">entity.bottomY()</td>
      <td style="text-align:center">double</td>
      <td style="text-align:left">&#x8FD4;&#x56DE;&#x5B9E;&#x4F53;&#x6700;&#x5E95;&#x90E8;&#x7EB5;&#x5750;&#x6807;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">entity.randX()</td>
      <td style="text-align:center">double</td>
      <td style="text-align:left">&#x8FD4;&#x56DE;&#x5B9E;&#x4F53;&#x6A2A;&#x5411;&#x6295;&#x5F71;&#x4E0A;&#x7684;&#x968F;&#x673A;&#x6A2A;&#x5750;&#x6807;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">entity.randY()</td>
      <td style="text-align:center">double</td>
      <td style="text-align:left">&#x8FD4;&#x56DE;&#x5B9E;&#x4F53;&#x7EB5;&#x5411;&#x6295;&#x5F71;&#x4E0A;&#x7684;&#x968F;&#x673A;&#x7EB5;&#x5750;&#x6807;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">entity.direction()</td>
      <td style="text-align:center">bool</td>
      <td style="text-align:left">
        <p>&#x8FD4;&#x56DE;&#x5B9E;&#x4F53;&#x671D;&#x5411;&#x3002;
          <br />&#x82E5;&#x5B9E;&#x4F53;&#x9762;&#x671D;&#x5DE6;&#x4FA7;&#xFF0C;&#x8FD4;&#x56DE;false&#x3002;</p>
        <p>&#x82E5;&#x5B9E;&#x4F53;&#x9762;&#x671D;&#x53F3;&#x4FA7;&#xFF0C;&#x8FD4;&#x56DE;true&#x3002;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">entity.setDirection(bool direction)</td>
      <td style="text-align:center">void</td>
      <td style="text-align:left">&#x8BBE;&#x7F6E;&#x5B9E;&#x4F53;&#x7684;&#x671D;&#x5411;&#xFF0C;false&#x8868;&#x793A;&#x9762;&#x671D;&#x5DE6;&#x4FA7;&#xFF0C;true&#x8868;&#x793A;&#x9762;&#x671D;&#x53F3;&#x4FA7;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">entity.angleTo(double desX, double desY)</td>
      <td style="text-align:center">double</td>
      <td style="text-align:left">&#x8FD4;&#x56DE;&#x5B9E;&#x4F53;&#x4E2D;&#x5FC3;&#x70B9;&#x5230;&#x76EE;&#x6807;&#x70B9;&#x7684;&#x89D2;&#x5EA6;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">entity.angleFrom(double srcX, double srcY)</td>
      <td style="text-align:center">double</td>
      <td style="text-align:left">&#x8FD4;&#x56DE;&#x6765;&#x6E90;&#x70B9;&#x5230;&#x5B9E;&#x4F53;&#x4E2D;&#x5FC3;&#x70B9;&#x7684;&#x89D2;&#x5EA6;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">entity.distance(double otherX, double otherY)</td>
      <td style="text-align:center">double</td>
      <td style="text-align:left">&#x8FD4;&#x56DE;&#x5B9E;&#x4F53;&#x4E2D;&#x5FC3;&#x5230;&#x6307;&#x5B9A;&#x70B9;&#x7684;&#x8DDD;&#x79BB;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">entity.rotateAngle()</td>
      <td style="text-align:center">double</td>
      <td style="text-align:left">&#x8FD4;&#x56DE;&#x5B9E;&#x4F53;&#x65CB;&#x8F6C;&#x89D2;&#x5EA6;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">entity.setRotateAngle(double angle)</td>
      <td style="text-align:center">void</td>
      <td style="text-align:left">&#x8BBE;&#x7F6E;&#x5B9E;&#x4F53;&#x65CB;&#x8F6C;&#x89D2;&#x5EA6;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">entity.rotate(double angle)</td>
      <td style="text-align:center">void</td>
      <td style="text-align:left">&#x5728;&#x539F;&#x6709;&#x89D2;&#x5EA6;&#x57FA;&#x7840;&#x4E0A;&#x7EE7;&#x7EED;&#x65CB;&#x8F6C;&#x6307;&#x5B9A;&#x89D2;&#x5EA6;&#x3002;</td>
    </tr>
  </tbody>
</table>

## 碰撞检测

如下是当前实体的碰撞检测相关API。

| API | 返回值 | 描述 |
| :--- | :---: | :--- |
| entity.hitbox\(\) | Hitbox | 若实体为轴对齐矩形，返回轴对齐碰撞箱，否则返回旋转矩形碰撞箱。 |
| entity.aabb\(\) | Hitbox | 返回实体旋转角度为0的轴对齐碰撞箱。 |
| entity.minAabb\(\) | Hitbox | 返回完全包裹实体的最小轴对齐碰撞箱。 |
| entity.stand\(\) | bool | 返回实体是否为站立状态（底部碰撞）。 |
| entity.isCollisionTop\(\) | bool | 返回实体是否顶部发生碰撞。 |
| entity.isCollisionLeft\(\) | bool | 返回实体是否左侧发生碰撞。 |
| entity.isCollisionRight\(\) | bool | 返回实体是否右侧发生碰撞。 |
| entity.isCollisionStuck\(\) | bool | 返回实体是否卡在方块内部。 |
| entity.isNoCollision\(\) | bool | 返回实体是否没有发生任何形式的碰撞。 |
| entity.onSlope\(\) | bool | 返回实体是否站在斜坡上。 |

## 用户自定义数据

您可以通过如下API，维护针对当前实体的用户自定义数据。在使用用户自定义数据之前，您需要在对应的初始化函数中申请自定义数据，得到自定义数据的索引，注意该索引为一个大于0的整数。之后，您可以使用这个索引来获取或修改自定义数据。

| API | 返回值 | 描述 |
| :--- | :---: | :--- |
| entity.applyUserInt\(\) | int | 申请一个用户自定义的整型数据，初始值为0，返回指向该数据的索引。 |
| entity.applyUserDouble\(\) | int | 申请一个用户自定义的浮点型数据，初始值为0.0，返回指向该数据的索引。 |
| entity.applyUserBool\(\) | int | 申请一个用户自定义的布尔型数据，初始值为false，返回指向该数据的索引。 |
| entity.userInt\(int index\) | int | 根据索引index返回用户自定义整型数据，若索引无效或指向的数据不是整型数据，返回0。 |
| entity.userDouble\(int index\) | double | 根据索引index返回用户自定义浮点型数据，若索引无效或指向的数据不是浮点型数据，返回0.0。 |
| entity.userBool\(int index\) | bool | 根据索引index返回用户自定义布尔型数据，若索引无效或指向的数据不是布尔型数据，返回false。 |
| entity.setUserInt\(int index, int value\) | bool | 根据索引index设置用户自定义整型数据，若设置成功返回true，若索引无效或指向的数据不是整型数据，返回false。 |
| entity.setUserDouble\(int index, double value\) | bool | 根据索引index设置用户自定义浮点型数据，若设置成功返回true，若索引无效或指向的数据不是浮点型数据，返回false。 |
| entity.setUserBool\(int index, bool value\) | bool | 根据索引index设置用户自定义布尔型数据，若设置成功返回true，若索引无效或指向的数据不是布尔型数据，返回false。 |

