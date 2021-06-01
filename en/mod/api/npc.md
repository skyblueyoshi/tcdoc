# NPC

NPC refers to all creatures except players, such as animals, enemies, villagers, BOSS, etc.

## Hook Funtion \(contents/npc\_ai/...\)

### void Init\(\)

```lua
function Init()
    
end
```

This function is called once when the NPC is spawned.

### void Update\(\)

```lua
function Update()
    
end
```

Called when NPC runs every update tick, usually write logic in this function.

### void PreUpdate\(\)

```lua
function PreUpdate()
    
end
```

Called before the NPC runs the `Update()` function every update tick. It is usually used to insert new logic before the original logic.

### void PostUpdate\(\)

```lua
function PostUpdate()
    
end
```

Called after the NPC runs the `Update()` function every update tick. It is usually used to insert new logic after the original logic.

### void UpdateSkeleton\(Skeleton skeleton\)

```lua
function UpdateSkeleton(skeleton)
    
end
```

If the NPC has a skeleton model, it is called after `PostUpdate()` to process the logic of the custom skeleton model. After executing this function, all joints of the skeleton model will be recalculated.

* `skeleton`Represents the skeleton model of the current NPC.

### void PreUpdateSkeleton\(Skeleton skeleton\)

```lua
function PreUpdateSkeleton(skeleton)
    
end
```

Called before the NPC runs the `UpdateSkeleton(skeleton)` function every update tick. It is usually used to insert new logic before the original logic.

* `skeleton`Represents the skeleton model of the current NPC.

### void PostUpdateSkeleton\(Skeleton skeleton\)

```lua
function PostUpdateSkeleton(skeleton)
    
end
```

Called after the NPC runs the `UpdateSkeleton(skeleton)` function every update tick. It is usually used to insert new logic after the original logic.

* `skeleton`Represents the skeleton model of the current NPC.

### void OnDraw\(\)

```lua
function OnDraw()
    
end
```

Called before each tick of NPC drawing, just write custom drawing behavior in this function.

### void OnKilled\(\)

```lua
function OnKilled()
    
end
```

Called when NPC was killed.

### void OnTileCollide\(double oldSpeedX, double oldSpeedY\)

```lua
function OnTileCollide(oldSpeedX, oldSpeedY)
    
end
```

Called when NPC collides the tiles.

* `oldSpeedX` represents the X speed before colliding tiles.
* `oldSpeedY` represents the Y speed before colliding tiles.

## NpcUtils

| 函数 | 返回值 | 描述 |
| :--- | :---: | :--- |
| NpcUtils.Create\(int id, double x, double y, double speedX = 0.0, double speedY = 0.0\) | Npc | 在指定位置创建一个NPC，返回创建好的NPC实体。 `id`：NPC的ID。`x`和`y`：创建NPC的坐标。`speedX`和`speedY`：初始运动速度。 |
| NpcUtils.SearchByRect\(double x, double y, int width, int height\) | ArrayList&lt;Npc&gt; | 返回包含于指定矩形区域内部的所有NPC列表。 |
| NpcUtils.SearchByCircle\(double centerX, double centerY, int radius\) | ArrayList&lt;Npc&gt; | 返回包含于指定圆形区域内部的所有NPC列表。 |
| NpcUtils.SearchNearestNpc\(double centerX, double centerY, int radius, bool noCrossTiles = false\) | Npc/nil | 搜索在指定圆形区域内部距离圆心最近的NPC，返回该NPC。若结果不存在，返回nil。`noCrossTiles`表示是否排除中心到圆心的连线被图格遮挡的NPC。 |
| NpcUtils.SearchNearestEnemy\(double centerX, double centerY, int radius, bool noCrossTiles = false\) | Npc/nil | 搜索在指定圆形区域内部距离圆心最近的敌对NPC，返回该NPC。若结果不存在，返回nil。noCrossTiles表示是否排除中心到圆心的连线被图格遮挡的NPC。 |

## Npc Class \(Inherited from Entity Class\)

The NPC class represents a non-player character entity class with basic biological information. 

_**Note: When writing an NPC AI script, `self` represents the NPC class currently being operated.**_

### Member

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

### Member Function

| Function | Returns | Description |
| :--- | :---: | :--- |
| Npc:Kill\(\) | void | Destroy current NPC entity without dropping items. |
| Npc:Strike\(Attack attack, double hitAngle = 0, bool immune = true, bool hurtSound = true, int lootingLevel = 0\) | void | Create a damage to the current NPC.`attack` represents the current damage attribute.`hitAngle` represents the angle at which the damage is generated.`immune` represents whether the NPC is in an invincible frame state after the current damage is generated.`hurtSound` represents whether to play the NPC injury sound effect. |
| Npc:StrikeFromPlayer\(Player player, Attack attack, double hitAngle = 0, bool immune = true, bool hurtSound = true, int lootingLevel = 0\) | void | Create a damage to the current NPC from player. `player` represents the player who caused the damage. |
| Npc:StrikeFromNpc\(Npc npc, Attack attack, double hitAngle = 0, bool immune = true, bool hurtSound = true, int lootingLevel = 0\) | void | Create a damage to the current NPC from other NPC. `npc` represents the NPC who caused the damage. |
| Npc:GetPlayerTarget\(\) | Player/nil | 若当前NPC的玩家锁定目标存在且存活，返回该玩家对象，否则返回nil。 |
| Npc:AddBuff\(int buffID, int buffTime\) | void | Add a buff to the current NPC. If the buff exists and new buff time greater than old's, use new buff time. |
| Npc:RemoveBuff\(int buffID\) | void | Remove a buff from current NPC. |
| Npc:RemoveAllBuff\(\) | void | Remove all buffs from current NPC. |
| Npc:HasBuff\(int buffID\) | bool | Returns whether the NPC has the target buff. |
| Npc:HasAnyBuff\(\) | bool | Returns whether the NPC has a buff. |
| Npc:TryMakeSound\(int tryTimes = 512\) | void | The NPC tries to make a normal voice randomly. Sound is emitted once after trying `tryTimes` times on average. |
| Npc:MakeSound\(\) | void | The NPC makes a normal voice randomly. |
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



