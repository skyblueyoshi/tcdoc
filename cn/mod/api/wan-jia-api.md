# 玩家API

## 玩家通用模块（PlayerUtils）

### 通用常量

| 常量 | 类型 | 值 | 描述 |
| :--- | :---: | :---: | :--- |
| PlayerUtils._GRAVITY_ | double | 0.40625 | 玩家默认重力加速度。 |
| PlayerUtils._MAX\_SPEED_ | double | 3.0 | 玩家默认最大速度。 |
| PlayerUtils._MAX\_FALL\_SPEED_ | double | 12.0 | 玩家默认最大下落速度。 |
| PlayerUtils._JUMP\_TIME_ | int | 19 | 玩家默认跳跃上升持续时间。 |
| PlayerUtils._JUMP\_SPEED_ | double | 5.3 | 玩家默认跳跃上升速度。 |
| PlayerUtils._DEFAULT\_MAX\_HEALTH_ | int | 100 | 玩家默认最大生命值。 |
| PlayerUtils._DEFAULT\_MAX\_MANA_ | int | 100 | 玩家默认最大魔法值。 |

### 通用函数

| 函数 | 返回值 | 描述 |
| :--- | :---: | :--- |
| PlayerUtils.SearchByRect\(double x, double y, int width, int height\) | ArrayList&lt;Player&gt; | 返回包含于指定矩形区域内部的所有玩家列表。 |
| PlayerUtils.SearchByCircle\(double centerX, double centerY, int radius\) | ArrayList&lt;Player&gt; | 返回包含于指定圆形区域内部的所有玩家列表。 |
| PlayerUtils.SearchNearestPlayer\(double centerX, double centerY, int radius, bool noCrossTiles = false\) | Player/nil | 搜索在指定圆形区域内部距离圆心最近的玩家，返回该玩家。若结果不存在，返回nil。noCrossTiles表示是否排除中心到圆心的连线被图格遮挡的玩家。 |

## 玩家类（Player Class）

**玩家（Player）**类表示玩家实际控制的角色实体类。

### 父类

该类的父类为[Entity类](entity.md#shi-ti-lei-entity-class)。可直接使用该父类的类成员属性与类成员函数。

由于玩家类的特殊性，该父类的所有**【类成员属性全部只读】**。

### 类成员属性

#### 控制器属性

| 属性 | 类型 | 描述 |
| :--- | :---: | :--- |
| Player.defaultMaxSpeed | double | **【只读】**玩家默认最大运动速度。 |
| Player.speedRate | double | 玩家最大运动速度与默认最大运动速度比率。每帧重置为`1.0`。 |
| Player.defaultJumpTime | int | **【只读】**玩家默认跳跃持续上升时间。 |
| Player.jumpRate | double | 玩家跳跃持续上升时间与默认跳跃持续上升时间比率。每帧重置为`1.0`。 |
| Player.defaultJumpSpeed | double | **【只读】**玩家默认跳跃上升速度。 |
| Player.jumpSpeedRate | double | 玩家跳跃上升速度与默认跳跃上升速度比率。每帧重置为`1.0`。 |
| Player.defaultFallSpeed | double | **【只读】**玩家默认最大下落速度。 |
| Player.fallSpeedRate | double | 玩家最大下落速度与默认最大下落速度比率。每帧重置为`1.0`。 |
| Player.digSpeedRate | double | 玩家挖掘速度与原始挖掘速度比率。每帧重置为`1.0`。 |

#### 数值属性

| 属性 | 类型 | 描述 |
| :--- | :---: | :--- |
| Player.health | int | **【只读】**玩家生命值。 |
| Player.maxHealth | int | **【只读】**玩家生命值上限。 |
| Player.maxMaxHealth | int | **【只读】**玩家最高能达到的生命值上限。 |
| Player.mana | int | **【只读】**玩家魔法值。 |
| Player.maxMana | int | **【只读】**玩家魔法值上限。 |
| Player.maxMaxMana | int | **【只读】**玩家最高能达到的魔法值上限。 |
| Player.expLevel | int | **【只读】**玩家经验等级。 |
| Player.isNoBreathing | bool | **【只读】**玩家当前是否不能呼吸。 |
| Player.breath | double | **【只读】**玩家呼吸值。有效范围为\[0.0, 1.0\]。当呼吸值为0.0时会产生窒息伤害。 |
| Player.foodLevel | int | **【只读】**玩家饥饿值。有效范围为\[1, 100\]。当饥饿值为0时会产生饥饿伤害。 |
| Player.foodSaturationLevel | int | **【只读】**玩家食物饱和度。有效范围为\[1, 100\]。当前食物饱和度不会超过当前饥饿值。 |

### 类成员函数

#### 控制函数

| 函数 | 返回值 | 描述 |
| :--- | :---: | :--- |
| Player:SetSpeedX\(double speedX\) | void | 设定玩家的横向速度。（对所控制的玩家生效） |
| Player:SetSpeedY\(double speedY\) | void | 设定玩家的纵向速度。（对所控制的玩家生效） |

#### 数值属性函数

| 函数 | 返回值 | 描述 |
| :--- | :---: | :--- |
| Player:Strike\(DeathReason reason, Attack attack, double hitAngle = 0, bool immune = false, bool hurtSound = true\) | void | 伤害当前玩家。`reason`表示死亡原因，`attack`表示当前伤害属性，`hitAngle`表示产生伤害的角度，`immune`表示产生当前伤害后是否让玩家处于无敌帧状态，`hurtSound`表示是否播放玩家受伤音效。 |
| Player:Heal\(int heal, bool showTip = true\) | void | 增加生命值。showTip表示是否显示数字提示。 |
| Player:AddMagic\(int heal, bool showTip = true\) | void | 增加魔法值。showTip表示是否显示数字提示。 |
| Player:AddMaxHealth\(int health\) | void | 增加生命值上限。 |
| Player:AddMaxMagic\(int magic\) | void | 增加魔法值上限。 |
| Player:AddExperience\(int amount\) | void | 增加经验值。 |
| Player:RemoveExpLevel\(int level\) | void | 减少经验等级。 |
| Player:AddBreath\(double breath\) | void | 增加呼吸值。 |
| Player:DecBreath\(double breath\) | void | 减少呼吸值。 |
| Player:SetBreath\(double breath\) | void | 设定呼吸值。 |
| Player:AddFood\(int foodLevel, int foodSaturationLevel\) | void | 增加饥饿值和食物饱和度。 |
| Player:DecFood\(int foodLevel, int foodSaturationLevel = 0\) | void | 减少饥饿值和食物饱和度。 |

#### BUFF相关函数

| 函数 | 返回值 | 描述 |
| :--- | :---: | :--- |
| Player:AddBuff\(int buffID, int buffTime\) | void | 为当前玩家添加一个状态效果。若原状态效果存在，以最长时间为新状态效果的持续时间。 |
| Player:RemoveBuff\(int buffID\) | void | 移除一个状态效果。 |
| Player:RemoveAllBuff\(\) | void | 移除全部状态效果。 |
| Player:RemoveAllBuffExceptHealthCold\(\) | void | 移除除“生命冷却”外的全部状态效果。 |
| Player:HasBuff\(int buffID\) | bool | 返回玩家是否拥有指定状态效果。 |
| Player:HasAnyBuff\(\) | bool | 返回玩家是否存在状态效果。 |





