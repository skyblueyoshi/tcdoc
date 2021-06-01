# NPC

NPC泛指除了玩家之外的所有生物，如动物、敌怪、村民、BOSS等。

## 钩子函数（NPC脚本：contents/npc\_ai/...）

### void Init\(\)

```lua
function Init()
    
end
```

NPC生成时调用一次该函数。

### void Update\(\)

```lua
function Update()
    
end
```

NPC每帧运行时调用，您可以在该函数内编写运动等逻辑。

### void PreUpdate\(\)

```lua
function PreUpdate()
    
end
```

NPC每帧运行`Update()`函数前调用。通常用于在原逻辑前插入新逻辑。

### void PostUpdate\(\)

```lua
function PostUpdate()
    
end
```

NPC每帧运行`Update()`函数后调用。通常用于追加逻辑。

### void UpdateSkeleton\(Skeleton skeleton\)

```lua
function UpdateSkeleton(skeleton)
    
end
```

若NPC拥有骨骼模型，每帧执行完`PostUpdate`后调用，用于处理自定义骨骼模型逻辑。执行完该函数后，会对所有骨骼模型关节重新计算。

* `skeleton`表示当前NPC的骨骼模型。

### void PreUpdateSkeleton\(Skeleton skeleton\)

```lua
function PreUpdateSkeleton(skeleton)
    
end
```

NPC每帧运行`UpdateSkeleton(Skeleton skeleton)`函数前调用。通常用于在使用AI重用后在原逻辑前插入新的骨骼模型逻辑。

* `skeleton`表示当前NPC的骨骼模型。

### void PostUpdateSkeleton\(Skeleton skeleton\)

```lua
function PostUpdateSkeleton(skeleton)
    
end
```

NPC每帧运行`UpdateSkeleton(Skeleton skeleton)`函数，并将全部骨骼关节进行修正后调用。当前函数中所有骨骼关节为实际作用数据。

* `skeleton`表示当前NPC的骨骼模型。

### void OnDraw\(\)

```lua
function OnDraw()
    
end
```

NPC每帧绘制前调用，在该函数内编写自定义绘制属性。不使用该钩子函数时采取默认处理方式。

### void OnKilled\(\)

```lua
function OnKilled()
    
end
```

NPC死亡时调用一次该函数。

### void OnTileCollide\(double oldSpeedX, double oldSpeedY\)

```lua
function OnTileCollide(oldSpeedX, oldSpeedY)
    
end
```

NPC与图块碰撞时调用该函数。

* `oldSpeedX`和`oldSpeedY`表示击中实心图块前一帧的横向和纵向速度。

## NPC通用模块（NpcUtils）

| 函数 | 返回值 | 描述 |
| :--- | :---: | :--- |
| NpcUtils.Create\(int id, double x, double y, double speedX = 0.0, double speedY = 0.0\) | Npc | 在指定位置创建一个NPC，返回创建好的NPC实体。 `id`：NPC的ID。`x`和`y`：创建NPC的坐标。`speedX`和`speedY`：初始运动速度。 |
| NpcUtils.SearchByRect\(double x, double y, int width, int height\) | ArrayList&lt;Npc&gt; | 返回包含于指定矩形区域内部的所有NPC列表。 |
| NpcUtils.SearchByCircle\(double centerX, double centerY, int radius\) | ArrayList&lt;Npc&gt; | 返回包含于指定圆形区域内部的所有NPC列表。 |
| NpcUtils.SearchNearestNpc\(double centerX, double centerY, int radius, bool noCrossTiles = false\) | Npc/nil | 搜索在指定圆形区域内部距离圆心最近的NPC，返回该NPC。若结果不存在，返回nil。`noCrossTiles`表示是否排除中心到圆心的连线被图格遮挡的NPC。 |
| NpcUtils.SearchNearestEnemy\(double centerX, double centerY, int radius, bool noCrossTiles = false\) | Npc/nil | 搜索在指定圆形区域内部距离圆心最近的敌对NPC，返回该NPC。若结果不存在，返回nil。noCrossTiles表示是否排除中心到圆心的连线被图格遮挡的NPC。 |

## NPC类（Npc Class，继承自Entity Class）

**NPC**类表示具有生物基本信息的非玩家实体类。

在编写NPC AI脚本时，**self表示当前正在操作的NPC类**。

### 父类

