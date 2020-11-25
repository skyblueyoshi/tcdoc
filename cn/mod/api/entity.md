# 实体API

## 实体类（Entity Class）

**实体（Entity）**类表示拥有图形以及碰撞检测相关的基本属性的对象。

Npc类、Projectile类、Effect类的基类均为Entity类，都可以使用如下的成员属性和成员函数。

### 类成员属性

#### 坐标与图形属性

<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x5C5E;&#x6027;</th>
      <th style="text-align:center">&#x7C7B;&#x578B;</th>
      <th style="text-align:left">&#x63CF;&#x8FF0;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">Entity.x</td>
      <td style="text-align:center">double</td>
      <td style="text-align:left">&#x5B9E;&#x4F53;&#x5DE6;&#x4E0A;&#x89D2;&#x6A2A;&#x5750;&#x6807;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">Entity.y</td>
      <td style="text-align:center">double</td>
      <td style="text-align:left">&#x5B9E;&#x4F53;&#x5DE6;&#x4E0A;&#x89D2;&#x7EB5;&#x5750;&#x6807;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">Entity.centerX</td>
      <td style="text-align:center">double</td>
      <td style="text-align:left"><b>&#x3010;&#x53EA;&#x8BFB;&#x3011;</b>&#x5B9E;&#x4F53;&#x6B63;&#x4E2D;&#x95F4;&#x6A2A;&#x5750;&#x6807;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">Entity.centerY</td>
      <td style="text-align:center">double</td>
      <td style="text-align:left"><b>&#x3010;&#x53EA;&#x8BFB;&#x3011;</b>&#x5B9E;&#x4F53;&#x6B63;&#x4E2D;&#x95F4;&#x7EB5;&#x5750;&#x6807;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">Entity.centerXi</td>
      <td style="text-align:center">int</td>
      <td style="text-align:left"><b>&#x3010;&#x53EA;&#x8BFB;&#x3011;</b>&#x5B9E;&#x4F53;&#x6B63;&#x4E2D;&#x95F4;&#x683C;&#x5B50;&#x6A2A;&#x5750;&#x6807;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">Entity.centerYi</td>
      <td style="text-align:center">int</td>
      <td style="text-align:left"><b>&#x3010;&#x53EA;&#x8BFB;&#x3011;</b>&#x5B9E;&#x4F53;&#x6B63;&#x4E2D;&#x95F4;&#x683C;&#x5B50;&#x7EB5;&#x5750;&#x6807;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">Entity.rightX</td>
      <td style="text-align:center">double</td>
      <td style="text-align:left"><b>&#x3010;&#x53EA;&#x8BFB;&#x3011;</b>&#x5B9E;&#x4F53;&#x6700;&#x53F3;&#x4FA7;&#x6A2A;&#x5750;&#x6807;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">Entity.bottomY</td>
      <td style="text-align:center">double</td>
      <td style="text-align:left"><b>&#x3010;&#x53EA;&#x8BFB;&#x3011;</b>&#x5B9E;&#x4F53;&#x6700;&#x5E95;&#x90E8;&#x7EB5;&#x5750;&#x6807;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">Entity.speedX</td>
      <td style="text-align:center">double</td>
      <td style="text-align:left">&#x5B9E;&#x4F53;&#x6A2A;&#x5411;&#x901F;&#x5EA6;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">Entity.speedY</td>
      <td style="text-align:center">double</td>
      <td style="text-align:left">&#x5B9E;&#x4F53;&#x7EB5;&#x5411;&#x901F;&#x5EA6;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">Entity.width</td>
      <td style="text-align:center">int</td>
      <td style="text-align:left"><b>&#x3010;&#x53EA;&#x8BFB;&#x3011;</b>&#x5B9E;&#x4F53;&#x78B0;&#x649E;&#x7BB1;&#x5BBD;&#x5EA6;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">Entity.height</td>
      <td style="text-align:center">int</td>
      <td style="text-align:left"><b>&#x3010;&#x53EA;&#x8BFB;&#x3011;</b>&#x5B9E;&#x4F53;&#x78B0;&#x649E;&#x7BB1;&#x9AD8;&#x5EA6;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">Entity.direction</td>
      <td style="text-align:center">bool</td>
      <td style="text-align:left">
        <p>&#x5B9E;&#x4F53;&#x671D;&#x5411;&#x3002;
          <br />&#x5B9E;&#x4F53;&#x9762;&#x671D;&#x5DE6;&#x4FA7;&#x4E3A;false&#x3002;</p>
        <p>&#x5B9E;&#x4F53;&#x9762;&#x671D;&#x53F3;&#x4FA7;&#x4E3A;true&#x3002;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Entity.rotateAngle</td>
      <td style="text-align:center">double</td>
      <td style="text-align:left">&#x5B9E;&#x4F53;&#x78B0;&#x649E;&#x7BB1;&#x7684;&#x65CB;&#x8F6C;&#x89D2;&#x5EA6;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">Entity.speedAngle</td>
      <td style="text-align:center">double</td>
      <td style="text-align:left"><b>&#x3010;&#x53EA;&#x8BFB;&#x3011;</b>&#x5F53;&#x524D;&#x5B9E;&#x4F53;&#x8FD0;&#x52A8;&#x901F;&#x5EA6;&#x7684;&#x5411;&#x91CF;&#x5939;&#x89D2;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">Entity.randX</td>
      <td style="text-align:center">double</td>
      <td style="text-align:left"><b>&#x3010;&#x53EA;&#x8BFB;&#x3011;</b>&#x5B9E;&#x4F53;&#x6A2A;&#x5411;&#x6295;&#x5F71;&#x4E0A;&#x7684;&#x968F;&#x673A;&#x6A2A;&#x5750;&#x6807;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">Entity.randY</td>
      <td style="text-align:center">double</td>
      <td style="text-align:left"><b>&#x3010;&#x53EA;&#x8BFB;&#x3011;</b>&#x5B9E;&#x4F53;&#x7EB5;&#x5411;&#x6295;&#x5F71;&#x4E0A;&#x7684;&#x968F;&#x673A;&#x7EB5;&#x5750;&#x6807;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">Entity.shape</td>
      <td style="text-align:center">Shape</td>
      <td style="text-align:left">&#x5B9E;&#x4F53;&#x78B0;&#x649E;&#x7BB1;&#x5F62;&#x72B6;&#x3002;</td>
    </tr>
  </tbody>
