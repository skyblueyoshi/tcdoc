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

## 玩家类（Player Class，继承自Entity Class）

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
| Player.isCurrentClientPlayer | bool | **【只读】**玩家是否为当前客户端所操作的玩家。若当前运行环境为服务端总是表示`false`。 |

#### 数值属性

<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x5C5E;&#x6027;</th>
      <th style="text-align:center">&#x7C7B;&#x578B;</th>
      <th style="text-align:left">&#x63CF;&#x8FF0;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">Player.name</td>
      <td style="text-align:center">string</td>
      <td style="text-align:left"><b>&#x3010;&#x53EA;&#x8BFB;&#x3011;</b>&#x73A9;&#x5BB6;&#x540D;&#x79F0;&#x3002;&#xFF08;UTF8&#x683C;&#x5F0F;&#xFF09;</td>
    </tr>
    <tr>
      <td style="text-align:left">Player.ip</td>
      <td style="text-align:center">string</td>
      <td style="text-align:left">
        <p><b>&#x3010;&#x53EA;&#x8BFB;&#x3011;</b>&#x73A9;&#x5BB6;&#x8FDE;&#x63A5;&#x4F1A;&#x8BDD;&#x7684;IP&#x5730;&#x5740;&#x3002;&#xFF08;UTF8&#x683C;&#x5F0F;&#xFF09;</p>
        <p>&#x5728;&#x5BA2;&#x6237;&#x7AEF;&#x4E2D;&#x8BE5;&#x503C;&#x603B;&#x662F;&#x8868;&#x793A;&#x4E3A;&#x7A7A;&#x5B57;&#x7B26;&#x4E32;&#x3002;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Player.portNumber</td>
      <td style="text-align:center">int</td>
      <td style="text-align:left">
        <p><b>&#x3010;&#x53EA;&#x8BFB;&#x3011;</b>&#x73A9;&#x5BB6;&#x8FDE;&#x63A5;&#x4F1A;&#x8BDD;&#x7684;&#x7AEF;&#x53E3;&#x53F7;&#x3002;</p>
        <p>&#x5728;&#x5BA2;&#x6237;&#x7AEF;&#x4E2D;&#x8BE5;&#x503C;&#x603B;&#x662F;&#x8868;&#x793A;&#x4E3A;0&#x3002;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Player.health</td>
      <td style="text-align:center">int</td>
      <td style="text-align:left"><b>&#x3010;&#x53EA;&#x8BFB;&#x3011;</b>&#x73A9;&#x5BB6;&#x751F;&#x547D;&#x503C;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">Player.maxHealth</td>
      <td style="text-align:center">int</td>
      <td style="text-align:left"><b>&#x3010;&#x53EA;&#x8BFB;&#x3011;</b>&#x73A9;&#x5BB6;&#x751F;&#x547D;&#x503C;&#x4E0A;&#x9650;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">Player.maxMaxHealth</td>
      <td style="text-align:center">int</td>
      <td style="text-align:left"><b>&#x3010;&#x53EA;&#x8BFB;&#x3011;</b>&#x73A9;&#x5BB6;&#x6700;&#x9AD8;&#x80FD;&#x8FBE;&#x5230;&#x7684;&#x751F;&#x547D;&#x503C;&#x4E0A;&#x9650;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">Player.mana</td>
      <td style="text-align:center">int</td>
      <td style="text-align:left"><b>&#x3010;&#x53EA;&#x8BFB;&#x3011;</b>&#x73A9;&#x5BB6;&#x9B54;&#x6CD5;&#x503C;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">Player.maxMana</td>
      <td style="text-align:center">int</td>
      <td style="text-align:left"><b>&#x3010;&#x53EA;&#x8BFB;&#x3011;</b>&#x73A9;&#x5BB6;&#x9B54;&#x6CD5;&#x503C;&#x4E0A;&#x9650;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">Player.maxMaxMana</td>
      <td style="text-align:center">int</td>
      <td style="text-align:left"><b>&#x3010;&#x53EA;&#x8BFB;&#x3011;</b>&#x73A9;&#x5BB6;&#x6700;&#x9AD8;&#x80FD;&#x8FBE;&#x5230;&#x7684;&#x9B54;&#x6CD5;&#x503C;&#x4E0A;&#x9650;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">Player.expLevel</td>
      <td style="text-align:center">int</td>
      <td style="text-align:left"><b>&#x3010;&#x53EA;&#x8BFB;&#x3011;</b>&#x73A9;&#x5BB6;&#x7ECF;&#x9A8C;&#x7B49;&#x7EA7;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">Player.isNoBreathing</td>
      <td style="text-align:center">bool</td>
      <td style="text-align:left"><b>&#x3010;&#x53EA;&#x8BFB;&#x3011;</b>&#x73A9;&#x5BB6;&#x5F53;&#x524D;&#x662F;&#x5426;&#x4E0D;&#x80FD;&#x547C;&#x5438;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">Player.breath</td>
      <td style="text-align:center">double</td>
      <td style="text-align:left"><b>&#x3010;&#x53EA;&#x8BFB;&#x3011;</b>&#x73A9;&#x5BB6;&#x547C;&#x5438;&#x503C;&#x3002;&#x6709;&#x6548;&#x8303;&#x56F4;&#x4E3A;[0.0,
        1.0]&#x3002;&#x5F53;&#x547C;&#x5438;&#x503C;&#x4E3A;0.0&#x65F6;&#x4F1A;&#x4EA7;&#x751F;&#x7A92;&#x606F;&#x4F24;&#x5BB3;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">Player.foodLevel</td>
      <td style="text-align:center">int</td>
      <td style="text-align:left"><b>&#x3010;&#x53EA;&#x8BFB;&#x3011;</b>&#x73A9;&#x5BB6;&#x9965;&#x997F;&#x503C;&#x3002;&#x6709;&#x6548;&#x8303;&#x56F4;&#x4E3A;[1,
        100]&#x3002;&#x5F53;&#x9965;&#x997F;&#x503C;&#x4E3A;0&#x65F6;&#x4F1A;&#x4EA7;&#x751F;&#x9965;&#x997F;&#x4F24;&#x5BB3;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">Player.foodSaturationLevel</td>
      <td style="text-align:center">int</td>
      <td style="text-align:left"><b>&#x3010;&#x53EA;&#x8BFB;&#x3011;</b>&#x73A9;&#x5BB6;&#x98DF;&#x7269;&#x9971;&#x548C;&#x5EA6;&#x3002;&#x6709;&#x6548;&#x8303;&#x56F4;&#x4E3A;[1,
        100]&#x3002;&#x5F53;&#x524D;&#x98DF;&#x7269;&#x9971;&#x548C;&#x5EA6;&#x4E0D;&#x4F1A;&#x8D85;&#x8FC7;&#x5F53;&#x524D;&#x9965;&#x997F;&#x503C;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">Player.baseAttack</td>
      <td style="text-align:center">Attack</td>
      <td style="text-align:left">&#x73A9;&#x5BB6;&#x7684;&#x57FA;&#x7840;&#x653B;&#x51FB;&#x5C5E;&#x6027;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">Player.baseDefence</td>
      <td style="text-align:center">Defence</td>
      <td style="text-align:left">&#x73A9;&#x5BB6;&#x7684;&#x57FA;&#x7840;&#x9632;&#x5FA1;&#x5C5E;&#x6027;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">Player.inLiquid</td>
      <td style="text-align:center">bool</td>
      <td style="text-align:left"><b>&#x3010;&#x53EA;&#x8BFB;&#x3011;</b>&#x5F53;&#x524D;&#x73A9;&#x5BB6;&#x662F;&#x5426;&#x5904;&#x5728;&#x6D41;&#x4F53;&#x73AF;&#x5883;&#x4E2D;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">Player.oldInLiquid</td>
      <td style="text-align:center">bool</td>
      <td style="text-align:left"><b>&#x3010;&#x53EA;&#x8BFB;&#x3011;</b>&#x4E0A;&#x4E00;&#x5E27;&#x7684;&#x73A9;&#x5BB6;&#x662F;&#x5426;&#x5904;&#x5728;&#x6D41;&#x4F53;&#x73AF;&#x5883;&#x4E2D;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">Player.touchLiquidID</td>
      <td style="text-align:center">int</td>
      <td style="text-align:left"><b>&#x3010;&#x53EA;&#x8BFB;&#x3011;</b>&#x5F53;&#x524D;&#x73A9;&#x5BB6;&#x6240;&#x5904;&#x6D41;&#x4F53;&#x73AF;&#x5883;&#x7684;ID&#x3002;&#x5982;&#x679C;&#x4E0D;&#x5728;&#x4EFB;&#x4F55;&#x6D41;&#x4F53;&#x5185;&#xFF0C;&#x5219;ID&#x603B;&#x662F;&#x4E3A;0&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">Player.isInvisibility</td>
      <td style="text-align:center">bool</td>
      <td style="text-align:left">&#x73A9;&#x5BB6;&#x662F;&#x5426;&#x9690;&#x8EAB;&#x3002;&#xFF08;&#x6BCF;&#x5E27;&#x91CD;&#x7F6E;&#x4E3A;<code>false</code>&#xFF09;</td>
    </tr>
  </tbody>
