# 玩家API

## 玩家通用模块（PlayerUtils）

| 函数 | 返回值 | 描述 |
| :--- | :---: | :--- |
| PlayerUtils.SearchByRect\(double x, double y, int width, int height\) | ArrayList&lt;Player&gt; | 返回包含于指定矩形区域内部的所有玩家列表。 |
| PlayerUtils.SearchByCircle\(double centerX, double centerY, int radius\) | ArrayList&lt;Player&gt; | 返回包含于指定圆形区域内部的所有玩家列表。 |
| PlayerUtils.SearchNearestPlayer\(double centerX, double centerY, int radius, bool noCrossTiles = false\) | Player/nil | 搜索在指定圆形区域内部距离圆心最近的玩家，返回该玩家。若结果不存在，返回nil。noCrossTiles表示是否排除中心到圆心的连线被图格遮挡的玩家。 |

## 玩家控制器类（PlayerController Class）

**玩家控制器（PlayerController）**类是玩家类的一个成员属性，用于控制玩家行为。

### 类成员属性

| 属性 | 类型 | 描述 |
| :--- | :---: | :--- |
| PlayerController.defaultMaxSpeed | double | **【只读】**玩家默认最大运动速度。 |
| PlayerController.speedRate | double | 玩家最大运动速度与默认最大运动速度比率。每帧重置为`1.0`。 |
| PlayerController.defaultJumpTime | int | **【只读】**玩家默认跳跃持续上升时间。 |
| PlayerController.jumpTime | double | 玩家跳跃持续上升时间与默认跳跃持续上升时间比率。每帧重置为`1.0`。 |

## 玩家类（Player Class）

**玩家（Player）**类表示玩家实际控制的角色实体类。

### 父类

该类的父类为[Entity类](entity.md#shi-ti-lei-entity-class)。可直接使用该父类的类成员属性与类成员函数。

由于玩家类的特殊性，该父类的所有**【类成员属性全部只读】**。

### 类成员属性

| 属性 | 类型 | 描述 |
| :--- | :---: | :--- |
| Player.controller | PlayerController | 玩家控制器，用于控制玩家行为。 |
| Player.health | int | **【只读】**玩家生命值。 |
| Player.maxHealth | int | **【只读】**玩家生命值上限。 |
| Player.maxMaxHealth | int | **【只读】**玩家最高能达到的生命值上限。 |
| Player.mana | int | **【只读】**玩家魔法值。 |
| Player.maxMana | int | **【只读】**玩家魔法值上限。 |
| Player.maxMaxMana | int | **【只读】**玩家最高能达到的魔法值上限。 |
| Player.expLevel | int | **【只读】**玩家经验等级。 |

### 类成员函数



#### 数值属性函数

| 函数 | 返回值 | 描述 |
| :--- | :---: | :--- |
| Player:Heal\(int heal, bool showTip = true\) | void | 为当前玩家增加生命值。showTip表示是否显示数字提示。 |
| Player:AddMagic\(int heal, bool showTip = true\) | void | 为当前玩家增加魔法值。showTip表示是否显示数字提示。 |
| Player:AddMaxHealth\(int health\) | void | 为当前玩家增加生命值上限。 |
| Player:AddMaxMagic\(int magic\) | void | 为当前玩家增加魔法值上限。 |
| Player:AddExperience\(int amount\) | void | 为当前玩家增加经验值。 |
| Player:RemoveExpLevel\(int level\) | void | 消耗当前玩家的经验等级。 |

#### BUFF相关函数

| 函数 | 返回值 | 描述 |
| :--- | :---: | :--- |
| Player:AddBuff\(int buffID, int buffTime\) | void | 为当前玩家添加一个状态效果。若原状态效果存在，以最长时间为新状态效果的持续时间。 |
| Player:RemoveBuff\(int buffID\) | void | 移除一个状态效果。 |
| Player:RemoveAllBuff\(\) | void | 移除全部状态效果。 |
| Player:RemoveAllBuffExceptHealthCold\(\) | void | 移除除“生命冷却”外的全部状态效果。 |
| Player:HasBuff\(int buffID\) | bool | 返回玩家是否拥有指定状态效果。 |
| Player:HasAnyBuff\(\) | bool | 返回玩家是否存在状态效果。 |





