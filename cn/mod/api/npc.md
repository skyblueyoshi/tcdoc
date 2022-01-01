# NPC API

NPC泛指除了玩家之外的所有生物，如动物、敌怪、村民、BOSS等。

## 钩子函数（NPC脚本：contents/npc\_ai/...）

### void Init()

```lua
function Init()
    
end
```

NPC生成时调用一次该函数。

### void Update()

```lua
function Update()
    
end
```

NPC每帧运行时调用，您可以在该函数内编写运动等逻辑。

### void PreUpdate()

```lua
function PreUpdate()
    
end
```

NPC每帧运行`Update()`函数前调用。通常用于在原逻辑前插入新逻辑。

### void PostUpdate()

```lua
function PostUpdate()
    
end
```

NPC每帧运行`Update()`函数后调用。通常用于追加逻辑。

### void UpdateSkeleton(Skeleton skeleton)

```lua
function UpdateSkeleton(skeleton)
    
end
```

若NPC拥有骨骼模型，每帧执行完`PostUpdate`后调用，用于处理自定义骨骼模型逻辑。执行完该函数后，会对所有骨骼模型关节重新计算。

* `skeleton`表示当前NPC的骨骼模型。

### void PreUpdateSkeleton(Skeleton skeleton)

```lua
function PreUpdateSkeleton(skeleton)
    
end
```

NPC每帧运行`UpdateSkeleton(Skeleton skeleton)`函数前调用。通常用于在使用AI重用后在原逻辑前插入新的骨骼模型逻辑。

* `skeleton`表示当前NPC的骨骼模型。

### void PostUpdateSkeleton(Skeleton skeleton)

```lua
function PostUpdateSkeleton(skeleton)
    
end
```

NPC每帧运行`UpdateSkeleton(Skeleton skeleton)`函数，并将全部骨骼关节进行修正后调用。当前函数中所有骨骼关节为实际作用数据。

* `skeleton`表示当前NPC的骨骼模型。

### void OnDraw()

```lua
function OnDraw()
    
end
```

NPC每帧绘制前调用，在该函数内编写自定义绘制属性。不使用该钩子函数时采取默认处理方式。

### void OnKilled()

```lua
function OnKilled()
    
end
```

NPC死亡时调用一次该函数。

### void OnTileCollide(double oldSpeedX, double oldSpeedY)

```lua
function OnTileCollide(oldSpeedX, oldSpeedY)
    
end
```

NPC与图块碰撞时调用该函数。

* `oldSpeedX`和`oldSpeedY`表示击中实心图块前一帧的横向和纵向速度。

## NPC通用模块（NpcUtils）

| 函数                                                                                                 |       返回值       | 描述                                                                                                                                                |
| -------------------------------------------------------------------------------------------------- | :-------------: | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| NpcUtils.Create(int id, double x, double y, double speedX = 0.0, double speedY = 0.0)              |       Npc       | <p>在指定位置创建一个NPC，返回创建好的NPC实体。<br><code>id</code>：NPC的ID。<code>x</code>和<code>y</code>：创建NPC的坐标。<code>speedX</code>和<code>speedY</code>：初始运动速度。</p> |
| NpcUtils.SearchByRect(double x, double y, int width, int height)                                   | ArrayList\<Npc> | 返回包含于指定矩形区域内部的所有NPC列表。                                                                                                                            |
| NpcUtils.SearchByCircle(double centerX, double centerY, int radius)                                | ArrayList\<Npc> | 返回包含于指定圆形区域内部的所有NPC列表。                                                                                                                            |
| NpcUtils.SearchNearestNpc(double centerX, double centerY, int radius, bool noCrossTiles = false)   |     Npc/nil     | 搜索在指定圆形区域内部距离圆心最近的NPC，返回该NPC。若结果不存在，返回nil。`noCrossTiles`表示是否排除中心到圆心的连线被图格遮挡的NPC。                                                                  |
| NpcUtils.SearchNearestEnemy(double centerX, double centerY, int radius, bool noCrossTiles = false) |     Npc/nil     | 搜索在指定圆形区域内部距离圆心最近的敌对NPC，返回该NPC。若结果不存在，返回nil。noCrossTiles表示是否排除中心到圆心的连线被图格遮挡的NPC。                                                                  |

## NPC类（Npc Class，继承自Entity Class）

**NPC**类表示具有生物基本信息的非玩家实体类。

在编写NPC AI脚本时，**self表示当前正在操作的NPC类**。

### 父类

