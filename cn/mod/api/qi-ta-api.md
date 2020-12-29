# 其他API

## 杂项通用模块（MiscUtils）

### 客户端通用变量

| 变量名 | 类型 | 描述 |
| :--- | :---: | :--- |
| MiscUtils.screenX | double | **【只读】**当前客户端屏幕左上角横坐标。 |
| MiscUtils.screenY | double | **【只读】**当前客户端屏幕左上角纵坐标。 |
| MiscUtils.screenWidth | int | **【只读】**当前客户端屏幕宽度（像素）。 |
| MiscUtils.screenHeight | int | **【只读】**当前客户端屏幕高度（像素）。 |

### 通用函数

#### 文本传输函数

注意：若使用了**UTF8文本**，请使用UTF8文本传输函数。

| 函数 | 返回值 | 描述 |
| :--- | :---: | :--- |
| MiscUtils.Unicast\(Player player, string message\) | void | 向指定玩家的客户端单播ASCII字符串。 |
| MiscUtils.Broadcast\(string message\) | void | 广播ASCII字符串到所有客户端。 |
| MiscUtils.UnicastUTF8\(Player player, string message\) | void | 向指定玩家的客户端单播UTF8字符串。 |
| MiscUtils.BroadcastUTF8\(string message\) | void | 广播UTF8字符串到所有客户端。 |

#### 特殊效果函数

| 函数 | 返回值 | 描述 |
| :--- | :---: | :--- |
| MiscUtils.RayDistance\(double fromX, double fromY, double shootAngle, int maxDistance = 1000\) | int | 从一个点发射射线，返回碰到固体时射线经过的距离。`maxDistance`表示最远检测距离。 |
| MiscUtils.RayReach\(double fromX, double fromY, double toX, double toY\) | bool | 从一个点朝另外一个点发射射线，返回射线是否未与任何固体发生碰撞。 |
| MiscUtils.CreateExplosion\(int xi, int yi, double power, bool hurtNpc, bool hurtPlayer, bool killTiles = true, bool killWalls = false, bool makeSound = true, int tileLimit = -1\) | void | 在指定格子位置发生一个爆炸。`power`表示爆炸攻击力。`hurtNpc`表示是否对NPC有效。`hurtPlayer`表示是否对玩家有效。`killTiles`表示是否破坏前景。`killWalls`表示是否破坏背景墙。`makeSound`表示是否发出爆炸音效。`tileLimit`为正数时表示爆炸作用的最小方块硬度，为负数表示作用全部方块。 |
| MiscUtils.SetDayTime\(int dayTime\) | void | 设置当日时间。一天的时间为0-86400。 |

