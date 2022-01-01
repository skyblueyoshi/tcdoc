# 地图API

## 区块有效性（Chunk Validity）

TerraCraft中的地图采用动态区块加载技术实现无限地图。一个区块为1024x1024格。如果地图格子所在的区块存在，则这个地图格子有效。

在使用地图API时，请使用`IsValid`或`IsAreaValid`函数来保证所操作格子是有效的。对无效格子进行任何操作都是**没有意义**的行为。

## **写入（Set）**和**放置（Place）方块**的区别

**写入**表示不需要靠着其他方块而加入新的方块，而**放置**必须靠着附近可以被附着的方块才能放入。

## 地图通用模块（MapUtils）

### 通用常量

| 常量                            |  类型 |   值  | 描述             |
| ----------------------------- | :-: | :--: | -------------- |
| MapUtils._UNDERGROUND\_LINE_  | int |  416 | 地表层与地下层分界格纵坐标。 |
| MapUtils._NETHER\_LINE_       | int | 2450 | 地下层与地狱层分界格纵坐标。 |
| MapUtils._NETHER\_CAVE\_LINE_ | int | 2560 | 地狱层大型洞穴分界格纵坐标。 |

### 通用函数

#### 查询地图相关函数

这些函数在客户端和服务端均有效。

| 函数                                                                                                          |       返回值       | 描述                                                                                                                                                                                                        |
| ----------------------------------------------------------------------------------------------------------- | :-------------: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| MapUtils.IsValid(int xi, int yi)                                                                            |       bool      | 判断指定格子是否**有效**，即所在区块是否存在。                                                                                                                                                                                 |
| MapUtils.IsAreaValid(int xi, int yi, int width, int height)                                                 |       bool      | 判断矩形区域内所有格子是否都**有效**，即矩形区域覆盖的区块是否全部存在。                                                                                                                                                                    |
| MapUtils.IsSolid(int xi, int yi)                                                                            |       bool      | <p>判断指定格子是否为<strong>实心前景</strong>。<br><em>格子无效时总是返回false。</em></p>                                                                                                                                        |
| MapUtils.HasFront(int xi, int yi)                                                                           |       bool      | <p>判断指定格子是否有<strong>前景方块（前景图块或家具）</strong>。</p><p><em>格子无效时总是返回false。</em></p>                                                                                                                            |
| MapUtils.GetFrontID(int xi, int yi)                                                                         |       int       | <p>获取指定格子的<strong>前景方块ID</strong>。<br><em>若不存在或格子无效总是返回0。</em></p>                                                                                                                                        |
| MapUtils.GetFrontIDTag(int xi, int yi)                                                                      |     int, int    | <p>获取指定格子的<strong>前景方块ID和附加值</strong>。<br><em>若不存在或格子无效总是返回两个0。</em></p>                                                                                                                                  |
| MapUtils.HasWall(int xi, int yi)                                                                            |       bool      | <p>判断指定格子是否有<strong>背景墙</strong>。</p><p><em>格子无效时总是返回false。</em></p>                                                                                                                                      |
| MapUtils.GetWallID(int xi, int yi)                                                                          |       int       | <p>获取指定格子的<strong>背景墙方块ID</strong>。<br><em>若不存在或格子无效总是返回0。</em></p>                                                                                                                                       |
| MapUtils.HasLiquid(int xi, int yi)                                                                          |       bool      | <p>判断指定格子是否有<strong>流体</strong>。</p><p><em>格子无效时总是返回false。</em></p>                                                                                                                                       |
| MapUtils.GetLiquidID(int xi, int yi)                                                                        |       int       | <p>获取指定格子的<strong>流体ID</strong>。<br><em>若不存在或格子无效总是返回0。</em></p>                                                                                                                                          |
| MapUtils.GetLiquidIDAmount(int xi, int yi)                                                                  |     int, int    | <p>获取指定格子的<strong>流体ID和流体量</strong>。<br><em>若不存在或格子无效总是返回两个0。</em></p>                                                                                                                                    |
| MapUtils.CanSetWall(int xi, int yi, int blockID)                                                            |       bool      | <p>判断指定格子<strong>是否允许写入背景墙方块</strong>。</p><p><em>格子无效、背景墙被占用、方块ID不可作为背景墙时总是返回false。</em></p>                                                                                                              |
| MapUtils.CanPlaceWall(int xi, int yi, int blockID)                                                          |       bool      | <p>判断指定格子<strong>是否允许放置背景墙方块</strong>。</p><p><em>格子无效、背景墙被占用、方块ID不可作为背景墙、附近无可依靠方块时总是返回false。</em></p>                                                                                                     |
| MapUtils.CanSetFront(int xi, int yi, int blockID, bool destroyFraglie = true, bool checkEntities = false)   |       bool      | <p>判断指定格子<strong>是否允许写入前景方块（前景图块或家具）</strong>。<br><code>destroyFraglie</code>表示是否将要强行破坏易碎方块来写入当前方块。<code>checkEntities</code>表示是否检测有无实体堵着格子。</p><p><em>格子无效、前景被占用、方块ID不可作为前景时总是返回false。</em></p>          |
| MapUtils.CanPlaceFront(int xi, int yi, int blockID, bool destroyFraglie = true, bool checkEntities = false) |       bool      | <p>判断指定格子<strong>是否允许放置前景方块（前景图块或家具）</strong>。<br><code>destroyFraglie</code>表示是否将要强行破坏易碎方块来写入当前方块。<code>checkEntities</code>表示是否检测有无实体堵着格子。</p><p><em>格子无效、前景被占用、方块ID不可作为前景、附近无可依靠方块时总是返回false。</em></p> |
| MapUtils.CanSetFrontTag(int xi, int yi)                                                                     |       bool      | <p>判断指定格子是否允许写入前景方块的附加值。</p><p><em>格子无效、前景不存在、前景是方块实体时总是返回false。</em></p>                                                                                                                                 |
| MapUtils.GetBlockEntity(int blockEntityID, int xi, int yi)                                                  | BlockEntity/nil | <p>返回指定格子的方块实体。<code>blockEntityID</code>表示待返回的方块实体ID。</p><p><em>格子无效或方块实体不存在时总是返回nil。</em></p>                                                                                                           |

