# 用户图形界面UI

## 钩子函数（用户图形界面脚本：contents/guis/...）

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

### void OnUnload\(\)

```lua
function OnUnload()
    
end
```

决定当前GUI的卸载时的行为。

### void OnPushSlot\(int cellID, KeyboardTag kbTag\)

```lua
function OnPushSlot(cellID, kbTag)
    
end
```

**【仅服务端调用】**当物品放入某个格子控件时执行。

* `cellID`表示被放入物品的格子控件ID，使用`self:GetCell(cellID).hookItem`获取对应物品格子。
* `kbTag`表示放入物品时键盘附加情况。

### void OnPickSlot\(int cellID, KeyboardTag kbTag\)

```lua
function OnPickSlot(cellID, kbTag)
    
end
```

**【仅服务端调用】**当物品从某个格子控件取出时执行。

### bool RequestQuickPush\(ItemSlot itemSlot\)

```lua
function RequestQuickPush(itemSlot)
    return false
end
```

**【仅服务端调用】**当收到快速放入物品的请求时执行。返回true表示执行成功，返回false表示执行未发生变化。

* `itemSlot`表示待快速放入的物品格子。



## 用户图形界面通用模块（GuiUtils）

### 通用函数

| 函数 | 返回值 | 描述 |
| :--- | :---: | :--- |
| GuiUtils.OpenGui\(Player player, string guiName, int xi, int yi, GuiHookData hookData\) | void | 打开指定GUI。`player`表示打开GUI的玩家，`guiName`表示待打开的GUI名称，`xi`和`yi`表示打开GUI所在的格子位置，`hookData`表示GUI的钩子数据，该钩子数据将成为GUI容器的属性。 |

## GUI钩子数据类（GuiHookData Class）

表示一个GUI所挂钩的原始数据。

| 属性 | 类型 | 描述 |
| :--- | :---: | :--- |
| GuiHookData.blockEntityRef | BlockEntityRef | 当前钩子数据对应的方块实体引用。 |
| GuiHookData.npcRef | NpcRef | 当前钩子数据对应的NPC引用。 |
| GuiHookData.projectileRef | ProjectileRef | 当前钩子数据对应的抛射物引用。 |
| GuiHookData.playerRef | PlayerRef | 当前钩子数据对应的玩家引用。 |

| 静态函数 | 返回值 | 描述 |
| :--- | :---: | :--- |
| GuiHookData:new\_local\(\) | GuiHookData | 返回一个GUI钩子数据对象。 |

## 控件类（Control Class）

所有控件对象的基类，需创建于GUI容器内使用。

| 属性 | 类型 | 描述 |
| :--- | :---: | :--- |
| Control.id | int | **【只读】**当前控件ID。 |
| Control.x | int | 当前控件在容器内的左上角横坐标。 |
| Control.y | int | 当前控件在容器内的左上角纵坐标。 |
| Control.width | int | 当前控件的宽度。 |
| Control.height | int | 当前控件的高度。 |
| Control.visible | bool | 当前控件是否可见。 |
| Control.enabled | bool | 当前控件是否可用。 |

## 物品格子控件类（Cell Class，继承自Control Class）

用于容纳物品格子的控件。

| 属性 | 类型 | 描述 |
| :--- | :---: | :--- |
| Cell.allowPush | bool | 当前物品格子控件是否允许放入物品。 |
| Cell.allowPick | bool | 当前物品格子控件是否允许取出物品。 |
| Cell.hookSlot | ItemSlot | 【只读】当前控件绑定的物品格子。 |

| 函数 | 返回值 | 描述 |
| :--- | :---: | :--- |
| Cell:HookTempSlot\(\) | void | 为当前控件绑定一个临时物品格子。 |
| Cell:HookBlockEntitySlot\(ItemSlot itemSlot\) | void | 为当前控件绑定一个方块实体的物品格子。该物品只能从`hookData.blockEntityRef`中获取。 |



