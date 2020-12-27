# 渲染API

## 渲染模块（Render）

### 通用变量

| 变量名 | 类型 | 描述 |
| :--- | :---: | :--- |
| Render.screenX | double | 当前客户端屏幕左上角横坐标。 |
| Render.screenY | double | 当前客户端屏幕左上角纵坐标。 |

### 通用函数

| 函数 | 返回值 | 描述 |
| :--- | :---: | :--- |
| Render.Draw\(int textureID, double drawX, double drawY, Rectangle sourceRectangle, Color color = _COLOR\_WHITE_\) | void | 将一个贴图绘制到屏幕内。`textureID`表示源贴图ID，`drawX`和`drawY`表示绘制位置的横坐标和纵坐标，`sourceRectangle`表示在源贴图的剪裁区域，`color`表示绘制贴图的颜色。 |
| Render.DrawEx\(int textureID, double drawX, double drawY, Rectangle sourceRectangle, SpriteEx spriteEx, Color color = _COLOR\_WHITE_\) | void | 将一个贴图绘制到屏幕内。`spriteEx`表示贴图绘制的拓展信息。 |

