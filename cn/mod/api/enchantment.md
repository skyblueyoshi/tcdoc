# 附魔API

## 钩子函数（附魔脚本：contents/enchantments/...）

### void UpdateArmoredByPlayer\(Player player, ItemSlot itemSlot, int level\)

```lua
function UpdateArmoredByPlayer(player, itemSlot, level)
    
end
```

玩家正确装备盔甲且拥有当前附魔时每帧调用该函数。

* `player`表示装备当前盔甲的玩家。
* `itemSlot`表示当前盔甲所在的物品格子。
* `level`表示当前附魔等级。

### void UpdateHeldByPlayer\(Player player, ItemSlot itemSlot, int level\)

```lua
function UpdateHeldByPlayer(player, itemSlot, level)
    
end
```

玩家手持工具且拥有当前附魔时每帧调用该函数。

* `player`表示当前玩家。
* `itemSlot`表示手持工具所在的物品格子。
* `level`表示当前附魔等级。

### void OnHitArmoredPlayerFromNpc\(Player player, Npc fromNpc, ItemSlot itemSlot, int level\)

```lua
function OnHitArmoredPlayerFromNpc(player, npc, itemSlot, level)
    
end
```

玩家正确装备盔甲且拥有当前附魔并被指定NPC击中时调用该函数。

* `player`表示当前玩家。
* `npc`攻击玩家的NPC。
* `itemSlot`表示手持工具所在的物品格子。
* `level`表示当前附魔等级。

