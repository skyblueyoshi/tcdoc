# 物品API

## 钩子函数（物品脚本：contents/item\_ai/...）

### void OnUseFromPlayer(Player player, ItemSlot itemSlot, Hitbox hitbox, double fireX, double fireY)

```lua
function OnUseFromPlayer(player, itemSlot, hitbox, fireX, fireY)
    
end
```

玩家正在使用该工具物品时调用该函数。

* `player`表示使用当前物品的玩家。
* `itemSlot`表示正在使用的物品所在的物品格子。
* `hitbox`表示当前物品的碰撞箱。
* `fireX`和`fireY`表示当前物品实际开火坐标。

### void OnUseFromNpc(Npc npc, ItemSlot itemSlot, Hitbox hitbox, double fireX, double fireY)

```lua
function OnUseFromNpc(Npc npc, itemSlot, hitbox, fireX, fireY)
    
end
```

NPC正在使用该工具物品时调用该函数。

* `npc`表示使用当前物品的NPC。

### bool CheckShoot(ItemSlot itemSlot, Hitbox hitbox, int consumeItemID, int projectileID, double fireX, double fireY, double shootSpeed, double shootAngle, Attack baseAttack)

```lua
function CheckShoot(itemSlot, hitbox, consumeItemID, projectileID, fireX, fireY, shootSpeed, shootAngle, baseAttack)
    return true
end
```

该工具物品发射抛射物前调用该函数，可以通过修改`baseAttack`参数决定攻击力，并允许自定义发射效果。`return true`表示决定发射，`return false`表示不会进行发射。若不编写该函数，默认决定发射。

* `itemSlot`表示正在使用的物品所在的物品格子。
* `hitbox`表示当前物品的碰撞箱。
* `consumeItemID`表示待消耗的物品ID。若不会消耗物品，总是表示0。
* `projectileID`表示发射的抛射物ID。
* `fireX`和`fireY`表示当前物品实际开火坐标。
* `shootSpeed`表示抛射物的发射初始速度。
* `shootAngle`表示抛射物的发射角度。
* `baseAttack`表示抛射物的初始攻击属性。

### bool OnShootFromPlayer(Player player, ItemSlot itemSlot, Hitbox hitbox, int consumeItemID, int projectileID, double fireX, double fireY, double shootSpeed, double shootAngle, Attack baseAttack)

```lua
function OnShootFromPlayer(player, itemSlot, hitbox, consumeItemID, projectileID, fireX, fireY, shootSpeed, shootAngle, baseAttack)
    return true
end
```

玩家使用该工具物品发射抛射物时调用该函数，可以在该函数内自定义具体的抛射物发射方式。`return true`表示发射成功。若发射成功则消耗背包抛射物物品。若不编写该函数，默认使用内置的发射逻辑。

* `player`表示使用当前物品的玩家。

### bool OnShootFromNpc(Npc npc, ItemSlot itemSlot, Hitbox hitbox, int consumeItemID, int projectileID, double fireX, double fireY, double shootSpeed, double shootAngle, Attack baseAttack)

```lua
function OnShootFromNpc(npc, itemSlot, hitbox, consumeItemID, projectileID, fireX, fireY, shootSpeed, shootAngle, baseAttack)
    return true
end
```

NPC使用该工具物品发射抛射物时调用该函数，可以在该函数内自定义具体的抛射物发射方式。`return true`表示是否发射成功。若不编写该函数，默认使用内置的发射逻辑。

* `npc`表示使用当前物品的NPC。

### bool CheckHitNpc(Npc npcTarget, ItemSlot itemSlot, Hitbox hitbox, double fireX, double fireY, double hitAngle, ref Attack baseAttack)

```lua
function CheckHitNpc(npcTarget, itemSlot, hitbox, fireX, fireY, hitAngle, baseAttack)
    return true
end
```

该工具物品击中NPC前调用该函数，可以通过修改`baseAttack`参数决定攻击力，并允许自定义击中效果。`return true`表示决定执行接下来的命中逻辑，`return false`表示取消命中逻辑。若不编写该函数，默认决定执行命中逻辑。

