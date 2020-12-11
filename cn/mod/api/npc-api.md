# NPC API

NPC在TerraCraft中泛指除了玩家之外的所有生物，如动物、敌怪、村民、BOSS等。

## 钩子函数

请在**NPCAI**脚本中使用这些钩子函数。

#### void Init\(\)

```lua
function Init()
    --init current npc here
end
```

NPC生成时调用一次该函数。

#### void Update\(\)

```lua
function Update()
    --update every game loop
end
```

NPC抛射物每帧运行时调用，您可以在该函数内编写运动等逻辑。

#### void PreUpdate\(\)

```lua
function ReadyUpdate()
    --update every game loop
end
```

NPC抛射物每帧运行`Update()`函数前调用。通常用于在使用AI重用后在原逻辑前插入新逻辑。

#### void PostUpdate\(\)

```lua
function PostUpdate()
    --update every game loop
end
```

NPC每帧运行`Update()`函数后调用。通常用于在使用AI重用后追加逻辑。

#### void OnDraw\(\)

```lua
function OnDraw()
    --change the sprite parameters before drawing every game loop
end
```

NPC每帧绘制前调用，在该函数内编写自定义绘制属性。不使用该钩子函数时采取默认处理方式。

#### void OnKilled\(\)

```lua
function OnKilled()
    --do something when npc is killed
end
```

NPC死亡时调用一次该函数。

#### void OnTileCollide\(double oldSpeedX, double oldSpeedY\)

```lua
function OnTileCollide()
    --do something when npc hit tiles
end
```

NPC与图块碰撞时调用该函数。

* `oldSpeedX`和`oldSpeedY`表示击中实心图块前一帧的横向和纵向速度。

## NPC通用模块（NpcUtils）

| 函数 | 返回值 | 描述 |
| :--- | :---: | :--- |
| NpcUtils.Create\(int id, double x, double y, double speedX = 0.0, double speedY = 0.0\) | Npc | 在指定位置创建一个NPC，返回创建好的NPC实体。 `id`：NPC的ID。`x`和`y`：创建NPC的坐标。`speedX`和`speedY`：初始运动速度。 |
| NpcUtils.SearchByRect\(double x, double y, int width, int height\) | ArrayList&lt;Npc&gt; | 返回包含于指定矩形区域内部的所有NPC列表。 |
| NpcUtils.SearchByCircle\(double centerX, double centerY, int radius\) | ArrayList&lt;Npc&gt; | 返回包含于指定圆形区域内部的所有NPC列表。 |
| NpcUtils.SearchNearestNpc\(double centerX, double centerY, int radius, bool noCrossTiles = false\) | Npc/nil | 搜索在指定圆形区域内部距离圆心最近的NPC，返回该NPC。若结果不存在，返回nil。noCrossTiles表示是否排除中心到圆心的连线被图格遮挡的NPC。 |
| NpcUtils.SearchNearestEnemy\(double centerX, double centerY, int radius, bool noCrossTiles = false\) | Npc/nil | 搜索在指定圆形区域内部距离圆心最近的敌对NPC，返回该NPC。若结果不存在，返回nil。noCrossTiles表示是否排除中心到圆心的连线被图格遮挡的NPC。 |

## NPC类（Npc Class）

**NPC**类表示具有生物基本信息的非玩家实体类。

在编写NPC AI脚本时，**self表示当前正在操作的NPC类**。

### 父类