该类的父类为[Entity类](entity.md#shi-ti-lei-entity-class)。可直接使用该父类的类成员属性与类成员函数。

### 类成员属性

| 属性                      |          类型          | 描述                                               |
| ----------------------- | :------------------: | ------------------------------------------------ |
| Npc.id                  |          int         | **【只读】**当前NPC的动态ID。                              |
| Npc.type                |        NpcType       | **【只读】**当前NPC的类型。                                |
| Npc.baseAttack          |        Attack        | 当前NPC的基础攻击属性。                                    |
| Npc.defaultMaxSpeed     |        double        | **【只读】**当前NPC的默认最大横向移动速度。                        |
| Npc.maxSpeed            |        double        | 当前NPC的最大横向移动速度。每帧重置为所在环境（流体黏性等）决定的最大移动速度。        |
| Npc.defaultGravity      |        double        | **【只读】**当前NPC的默认重力加速度。                           |
| Npc.gravity             |        double        | 当前NPC的纵向加速度。每帧重置为作用了所在环境纵向受力以及重力后的纵向加速度。         |
| Npc.defaultMaxFallSpeed |        double        | **【只读】**当前NPC的默认最大下落速度。                          |
| Npc.maxFallSpeed        |        double        | 当前NPC的最大下落速度。每帧重置为作用了所在环境纵向阻力后的最大下落速度。           |
| Npc.defaultJumpForce    |        double        | **【只读】**当前NPC的默认跳跃力度。                            |
| Npc.jumpForce           |        double        | 当前NPC的跳跃力度。每帧重置为作用了所在环境纵向阻力后的跳跃力度。               |
| Npc.noMove              |         bool         | 决定当前NPC在行走模板中是否停止行走。                             |
| Npc.inLiquid            |         bool         | **【只读】**当前NPC是否处在流体环境中。                          |
| Npc.oldInLiquid         |         bool         | **【只读】**上一帧的NPC是否处在流体环境中。                        |
| Npc.touchLiquidID       |          int         | **【只读】**当前NPC所处流体环境的ID。如果不在任何流体内，则ID总是为0。        |
| Npc.isEnemy             |         bool         | **【只读】**当前NPC是否会伤害玩家。                            |
| Npc.state               |         bool         | NPC当前在简单有限状态机中的状态。                               |
| Npc.stateTimer          |          int         | NPC的状态机计时器。                                      |
| Npc.hurry               |         bool         | 当前NPC是否为匆忙状态。匆忙状态下随机走模板不会停下来。                    |
| Npc.maxHealth           |          int         | 当前NPC的生命值上限。                                     |
| Npc.health              |          int         | 当前NPC的生命值。                                       |
| Npc.angry               |         bool         | 当前NPC是否为愤怒状态。易怒的NPC在被玩家击中后会将该玩家视为目标，并置愤怒状态为true。 |
| Npc.animation           |          int         | NPC当前执行的动画状态。通常用于表示骨骼模型的动画状态。                    |
| Npc.animationTickTime   |          int         | NPC在当前动画索引所经过的时间。每帧自动自增1，当动画状态切换时自动重置为0。         |
| Npc.watchAngle          |        double        | **【只读】**NPC的目视角度。若NPC目标存在，则总是目视目标。否则总是根据朝向水平目视。  |
| Npc.itemSlots           | ArrayList\<ItemSlot> | 当前NPC自己的物品格子列表。物品格子数目在NPC的AI数据表中指定。              |

### 类成员函数

| 函数                                                                                                                                       |     返回值    | 描述                                                                                                                               |
| ---------------------------------------------------------------------------------------------------------------------------------------- | :--------: | -------------------------------------------------------------------------------------------------------------------------------- |
| Npc:Kill()                                                                                                                               |    void    | 不掉落物品直接清除当前NPC对象。                                                                                                                |
| Npc:Strike(Attack attack, double hitAngle = 0, bool immune = true, bool hurtSound = true, int lootingLevel = 0)                          |    void    | 制造一个对当前NPC的伤害。`attack`表示当前伤害属性，`hitAngle`表示产生伤害的角度，`immune`表示产生当前伤害后是否让NPC处于无敌帧状态，`hurtSound`表示是否播放NPC受伤音效，`lootingLevel`表示掠夺等级。 |
| Npc:StrikeFromPlayer(Player player, Attack attack, double hitAngle = 0, bool immune = true, bool hurtSound = true, int lootingLevel = 0) |    void    | 制造一个某玩家对当前NPC的伤害。其中`player`表示造成伤害的玩家。                                                                                            |
| Npc:StrikeFromNpc(Npc npc, Attack attack, double hitAngle = 0, bool immune = true, bool hurtSound = true, int lootingLevel = 0)          |    void    | 制造一个某NPC对当前NPC的伤害。其中`npc`表示造成伤害的NPC。                                                                                             |
| Npc:GetPlayerTarget()                                                                                                                    | Player/nil | 若当前NPC的玩家锁定目标存在且存活，返回该玩家对象，否则返回nil。                                                                                              |
| Npc:AddBuff(int buffID, int buffTime)                                                                                                    |    void    | 为当前NPC添加一个状态效果。若原状态效果存在，以最长时间为新状态效果的持续时间。                                                                                        |
| Npc:RemoveBuff(int buffID)                                                                                                               |    void    | 移除一个状态效果。                                                                                                                        |
| Npc:RemoveAllBuff()                                                                                                                      |    void    | 移除全部状态效果。                                                                                                                        |
| Npc:HasBuff(int buffID)                                                                                                                  |    bool    | 返回NPC是否拥有指定状态效果。                                                                                                                 |
| Npc:HasAnyBuff()                                                                                                                         |    bool    | 返回NPC是否存在状态效果。                                                                                                                   |
| Npc:TryMakeSound(int tryTimes = 512)                                                                                                     |    void    | NPC尝试发出平时声音。平均经过tryTimes时间发出一次平时声音。                                                                                              |
| Npc:MakeSound()                                                                                                                          |    void    | NPC发出平时声音。                                                                                                                       |
| Npc:UseTool(ItemSlot itemSlot, int skJointID)                                                                                            |    void    | NPC使用指定物品格子内的工具。itemSlot为指定物品格子，skJointID为当前NPC使用工具的骨骼模型关节ID。                                                                    |

### 运动模板函数

调用这些函数执行内置的运动逻辑。

| 函数                                                                                                      |  返回值 | 描述              |
| ------------------------------------------------------------------------------------------------------- | :--: | --------------- |
| Npc:Stand(bool faceToTarget = true)                                                                     | void | 执行**静立**运动模板。   |
| Npc:RandomWalk(int idleTime = 128, int idleTimeOffset = 64, int walkTime = 96, int walkTimeOffset = 32) | void | 执行**随机行走**运动模板。 |
| Npc:KeepWalking(bool followTarget = true)                                                               | void | 执行**持续行走**运动模板。 |
| Npc:Walk(bool followTarget = true)                                                                      | void | 执行_**行走运动**_模板。 |
| Npc:Swim(bool followTarget = true)                                                                      | void | 执行**游泳**模板。     |
| Npc:Fly(bool followTarget = true, double force = 0.1, bool gradientSpeed = false)                       | void | 执行**飞行**模板。     |
| Npc:RandomTeleport(int distance, bool noToAir = true, bool noToLiquid = true)                           | bool | 执行**随机传送**模板。   |

| 运动模板     | 描述                                                                                                                                                                              |
| -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **静立**   | 站立静止不动。目标存在时，`faceToTarget`表示始终面朝玩家。                                                                                                                                            |
| **随机行走** | <p>随机地朝一个方向行走或停下或转弯。</p><p>停下时闲置<code>idleTime ± idleTimeOffset</code>范围内随机时间。</p><p>朝一个方向行走时持续<code>walkTime ± walkTimeOffset</code>范围内随机时间。</p><p>使用内置寻路逻辑，遇到墙壁会尝试跳跃3次。</p>   |
| **持续行走** | <p>持续行走而不停下。<br><code>followTarget</code>表示在目标存在的情况下，尽可能靠近目标。</p><p>使用内置寻路逻辑，遇到墙壁会尝试跳跃3次。</p>                                                                                   |
| **行走**   | <p>目标存在时，采用<em><strong>持续行走</strong></em>模板，<code>followTarget</code>表示尽可能靠近目标。</p><p>目标不存在时，采用<em><strong>随机行走</strong></em>模板。</p>                                            |
| **游泳**   | <p>在流体中游泳，在空气中蹦跶。</p><p>目标存在时，<code>followTarget</code>表示尽可能靠近目标。否则在流体中随机运动。</p>                                                                                                |
| **飞行**   | <p>在空气中飞行。</p><p>目标存在时，<code>followTarget</code>表示尽可能靠近目标，<code>force</code>表示飞向目标的力，<code>gradientSpeed</code>表示是否使用渐变速度，否则运动速度的向量大小总是恒定的。<br>目标不存在时，在空气中随机运动。</p>             |
| **随机传送** | <p>传送NPC自己到以自己为圆心的圆形区域随机位置。</p><p><code>distance</code>表示圆形区域的半径，<code>noToAir</code>表示是否不传送到半空中（即传送到地面上），<code>noToLiquid</code>表示是否不传送到流体内。</p><p>若传送成功，返回true，否则返回false。</p> |

