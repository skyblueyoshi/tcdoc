# Entity

### 属性

| 属性                                                                                                                                                                                         |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| <p>double x</p><p>实体左上角横坐标。</p>                                                                                                                                                            |
| <p>double y<br>实体左上角纵坐标。</p>                                                                                                                                                               |
| <p>double centerX<br><strong>【只读】</strong>实体正中间横坐标。</p>                                                                                                                                    |
| <p>double centerY<br><strong>【只读】</strong>实体正中间纵坐标。</p>                                                                                                                                    |
| <p>int centerXi<br><strong>【只读】</strong>实体正中间格子横坐标。</p>                                                                                                                                    |
| <p>int centerYi<br><strong>【只读】</strong>实体正中间格子纵坐标。</p>                                                                                                                                    |
| <p>double rightX<br><strong>【只读】</strong>实体最右侧横坐标。</p>                                                                                                                                     |
| <p>double bottomY<br><strong>【只读】</strong>实体最底部纵坐标。</p>                                                                                                                                    |
| <p>double speedX<br>实体横向速度。</p>                                                                                                                                                            |
| <p>double speedY<br>实体纵向速度。</p>                                                                                                                                                            |
| <p>double gravity<br>实体的重力加速度。</p>                                                                                                                                                         |
| <p>int width<br><strong>【只读】</strong>实体碰撞箱宽度。</p>                                                                                                                                          |
| <p>int height<br><strong>【只读】</strong>实体碰撞箱高度。</p>                                                                                                                                         |
| <p>bool direction<br>实体朝向。<br>实体面朝左侧为false。</p><p>实体面朝右侧为true。</p><p>（当实体为玩家时只读）</p>                                                                                                       |
| <p>double rotateAngle<br>实体碰撞箱的旋转角度。</p>                                                                                                                                                   |
| <p>double speedAngle<br><strong>【只读】</strong>当前实体运动速度的向量夹角。</p>                                                                                                                            |
| <p>double randX<br><strong>【只读】</strong>实体横向投影上的随机横坐标。</p>                                                                                                                                 |
| <p>double randY<br><strong>【只读】</strong>实体纵向投影上的随机纵坐标。</p>                                                                                                                                 |
| <p>Shape shape<br><strong>【只读】</strong>实体碰撞箱形状。</p>                                                                                                                                        |
| <p>bool stand<br><strong>【只读】</strong>实体是否为站立状态（底部碰撞）。</p>                                                                                                                                 |
| <p>bool isCollisionTop<br><strong>【只读】</strong>实体是否顶部发生碰撞。</p>                                                                                                                             |
| <p>bool isCollisionLeft<br><strong>【只读】</strong>实体是否左侧发生碰撞。</p>                                                                                                                            |
| <p>bool isCollisionRight<br><strong>【只读】</strong>实体是否右侧发生碰撞。</p>                                                                                                                           |
| <p>bool isCollisionStuck<br><strong>【只读】</strong>实体是否卡在方块内部。</p>                                                                                                                           |
| <p>bool isNoCollision<br><strong>【只读】</strong>实体是否没有发生任何形式的碰撞。</p>                                                                                                                         |
| <p>bool onSlope<br>【只读<strong>】</strong>实体是否站在斜坡上。</p>                                                                                                                                     |
| <p>Hitbox hitbox<br><strong>【只读】</strong>若实体为轴对齐矩形，表轴对齐碰撞箱，否则表示旋转矩形碰撞箱。</p>                                                                                                                |
| <p>Hitbox aabb<br><strong>【只读】</strong>实体旋转角度为0的轴对齐碰撞箱。</p>                                                                                                                                |
| <p>Hitbox minAABB<br><strong>【只读】</strong>完全包裹实体的最小轴对齐碰撞箱。</p>                                                                                                                             |
| <p>bool allowCheckCollision<br>决定是否执行与方块的碰撞检测。</p>                                                                                                                                         |
| <p>int spriteDefaultWidth<br><strong>【只读】</strong>实体默认绘制宽度。</p>                                                                                                                            |
| <p>int spriteDefaultHeight<br><strong>【只读】</strong>实体默认绘制高度。</p>                                                                                                                           |
| <p>Rectangle spriteRect<br>实体绘制时在目标贴图的剪裁区域。<br><code>spriteRect.width</code>默认为<code>spriteDefaultWidth</code></p><p><code>spriteRect.height</code>默认为<code>spriteDefaultHeight</code></p> |
| <p>SpriteEx spriteEx<br>实体绘制的拓展信息。</p>                                                                                                                                                     |
| <p>int spriteOffsetX<br>实体绘制的横向偏移量。（默认为0.0）</p>                                                                                                                                            |
| <p>int spriteOffsetY<br>实体绘制的纵向偏移量。（默认为0.0）</p>                                                                                                                                            |
| <p>Color color<br>实体绘制的颜色。（默认为<em><code>COLOR_WHITE</code></em>）</p>                                                                                                                       |
| <p>int frameTickTime<br>实体绘制用的帧计时器。（每帧自增1）</p>                                                                                                                                             |
| <p>int frameIndex<br><strong>【只读】</strong>当前实体帧索引，即<code>(frameTickTime/frameSpeed)%frames</code>。</p>                                                                                     |
| <p>int frameStyles<br><strong>【只读】</strong>实体样式数。</p>                                                                                                                                      |
| <p>int frames<br><strong>【只读】</strong>实体总帧数。</p>                                                                                                                                           |
| <p>int frameSpeed<br><strong>【只读】</strong>实体帧切换周期。</p>                                                                                                                                     |
| <p>int tickTime<br><strong>【只读】</strong>实体的实际生存的时间。</p>                                                                                                                                    |
| <p>int randSeed<br><strong>【只读】</strong>实体的随机数种子。</p>                                                                                                                                      |

### 函数

| 函数                                                                               |
| -------------------------------------------------------------------------------- |
| <p>void Entity:SetCenterX(double newCenterX)<br>将实体中心横坐标设为指定位置。</p>              |
| <p>void Entity:SetCenterY(double newCenterY)<br>将实体中心纵坐标设为指定位置。</p>              |
| <p>double Entity:GetAngleTo(double desX, double desY)<br>返回实体中心点到目标点的角度。</p>     |
| <p>double Entity:GetAngleFrom(double srcX, double srcY)<br>返回来源点到实体中心点的角度。</p>   |
| <p>double Entity:GetDistance(double otherX, double otherY)<br>返回实体中心到指定点的距离。</p> |
| <p>void Entity:Rotate(double angle)<br>在原有角度基础上继续旋转指定角度。</p>                     |
| <p>void Entity:RotateSpeed(double angle)<br>在原有速度角度基础上继续旋转指定速度角度。</p>            |

