---
description: NPC通用模块。
---

# NpcUtils

## 函数

| 函数                                                                                                                                                                                                                                                                      |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <p><strong>Npc NpcUtils.Create(int id, double x, double y, double speedX = 0.0, double speedY = 0.0)</strong><br>在指定位置创建一个NPC，返回创建好的NPC实体。<br><code>id</code>：NPC的ID。<br><code>x</code>和<code>y</code>：创建NPC的坐标。<br><code>speedX</code>和<code>speedY</code>：初始运动速度。</p> |
| <p><strong>ArrayList&#x3C;Npc> NpcUtils.SearchByRect(double x, double y, int width, int height)</strong><br>返回包含于指定矩形区域内部的所有NPC列表。</p>                                                                                                                                  |
| <p><strong>ArrayList&#x3C;Npc> NpcUtils.SearchByCircle(double centerX, double centerY, int radius)</strong><br>返回包含于指定圆形区域内部的所有NPC列表。</p>                                                                                                                               |
| <p><strong>Npc/nil NpcUtils.SearchNearestNpc(double centerX, double centerY, int radius, bool noCrossTiles = false)</strong><br>搜索在指定圆形区域内部距离圆心最近的NPC，返回该NPC。若结果不存在，返回nil。<code>noCrossTiles</code>表示是否排除中心到圆心的连线被图格遮挡的NPC。</p>                                         |
| <p><strong>Npc/nil NpcUtils.SearchNearestEnemy(double centerX, double centerY, int radius, bool noCrossTiles = false)</strong><br>搜索在指定圆形区域内部距离圆心最近的敌对NPC，返回该NPC。若结果不存在，返回nil。noCrossTiles表示是否排除中心到圆心的连线被图格遮挡的NPC。</p>                                                  |