#### 修改地图相关函数

这些函数只在服务端执行，操作成功均返回true。

**在客户端中或者格子无效时不进行任何操作并总是返回false。游戏会通过内部算法自动将服务端的地图变化同步到客户端。**

| 函数                                                                                                                                           |  返回值 | 描述                                                                                                                                                                                                            |
| -------------------------------------------------------------------------------------------------------------------------------------------- | :--: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| MapUtils.RemoveFront(int xi, int yi, bool showEffect = false, bool playSound = false)                                                        | bool | <p><strong>移除</strong>指定格子的<strong>前景方块（前景图块或家具）</strong>。<br><em>需保证<code>HasFront(xi, yi)</code>为真。</em></p>                                                                                                |
| MapUtils.RemoveFrontAndDrop(int xi, int yi, bool isDropOriginal = false, int dropFortune = 0, bool showEffect = true, bool playSound = true) | bool | <p><strong>移除</strong>指定格子的<strong>前景方块（前景图块或家具）</strong>，并生成<strong>掉落物</strong>。<br><code>isDropOriginal</code>表示是否精准采集，<code>dropFortune</code>表示时运量。<br><em>需保证<code>HasFront(xi, yi)</code>为真。</em></p>  |
| MapUtils.RemoveWall(int xi, int yi, bool showEffect = false, bool playSound = false)                                                         | bool | <p><strong>移除</strong>指定格子的<strong>背景墙方块</strong>。<br><em>需保证<code>HasWall(xi, yi)</code>为真。</em></p>                                                                                                         |
| MapUtils.RemoveWallAndDrop(int xi, int yi, bool isDropOriginal = false, int dropFortune = 0, bool showEffect = true, bool playSound = true)  | bool | <p><strong>移除</strong>指定格子的<strong>背景墙方块</strong>，并生成<strong>掉落物</strong>。<br><code>isDropOriginal</code>表示是否精准采集，<code>dropFortune</code>表示时运量。<br><em>需保证<code>HasWall(xi, yi)</code>为真。</em></p>           |
| MapUtils.SetWall(int xi, int yi, int blockID, bool showEffect = false, bool playSound = false)                                               | bool | <p>在指定格子<strong>写入背景墙</strong>。<br><code>showEffect</code>表示写入瞬间是否产生粒子效果。<code>playSound</code>表示写入瞬间是否播放放置音效。</p><p><em>需保证<code>CanSetWall(xi, yi, blockID)</code>为真。</em></p>                              |
| MapUtils.PlaceWall(int xi, int yi, int blockID, bool showEffect = true, bool playSound = true)                                               | bool | <p>在指定格子<strong>放置背景墙</strong>。<br><code>showEffect</code>表示放置瞬间是否产生粒子效果。<code>playSound</code>表示放置瞬间是否播放放置音效。</p><p><em>需保证<code>CanPlaceWall(xi, yi, blockID)</code>为真。</em></p>                            |
| MapUtils.SetFront(int xi, int yi, int blockID, bool destroyFraglie = true, bool showEffect = false, bool playSound = false)                  | bool | <p>在指定格子<strong>写入前景方块（前景图块或家具）</strong>。<br><code>showEffect</code>表示写入瞬间是否产生粒子效果。<code>playSound</code>表示写入瞬间是否播放放置音效。</p><p><em>需保证<code>CanSetFront(xi, yi, blockID, destroyFraglie)</code>为真。</em></p>   |
| MapUtils.PlaceFront(int xi, int yi, int blockID, bool destroyFraglie = true, bool showEffect = true, bool playSound = true)                  | bool | <p>在指定格子<strong>放置前景方块（前景图块或家具）</strong>。<br><code>showEffect</code>表示放置瞬间是否产生粒子效果。<code>playSound</code>表示放置瞬间是否播放放置音效。</p><p><em>需保证<code>CanPlaceFront(xi, yi, blockID, destroyFraglie)</code>为真。</em></p> |
| MapUtils.SetFrontTag(int xi, int yi, int tag)                                                                                                | bool | <p>在指定格子写入<strong>前景附加值</strong>。</p><p><code>tag</code>表示前景的附加值。</p><p><em>需保证<code>CanSetFrontTag(xi, yi)</code>为真。</em></p>                                                                                |
| MapUtils.TriggerSignal(int xi, int yi, bool isOn)                                                                                            | bool | <p>在指定格子写入<strong>触发一个红石信号</strong>。</p><p><code>isOn</code>表示红石信号是激活还是取消激活。</p>                                                                                                                              |
| MapUtils.DelayTriggerSignal(int xi, int yi, bool isOn, int delayTime)                                                                        | bool | <p>在指定格子等待指定延迟时间后<strong>触发一个红石信号</strong>。</p><p><code>isOn</code>表示红石信号是激活还是取消激活，<code>delayTime</code>表示延迟时间。</p>                                                                                          |

####
