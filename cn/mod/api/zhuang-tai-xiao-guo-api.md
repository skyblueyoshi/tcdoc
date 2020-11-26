# 状态效果API

## 钩子函数

请在状态效果（Buff）脚本中使用这些钩子函数。

### void UpdatePlayer\(Player player, int tickTime, int buffRemainTime\)

```lua
function UpdatePlayer(player, tickTime, buffRemainTime)
    --call this function every game tick if player has this buff
end
```

玩家拥有该状态效果时每帧调用该函数。tickTime表示当前玩家实际生存时间（帧）。buffRemainTime表示BUFF剩余生效时间。

### void UpdateNpc\(Npc npc, int tickTime, int buffRemainTime\)

```lua
function UpdateNpc(npc, tickTime, buffRemainTime)
    --call this function every game tick if npc has this buff
end
```

NPC拥有该状态效果时每帧调用该函数。tickTime表示当前NPC实际生存时间（帧）。buffRemainTime表示BUFF剩余生效时间。