该类的父类为[Entity类](../../../cn/mod/api/entity.md#shi-ti-lei-entity-class)。可直接使用该父类的类成员属性与类成员函数。

### 类成员属性

| 属性 | 类型 | 描述 |
| :--- | :---: | :--- |
| Npc.id | int | **【只读】**当前NPC的动态ID。 |
| Npc.type | NpcType | **【只读】**当前NPC的类型。 |
| Npc.baseAttack | Attack | 当前NPC的基础攻击属性。 |
| Npc.defaultMaxSpeed | double | **【只读】**当前NPC的默认最大横向移动速度。 |
| Npc.maxSpeed | double | 当前NPC的最大横向移动速度。每帧重置为所在环境（流体黏性等）决定的最大移动速度。 |
| Npc.defaultGravity | double | **【只读】**当前NPC的默认重力加速度。 |
| Npc.gravity | double | 当前NPC的纵向加速度。每帧重置为作用了所在环境纵向受力以及重力后的纵向加速度。 |
| Npc.defaultMaxFallSpeed | double | **【只读】**当前NPC的默认最大下落速度。 |
| Npc.maxFallSpeed | double | 当前NPC的最大下落速度。每帧重置为作用了所在环境纵向阻力后的最大下落速度。 |
| Npc.defaultJumpForce | double | **【只读】**当前NPC的默认跳跃力度。 |
| Npc.jumpForce | double | 当前NPC的跳跃力度。每帧重置为作用了所在环境纵向阻力后的跳跃力度。 |
| Npc.noMove | bool | 决定当前NPC在行走模板中是否停止行走。 |
| Npc.inLiquid | bool | **【只读】**当前NPC是否处在流体环境中。 |
| Npc.oldInLiquid | bool | **【只读】**上一帧的NPC是否处在流体环境中。 |
| Npc.touchLiquidID | int | **【只读】**当前NPC所处流体环境的ID。如果不在任何流体内，则ID总是为0。 |
| Npc.isEnemy | bool | **【只读】**当前NPC是否会伤害玩家。 |
| Npc.state | bool | NPC当前在简单有限状态机中的状态。 |
| Npc.stateTimer | int | NPC的状态机计时器。 |
| Npc.hurry | bool | 当前NPC是否为匆忙状态。匆忙状态下随机走模板不会停下来。 |
| Npc.maxHealth | int | 当前NPC的生命值上限。 |
| Npc.health | int | 当前NPC的生命值。 |
| Npc.angry | bool | 当前NPC是否为愤怒状态。易怒的NPC在被玩家击中后会将该玩家视为目标，并置愤怒状态为true。 |
| Npc.animation | int | NPC当前执行的动画状态。通常用于表示骨骼模型的动画状态。 |
| Npc.animationTickTime | int | NPC在当前动画索引所经过的时间。每帧自动自增1，当动画状态切换时自动重置为0。 |
| Npc.watchAngle | double | **【只读】**NPC的目视角度。若NPC目标存在，则总是目视目标。否则总是根据朝向水平目视。 |
| Npc.itemSlots | ArrayList&lt;ItemSlot&gt; | 当前NPC自己的物品格子列表。物品格子数目在NPC的AI数据表中指定。 |

### 类成员函数

| 函数 | 返回值 | 描述 |
| :--- | :---: | :--- |
| Npc:Kill\(\) | void | 不掉落物品直接清除当前NPC对象。 |
| Npc:Strike\(Attack attack, double hitAngle = 0, bool immune = true, bool hurtSound = true, int lootingLevel = 0\) | void | 制造一个对当前NPC的伤害。`attack`表示当前伤害属性，`hitAngle`表示产生伤害的角度，`immune`表示产生当前伤害后是否让NPC处于无敌帧状态，`hurtSound`表示是否播放NPC受伤音效，`lootingLevel`表示掠夺等级。 |
| Npc:StrikeFromPlayer\(Player player, Attack attack, double hitAngle = 0, bool immune = true, bool hurtSound = true, int lootingLevel = 0\) | void | 制造一个某玩家对当前NPC的伤害。其中`player`表示造成伤害的玩家。 |
| Npc:StrikeFromNpc\(Npc npc, Attack attack, double hitAngle = 0, bool immune = true, bool hurtSound = true, int lootingLevel = 0\) | void | 制造一个某NPC对当前NPC的伤害。其中`npc`表示造成伤害的NPC。 |
| Npc:GetPlayerTarget\(\) | Player/nil | 若当前NPC的玩家锁定目标存在且存活，返回该玩家对象，否则返回nil。 |
| Npc:AddBuff\(int buffID, int buffTime\) | void | 为当前NPC添加一个状态效果。若原状态效果存在，以最长时间为新状态效果的持续时间。 |
| Npc:RemoveBuff\(int buffID\) | void | 移除一个状态效果。 |
| Npc:RemoveAllBuff\(\) | void | 移除全部状态效果。 |
| Npc:HasBuff\(int buffID\) | bool | 返回NPC是否拥有指定状态效果。 |
| Npc:HasAnyBuff\(\) | bool | 返回NPC是否存在状态效果。 |
| Npc:TryMakeSound\(int tryTimes = 512\) | void | NPC尝试发出平时声音。平均经过tryTimes时间发出一次平时声音。 |
| Npc:MakeSound\(\) | void | NPC发出平时声音。 |
| Npc:UseTool\(ItemSlot itemSlot, int skJointID\) | void | NPC使用指定物品格子内的工具。itemSlot为指定物品格子，skJointID为当前NPC使用工具的骨骼模型关节ID。 |

### Movement Member Function

Call these functions to execute the built-in movement logic.

| Function | Returns | Description |
| :--- | :---: | :--- |
| Npc:Stand\(bool faceToTarget = true\) | void | See below. |
| Npc:RandomWalk\(int idleTime = 128, int idleTimeOffset = 64, int walkTime = 96, int walkTimeOffset = 32\) | void | See below. |
| Npc:KeepWalking\(bool followTarget = true\) | void | See below. |
| Npc:Walk\(bool followTarget = true\) | void | See below. |
| Npc:Swim\(bool followTarget = true\) | void | See below. |
| Npc:Fly\(bool followTarget = true, double force = 0.1, bool gradientSpeed = false\) | void | See below. |
| Npc:RandomTeleport\(int distance, bool noToAir = true, bool noToLiquid = true\) | bool | See below. |

<table>
  <thead>
    <tr>
      <th style="text-align:left">Movement</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">Stand</td>
      <td style="text-align:left">
        <p>Just stand and no move.</p>
        <p><code>faceToTarget</code> represents whether to always face the player.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">RandomWalk</td>
      <td style="text-align:left">
        <p>Randomly walk or stop or turn the direction.</p>
        <p>Random time within the range of <code>idleTime &#xB1; idleTimeOffset</code> when
          it stops.</p>
        <p>When walking in one direction, continue for a random time within the range
          of <code>walkTime &#xB1; walkTimeOffset</code>.</p>
        <p>This function will use the built-in pathfinding logic and it will try
          to jump 3 times when touch a wall.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">KeepWalking</td>
      <td style="text-align:left">
        <p>Keep walking without stopping.
          <br /><code>followTarget</code>represents that if the target exists, it will
          walk towards the target as possible.</p>
        <p>This function will use the built-in pathfinding logic and it will try
          to jump 3 times when touch a wall.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Walk</td>
      <td style="text-align:left">When the target exists, call <code>KeepWalking(followTarget)</code>, otherwise
        call <code>RandomWalk()</code>.</td>
    </tr>
    <tr>
      <td style="text-align:left">Swim</td>
      <td style="text-align:left">
        <p>Swim in the liquid, bouncing in the air.</p>
        <p>When the target does not exist, it moves randomly in the liquid.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Fly</td>
      <td style="text-align:left">
        <p>Flying in the air.</p>
        <p><code>followTarget </code>represents that if the target exists, it will
          walk towards the target as possible, otherwise flies randomly.</p>
        <p><code>force</code> represents the force to fly towards the target.</p>
        <p><code>gradientSpeed</code> indicates whether to use gradual speed, otherwise
          the vector length of the speed is always constant.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">RandomTeleport</td>
      <td style="text-align:left">
        <p>Send the NPC to a random location in a circular area centered on itself.</p>
        <p><code>distance</code> represents the radius of the circular area.
          <br /><code>noToAir</code> represents whether it will be teleported to the ground.</p>
        <p><code>noToLiquid</code> represents whether it will not be teleported into
          any liquid.</p>
        <p>Returns true if teleport success, otherwise returns false.</p>
      </td>
    </tr>
  </tbody>
</table>