该类的父类为[Entity类](entity.md#shi-ti-lei-entity-class)。可直接使用该父类的类成员属性与类成员函数。

### 类成员属性

| 属性 | 类型 | 描述 |
| :--- | :---: | :--- |
| Npc.id | int | **【只读】**当前NPC的动态ID。 |
| Npc.baseAttack | Attack | 当前NPC的基础攻击属性。 |
| Npc.defaultMaxSpeed | double | **【只读】**当前NPC的默认最大横向移动速度。 |
| Npc.maxSpeed | double | 当前NPC的最大横向移动速度。每帧重置为所在环境（流体黏性等）决定的最大移动速度。 |
| Npc.defaultGravity | double | **【只读】**当前NPC的默认重力加速度。 |
| Npc.gravity | double | 当前NPC的纵向加速度。每帧重置为作用了所在环境纵向受力以及重力后的纵向加速度。 |
| Npc.defaultMaxFallSpeed | double | **【只读】**当前NPC的默认最大下落速度。 |
| Npc.maxFallSpeed | double | 当前NPC的最大下落速度。每帧重置为作用了所在环境纵向阻力后的最大下落速度。 |
| Npc.hurry | bool | 当前NPC是否为匆忙状态。匆忙状态下随机走运动模板不会停下来。 |

### 类成员函数

| 函数 | 返回值 | 描述 |
| :--- | :---: | :--- |
| Npc:AddBuff\(int buffID, int buffTime\) | void | 为当前NPC添加一个状态效果。若原状态效果存在，以最长时间为新状态效果的持续时间。 |
| Npc:RemoveBuff\(int buffID\) | void | 移除一个状态效果。 |
| Npc:RemoveAllBuff\(\) | void | 移除全部状态效果。 |
| Npc:HasBuff\(int buffID\) | bool | 返回NPC是否拥有指定状态效果。 |
| Npc:HasAnyBuff\(\) | bool | 返回NPC是否存在状态效果。 |

#### 运动模板函数

调用这些函数可以执行内置的运动逻辑。

| 函数 | 返回值 | 描述 |
| :--- | :---: | :--- |
| Npc:RandomWalk\(int idleTime = 128, int idleTimeOffset = 64, int walkTime = 96, int walkTimeOffset = 32\) | void | 执行_**随机行走**_运动模板。 |
| Npc:KeepWalking\(bool followTarget = true\) | void | 执行_**持续行走**_运动模板。 |
| Npc:Walk\(bool followTarget = true\) | void | 执行_**行走**_运动模板。 |
| Npc:Swim\(bool followTarget = true\) | void | 执行_**游泳**_模板。 |

<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x8FD0;&#x52A8;&#x6A21;&#x677F;</th>
      <th style="text-align:left">&#x63CF;&#x8FF0;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>&#x968F;&#x673A;&#x884C;&#x8D70;</b>
      </td>
      <td style="text-align:left">
        <p>&#x968F;&#x673A;&#x5730;&#x671D;&#x4E00;&#x4E2A;&#x65B9;&#x5411;&#x884C;&#x8D70;&#x6216;&#x505C;&#x4E0B;&#x6216;&#x8F6C;&#x5F2F;&#x3002;</p>
        <p>&#x505C;&#x4E0B;&#x65F6;&#x95F2;&#x7F6E;<code>idleTime &#xB1; idleTimeOffset</code>&#x8303;&#x56F4;&#x5185;&#x968F;&#x673A;&#x65F6;&#x95F4;&#x3002;</p>
        <p>&#x671D;&#x4E00;&#x4E2A;&#x65B9;&#x5411;&#x884C;&#x8D70;&#x65F6;&#x6301;&#x7EED;<code>walkTime &#xB1; walkTimeOffset</code>&#x8303;&#x56F4;&#x5185;&#x968F;&#x673A;&#x65F6;&#x95F4;&#x3002;</p>
        <p>&#x4F7F;&#x7528;&#x5185;&#x7F6E;&#x5BFB;&#x8DEF;&#x903B;&#x8F91;&#xFF0C;&#x9047;&#x5230;&#x5899;&#x58C1;&#x4F1A;&#x5C1D;&#x8BD5;&#x8DF3;&#x8DC3;3&#x6B21;&#x3002;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>&#x6301;&#x7EED;&#x884C;&#x8D70;</b>
      </td>
      <td style="text-align:left">
        <p>&#x6301;&#x7EED;&#x884C;&#x8D70;&#x800C;&#x4E0D;&#x505C;&#x4E0B;&#x3002;
          <br
          /><code>followTarget</code>&#x8868;&#x793A;&#x5728;&#x76EE;&#x6807;&#x5B58;&#x5728;&#x7684;&#x60C5;&#x51B5;&#x4E0B;&#xFF0C;&#x5C3D;&#x53EF;&#x80FD;&#x9760;&#x8FD1;&#x76EE;&#x6807;&#x3002;</p>
        <p>&#x4F7F;&#x7528;&#x5185;&#x7F6E;&#x5BFB;&#x8DEF;&#x903B;&#x8F91;&#xFF0C;&#x9047;&#x5230;&#x5899;&#x58C1;&#x4F1A;&#x5C1D;&#x8BD5;&#x8DF3;&#x8DC3;3&#x6B21;&#x3002;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>&#x884C;&#x8D70;</b>
      </td>
      <td style="text-align:left">
        <p>&#x76EE;&#x6807;&#x5B58;&#x5728;&#x65F6;&#xFF0C;&#x91C7;&#x7528;<em><b>&#x6301;&#x7EED;&#x884C;&#x8D70;</b></em>&#x6A21;&#x677F;&#xFF0C;<code>followTarget</code>&#x8868;&#x793A;&#x5C3D;&#x53EF;&#x80FD;&#x9760;&#x8FD1;&#x76EE;&#x6807;&#x3002;</p>
        <p>&#x76EE;&#x6807;&#x4E0D;&#x5B58;&#x5728;&#x65F6;&#xFF0C;&#x91C7;&#x7528;<em><b>&#x968F;&#x673A;&#x884C;&#x8D70;</b></em>&#x6A21;&#x677F;&#x3002;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>&#x6E38;&#x6CF3;</b>
      </td>
      <td style="text-align:left">
        <p>&#x5728;&#x6D41;&#x4F53;&#x4E2D;&#x6E38;&#x6CF3;&#xFF0C;&#x5728;&#x7A7A;&#x6C14;&#x4E2D;&#x8E66;&#x8DF6;&#x3002;</p>
        <p>&#x76EE;&#x6807;&#x5B58;&#x5728;&#x65F6;&#xFF0C;<code>followTarget</code>&#x8868;&#x793A;&#x5C3D;&#x53EF;&#x80FD;&#x9760;&#x8FD1;&#x76EE;&#x6807;&#x3002;&#x5426;&#x5219;&#x5728;&#x6D41;&#x4F53;&#x4E2D;&#x968F;&#x673A;&#x8FD0;&#x52A8;&#x3002;</p>
      </td>
    </tr>
  </tbody>
</table>



