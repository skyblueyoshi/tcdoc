# 其他API

## 杂项通用模块（MiscUtils）

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
| MiscUtils.CreateExplosion\(int xi, int yi, double power, bool hurtNpc, bool hurtPlayer, bool killTiles = true, bool killWalls = false, bool makeSound = true, int tileLimit = -1\) | void | 在指定格子位置发生一个爆炸。`power`表示爆炸攻击力。`hurtNpc`表示是否对NPC有效。`hurtPlayer`表示是否对玩家有效。`killTiles`表示是否破坏前景。`killWalls`表示是否破坏背景墙。`makeSound`表示是否发出爆炸音效。`tileLimit`为正数时表示爆炸作用的最小方块硬度，为负数表示作用全部方块。 |
|  |  |  |

