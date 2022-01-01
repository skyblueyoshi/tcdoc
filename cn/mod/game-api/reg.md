# Reg

ID是游戏运行中动态生成的正整数数值。ID在游戏过程中不会变化，但是在每次启动游戏时ID会发生变化。因此需要注意：**任何情况下都不允许将ID存储到文件或存档内。**

若需要存储ID，请使用GetXXXName(int id)来获取并存储其ID的字符串名称。若需要读取ID，请使用GetXXXID(string name)来获取其动态生成的ID。

## 函数

| 函数                                                                                                                                                        |
| --------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <p><strong>int Reg.ItemID(string name)</strong><br>根据<strong>物品名</strong>返回注册的动态ID。</p>                                                                   |
| <p><strong>int Reg.BlockID(string name)</strong><br>根据<strong>方块名</strong>返回注册的动态ID。</p>                                                                  |
| <p><strong>int Reg.BlockGroupID(string name)</strong><br>根据<strong>方块组名</strong>返回注册的动态ID。</p>                                                            |
| <p><strong>int Reg.BlockSubGroupID(string name)</strong><br>根据<strong>方块子组名</strong>返回注册的动态ID。</p>                                                        |
| <p>i<strong>nt Reg.BlockEntityID(string name)</strong><br>根据<strong>方块实体名</strong>返回注册的动态ID。</p>                                                          |
| <p><strong>int Reg.EffectID(string name)</strong><br>根据<strong>特效名</strong>返回注册的动态ID。</p>                                                                 |
| <p>i<strong>nt Reg.BuffID(string name)</strong><br>根据<strong>BUFF名</strong>返回注册的动态ID。</p>                                                                 |
| <p><strong>int Reg.EnchantmentID(string name)</strong><br>根据<strong>附魔名</strong>返回注册的动态ID。</p>                                                            |
| <p>i<strong>nt Reg.NpcID(string name)</strong><br>根据<strong>NPC名</strong>返回注册的动态ID。</p>                                                                   |
| <p><strong>int Reg.ProjectileID(string name)</strong><br>根据<strong>抛射物名</strong>返回注册的动态ID。</p>                                                            |
| <p>i<strong>nt Reg.SoundID(string name)</strong><br>根据<strong>音效名</strong>返回注册的动态ID。</p>                                                                  |
| <p><strong>int Reg.SoundGroupID(string name)</strong><br>根据<strong>音效组名</strong>返回注册的动态ID。</p>                                                            |
| <p><strong>int Reg.LiquidID(string name)</strong><br>根据<strong>流体名</strong>返回注册的动态ID。</p>                                                                 |
| <p><strong>int Reg.SkeletonJointID(string skeletonName, string jointName)</strong><br>根据<strong>骨骼模型名</strong>和<strong>关节名</strong>返回关节在该骨骼模型注册的动态ID。</p> |
| <p><strong>int Reg.ModTextureID(string name)</strong><br>根据<strong>模组贴图名</strong>返回注册的动态<strong>贴图ID</strong>。服务端总是返回0。</p>                               |