</table>

#### 碰撞检测属性

| 属性 | 类型 | 描述 |
| :--- | :---: | :--- |
| Entity.stand | bool | **【只读】**实体是否为站立状态（底部碰撞）。 |
| Entity.isCollisionTop | bool | **【只读】**实体是否顶部发生碰撞。 |
| Entity.isCollisionLeft | bool | **【只读】**实体是否左侧发生碰撞。 |
| Entity.isCollisionRight | bool | **【只读】**实体是否右侧发生碰撞。 |
| Entity.isCollisionStuck | bool | **【只读】**实体是否卡在方块内部。 |
| Entity.isNoCollision | bool | **【只读】**实体是否没有发生任何形式的碰撞。 |
| Entity.onSlope | bool | **【只读】**实体是否站在斜坡上。 |
| Entity.hitbox | Hitbox | **【只读】**若实体为轴对齐矩形，表轴对齐碰撞箱，否则表示旋转矩形碰撞箱。 |
| Entity.aabb | Hitbox | **【只读】**实体旋转角度为0的轴对齐碰撞箱。 |
| Entity.minAABB | Hitbox | **【只读】**完全包裹实体的最小轴对齐碰撞箱。 |

#### 绘制相关属性

您可以通过修改如下属性来自定义实体的绘制方式。

