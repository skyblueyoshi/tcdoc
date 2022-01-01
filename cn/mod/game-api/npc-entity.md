---
description: NPC泛指除了玩家之外的所有生物，如动物、敌怪、村民、BOSS等。Npc类表示具有生物基本信息的非玩家实体类。
---

# Npc : Entity

NPC泛指除了玩家之外的所有生物，如动物、敌怪、村民、BOSS等。Npc类表示具有生物基本信息的非玩家实体类。

## 属性

| 属性                                                                                                        |
| --------------------------------------------------------------------------------------------------------- |
| <p><strong>int id</strong><br><strong>【只读】</strong>当前NPC的动态ID。</p>                                        |
| <p><strong>NpcType type</strong><br><strong>【只读】</strong>当前NPC的类型。</p>                                    |
| <p><strong>Attack baseAttack</strong><br>当前NPC的基础攻击属性。</p>                                                |
| <p><strong>double defaultMaxSpeed</strong><br><strong>【只读】</strong>当前NPC的默认最大横向移动速度。</p>                  |
| <p><strong>double maxSpeed</strong><br>当前NPC的最大横向移动速度。每帧重置为所在环境（流体黏性等）决定的最大移动速度。</p>                      |
| <p><strong>double defaultGravity</strong><br><strong>【只读】</strong>当前NPC的默认重力加速度。</p>                      |
| <p><strong>double gravity</strong><br>当前NPC的纵向加速度。每帧重置为作用了所在环境纵向受力以及重力后的纵向加速度。</p>                        |
| <p><strong>double defaultMaxFallSpeed</strong><br><strong>【只读】</strong>当前NPC的默认最大下落速度。</p>                |
| <p><strong>double maxFallSpeed</strong><br>当前NPC的最大下落速度。每帧重置为作用了所在环境纵向阻力后的最大下落速度。</p>                     |
| <p><strong>double defaultJumpForce</strong><br><strong>【只读】</strong>当前NPC的默认跳跃力度。</p>                     |
| <p><strong>double jumpForce</strong><br>当前NPC的跳跃力度。每帧重置为作用了所在环境纵向阻力后的跳跃力度。</p>                            |
| <p><strong>bool noMove</strong><br>决定当前NPC在行走模板中是否停止行走。</p>                                               |
| <p><strong>bool inLiquid</strong><br>【<strong>只读】</strong>当前NPC是否处在流体环境中。</p>                             |
| <p><strong>bool oldInLiquid</strong><br><strong>【只读】</strong>上一帧的NPC是否处在流体环境中。</p>                        |
| <p><strong>int touchLiquidID</strong><br><strong>【只读】</strong>当前NPC所处流体环境的ID。如果不在任何流体内，则ID总是为0。</p>       |
| <p><strong>bool isEnemy</strong><br><strong>【只读】</strong>当前NPC是否会伤害玩家。</p>                                |
| <p><strong>bool state</strong><br>NPC当前在简单有限状态机中的状态。</p>                                                  |
| <p><strong>int stateTimer</strong><br>NPC的状态机计时器。</p>                                                     |
| <p><strong>bool hurry</strong><br>当前NPC是否为匆忙状态。匆忙状态下随机走模板不会停下来。</p>                                       |
| <p><strong>int maxHealth</strong><br>当前NPC的生命值上限。</p>                                                     |
| <p><strong>int health</strong><br>当前NPC的生命值。</p>                                                          |
| <p><strong>bool angry</strong><br>当前NPC是否为愤怒状态。易怒的NPC在被玩家击中后会将该玩家视为目标，并置愤怒状态为true。</p>                    |
| <p><strong>int animation</strong><br>NPC当前执行的动画状态。通常用于表示骨骼模型的动画状态。</p>                                    |
| <p><strong>int animationTickTime</strong><br>NPC在当前动画索引所经过的时间。每帧自动自增1，当动画状态切换时自动重置为0。</p>                 |
| <p><strong>double watchAngle</strong><br><strong>【只读】</strong>NPC的目视角度。若NPC目标存在，则总是目视目标。否则总是根据朝向水平目视。</p> |
| <p><strong>ArrayList&#x3C;ItemSlot> itemSlots</strong><br>当前NPC自己的物品格子列表。物品格子数目在NPC的AI数据表中指定。</p>         |

### 类成员函数

