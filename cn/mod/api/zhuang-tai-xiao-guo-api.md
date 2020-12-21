# 状态效果API

## 钩子函数

请在**状态效果（Buff）**脚本中使用这些钩子函数。

#### void UpdatePlayer\(Player player, int buffRemainTime\)

```lua
function UpdatePlayer(player, buffRemainTime)
    
end
```

玩家拥有该状态效果时每帧调用该函数。

* `buffRemainTime`表示BUFF剩余生效时间。

#### void UpdateNpc\(Npc npc, int buffRemainTime\)

```lua
function UpdateNpc(npc, buffRemainTime)
    
end
```

NPC拥有该状态效果时每帧调用该函数。

* `buffRemainTime`表示BUFF剩余生效时间。





