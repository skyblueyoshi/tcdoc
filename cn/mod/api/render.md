# 渲染API

## 精灵渲染模块（SpriteRender）

### 客户端通用函数

| 函数                                                             |    返回值    | 描述                                                                                                                   |
| -------------------------------------------------------------- | :-------: | -------------------------------------------------------------------------------------------------------------------- |
| SpriteRender.GetSpriteEx()                                     |  SpriteEx | 获取当前用于渲染的精灵拓展信息。                                                                                                     |
| SpriteRender.GetSourceRect()                                   | Rectangle | 获取当前源贴图的渲染剪裁区域。                                                                                                      |
| SpriteRender.Draw(int textureID, double drawX, double drawY)   |    void   | <p>将一个贴图绘制到屏幕内。（不使用精灵拓展信息）<br><code>textureID</code>表示源贴图ID，<code>drawX</code>和<code>drawY</code>表示绘制位置的横坐标和纵坐标。</p> |
| SpriteRender.DrawEx(int textureID, double drawX, double drawY) |    void   | 将一个贴图绘制到屏幕内。（使用精灵拓展信息）                                                                                               |

