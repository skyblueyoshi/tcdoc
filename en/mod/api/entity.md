# Entity

## Entity Class

The Entity class represents an object with basic properties related to graphics and collision detection.

### Member

#### Coordinates and Graphics Member 

_note: all members read only when the entity is a player._

| Member | Type | Description |
| :--- | :---: | :--- |
| Entity.x | double | The x coordinate of the upper left corner of the entity. |
| Entity.y | double | The y coordinate of the upper left corner of the entity. |
| Entity.centerX | double | **\[ Read-only \]** Returns the center x coordinate of the entity. |
| Entity.centerY | double | **\[ Read-only \]** Returns the center y coordinate of the entity. |
| Entity.centerXi | int | **\[ Read-only \]** Returns the center grid x index of the entity. |
| Entity.centerYi | int | **\[ Read-only \]** Returns the center grid y index of the entity. |
| Entity.rightX | double | **\[ Read-only \]** Returns the x coordinate of the right border of entity. |
| Entity.bottomY | double | **\[ Read-only \]** Returns the y coordinate of the bottom border of entity. |
| Entity.speedX | double | The horizontal speed of the entity. |
| Entity.speedY | double | The vertical speed of the entity. |
| Entity.gravity | double | The gravitational acceleration of the entity. |
| Entity.width | int | **\[ Read-only \]** Returns the width of the hitbox. |
| Entity.height | int | **\[ Read-only \]** Returns the height of the hitbox. |
| Entity.direction | bool | Facing right if true, otherwise facing left. |
| Entity.rotateAngle | double | The rotation angle of the hitbox. |
| Entity.speedAngle | double | **\[ Read-only \]** Returns the vector angle of the current speed. |
| Entity.randX | double | **\[ Read-only \]** Return the random coordinates of the entity on the x-axis projection. |
| Entity.randY | double | **\[ Read-only \]** Return the random coordinates of the entity on the y-axis projection. |
| Entity.shape | Shape | **\[ Read-only \]** Returns the shape of the hitbox. |

#### Collision Member

_note: all members read only when the entity is a player._

| Member | Type | Description |
| :--- | :---: | :--- |
| Entity.stand | bool | **\[ Read-only \]** Returns whether the entity is standing. |
| Entity.isCollisionTop | bool | **\[ Read-only \]** Returns whether the top of the entity collides with the map. |
| Entity.isCollisionLeft | bool | **\[ Read-only \]** Returns whether the left of the entity collides with the map. |
| Entity.isCollisionRight | bool | **\[ Read-only \]** Returns whether the right of the entity collides with the map. |
| Entity.isCollisionStuck | bool | **\[ Read-only \]** Returns whether the entity is stuck inside the block. |
| Entity.isNoCollision | bool | **\[ Read-only \]** Returns whether the entity has not collided in any form. |
| Entity.onSlope | bool | **\[ Read-only \]** Returns whether the entity is standing on the slope. |
| Entity.hitbox | Hitbox | **\[ Read-only \]** If the entity is an axis-aligned rectangle, returns an axis-aligned hitbox, otherwise returns a rotating rectangular collision box. |
| Entity.aabb | Hitbox | **\[ Read-only \]** The axis-aligned hitbox when rotation angle is 0. |
| Entity.minAABB | Hitbox | **\[ Read-only \]** The smallest axis-aligned hitbox that completely wraps the entity. |
| Entity.allowCheckCollision | bool | Decide whether to check collision detection with the map. |

#### Rendering Related Member

_note: all members read only when the entity is a player._

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
      <td style="text-align:left">&#x5B9E;&#x4F53;&#x7ED8;&#x5236;&#x7684;&#x989C;&#x8272;&#x3002;&#xFF08;&#x9ED8;&#x8BA4;&#x4E3A;<em><code>COLOR_WHITE</code></em>&#xFF09;</td>
    </tr>
    <tr>
      <td style="text-align:left">Entity.frameTickTime</td>
      <td style="text-align:center">int</td>
      <td style="text-align:left">&#x5B9E;&#x4F53;&#x7ED8;&#x5236;&#x7528;&#x7684;&#x5E27;&#x8BA1;&#x65F6;&#x5668;&#x3002;&#xFF08;&#x6BCF;&#x5E27;&#x81EA;&#x589E;1&#xFF09;</td>
    </tr>
    <tr>
      <td style="text-align:left">Entity.frameIndex</td>
      <td style="text-align:center">int</td>
      <td style="text-align:left"><b>&#x3010;&#x53EA;&#x8BFB;&#x3011;</b>&#x5F53;&#x524D;&#x5B9E;&#x4F53;&#x5E27;&#x7D22;&#x5F15;&#xFF0C;&#x5373;<code>(frameTickTime/frameSpeed)%frames</code>&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">Entity.frameStyles</td>
      <td style="text-align:center">int</td>
      <td style="text-align:left"><b>&#x3010;&#x53EA;&#x8BFB;&#x3011;</b>&#x5B9E;&#x4F53;&#x6837;&#x5F0F;&#x6570;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">Entity.frames</td>
      <td style="text-align:center">int</td>
      <td style="text-align:left"><b>&#x3010;&#x53EA;&#x8BFB;&#x3011;</b>&#x5B9E;&#x4F53;&#x603B;&#x5E27;&#x6570;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">Entity.frameSpeed</td>
      <td style="text-align:center">int</td>
      <td style="text-align:left"><b>&#x3010;&#x53EA;&#x8BFB;&#x3011;</b>&#x5B9E;&#x4F53;&#x5E27;&#x5207;&#x6362;&#x5468;&#x671F;&#x3002;</td>
    </tr>
  </tbody>
</table>

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

