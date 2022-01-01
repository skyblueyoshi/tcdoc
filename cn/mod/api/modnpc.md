---
description: 每个Npc实例都会挂载一个ModNpc对象。
---

# ModNpc

## 属性

| 属性                                   |
| ------------------------------------ |
| <p>Npc npc<br>当前ModNpc所控制的npc实例。</p> |

## 函数

| 函数                                                                                                                                                                   |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <p>void ModNpc:Init()<br>NPC生成时调用。</p>                                                                                                                               |
| <p>void ModNpc:Update()<br>NPC每帧运行时调用，您可以在该函数内编写运动等逻辑。</p>                                                                                                           |
| <p>void ModNpc:PreUpdate()<br>NPC每帧运行<code>Update()</code>函数前调用。通常用于在原逻辑前插入新逻辑。</p>                                                                                  |
| <p>void ModNpc:PostUpdate()<br>NPC每帧运行<code>Update()</code>函数后调用。通常用于追加逻辑。</p>                                                                                       |
| <p>void ModNpc:UpdateSkeleton(skeleton)</p><p>若NPC拥有骨骼模型，每帧执行完<code>PostUpdate</code>后调用，用于处理自定义骨骼模型逻辑。执行完该函数后，会对所有骨骼模型关节重新计算。<code>skeleton</code>表示当前NPC的骨骼模型。</p> |
| <p>void ModNpc:PreUpdateSkeleton(skeleton)<br>NPC每帧运行<code>UpdateSkeleton</code>函数前调用。通常用于在使用AI重用后在原逻辑前插入新的骨骼模型逻辑。</p>                                               |
| <p>void ModNpc:PostUpdateSkeleton(skeleton)<br>NPC每帧运行<code>UpdateSkeleton</code>函数、并将全部骨骼关节进行修正后调用。当前函数中所有骨骼关节为实际作用数据。</p>                                          |
| <p>void ModNpc:OnDraw()<br>NPC每帧绘制前调用，在该函数内编写自定义绘制属性。不重写该函数时采取默认处理方式。</p>                                                                                            |
| <p>void ModNpc:OnKilled()<br>NPC死亡时调用。</p>                                                                                                                           |
| <p>void ModNpc:OnTileCollide(double oldSpeedX, double oldSpeed)<br>NPC与图块碰撞时调用该函数。 oldSpeedX和oldSpeedY表示击中实心图块前一帧的横向和纵向速度。</p>                                       |