<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x5C5E;&#x6027;</th>
      <th style="text-align:center">&#x7C7B;&#x578B;</th>
      <th style="text-align:left">&#x63CF;&#x8FF0;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">Entity.spriteDefaultWidth</td>
      <td style="text-align:center">int</td>
      <td style="text-align:left"><b>&#x3010;&#x53EA;&#x8BFB;&#x3011;</b>&#x5B9E;&#x4F53;&#x9ED8;&#x8BA4;&#x7ED8;&#x5236;&#x5BBD;&#x5EA6;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">Entity.spriteDefaultHeight</td>
      <td style="text-align:center">int</td>
      <td style="text-align:left"><b>&#x3010;&#x53EA;&#x8BFB;&#x3011;</b>&#x5B9E;&#x4F53;&#x9ED8;&#x8BA4;&#x7ED8;&#x5236;&#x9AD8;&#x5EA6;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">Entity.spriteRect</td>
      <td style="text-align:center">Rectangle</td>
      <td style="text-align:left">
        <p>&#x5B9E;&#x4F53;&#x7ED8;&#x5236;&#x65F6;&#x5728;&#x76EE;&#x6807;&#x8D34;&#x56FE;&#x7684;&#x526A;&#x88C1;&#x533A;&#x57DF;&#x3002;
          <br
          /><code>spriteRect.width</code>&#x9ED8;&#x8BA4;&#x4E3A;<code>spriteDefaultWidth</code>
        </p>
        <p><code>spriteRect.height</code>&#x9ED8;&#x8BA4;&#x4E3A;<code>spriteDefaultHeight</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Entity.spriteEx</td>
      <td style="text-align:center">SpriteEx</td>
      <td style="text-align:left">&#x5B9E;&#x4F53;&#x7ED8;&#x5236;&#x7684;&#x62D3;&#x5C55;&#x4FE1;&#x606F;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">Entity.spriteOffsetX</td>
      <td style="text-align:center">int</td>
      <td style="text-align:left">&#x5B9E;&#x4F53;&#x7ED8;&#x5236;&#x7684;&#x6A2A;&#x5411;&#x504F;&#x79FB;&#x91CF;&#x3002;&#xFF08;&#x9ED8;&#x8BA4;&#x4E3A;0.0&#xFF09;</td>
    </tr>
    <tr>
      <td style="text-align:left">Entity.spriteOffsetY</td>
      <td style="text-align:center">int</td>
      <td style="text-align:left">&#x5B9E;&#x4F53;&#x7ED8;&#x5236;&#x7684;&#x7EB5;&#x5411;&#x504F;&#x79FB;&#x91CF;&#x3002;&#xFF08;&#x9ED8;&#x8BA4;&#x4E3A;0.0&#xFF09;</td>
    </tr>
    <tr>
      <td style="text-align:left">Entity.color</td>
      <td style="text-align:center">Color</td>
      <td style="text-align:left">&#x5B9E;&#x4F53;&#x7ED8;&#x5236;&#x7684;&#x989C;&#x8272;&#x3002;&#xFF08;&#x9ED8;&#x8BA4;&#x4E3A;<code>COLOR_WHITE</code>&#xFF09;</td>
    </tr>
  </tbody>
</table>

#### 用户自定义数据

您可以通过如下API，维护针对当前实体的用户自定义数据。

| 属性 | 类型 | 描述 |
| :--- | :---: | :--- |
| Entity.state | int | 实体的当前在简单有限状态机中的状态。 |
| Entity.ivar | UserVar&lt;int&gt; | 实体的用户自定义整型数据。 |
| Entity.dvar | UserVar&lt;double&gt; | 实体的用户自定义浮点型数据。 |
| Entity.flags | Flags | 实体的用户自定义布尔型数据。 |

#### 其他属性

| 属性 | 类型 | 描述 |
| :--- | :---: | :--- |
| Entity.tickTime | int | **【只读】**实体的实际生存的时间。 |
| Entity.randSeed | int | **【只读】**实体的随机数种子。 |

### 类成员函数

#### 坐标与图形函数

| 函数 | 返回值 | 描述 |
| :--- | :---: | :--- |
| Entity:SetCenterX\(double newCenterX\) | void | 将实体中心横坐标设为指定位置。 |
| Entity:SetCenterY\(double newCenterY\) | void | 将实体中心纵坐标设为指定位置。 |
| Entity:GetAngleTo\(double desX, double desY\) | double | 返回实体中心点到目标点的角度。 |
| Entity:GetAngleFrom\(double srcX, double srcY\) | double | 返回来源点到实体中心点的角度。 |
| Entity:GetDistance\(double otherX, double otherY\) | double | 返回实体中心到指定点的距离。 |
| Entity:Rotate\(double angle\) | void | 在原有角度基础上继续旋转指定角度。 |
| Entity:RotateSpeed\(double angle\) | void | 在原有速度角度基础上继续旋转指定速度角度。 |



