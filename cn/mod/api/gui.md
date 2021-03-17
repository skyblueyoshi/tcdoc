# 用户图形界面UI

## 钩子函数

请在**用户图形界面（GUI）**脚本中使用这些钩子函数。

### void CheckOnLoad\(\)

```lua
function CheckOnLoad()
    return true
end
```

决定当前GUI是否加载。返回`true`表示加载，返回`false`表示取消加载。

### void OnLoad\(\)

```lua
function OnLoad()
    
end
```

决定当前GUI的加载行为。一般在该函数中设置GUI属性、创建控件等初始化操作。

