---
description: 实体（Entity）类表示拥有图形以及碰撞检测相关的基本属性的对象。 Npc类、Projectile类、Effect类、Player类继承Entity类。
---

# Entity

## 属性

| 属性                                                                                                                                                                                                          |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <p><strong>double x</strong></p><p>实体左上角横坐标。</p>                                                                                                                                                            |
| <p>d<strong>ouble y</strong><br>实体左上角纵坐标。</p>                                                                                                                                                               |
| <p><strong>double centerX</strong><br><strong>【只读】</strong>实体正中间横坐标。</p>                                                                                                                                    |
| <p><strong>double centerY</strong><br><strong>【只读】</strong>实体正中间纵坐标。</p>                                                                                                                                    |
| <p><strong>int centerXi</strong><br><strong>【只读】</strong>实体正中间格子横坐标。</p>                                                                                                                                    |
| <p><strong>int centerYi</strong><br><strong>【只读】</strong>实体正中间格子纵坐标。</p>                                                                                                                                    |
| <p><strong>double rightX</strong><br><strong>【只读】</strong>实体最右侧横坐标。</p>                                                                                                                                     |
| <p><strong>double bottomY</strong><br><strong>【只读】</strong>实体最底部纵坐标。</p>                                                                                                                                    |
| <p><strong>double speedX</strong><br>实体横向速度。</p>                                                                                                                                                            |
| <p><strong>double speedY</strong><br>实体纵向速度。</p>                                                                                                                                                            |
| <p><strong>double gravity</strong><br>实体的重力加速度。</p>                                                                                                                                                         |
| <p><strong>int width</strong><br><strong>【只读】</strong>实体碰撞箱宽度。</p>                                                                                                                                          |
| <p><strong>int height</strong><br><strong>【只读】</strong>实体碰撞箱高度。</p>                                                                                                                                         |
| <p><strong>bool direction</strong><br>实体朝向。<br>实体面朝左侧为false。</p><p>实体面朝右侧为true。</p><p>（当实体为玩家时只读）</p>                                                                                                       |
| <p><strong>double rotateAngle</strong><br>实体碰撞箱的旋转角度。</p>                                                                                                                                                   |
| <p><strong>double speedAngle</strong><br><strong>【只读】</strong>当前实体运动速度的向量夹角。</p>                                                                                                                            |
| <p><strong>double randX</strong><br><strong>【只读】</strong>实体横向投影上的随机横坐标。</p>                                                                                                                                 |
| <p><strong>double randY</strong><br><strong>【只读】</strong>实体纵向投影上的随机纵坐标。</p>                                                                                                                                 |
| <p>S<strong>hape shape</strong><br><strong>【只读】</strong>实体碰撞箱形状。</p>                                                                                                                                        |
| <p><strong>bool stand</strong><br><strong>【只读】</strong>实体是否为站立状态（底部碰撞）。</p>                                                                                                                                 |
| <p><strong>bool isCollisionTop</strong><br><strong>【只读】</strong>实体是否顶部发生碰撞。</p>                                                                                                                             |
| <p><strong>bool isCollisionLeft</strong><br><strong>【只读】</strong>实体是否左侧发生碰撞。</p>                                                                                                                            |
| <p><strong>bool isCollisionRight</strong><br><strong>【只读】</strong>实体是否右侧发生碰撞。</p>                                                                                                                           |
| <p><strong>bool isCollisionStuck</strong><br><strong>【只读】</strong>实体是否卡在方块内部。</p>                                                                                                                           |
| <p><strong>bool isNoCollision</strong><br><strong>【只读】</strong>实体是否没有发生任何形式的碰撞。</p>                                                                                                                         |
| <p><strong>bool onSlope</strong><br>【只读<strong>】</strong>实体是否站在斜坡上。</p>                                                                                                                                     |
| <p><strong>Hitbox hitbox</strong><br><strong>【只读】</strong>若实体为轴对齐矩形，表轴对齐碰撞箱，否则表示旋转矩形碰撞箱。</p>                                                                                                                |
| <p><strong>Hitbox aabb</strong><br><strong>【只读】</strong>实体旋转角度为0的轴对齐碰撞箱。</p>                                                                                                                                |
| <p><strong>Hitbox minAABB</strong><br><strong>【只读】</strong>完全包裹实体的最小轴对齐碰撞箱。</p>                                                                                                                             |
| <p><strong>bool allowCheckCollision</strong><br>决定是否执行与方块的碰撞检测。</p>                                                                                                                                         |
| <p><strong>int spriteDefaultWidth</strong><br><strong>【只读】</strong>实体默认绘制宽度。</p>                                                                                                                            |
| <p><strong>int spriteDefaultHeight</strong><br><strong>【只读】</strong>实体默认绘制高度。</p>                                                                                                                           |
| <p><strong>Rectangle spriteRect</strong><br>实体绘制时在目标贴图的剪裁区域。<br><code>spriteRect.width</code>默认为<code>spriteDefaultWidth</code></p><p><code>spriteRect.height</code>默认为<code>spriteDefaultHeight</code></p> |
| <p><strong>SpriteEx spriteEx</strong><br>实体绘制的拓展信息。</p>                                                                                                                                                     |
| <p><strong>int spriteOffsetX</strong><br>实体绘制的横向偏移量。（默认为0.0）</p>                                                                                                                                            |
| <p><strong>int spriteOffsetY</strong><br>实体绘制的纵向偏移量。（默认为0.0）</p>                                                                                                                                            |
| <p><strong>Color color</strong><br>实体绘制的颜色。（默认为<em><code>COLOR_WHITE</code></em>）</p>                                                                                                                       |
| <p><strong>int frameTickTime</strong><br>实体绘制用的帧计时器。（每帧自增1）</p>                                                                                                                                             |
| <p><strong>int frameIndex</strong><br><strong>【只读】</strong>当前实体帧索引，即<code>(frameTickTime/frameSpeed)%frames</code>。</p>                                                                                     |
| <p><strong>int frameStyles</strong><br><strong>【只读】</strong>实体样式数。</p>                                                                                                                                      |
| <p><strong>int frames</strong><br><strong>【只读】</strong>实体总帧数。</p>                                                                                                                                           |
| <p><strong>int frameSpeed</strong><br><strong>【只读】</strong>实体帧切换周期。</p>                                                                                                                                     |
| <p><strong>int tickTime</strong><br><strong>【只读】</strong>实体的实际生存的时间。</p>                                                                                                                                    |
| <p><strong>int randSeed</strong><br><strong>【只读】</strong>实体的随机数种子。</p>                                                                                                                                      |

## 函数

| 函数                                                                                                |
| ------------------------------------------------------------------------------------------------- |
| <p><strong>void Entity:SetCenterX(double newCenterX)</strong><br>将实体中心横坐标设为指定位置。</p>              |
| <p><strong>void Entity:SetCenterY(double newCenterY)</strong><br>将实体中心纵坐标设为指定位置。</p>              |
| <p><strong>double Entity:GetAngleTo(double desX, double desY)</strong><br>返回实体中心点到目标点的角度。</p>     |
| <p><strong>double Entity:GetAngleFrom(double srcX, double srcY)</strong><br>返回来源点到实体中心点的角度。</p>   |
| <p><strong>double Entity:GetDistance(double otherX, double otherY)</strong><br>返回实体中心到指定点的距离。</p> |
| <p><strong>void Entity:Rotate(double angle)</strong><br>在原有角度基础上继续旋转指定角度。</p>                     |
| <p><strong>void Entity:RotateSpeed(double angle)</strong><br>在原有速度角度基础上继续旋转指定速度角度。</p>            |

