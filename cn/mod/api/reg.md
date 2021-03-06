# 注册信息API

## 注册表模块（Reg）

ID是游戏运行中动态生成的正整数数值。ID在游戏过程中不会变化，但是在每次启动游戏时ID会发生变化。因此需要注意：**任何情况下都不允许将ID存储到文件或存档内！！**

若需要存储ID，请使用GetXXXName\(int id\)来获取并存储其ID的字符串名称。若需要读取ID，请使用GetXXXID\(string name\)来获取其动态生成的ID。

| API | 返回值 | 描述 |
| :--- | :---: | :--- |
| Reg.ItemID\(string name\) | int | 根据**物品名**返回注册的动态ID。 |
| Reg.BlockID\(string name\) | int | 根据**方块名**返回注册的动态ID。 |
| Reg.BlockGroupID\(string name\) | int | 根据**方块组名**返回注册的动态ID。 |
| Reg.BlockSubGroupID\(string name\) | int | 根据**方块子组名**返回注册的动态ID。 |
| Reg.BlockEntityID\(string name\) | int | 根据**方块实体名**返回注册的动态ID。 |
| Reg.EffectID\(string name\) | int | 根据**特效名**返回注册的动态ID。 |
| Reg.BuffID\(string name\) | int | 根据**BUFF名**返回注册的动态ID。 |
| Reg.EnchantmentID\(string name\) | int | 根据**附魔名**返回注册的动态ID。 |
| Reg.NpcID\(string name\) | int | 根据**NPC名**返回注册的动态ID。 |
| Reg.ProjectileID\(string name\) | int | 根据**抛射物名**返回注册的动态ID。 |
| Reg.SoundID\(string name\) | int | 根据**音效名**返回注册的动态ID。 |
| Reg.SoundGroupID\(string name\) | int | 根据**音效组名**返回注册的动态ID。 |
| Reg.LiquidID\(string name\) | int | 根据**流体名**返回注册的动态ID。 |
| Reg.SkeletonJointID\(string skeletonName, string jointName\) | int | 根据**骨骼模型名**和**关节名**返回关节在该骨骼模型注册的动态ID。 |
| Reg.ModTextureID\(string name\) | int | 根据**模组贴图名**返回注册的动态**贴图ID**。服务端总是返回0。 |



