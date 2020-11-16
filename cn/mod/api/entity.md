# 实体API

实体（entity）用于表示实体图形以及碰撞检测相关的基本属性。npc、projectile、effect的基类均为entity，都可以使用如下的成员属性和成员函数。

## 成员属性

如下是实体的成员属性，请按照`变量名.属性名`来使用这些属性。

### 坐标与图形属性

<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x5C5E;&#x6027;</th>
      <th style="text-align:left">&#x7C7B;&#x578B;</th>
      <th style="text-align:left">&#x63CF;&#x8FF0;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">entity.x</td>
      <td style="text-align:left">double</td>
      <td style="text-align:left">&#x5B9E;&#x4F53;&#x5DE6;&#x4E0A;&#x89D2;&#x6A2A;&#x5750;&#x6807;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">entity.y</td>
      <td style="text-align:left">double</td>
      <td style="text-align:left">&#x5B9E;&#x4F53;&#x5DE6;&#x4E0A;&#x89D2;&#x7EB5;&#x5750;&#x6807;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">entity.speedX</td>
      <td style="text-align:left">double</td>
      <td style="text-align:left">&#x5B9E;&#x4F53;&#x6A2A;&#x5411;&#x901F;&#x5EA6;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">entity.speedY</td>
      <td style="text-align:left">double</td>
      <td style="text-align:left">&#x5B9E;&#x4F53;&#x7EB5;&#x5411;&#x901F;&#x5EA6;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">entity.width</td>
      <td style="text-align:left">int</td>
      <td style="text-align:left">&#x3010;&#x53EA;&#x8BFB;&#x3011;&#x5B9E;&#x4F53;&#x78B0;&#x649E;&#x7BB1;&#x5BBD;&#x5EA6;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">entity.height</td>
      <td style="text-align:left">int</td>
      <td style="text-align:left">&#x3010;&#x53EA;&#x8BFB;&#x3011;&#x5B9E;&#x4F53;&#x78B0;&#x649E;&#x7BB1;&#x9AD8;&#x5EA6;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">entity.direction</td>
      <td style="text-align:left">bool</td>
      <td style="text-align:left">
        <p>&#x5B9E;&#x4F53;&#x671D;&#x5411;&#x3002;
          <br />&#x5B9E;&#x4F53;&#x9762;&#x671D;&#x5DE6;&#x4FA7;&#x4E3A;false&#x3002;</p>
        <p>&#x5B9E;&#x4F53;&#x9762;&#x671D;&#x53F3;&#x4FA7;&#x4E3A;true&#x3002;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">entity.rotateAngle</td>
      <td style="text-align:left">double</td>
      <td style="text-align:left">&#x5B9E;&#x4F53;&#x65CB;&#x8F6C;&#x89D2;&#x5EA6;&#x3002;</td>
    </tr>
  </tbody>
</table>

### 碰撞检测属性

| 属性 | 类型 | 描述 |
| :--- | :--- | :--- |
| entity.stand | bool | 【只读】实体是否为站立状态（底部碰撞）。 |
| entity.isCollisionTop | bool | 【只读】实体是否顶部发生碰撞。 |
| entity.isCollisionLeft | bool | 【只读】实体是否左侧发生碰撞。 |
| entity.isCollisionRight | bool | 【只读】实体是否右侧发生碰撞。 |
| entity.isCollisionStuck | bool | 【只读】实体是否卡在方块内部。 |
| entity.onSlope | bool | 【只读】实体是否站在斜坡上。 |

## 成员函数

如下实体的成员函数，请按照`变量名:函数名(参数1, 参数2, ...)`来使用这些函数。

### 坐标与图形函数

| 函数 | 返回值 | 描述 |
| :--- | :---: | :--- |
| entity:getCenterX\(\) | double | 返回实体正中间横坐标。 |
| entity:getCenterY\(\) | double | 返回实体正中间纵坐标。 |
| entity:setCenterX\(\) | void | 将实体中心横坐标设为指定位置。 |
| entity:setCenterY\(\) | void | 将实体中心纵坐标设为指定位置。 |
| entity:getRightX\(\) | double | 返回实体最右侧横坐标。 |
| entity:getBottomY\(\) | double | 返回实体最底部纵坐标。 |
| entity:randX\(\) | double | 返回实体横向投影上的随机横坐标。 |
| entity:randY\(\) | double | 返回实体纵向投影上的随机纵坐标。 |
| entity:getAngleTo\(double desX, double desY\) | double | 返回实体中心点到目标点的角度。 |
| entity:getAngleFrom\(double srcX, double srcY\) | double | 返回来源点到实体中心点的角度。 |
| entity:getDistance\(double otherX, double otherY\) | double | 返回实体中心到指定点的距离。 |
| entity:rotate\(double angle\) | void | 在原有角度基础上继续旋转指定角度。 |

### 碰撞检测函数

如下是当前实体的碰撞检测相关API。

| API | 返回值 | 描述 |
| :--- | :---: | :--- |
| entity:getHitbox\(\) | Hitbox | 若实体为轴对齐矩形，返回轴对齐碰撞箱，否则返回旋转矩形碰撞箱。 |
| entity:getAABB\(\) | Hitbox | 返回实体旋转角度为0的轴对齐碰撞箱。 |
| entity:getMinAABB\(\) | Hitbox | 返回完全包裹实体的最小轴对齐碰撞箱。 |
| entity:isNoCollision\(\) | bool | 返回实体是否没有发生任何形式的碰撞。 |

### 用户自定义数据

您可以通过如下API，维护针对当前实体的用户自定义数据。在使用用户自定义数据之前，您需要在对应的初始化函数中申请自定义数据，得到自定义数据的索引，注意该索引为一个大于0的整数。之后，您可以使用这个索引来获取或修改自定义数据。

| API | 返回值 | 描述 |
| :--- | :---: | :--- |
| entity:applyUserInt\(\) | int | 申请一个用户自定义的整型数据，初始值为0，返回指向该数据的索引。 |
| entity:applyUserDouble\(\) | int | 申请一个用户自定义的浮点型数据，初始值为0.0，返回指向该数据的索引。 |
| entity:applyUserBool\(\) | int | 申请一个用户自定义的布尔型数据，初始值为false，返回指向该数据的索引。 |
| entity:userInt\(int index\) | int | 根据索引index返回用户自定义整型数据，若索引无效或指向的数据不是整型数据，返回0。 |
| entity:userDouble\(int index\) | double | 根据索引index返回用户自定义浮点型数据，若索引无效或指向的数据不是浮点型数据，返回0.0。 |
| entity:userBool\(int index\) | bool | 根据索引index返回用户自定义布尔型数据，若索引无效或指向的数据不是布尔型数据，返回false。 |
| entity:setUserInt\(int index, int value\) | bool | 根据索引index设置用户自定义整型数据，若设置成功返回true，若索引无效或指向的数据不是整型数据，返回false。 |
| entity:setUserDouble\(int index, double value\) | bool | 根据索引index设置用户自定义浮点型数据，若设置成功返回true，若索引无效或指向的数据不是浮点型数据，返回false。 |
| entity:setUserBool\(int index, bool value\) | bool | 根据索引index设置用户自定义布尔型数据，若设置成功返回true，若索引无效或指向的数据不是布尔型数据，返回false。 |

