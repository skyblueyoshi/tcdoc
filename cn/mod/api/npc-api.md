# NPC API

NPC在TerraCraft中泛指除了玩家之外的所有生物，如动物、敌怪、村民、BOSS等。

## 钩子函数

请在**NPCAI**脚本中使用这些钩子函数。

### void Init\(\)

```lua
function Init()
    
end
```

NPC生成时调用一次该函数。

### void Update\(\)

```lua
function Update()
    
end
```

NPC每帧运行时调用，您可以在该函数内编写运动等逻辑。

### void PreUpdate\(\)

```lua
function PreUpdate()
    
end
```

NPC每帧运行`Update()`函数前调用。通常用于在使用AI重用后在原逻辑前插入新逻辑。

### void PostUpdate\(\)

```lua
function PostUpdate()
    
end
```

NPC每帧运行`Update()`函数后调用。通常用于在使用AI重用后追加逻辑。

### void UpdateSkeleton\(Skeleton skeleton\)

```lua
function UpdateSkeleton(Skeleton skeleton)
    
end
```

若NPC拥有骨骼模型，每帧执行完`PostUpdate`后调用，用于处理自定义骨骼模型逻辑。执行完该函数后，会对所有骨骼模型关节重新计算。

* `skeleton`表示当前NPC的骨骼模型。

### void PreUpdateSkeleton\(Skeleton skeleton\)

```lua
function PreUpdateSkeleton(Skeleton skeleton)
    
end
```

NPC每帧运行`UpdateSkeleton(Skeleton skeleton)`函数前调用。通常用于在使用AI重用后在原逻辑前插入新的骨骼模型逻辑。

* `skeleton`表示当前NPC的骨骼模型。

### void PostUpdateSkeleton\(Skeleton skeleton\)

```lua
function PostUpdateSkeleton(Skeleton skeleton)
    
end
```

NPC每帧运行`UpdateSkeleton(Skeleton skeleton)`函数，并将全部骨骼关节进行修正后调用。当前函数中所有骨骼关节为实际作用数据。

* `skeleton`表示当前NPC的骨骼模型。

### void OnDraw\(\)

```lua
function OnDraw()
    
end
```

NPC每帧绘制前调用，在该函数内编写自定义绘制属性。不使用该钩子函数时采取默认处理方式。

### void OnKilled\(\)

```lua
function OnKilled()
    
end
```

NPC死亡时调用一次该函数。

### void OnTileCollide\(double oldSpeedX, double oldSpeedY\)