* `npcTarget`表示被击中的NPC。
* `itemSlot`表示正在使用的物品所在的物品格子。
* `hitbox`表示当前物品的碰撞箱。
* `fireX`和`fireY`表示当前物品实际开火坐标。
* `hitAngle`表示击中角度。
* `baseAttack`表示初始攻击属性。

### bool CheckHitPlayer(Player playerTarget, ItemSlot itemSlot, Hitbox hitbox, double fireX, double fireY, double hitAngle, Attack baseAttack)

```lua
function CheckHitPlayer(playerTarget, itemSlot, hitbox, fireX, fireY, hitAngle, baseAttack)
    return true
end
```

该工具物品击中玩家前调用该函数，可以通过修改`baseAttack`参数决定攻击力，并允许自定义击中效果。`return true`表示决定执行接下来的命中逻辑，`return false`表示取消命中逻辑。若不编写该函数，默认决定执行命中逻辑。

* `playerTarget`表示被击中的玩家。

### bool CheckConsumeItem(Player player, ItemSlot itemSlot, int projectileID)

```lua
function CheckConsumeItem(player, itemSlot, projectileID)
    return true
end
```

决定当前工具物品发射出抛射物后是否消耗背包抛射物物品。`return false`表示不会消耗背包抛射物物品。若不编写该函数，默认按内部逻辑决定是否消耗背包抛射物物品。

## 物品通用模块（ItemUtils）

#### 数值函数

| 函数                             |    返回值   | 描述                                                |
| ------------------------------ | :------: | ------------------------------------------------- |
| ItemUtils.MaxCount(int itemID) |    int   | 返回指定物品ID的最大允许数量。若物品ID为0，返回0。                      |
| ItemUtils.Type(int itemID)     | ItemType | 返回指定物品ID的物品类型。若物品ID为0，返回_`ITEM_TYPE_NONE`_。       |
| ItemUtils.ToolType(int itemID) | ToolType | 若指定物品ID为工具，表示指定物品ID的工具类型，否则总是为_`TOOL_TYPE_NONE`_。 |
| ItemUtils.ColdTime(int itemID) |    int   | 若指定物品ID为工具，返回指定物品ID的工具冷却时间（使用时间），否则总是返回0。         |

#### 功能函数

| 函数                                                                                                                          |  返回值 | 描述                                                                                                                                                                                                                       |
| --------------------------------------------------------------------------------------------------------------------------- | :--: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| ItemUtils.CreateDrop(int itemID, int count, double centerX, double centerY, double speedX, double speedY, int coldTime = 0) | void | <p>创建一个物品掉落物。<br><code>itemID</code>：创建的物品ID。<code>count</code>：创建的物品个数。<code>centerX</code>和<code>centerY</code>：创建掉落物的中心位置。<code>speedX</code>和<code>speedY</code>：创建掉落物的初始速度。<code>coldTime</code>：掉落物能被玩家前的等待时间。</p> |

## 物品格类（ItemSlot Class）

**物品格（ItemSlot）**类表示拥有物品格子基本信息的类对象。

物品格可能包含某种类型的物品，也可能不包含任何物品，即**空物品格**。

以Minecraft为例，下图描述了有物品和无物品的两种物品格：

![包含“河豚”物品的物品格](../../../.gitbook/assets/item\_slot\_has\_item.png)

![不包含物品的空物品格](../../../.gitbook/assets/item\_slot\_empty.png)

**在对物品格进行相关物品操作时必须预先判断当前物品格是否包含物品。**

### **类成员属性**

| 属性                  |    类型    | 描述                                                             |
| ------------------- | :------: | -------------------------------------------------------------- |
| ItemSlot.hasItem    |   bool   | **【只读】**当前物品格是否包含物品。                                           |
| ItemSlot.id         |    int   | **【只读】**若物品格不为空，表示包含的**物品ID**，否则总是为0。                          |
| ItemSlot.count      |    int   | **【只读】**若物品格不为空，表示包含的物品**数量**，否则总是为0。                          |
| ItemSlot.maxCount   |    int   | **【只读】**若物品格不为空，表示包含的物品**最大允许数量**，否则总是为0。                      |
| ItemSlot.type       | ItemType | **【只读】**若物品格不为空，表示内置物品**类型**，否则总是为_`ITEM_TYPE_NONE`_。          |
| ItemSlot.toolType   | ToolType | **【只读】**若物品格不为空且物品为工具，表示内置物品的**工具类型**，否则总是为_`TOOL_TYPE_NONE`_。 |
| ItemSlot.coldTime   |    int   | **【只读】**若物品格不为空且物品为工具，表示内置物品的工具**冷却时间（使用时间）**，否则总是为0。          |
| ItemSlot.shootTimes |    int   | **【只读】**若物品格不为空且物品为工具，表示内置物品工具的**发射次数**，否则总是为0。                |
| ItemSlot.deviation  |  double  | **【只读】**若物品格不为空且物品为工具，表示内置物品工具的**发射偏差角度**，否则总是为0。              |