</table>

#### 权限属性

| 属性 | 类型 | 描述 |
| :--- | :---: | :--- |
| Player.gameMode | int | **【只读】**玩家游戏模式。 |
| Player.op | int | **【只读】**玩家权限等级。 |

### 类成员函数

#### 控制函数

| 函数 | 返回值 | 描述 |
| :--- | :---: | :--- |
| Player:SetSpeedX\(double speedX\) | void | 设定玩家的横向速度。（对所控制的玩家生效） |
| Player:SetSpeedY\(double speedY\) | void | 设定玩家的纵向速度。（对所控制的玩家生效） |

#### 其他函数

| 函数 | 返回值 | 描述 |
| :--- | :---: | :--- |
| Player:Strike\(DeathReason reason, Attack attack, double hitAngle = 0, bool immune = false, bool hurtSound = true\) | void | 伤害当前玩家。`reason`表示死亡原因，`attack`表示当前伤害属性，`hitAngle`表示产生伤害的角度，`immune`表示产生当前伤害后是否让玩家处于无敌帧状态，`hurtSound`表示是否播放玩家受伤音效。 |
| Player:StrikeFromNpcWeapon\(Npc npc, ItemSlot weaponItemSlot, Attack attack, double hitAngle = 0, bool immune = false, bool hurtSound = true\) | void | 指定NPC使用武器伤害当前玩家。`npc`表示造成伤害的NPC，`weaponItemSlot`表示NPC所用的武器物品格子。 |
| Player:StrikeFromPlayerWeapon\(Player player, ItemSlot weaponItemSlot, Attack attack, double hitAngle = 0, bool immune = false, bool hurtSound = true\) | void | 指定玩家使用武器伤害当前玩家。`player`表示造成伤害的玩家，`weaponItemSlot`表示玩家所用的武器物品格子。 |
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
| Player:GetHeldItemSlot\(\) | ItemSlot | 返回玩家当前手持物品格子。 |
| Player:AddBuff\(int buffID, int buffTime\) | void | 为当前玩家添加一个状态效果。若原状态效果存在，以最长时间为新状态效果的持续时间。 |
| Player:RemoveBuff\(int buffID\) | void | 移除一个状态效果。 |
| Player:RemoveAllBuff\(\) | void | 移除全部状态效果。 |
| Player:RemoveAllBuffExceptHealthCold\(\) | void | 移除除“生命冷却”外的全部状态效果。 |
| Player:HasBuff\(int buffID\) | bool | 返回玩家是否拥有指定状态效果。 |
| Player:HasAnyBuff\(\) | bool | 返回玩家是否存在状态效果。 |