```lua
function OnTileCollide()
    
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
| NpcUtils.SearchNearestNpc\(double centerX, double centerY, int radius, bool noCrossTiles = false\) | Npc/nil | 搜索在指定圆形区域内部距离圆心最近的NPC，返回该NPC。若结果不存在，返回nil。`noCrossTiles`表示是否排除中心到圆心的连线被图格遮挡的NPC。 |
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
| Npc.type | NpcType | **【只读】**当前NPC的类型。 |
| Npc.baseAttack | Attack | 当前NPC的基础攻击属性。 |
| Npc.defaultMaxSpeed | double | **【只读】**当前NPC的默认最大横向移动速度。 |
| Npc.maxSpeed | double | 当前NPC的最大横向移动速度。每帧重置为所在环境（流体黏性等）决定的最大移动速度。 |
| Npc.defaultGravity | double | **【只读】**当前NPC的默认重力加速度。 |
| Npc.gravity | double | 当前NPC的纵向加速度。每帧重置为作用了所在环境纵向受力以及重力后的纵向加速度。 |
| Npc.defaultMaxFallSpeed | double | **【只读】**当前NPC的默认最大下落速度。 |
| Npc.maxFallSpeed | double | 当前NPC的最大下落速度。每帧重置为作用了所在环境纵向阻力后的最大下落速度。 |
| Npc.defaultJumpForce | double | **【只读】**当前NPC的默认跳跃力度。 |
| Npc.jumpForce | double | 当前NPC的跳跃力度。每帧重置为作用了所在环境纵向阻力后的跳跃力度。 |
| Npc.noMove | bool | 决定当前NPC在行走模板中是否停止行走。 |
| Npc.inLiquid | bool | **【只读】**当前NPC是否处在流体环境中。 |
| Npc.oldInLiquid | bool | **【只读】**上一帧的NPC是否处在流体环境中。 |
| Npc.touchLiquidID | int | **【只读】**当前NPC所处流体环境的ID。如果不在任何流体内，则ID总是为0。 |
| Npc.isEnemy | bool | **【只读】**当前NPC是否会伤害玩家。 |
| Npc.state | bool | NPC当前在简单有限状态机中的状态。 |
| Npc.hurry | bool | 当前NPC是否为匆忙状态。匆忙状态下随机走模板不会停下来。 |
| Npc.maxHealth | int | 当前NPC的生命值上限。 |
| Npc.health | int | 当前NPC的生命值。 |
| Npc.angry | bool | 当前NPC是否为愤怒状态。易怒的NPC在被玩家击中后会将该玩家视为目标，并置愤怒状态为true。 |
| Npc.animation | int | NPC当前执行的动画状态。通常用于表示骨骼模型的动画状态。 |
| Npc.animationTickTime | int | NPC在当前动画索引所经过的时间。每帧自动自增1，当动画状态切换时自动重置为0。 |
| Npc.watchAngle | double | **【只读】**NPC的目视角度。若NPC目标存在，则总是目视目标。否则总是根据朝向水平目视。 |
| Npc.itemSlots | ArrayList&lt;ItemSlot&gt; | 当前NPC自己的物品格子列表。物品格子数目在NPC的AI数据表中指定。 |

### 类成员函数

| 函数 | 返回值 | 描述 |
| :--- | :---: | :--- |
| Npc:Kill\(\) | void | 不掉落物品直接清除当前NPC对象。 |
| Npc:Strike\(Attack attack, double hitAngle = 0, bool immune = true, bool hurtSound = true, int lootingLevel = 0\) | void | 制造一个对当前NPC的伤害。`attack`表示当前伤害属性，`hitAngle`表示产生伤害的角度，`immune`表示产生当前伤害后是否让NPC处于无敌帧状态，`hurtSound`表示是否播放NPC受伤音效，`lootingLevel`表示掠夺等级。 |
| Npc:StrikeFromPlayer\(Player player, Attack attack, double hitAngle = 0, bool immune = true, bool hurtSound = true, int lootingLevel = 0\) | void | 制造一个某玩家对当前NPC的伤害。其中`player`表示造成伤害的玩家。 |
| Npc:StrikeFromNpc\(Npc npc, Attack attack, double hitAngle = 0, bool immune = true, bool hurtSound = true, int lootingLevel = 0\) | void | 制造一个某NPC对当前NPC的伤害。其中`npc`表示造成伤害的NPC。 |
| Npc:GetPlayerTarget\(\) | Player/nil | 若当前NPC的玩家锁定目标存在且存活，返回该玩家对象，否则返回nil。 |
| Npc:AddBuff\(int buffID, int buffTime\) | void | 为当前NPC添加一个状态效果。若原状态效果存在，以最长时间为新状态效果的持续时间。 |
| Npc:RemoveBuff\(int buffID\) | void | 移除一个状态效果。 |
| Npc:RemoveAllBuff\(\) | void | 移除全部状态效果。 |
| Npc:HasBuff\(int buffID\) | bool | 返回NPC是否拥有指定状态效果。 |
| Npc:HasAnyBuff\(\) | bool | 返回NPC是否存在状态效果。 |
| Npc:TryMakeSound\(int tryTimes = 512\) | void | NPC尝试发出平时声音。平均经过tryTimes时间发出一次平时声音。 |
| Npc:MakeSound\(\) | void | NPC发出平时声音。 |
| Npc:UseTool\(ItemSlot itemSlot, int skJointID\) | void | NPC使用指定物品格子内的工具。itemSlot为指定物品格子，skJointID为当前NPC使用工具的骨骼模型关节ID。 |

### 运动模板函数

调用这些函数执行内置的运动逻辑。

| 函数 | 返回值 | 描述 |
| :--- | :---: | :--- |
| Npc:Stand\(bool faceToTarget = true\) | void | 执行**静立**运动模板。 |
| Npc:RandomWalk\(int idleTime = 128, int idleTimeOffset = 64, int walkTime = 96, int walkTimeOffset = 32\) | void | 执行**随机行走**运动模板。 |
| Npc:KeepWalking\(bool followTarget = true\) | void | 执行**持续行走**运动模板。 |
| Npc:Walk\(bool followTarget = true\) | void | 执行_**行走运动**_模板。 |
| Npc:Swim\(bool followTarget = true\) | void | 执行**游泳**模板。 |
| Npc:Fly\(bool followTarget = true, double force = 0.1, bool gradientSpeed = false\) | void | 执行**飞行**模板。 |
| Npc:RandomTeleport\(int distance, bool noToAir = true, bool noToLiquid = true\) | bool | 执行**随机传送**模板。 |

<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x8FD0;&#x52A8;&#x6A21;&#x677F;</th>
      <th style="text-align:left">&#x63CF;&#x8FF0;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>&#x9759;&#x7ACB;</b>
      </td>
      <td style="text-align:left">&#x7AD9;&#x7ACB;&#x9759;&#x6B62;&#x4E0D;&#x52A8;&#x3002;&#x76EE;&#x6807;&#x5B58;&#x5728;&#x65F6;&#xFF0C;<code>faceToTarget</code>&#x8868;&#x793A;&#x59CB;&#x7EC8;&#x9762;&#x671D;&#x73A9;&#x5BB6;&#x3002;</td>
    </tr>
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
    <tr>
      <td style="text-align:left"><b>&#x98DE;&#x884C;</b>
      </td>
      <td style="text-align:left">
        <p>&#x5728;&#x7A7A;&#x6C14;&#x4E2D;&#x98DE;&#x884C;&#x3002;</p>
        <p>&#x76EE;&#x6807;&#x5B58;&#x5728;&#x65F6;&#xFF0C;<code>followTarget</code>&#x8868;&#x793A;&#x5C3D;&#x53EF;&#x80FD;&#x9760;&#x8FD1;&#x76EE;&#x6807;&#xFF0C;<code>force</code>&#x8868;&#x793A;&#x98DE;&#x5411;&#x76EE;&#x6807;&#x7684;&#x529B;&#xFF0C;<code>gradientSpeed</code>&#x8868;&#x793A;&#x662F;&#x5426;&#x4F7F;&#x7528;&#x6E10;&#x53D8;&#x901F;&#x5EA6;&#xFF0C;&#x5426;&#x5219;&#x8FD0;&#x52A8;&#x901F;&#x5EA6;&#x7684;&#x5411;&#x91CF;&#x5927;&#x5C0F;&#x603B;&#x662F;&#x6052;&#x5B9A;&#x7684;&#x3002;
          <br
          />&#x76EE;&#x6807;&#x4E0D;&#x5B58;&#x5728;&#x65F6;&#xFF0C;&#x5728;&#x7A7A;&#x6C14;&#x4E2D;&#x968F;&#x673A;&#x8FD0;&#x52A8;&#x3002;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>&#x968F;&#x673A;&#x4F20;&#x9001;</b>
      </td>
      <td style="text-align:left">
        <p>&#x4F20;&#x9001;NPC&#x81EA;&#x5DF1;&#x5230;&#x4EE5;&#x81EA;&#x5DF1;&#x4E3A;&#x5706;&#x5FC3;&#x7684;&#x5706;&#x5F62;&#x533A;&#x57DF;&#x968F;&#x673A;&#x4F4D;&#x7F6E;&#x3002;</p>
        <p><code>distance</code>&#x8868;&#x793A;&#x5706;&#x5F62;&#x533A;&#x57DF;&#x7684;&#x534A;&#x5F84;&#xFF0C;<code>noToAir</code>&#x8868;&#x793A;&#x662F;&#x5426;&#x4E0D;&#x4F20;&#x9001;&#x5230;&#x534A;&#x7A7A;&#x4E2D;&#xFF08;&#x5373;&#x4F20;&#x9001;&#x5230;&#x5730;&#x9762;&#x4E0A;&#xFF09;&#xFF0C;<code>noToLiquid</code>&#x8868;&#x793A;&#x662F;&#x5426;&#x4E0D;&#x4F20;&#x9001;&#x5230;&#x6D41;&#x4F53;&#x5185;&#x3002;</p>
        <p>&#x82E5;&#x4F20;&#x9001;&#x6210;&#x529F;&#xFF0C;&#x8FD4;&#x56DE;true&#xFF0C;&#x5426;&#x5219;&#x8FD4;&#x56DE;false&#x3002;</p>
      </td>
    </tr>
  </tbody>
</table>