### 类成员函数

| 函数                                                    |  返回值 | 描述                                                                                                                                                                                             |
| ----------------------------------------------------- | :--: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ItemSlot:Create(int itemID, int count = 1)            | bool | <p>若物品格为空，创建新的指定物品，返回true。</p><p>若物品格不为空，先销毁原包含物品，再创建新的指定物品，返回true。</p><p>若itemID非法或count非正数，销毁原包含物品并返回false。</p>                                                                              |
| ItemSlot:Replace(ItemSlot slot)                       | void | 将当前物品格替换为指定物品格。                                                                                                                                                                                |
| ItemSlot:Swap(ItemSlot slot)                          | void | 将当前物品格与另一个物品格交换。                                                                                                                                                                               |
| ItemSlot:Clear()                                      | void | 销毁内部的全部物品。                                                                                                                                                                                     |
| ItemSlot:RemoveOne()                                  | bool | <p>若物品格不为空，移除内部1个物品。</p><p>若操作后物品格物品格为空，返回true。若物品格仍然存在物品，返回false。</p>                                                                                                                         |
| ItemSlot:MoveFrom(ItemSlot slot)                      |  int | <p>将指定物品格的内容物品移入到当前物品格。返回成功移入的物品个数。</p><p>转移规则见：<a href="item.md#wu-pin-zhuan-yi-gui-ze">物品转移规则</a></p>                                                                                        |
| ItemSlot:MoveTo(ItemSlot slot)                        |  int | <p>将当前物品格的内容物移出到指定物品格。返回成功移出的物品个数。</p><p>转移规则见：<a href="item.md#wu-pin-zhuan-yi-gui-ze">物品转移规则</a></p>                                                                                         |
| ItemSlot:SetCount(int count)                          |  int | <p>若物品格不为空，设置包含的物品数量，返回设置后物品数量。</p><p>若物品格为空，不进行任何操作并返回0。</p><p>设定规则见：<a href="item.md#wu-pin-shu-liang-she-ding-yuan-ze">物品数量设定规则</a></p>                                                     |
| ItemSlot:AddCount(int addCount)                       |  int | <p>若物品格不为空，为包含的物品添加数量，返回添加后物品数量。</p><p>若addCount为正数，表示添加物品数量。若addCount为负数，表示减少物品数量。</p><p>若物品格为空，不进行任何操作并返回0。</p><p>设定规则见：<a href="item.md#wu-pin-shu-liang-she-ding-yuan-ze">物品数量设定规则</a></p> |
| ItemSlot:GetEnchantmentLevel(int enchantmentID)       |  int | 若物品格不为空且内容物品拥有附魔，返回指定附魔的等级。若附魔不存在，总是返回0。                                                                                                                                                       |
| ItemSlot:AddEnchantment(int enchantmentID, int level) | bool | <p>为指定物品格的内容物品添加一个附魔，返回是否添加成功。</p><p>若物品格为空，不进行任何操作并返回false。</p><p>若物品格内物品无法与附魔对应，不进行任何操作并返回false。</p>                                                                                         |

## 物品数量设定规则

在物品格不包含物品的情况下，不会进行任何设定操作。

在物品格包含物品的情况下，若设定数量在区间**\[1, 最大允许数量]**，则设定数量合法，直接将物品数量设为指定数量。否则：

1. 若设定数量超过最大允许数量，将物品数量设为最大允许数量。
2. 若设定数量非正数，清除内部包含的物品。

## 物品转移规则

将一个物品格的物品转移至另一个物品格时，若两个物品格的物品不是同类物品，不会进行转移。若物品格转移达到最大允许数量，则终止转移。



