# 注册信息API

全局表名称：reg

## 动态ID注册表

ID是游戏运行中动态生成的正整数数值。ID在游戏过程中不会变化，但是在每次启动游戏时ID会发生变化。因此需要注意：**任何情况下都不允许将ID存储到文件或存档内！！**

若需要存储ID，请使用GetXXXName\(int id\)来获取并存储其ID的字符串名称。若需要读取ID，请使用GetXXXID\(string name\)来获取其动态生成的ID。

| API | 返回值 | 描述 |
| :--- | :---: | :--- |
| Reg.ItemID\(string name\) | int | 根据**物品名**返回注册的动态ID。 |
| Reg.EffectID\(string name\) | int | 根据**特效名**返回注册的动态ID。 |
| Reg.BuffID\(string name\) | int | 根据**BUFF名**返回注册的动态ID。 |
| Reg.SoundID\(string name\) | int | 根据**音效名**返回注册的动态ID。 |
| Reg.SoundGroupID\(string name\) | int | 根据**音效组名**返回注册的动态ID。 |
| Reg.LiquidID\(string name\) | int | 根据**流体名**返回注册的动态ID。 |

