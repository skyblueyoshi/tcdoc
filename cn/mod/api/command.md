# 指令API

## 钩子函数（指令脚本：contents/commands/...）

### void RunCommandFromPlayer\(Player player, ...\)

```lua
function RunCommand(player, ...)
    
end
```

成功解析由玩家输入的当前指令后执行该函数。

* `player`表示输入当前指令的玩家。
* 后面的参数由指令具体参数列表决定。

### void RunCommand\(SourceCmd sourceCmd, ...\)

```lua
function RunCommand(sourceCmd, ...)
    
end
```

成功解析由服务端控制台或玩家输入的当前指令后执行该函数。

* `sourceCmd`表示指令输入源。

## 指令源（SourceCmd Class）

指令源（SourceCmd）类输入当前指令的来源。

### 类成员函数

| 函数 | 返回值 | 描述 |
| :--- | :--- | :--- |
| SourceCmd:Response\(string message\) | void | 给当前指令源返回一条响应信息。若指令源为服务端控制台，则在控制台打印响应信息。若指令源为玩家，则会单播响应消息到玩家所在的客户端。 |
| SourceCmd:ResponseUTF8\(string message\) | void | 给当前指令源返回一条UTF8格式的响应信息。 |



