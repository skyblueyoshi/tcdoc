---
description: 每个Npc实例都会挂载一个ModNpc对象。
---

# ModNpc

每个Npc实例都会挂载的一个ModNpc对象。

## 属性

| 属性                                                    |
| ----------------------------------------------------- |
| <p><strong>Npc npc</strong><br>当前ModNpc所控制的npc实例。</p> |

## 函数

| 函数                                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <p><strong>void ModNpc:Init()</strong><br>NPC生成时调用。</p>                                                                                                                               |
| <p><strong>void ModNpc:Update()</strong><br>NPC每帧运行时调用，您可以在该函数内编写运动等逻辑。</p>                                                                                                           |
| <p><strong>bool ModNpc:CanUpdate()</strong><br>NPC每帧运行<code>Update()</code>函数前调用，如果返回true则执行所有Update逻辑，返回false则不执行所有Update逻辑。可在该函数写入新的逻辑，并屏蔽原有逻辑。默认返回true。</p>                        |
| <p><strong>void ModNpc:PreUpdate()</strong><br>NPC每帧运行<code>Update()</code>函数前调用。通常用于在原逻辑前插入新逻辑。</p>                                                                                  |
| <p><strong>void ModNpc:PostUpdate()</strong><br>NPC每帧运行<code>Update()</code>函数后调用。通常用于追加逻辑。</p>                                                                                       |
| <p><strong>void ModNpc:UpdateSkeleton(skeleton)</strong></p><p>若NPC拥有骨骼模型，每帧执行完<code>PostUpdate</code>后调用，用于处理自定义骨骼模型逻辑。执行完该函数后，会对所有骨骼模型关节重新计算。<code>skeleton</code>表示当前NPC的骨骼模型。</p> |
| <p><strong>void ModNpc:PreUpdateSkeleton(skeleton)</strong><br>NPC每帧运行<code>UpdateSkeleton</code>函数前调用。通常用于在使用AI重用后在原逻辑前插入新的骨骼模型逻辑。</p>                                               |
| <p><strong>void ModNpc:PostUpdateSkeleton(skeleton)</strong><br>NPC每帧运行<code>UpdateSkeleton</code>函数、并将全部骨骼关节进行修正后调用。当前函数中所有骨骼关节为实际作用数据。</p>                                          |
| <p><strong>bool ModNpc:CanDraw()</strong><br>NPC每帧绘制前调用，如果返回true则执行所有Draw逻辑，返回false则不执行所有Draw逻辑。可在该函数写入新的逻辑，并屏蔽原有逻辑。默认返回true。</p>                                                     |
| <p><strong>void ModNpc:OnDraw()</strong><br>NPC每帧绘制前调用，在该函数内编写自定义绘制属性。不重写该函数时采取默认处理方式。</p>                                                                                            |
| <p><strong>void ModNpc:OnKilled()</strong><br>NPC死亡时调用。</p>                                                                                                                           |
| <p><strong>void ModNpc:OnTileCollide(double oldSpeedX, double oldSpeed)</strong><br>NPC与图块碰撞时调用该函数。 oldSpeedX和oldSpeedY表示击中实心图块前一帧的横向和纵向速度。</p>                                       |