| 函数                                                                                                                                                                                                                                                                                                                                                     |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| <p><strong>void Npc:Kill()</strong><br>不掉落物品直接清除当前NPC对象。</p>                                                                                                                                                                                                                                                                                           |
| <p><strong>void Npc:Strike(Attack attack, double hitAngle = 0, bool immune = true, bool hurtSound = true, int lootingLevel = 0)</strong><br>制造一个对当前NPC的伤害。<br><code>attack</code>：当前伤害属性。<br><code>hitAngle</code>：产生伤害的角度。<br><code>immune</code>：产生当前伤害后是否让NPC处于无敌帧状态。<br><code>hurtSound</code>：是否播放NPC受伤音效。<br><code>lootingLevel</code>：掠夺等级。</p> |
| <p><strong>void Npc:StrikeFromPlayer(Player player, Attack attack, double hitAngle = 0, bool immune = true, bool hurtSound = true, int lootingLevel = 0)</strong><br>制造一个某玩家对当前NPC的伤害。<br><code>player：</code>造成伤害的玩家。</p>                                                                                                                             |
| <p><strong>void Npc:StrikeFromNpc(Npc npc, Attack attack, double hitAngle = 0, bool immune = true, bool hurtSound = true, int lootingLevel = 0)</strong><br>制造一个某NPC对当前NPC的伤害。<br><code>npc</code>：造成伤害的NPC。</p>                                                                                                                                       |
| <p><strong>Player/nil Npc:GetPlayerTarget()</strong><br>若当前NPC的玩家锁定目标存在且存活，返回该玩家对象，否则返回nil。</p>                                                                                                                                                                                                                                                        |
| <p><strong>void Npc:AddBuff(int buffID, int buffTime)</strong><br>为当前NPC添加一个状态效果。若原状态效果存在，以最长时间为新状态效果的持续时间。</p>                                                                                                                                                                                                                                        |
| <p><strong>void Npc:RemoveBuff(int buffID)</strong><br>移除一个状态效果。</p>                                                                                                                                                                                                                                                                                   |
| <p><strong>void Npc:RemoveAllBuff()</strong><br>移除全部状态效果。</p>                                                                                                                                                                                                                                                                                          |
| <p><strong>bool Npc:HasBuff(int buffID)</strong><br>返回NPC是否拥有指定状态效果。</p>                                                                                                                                                                                                                                                                               |
| <p><strong>bool Npc:HasAnyBuff()</strong><br>返回NPC是否存在状态效果。</p>                                                                                                                                                                                                                                                                                        |
| <p><strong>void Npc:TryMakeSound(int tryTimes = 512)</strong><br>NPC尝试发出平时声音。平均经过tryTimes时间发出一次平时声音。</p>                                                                                                                                                                                                                                               |
| <p><strong>void Npc:MakeSound()</strong><br>NPC发出平时声音。</p>                                                                                                                                                                                                                                                                                             |
| <p><strong>void Npc:UseTool(ItemSlot itemSlot, int skJointID)</strong><br>NPC使用指定物品格子内的工具。<br>itemSlot：指定物品格子。<br>skJointID：当前NPC使用工具的骨骼模型关节ID。</p>                                                                                                                                                                                                    |
| <p><strong>void Npc:Stand(bool faceToTarget = true)</strong><br>站立静止不动。目标存在时，<code>faceToTarget</code>表示始终面朝玩家。</p>                                                                                                                                                                                                                                    |
| <p><strong>void Npc:RandomWalk(int idleTime = 128, int idleTimeOffset = 64, int walkTime = 96, int walkTimeOffset = 32)</strong><br>随机地朝一个方向行走或停下或转弯。</p><p>停下时闲置<code>idleTime ± idleTimeOffset</code>范围内随机时间。</p><p>朝一个方向行走时持续<code>walkTime ± walkTimeOffset</code>范围内随机时间。</p><p>使用内置寻路逻辑，遇到墙壁会尝试跳跃3次。</p>                                         |
| <p><strong>void Npc:KeepWalking(bool followTarget = true)</strong><br>持续行走而不停下。<code>followTarget</code>表示在目标存在的情况下，尽可能靠近目标。</p><p>使用内置寻路逻辑，遇到墙壁会尝试跳跃3次。</p>                                                                                                                                                                                           |
| <p><strong>void Npc:Walk(bool followTarget = true)</strong><br>目标存在时，采用Npc:KeepWalking，<code>followTarget</code>表示尽可能靠近目标。</p><p>目标不存在时，采用Npc:RandomWalk。</p>                                                                                                                                                                                          |
| <p><strong>void Npc:Swim(bool followTarget = true)</strong><br>在流体中游泳，在空气中蹦跶。</p><p>目标存在时，<code>followTarget</code>表示尽可能靠近目标。否则在流体中随机运动。</p>                                                                                                                                                                                                           |
| <p><strong>void Npc:Fly(bool followTarget = true, double force = 0.1, bool gradientSpeed = false)</strong><br>在空气中飞行。</p><p>目标存在时，<code>followTarget</code>表示尽可能靠近目标，<code>force</code>表示飞向目标的力，<code>gradientSpeed</code>表示是否使用渐变速度，否则运动速度的向量大小总是恒定的。<br>目标不存在时，在空气中随机运动。</p>                                                                         |
| <p><strong>bool Npc:RandomTeleport(int distance, bool noToAir = true, bool noToLiquid = true)</strong><br>传送NPC自己到以自己为圆心的圆形区域随机位置。若传送成功，返回true，否则返回false。</p><p><code>distance</code>：圆形区域的半径。<br><code>noToAir</code>：是否不传送到半空中（即传送到地面上）。<br><code>noToLiquid</code>：是否不传送到流体内。</p>                                                                   |