#### 服务端函数

| 函数 | 返回值 | 描述 |
| :--- | :---: | :--- |
| Player:SetGameMode\(GameMode gameMode, bool changeFromSelf = false\) | void | 为当前玩家设定游戏模式。`changeFromSelf`表示变更是否来自玩家自己，若为`true`且玩家先前为创造模式，则仍然拥有创造模式指令权限。 |
| Player:SetOP\(OP op\) | void | 为当前玩家设定权限等级。 |
| Player:Teleport\(double newCenterX, double newBottomY, bool playTeleportSound = false\) | void | 传送当前玩家到指定坐标。`newCenterX`表示玩家传送后中心横坐标，`newBottomY`表示玩家传送后的底部纵坐标，`playTeleportSound`表示是否播放传送音效。 |
| Player:TeleportToSpawn\(\) | void | 传送当前玩家到出生点。 |
| Player:GoHome\(\) | bool | 传送当前玩家到玩家设定重生点，传送成功返回true。如果玩家设定重生点不存在，不执行传送并返回false。 |
| Player:AddBackpack\(int itemID, int itemCount\) | void | 添加指定物品ID和数量的物品到玩家背包。如果玩家背包已满则会以掉落物的形式抛出。 |
| Player:ClearBackpack\(\) | void | 清空玩家背包数据。 |



