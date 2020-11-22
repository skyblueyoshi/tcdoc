# 玩家API

## 玩家类（Player Class）

**玩家（Player）**类表示玩家实际控制的角色实体类。

### 类成员属性

| 属性 | 类型 | 描述 |
| :--- | :--- | :--- |
| Player.health | int | **【只读】**玩家生命值。 |
| Player.maxHealth | int | **【只读】**玩家生命值上限。 |
| Player.mana | int | **【只读】**玩家魔法值。 |
| Player.maxMana | int | **【只读】**玩家魔法值上限。 |
| Player.expLevel | int | **【只读】**玩家经验等级。 |
|  |  |  |

### 类成员函数

| 函数 | 返回值 | 描述 |
| :--- | :--- | :--- |
| Player:Heal\(int heal, bool showTip = true\) | void | 为当前玩家增加生命值。showTip表示是否显示数字提示。 |
| Player:AddMagic\(int heal, bool showTip = true\) | void | 为当前玩家增加魔法值。showTip表示是否显示数字提示。 |
| Player:AddMaxHealth\(int health\) | void | 为当前玩家增加生命值上限。 |
| Player:AddMaxMagic\(int magic\) | void | 为当前玩家增加魔法值上限。 |
| Player:AddExperience\(int amount\) | void | 为当前玩家增加经验值。 |
| Player:RemoveExpLevel\(int level\) | void | 消耗当前玩家的经验等级。 |
| Player:AddBuff\(int buffID, int buffTime\) | void | 为当前玩家添加一个状态效果。若原状态效果存在，以最长时间为新状态效果的持续时间。 |
| Player:RemoveBuff\(int buffID\) | void | 移除一个状态效果。 |
| Player:HasBuff\(int buffID\) | bool | 返回玩家是否拥有指定状态效果。 |
| Player:HasAnyBuff\(\) | bool | 返回玩家是否存在状态效果。 |





