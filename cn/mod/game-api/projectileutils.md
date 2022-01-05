---
description: 抛射物通用模块。
---

# ProjectileUtils

## 函数

| <p><strong>Projectile/nil ProjectileUtils.Get(EntityIndex entityIndex)</strong><br><strong></strong>获取指定索引表示的抛射物，如果不存在，返回nil。</p>                                                                                                                                                                                                                                                 |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <p><strong>bool ProjectileUtils.IsAlive(EntityIndex entityIndex)</strong><br><strong></strong>判断指定索引的抛射物是否存在。</p>                                                                                                                                                                                                                                                                 |
| <p><strong>Projectile ProjectileUtils.Create(int id, double centerX, double centerY, double speedX = 0.0, double speedY = 0.0, Attack attack = Attack:new(0, 0, 0))</strong><br>创建一个抛射物实体，返回创建好的抛射物实体。<br><code>id</code>：抛射物ID。<br><code>centerX</code>和<code>centerY</code>：创建抛射物的中心点。<br><code>speedX</code>和<code>speedY</code>：初始运动速度。<br><code>Attack</code>：抛射物的基础攻击力。</p> |
| <p><strong>Projectile ProjectileUtils.CreateFromPlayer(Player playerOwner, int id, double centerX, double centerY, double speedX = 0.0, double speedY = 0.0, Attack attack = Attack:new(0, 0, 0))</strong><br>创建一个以指定玩家为拥有者的抛射物实体，返回创建好的抛射物实体。</p>                                                                                                                                |
| <p><strong>Projectile ProjectileUtils.CreateFromNpc(Npc npcOwner, int id, double centerX, double centerY, double speedX = 0.0, double speedY = 0.0, Attack attack = Attack:new(0, 0, 0))</strong><br>创建一个以指定NPC为拥有者的抛射物实体，返回创建好的抛射物实体。</p>                                                                                                                                        |
| <p><strong>ArrayList&#x3C;Projectile> ProjectileUtils.SearchByRect(double x, double y, int width, int height)</strong><br>返回包含于指定矩形区域内部的所有抛射物列表。</p>                                                                                                                                                                                                                              |
| <p><strong>ArrayList&#x3C;Projectile> ProjectileUtils.SearchByCircle(double centerX, double centerY, int radius)</strong><br>返回包含于指定圆形区域内部的所有抛射物列表。</p>                                                                                                                                                                                                                           |
| <p>Projectile/nil ProjectileUtils.SearchNearestProjectile(double centerX, double centerY, int <strong>radius, bool noCrossTiles = false)</strong><br>搜索在指定圆形区域内部距离圆心最近的抛射物，返回该抛射物。若结果不存在，返回nil。<code>noCrossTiles</code>表示是否排除中心到圆心的连线被图格遮挡的抛射物。</p>                                                                                                                              |

##
