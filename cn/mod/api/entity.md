# 实体API

## 实体类（Entity Class）

**实体（Entity）**类表示拥有图形以及碰撞检测相关的基本属性的对象。

Npc类、Projectile类、Effect类、Player类的基类均为Entity类，都可以使用如下的成员属性和成员函数。

### 类成员属性

#### 坐标与图形属性（当实体为玩家时全部只读）

| 属性                 |   类型   | 描述                                                                 |
| ------------------ | :----: | ------------------------------------------------------------------ |
| Entity.x           | double | 实体左上角横坐标。                                                          |
| Entity.y           | double | 实体左上角纵坐标。                                                          |
| Entity.centerX     | double | **【只读】**实体正中间横坐标。                                                  |
| Entity.centerY     | double | **【只读】**实体正中间纵坐标。                                                  |
| Entity.centerXi    |   int  | **【只读】**实体正中间格子横坐标。                                                |
| Entity.centerYi    |   int  | **【只读】**实体正中间格子纵坐标。                                                |
| Entity.rightX      | double | **【只读】**实体最右侧横坐标。                                                  |
| Entity.bottomY     | double | **【只读】**实体最底部纵坐标。                                                  |
| Entity.speedX      | double | 实体横向速度。                                                            |
| Entity.speedY      | double | 实体纵向速度。                                                            |
| Entity.gravity     | double | 实体的重力加速度。                                                          |
| Entity.width       |   int  | **【只读】**实体碰撞箱宽度。                                                   |
| Entity.height      |   int  | **【只读】**实体碰撞箱高度。                                                   |
| Entity.direction   |  bool  | <p>实体朝向。<br>实体面朝左侧为false。</p><p>实体面朝右侧为true。</p><p>（当实体为玩家时只读）</p> |
| Entity.rotateAngle | double | 实体碰撞箱的旋转角度。                                                        |
| Entity.speedAngle  | double | **【只读】**当前实体运动速度的向量夹角。                                             |
| Entity.randX       | double | **【只读】**实体横向投影上的随机横坐标。                                             |
| Entity.randY       | double | **【只读】**实体纵向投影上的随机纵坐标。                                             |
| Entity.shape       |  Shape | **【只读】**实体碰撞箱形状。                                                   |

#### 碰撞检测属性

| 属性                         |   类型   | 描述                                     |
| -------------------------- | :----: | -------------------------------------- |
| Entity.stand               |  bool  | **【只读】**实体是否为站立状态（底部碰撞）。               |
| Entity.isCollisionTop      |  bool  | **【只读】**实体是否顶部发生碰撞。                    |
| Entity.isCollisionLeft     |  bool  | **【只读】**实体是否左侧发生碰撞。                    |
| Entity.isCollisionRight    |  bool  | **【只读】**实体是否右侧发生碰撞。                    |
| Entity.isCollisionStuck    |  bool  | **【只读】**实体是否卡在方块内部。                    |
| Entity.isNoCollision       |  bool  | **【只读】**实体是否没有发生任何形式的碰撞。               |
| Entity.onSlope             |  bool  | **【只读】**实体是否站在斜坡上。                     |
| Entity.hitbox              | Hitbox | **【只读】**若实体为轴对齐矩形，表轴对齐碰撞箱，否则表示旋转矩形碰撞箱。 |
| Entity.aabb                | Hitbox | **【只读】**实体旋转角度为0的轴对齐碰撞箱。               |
| Entity.minAABB             | Hitbox | **【只读】**完全包裹实体的最小轴对齐碰撞箱。               |
| Entity.allowCheckCollision |  bool  | 决定是否执行与方块的碰撞检测。                        |

#### 绘制相关属性（当实体为玩家时全部只读）

您可以通过修改如下属性来自定义实体的绘制方式。

| 属性                         |     类型    | 描述                                                                                                                                                                 |
| -------------------------- | :-------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Entity.spriteDefaultWidth  |    int    | **【只读】**实体默认绘制宽度。                                                                                                                                                  |
| Entity.spriteDefaultHeight |    int    | **【只读】**实体默认绘制高度。                                                                                                                                                  |
| Entity.spriteRect          | Rectangle | <p>实体绘制时在目标贴图的剪裁区域。<br><code>spriteRect.width</code>默认为<code>spriteDefaultWidth</code></p><p><code>spriteRect.height</code>默认为<code>spriteDefaultHeight</code></p> |
| Entity.spriteEx            |  SpriteEx | 实体绘制的拓展信息。                                                                                                                                                         |
| Entity.spriteOffsetX       |    int    | 实体绘制的横向偏移量。（默认为0.0）                                                                                                                                                |
| Entity.spriteOffsetY       |    int    | 实体绘制的纵向偏移量。（默认为0.0）                                                                                                                                                |
| Entity.color               |   Color   | 实体绘制的颜色。（默认为_`COLOR_WHITE`_）                                                                                                                                       |
| Entity.frameTickTime       |    int    | 实体绘制用的帧计时器。（每帧自增1）                                                                                                                                                 |
| Entity.frameIndex          |    int    | **【只读】**当前实体帧索引，即`(frameTickTime/frameSpeed)%frames`。                                                                                                              |
| Entity.frameStyles         |    int    | **【只读】**实体样式数。                                                                                                                                                     |
| Entity.frames              |    int    | **【只读】**实体总帧数。                                                                                                                                                     |
| Entity.frameSpeed          |    int    | **【只读】**实体帧切换周期。                                                                                                                                                   |

#### 其他属性

| 属性              |  类型 | 描述                  |
| --------------- | :-: | ------------------- |
| Entity.tickTime | int | **【只读】**实体的实际生存的时间。 |
| Entity.randSeed | int | **【只读】**实体的随机数种子。   |

### 类成员函数

#### 坐标与图形函数

| 函数                                               |   返回值  | 描述                    |
| ------------------------------------------------ | :----: | --------------------- |
| Entity:SetCenterX(double newCenterX)             |  void  | 将实体中心横坐标设为指定位置。       |
| Entity:SetCenterY(double newCenterY)             |  void  | 将实体中心纵坐标设为指定位置。       |
| Entity:GetAngleTo(double desX, double desY)      | double | 返回实体中心点到目标点的角度。       |
| Entity:GetAngleFrom(double srcX, double srcY)    | double | 返回来源点到实体中心点的角度。       |
| Entity:GetDistance(double otherX, double otherY) | double | 返回实体中心到指定点的距离。        |
| Entity:Rotate(double angle)                      |  void  | 在原有角度基础上继续旋转指定角度。     |
| Entity:RotateSpeed(double angle)                 |  void  | 在原有速度角度基础上继续旋转指定速度角度。 |

