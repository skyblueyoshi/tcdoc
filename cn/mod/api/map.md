# 地图API

## 区块有效性（Chunk Validity）

TerraCraft中的地图采用动态区块加载技术实现无限地图。一个区块为1024x1024格。如果地图格子所在的区块存在，则这个地图格子有效。

在使用地图API时，请使用`IsValid`或`IsAreaValid`函数来保证所操作格子是有效的。对无效格子进行任何操作都是**没有意义**的行为。

## **写入（Set）**和**放置（Place）方块**的区别

**写入**表示不需要靠着其他方块而加入新的方块，而**放置**必须靠着附近可以被附着的方块才能放入。

## 地图通用模块（MapUtils）

### 通用常量

| 常量 | 类型 | 值 | 描述 |
| :--- | :---: | :---: | :--- |
| MapUtils._UNDERGROUND\_LINE_ | int | 416 | 地表层与地下层分界格纵坐标。 |
| MapUtils._NETHER\_LINE_ | int | 2450 | 地下层与地狱层分界格纵坐标。 |
| MapUtils._NETHER\_CAVE\_LINE_ | int | 2560 | 地狱层大型洞穴分界格纵坐标。 |

### 通用函数

#### 查询地图相关函数

这些函数在客户端和服务端均有效。

<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x51FD;&#x6570;</th>
      <th style="text-align:center">&#x8FD4;&#x56DE;&#x503C;</th>
      <th style="text-align:left">&#x63CF;&#x8FF0;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">MapUtils.IsValid(int xi, int yi)</td>
      <td style="text-align:center">bool</td>
      <td style="text-align:left">&#x5224;&#x65AD;&#x6307;&#x5B9A;&#x683C;&#x5B50;&#x662F;&#x5426;<b>&#x6709;&#x6548;</b>&#xFF0C;&#x5373;&#x6240;&#x5728;&#x533A;&#x5757;&#x662F;&#x5426;&#x5B58;&#x5728;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">MapUtils.IsAreaValid(int xi, int yi, int width, int height)</td>
      <td style="text-align:center">bool</td>
      <td style="text-align:left">&#x5224;&#x65AD;&#x77E9;&#x5F62;&#x533A;&#x57DF;&#x5185;&#x6240;&#x6709;&#x683C;&#x5B50;&#x662F;&#x5426;&#x90FD;<b>&#x6709;&#x6548;</b>&#xFF0C;&#x5373;&#x77E9;&#x5F62;&#x533A;&#x57DF;&#x8986;&#x76D6;&#x7684;&#x533A;&#x5757;&#x662F;&#x5426;&#x5168;&#x90E8;&#x5B58;&#x5728;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">MapUtils.IsSolid(int xi, int yi)</td>
      <td style="text-align:center">bool</td>
      <td style="text-align:left">&#x5224;&#x65AD;&#x6307;&#x5B9A;&#x683C;&#x5B50;&#x662F;&#x5426;&#x4E3A;<b>&#x5B9E;&#x5FC3;&#x524D;&#x666F;</b>&#x3002;
        <br
        /><em>&#x683C;&#x5B50;&#x65E0;&#x6548;&#x65F6;&#x603B;&#x662F;&#x8FD4;&#x56DE;false&#x3002;</em>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">MapUtils.HasFront(int xi, int yi)</td>
      <td style="text-align:center">bool</td>
      <td style="text-align:left">
        <p>&#x5224;&#x65AD;&#x6307;&#x5B9A;&#x683C;&#x5B50;&#x662F;&#x5426;&#x6709;<b>&#x524D;&#x666F;&#x65B9;&#x5757;&#xFF08;&#x524D;&#x666F;&#x56FE;&#x5757;&#x6216;&#x5BB6;&#x5177;&#xFF09;</b>&#x3002;</p>
        <p><em>&#x683C;&#x5B50;&#x65E0;&#x6548;&#x65F6;&#x603B;&#x662F;&#x8FD4;&#x56DE;false&#x3002;</em>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">MapUtils.GetFrontID(int xi, int yi)</td>
      <td style="text-align:center">int</td>
      <td style="text-align:left">&#x83B7;&#x53D6;&#x6307;&#x5B9A;&#x683C;&#x5B50;&#x7684;<b>&#x524D;&#x666F;&#x65B9;&#x5757;ID</b>&#x3002;
        <br
        /><em>&#x82E5;&#x4E0D;&#x5B58;&#x5728;&#x6216;&#x683C;&#x5B50;&#x65E0;&#x6548;&#x603B;&#x662F;&#x8FD4;&#x56DE;0&#x3002;</em>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">MapUtils.GetFrontIDTag(int xi, int yi)</td>
      <td style="text-align:center">int, int</td>
      <td style="text-align:left">&#x83B7;&#x53D6;&#x6307;&#x5B9A;&#x683C;&#x5B50;&#x7684;<b>&#x524D;&#x666F;&#x65B9;&#x5757;ID&#x548C;&#x9644;&#x52A0;&#x503C;</b>&#x3002;
        <br
        /><em>&#x82E5;&#x4E0D;&#x5B58;&#x5728;&#x6216;&#x683C;&#x5B50;&#x65E0;&#x6548;&#x603B;&#x662F;&#x8FD4;&#x56DE;&#x4E24;&#x4E2A;0&#x3002;</em>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">MapUtils.HasWall(int xi, int yi)</td>
      <td style="text-align:center">bool</td>
      <td style="text-align:left">
        <p>&#x5224;&#x65AD;&#x6307;&#x5B9A;&#x683C;&#x5B50;&#x662F;&#x5426;&#x6709;<b>&#x80CC;&#x666F;&#x5899;</b>&#x3002;</p>
        <p><em>&#x683C;&#x5B50;&#x65E0;&#x6548;&#x65F6;&#x603B;&#x662F;&#x8FD4;&#x56DE;false&#x3002;</em>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">MapUtils.GetWallID(int xi, int yi)</td>
      <td style="text-align:center">int</td>
      <td style="text-align:left">&#x83B7;&#x53D6;&#x6307;&#x5B9A;&#x683C;&#x5B50;&#x7684;<b>&#x80CC;&#x666F;&#x5899;&#x65B9;&#x5757;ID</b>&#x3002;
        <br
        /><em>&#x82E5;&#x4E0D;&#x5B58;&#x5728;&#x6216;&#x683C;&#x5B50;&#x65E0;&#x6548;&#x603B;&#x662F;&#x8FD4;&#x56DE;0&#x3002;</em>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">MapUtils.HasLiquid(int xi, int yi)</td>
      <td style="text-align:center">bool</td>
      <td style="text-align:left">
        <p>&#x5224;&#x65AD;&#x6307;&#x5B9A;&#x683C;&#x5B50;&#x662F;&#x5426;&#x6709;<b>&#x6D41;&#x4F53;</b>&#x3002;</p>
        <p><em>&#x683C;&#x5B50;&#x65E0;&#x6548;&#x65F6;&#x603B;&#x662F;&#x8FD4;&#x56DE;false&#x3002;</em>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">MapUtils.GetLiquidID(int xi, int yi)</td>
      <td style="text-align:center">int</td>
      <td style="text-align:left">&#x83B7;&#x53D6;&#x6307;&#x5B9A;&#x683C;&#x5B50;&#x7684;<b>&#x6D41;&#x4F53;ID</b>&#x3002;
        <br
        /><em>&#x82E5;&#x4E0D;&#x5B58;&#x5728;&#x6216;&#x683C;&#x5B50;&#x65E0;&#x6548;&#x603B;&#x662F;&#x8FD4;&#x56DE;0&#x3002;</em>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">MapUtils.GetLiquidIDAmount(int xi, int yi)</td>
      <td style="text-align:center">int, int</td>
      <td style="text-align:left">&#x83B7;&#x53D6;&#x6307;&#x5B9A;&#x683C;&#x5B50;&#x7684;<b>&#x6D41;&#x4F53;ID&#x548C;&#x6D41;&#x4F53;&#x91CF;</b>&#x3002;
        <br
        /><em>&#x82E5;&#x4E0D;&#x5B58;&#x5728;&#x6216;&#x683C;&#x5B50;&#x65E0;&#x6548;&#x603B;&#x662F;&#x8FD4;&#x56DE;&#x4E24;&#x4E2A;0&#x3002;</em>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">MapUtils.CanSetWall(int xi, int yi, int blockID)</td>
      <td style="text-align:center">bool</td>
      <td style="text-align:left">
        <p>&#x5224;&#x65AD;&#x6307;&#x5B9A;&#x683C;&#x5B50;<b>&#x662F;&#x5426;&#x5141;&#x8BB8;&#x5199;&#x5165;&#x80CC;&#x666F;&#x5899;&#x65B9;&#x5757;</b>&#x3002;</p>
        <p><em>&#x683C;&#x5B50;&#x65E0;&#x6548;&#x3001;&#x80CC;&#x666F;&#x5899;&#x88AB;&#x5360;&#x7528;&#x3001;&#x65B9;&#x5757;ID&#x4E0D;&#x53EF;&#x4F5C;&#x4E3A;&#x80CC;&#x666F;&#x5899;&#x65F6;&#x603B;&#x662F;&#x8FD4;&#x56DE;false&#x3002;</em>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">MapUtils.CanPlaceWall(int xi, int yi, int blockID)</td>
      <td style="text-align:center">bool</td>
      <td style="text-align:left">
        <p>&#x5224;&#x65AD;&#x6307;&#x5B9A;&#x683C;&#x5B50;<b>&#x662F;&#x5426;&#x5141;&#x8BB8;&#x653E;&#x7F6E;&#x80CC;&#x666F;&#x5899;&#x65B9;&#x5757;</b>&#x3002;</p>
        <p><em>&#x683C;&#x5B50;&#x65E0;&#x6548;&#x3001;&#x80CC;&#x666F;&#x5899;&#x88AB;&#x5360;&#x7528;&#x3001;&#x65B9;&#x5757;ID&#x4E0D;&#x53EF;&#x4F5C;&#x4E3A;&#x80CC;&#x666F;&#x5899;&#x3001;&#x9644;&#x8FD1;&#x65E0;&#x53EF;&#x4F9D;&#x9760;&#x65B9;&#x5757;&#x65F6;&#x603B;&#x662F;&#x8FD4;&#x56DE;false&#x3002;</em>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">MapUtils.CanSetFront(int xi, int yi, int blockID, bool destroyFraglie
        = true, bool checkEntities = false)</td>
      <td style="text-align:center">bool</td>
      <td style="text-align:left">
        <p>&#x5224;&#x65AD;&#x6307;&#x5B9A;&#x683C;&#x5B50;<b>&#x662F;&#x5426;&#x5141;&#x8BB8;&#x5199;&#x5165;&#x524D;&#x666F;&#x65B9;&#x5757;&#xFF08;&#x524D;&#x666F;&#x56FE;&#x5757;&#x6216;&#x5BB6;&#x5177;&#xFF09;</b>&#x3002;
          <br
          /><code>destroyFraglie</code>&#x8868;&#x793A;&#x662F;&#x5426;&#x5C06;&#x8981;&#x5F3A;&#x884C;&#x7834;&#x574F;&#x6613;&#x788E;&#x65B9;&#x5757;&#x6765;&#x5199;&#x5165;&#x5F53;&#x524D;&#x65B9;&#x5757;&#x3002;<code>checkEntities</code>&#x8868;&#x793A;&#x662F;&#x5426;&#x68C0;&#x6D4B;&#x6709;&#x65E0;&#x5B9E;&#x4F53;&#x5835;&#x7740;&#x683C;&#x5B50;&#x3002;</p>
        <p><em>&#x683C;&#x5B50;&#x65E0;&#x6548;&#x3001;&#x524D;&#x666F;&#x88AB;&#x5360;&#x7528;&#x3001;&#x65B9;&#x5757;ID&#x4E0D;&#x53EF;&#x4F5C;&#x4E3A;&#x524D;&#x666F;&#x65F6;&#x603B;&#x662F;&#x8FD4;&#x56DE;false&#x3002;</em>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">MapUtils.CanPlaceFront(int xi, int yi, int blockID, bool destroyFraglie
        = true, bool checkEntities = false)</td>
      <td style="text-align:center">bool</td>
      <td style="text-align:left">
        <p>&#x5224;&#x65AD;&#x6307;&#x5B9A;&#x683C;&#x5B50;<b>&#x662F;&#x5426;&#x5141;&#x8BB8;&#x653E;&#x7F6E;&#x524D;&#x666F;&#x65B9;&#x5757;&#xFF08;&#x524D;&#x666F;&#x56FE;&#x5757;&#x6216;&#x5BB6;&#x5177;&#xFF09;</b>&#x3002;
          <br
          /><code>destroyFraglie</code>&#x8868;&#x793A;&#x662F;&#x5426;&#x5C06;&#x8981;&#x5F3A;&#x884C;&#x7834;&#x574F;&#x6613;&#x788E;&#x65B9;&#x5757;&#x6765;&#x5199;&#x5165;&#x5F53;&#x524D;&#x65B9;&#x5757;&#x3002;<code>checkEntities</code>&#x8868;&#x793A;&#x662F;&#x5426;&#x68C0;&#x6D4B;&#x6709;&#x65E0;&#x5B9E;&#x4F53;&#x5835;&#x7740;&#x683C;&#x5B50;&#x3002;</p>
        <p><em>&#x683C;&#x5B50;&#x65E0;&#x6548;&#x3001;&#x524D;&#x666F;&#x88AB;&#x5360;&#x7528;&#x3001;&#x65B9;&#x5757;ID&#x4E0D;&#x53EF;&#x4F5C;&#x4E3A;&#x524D;&#x666F;&#x3001;&#x9644;&#x8FD1;&#x65E0;&#x53EF;&#x4F9D;&#x9760;&#x65B9;&#x5757;&#x65F6;&#x603B;&#x662F;&#x8FD4;&#x56DE;false&#x3002;</em>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">MapUtils.CanSetFrontTag(int xi, int yi)</td>
      <td style="text-align:center">bool</td>
      <td style="text-align:left">
        <p>&#x5224;&#x65AD;&#x6307;&#x5B9A;&#x683C;&#x5B50;&#x662F;&#x5426;&#x5141;&#x8BB8;&#x5199;&#x5165;&#x524D;&#x666F;&#x65B9;&#x5757;&#x7684;&#x9644;&#x52A0;&#x503C;&#x3002;</p>
        <p><em>&#x683C;&#x5B50;&#x65E0;&#x6548;&#x3001;&#x524D;&#x666F;&#x4E0D;&#x5B58;&#x5728;&#x3001;&#x524D;&#x666F;&#x662F;&#x65B9;&#x5757;&#x5B9E;&#x4F53;&#x65F6;&#x603B;&#x662F;&#x8FD4;&#x56DE;false&#x3002;</em>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">MapUtils.GetBlockEntity(int blockEntityID, int xi, int yi)</td>
      <td style="text-align:center">BlockEntity/nil</td>
      <td style="text-align:left">
        <p>&#x8FD4;&#x56DE;&#x6307;&#x5B9A;&#x683C;&#x5B50;&#x7684;&#x65B9;&#x5757;&#x5B9E;&#x4F53;&#x3002;<code>blockEntityID</code>&#x8868;&#x793A;&#x5F85;&#x8FD4;&#x56DE;&#x7684;&#x65B9;&#x5757;&#x5B9E;&#x4F53;ID&#x3002;</p>
        <p><em>&#x683C;&#x5B50;&#x65E0;&#x6548;&#x6216;&#x65B9;&#x5757;&#x5B9E;&#x4F53;&#x4E0D;&#x5B58;&#x5728;&#x65F6;&#x603B;&#x662F;&#x8FD4;&#x56DE;nil&#x3002;</em>
        </p>
      </td>
    </tr>
  </tbody>
</table>

#### 修改地图相关函数

这些函数只在服务端执行，操作成功均返回true。

**在客户端中或者格子无效时不进行任何操作并总是返回false。游戏会通过内部算法自动将服务端的地图变化同步到客户端。**

<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x51FD;&#x6570;</th>
      <th style="text-align:center">&#x8FD4;&#x56DE;&#x503C;</th>
      <th style="text-align:left">&#x63CF;&#x8FF0;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">MapUtils.RemoveFront(int xi, int yi, bool showEffect = false, bool playSound
        = false)</td>
      <td style="text-align:center">bool</td>
      <td style="text-align:left"><b>&#x79FB;&#x9664;</b>&#x6307;&#x5B9A;&#x683C;&#x5B50;&#x7684;<b>&#x524D;&#x666F;&#x65B9;&#x5757;&#xFF08;&#x524D;&#x666F;&#x56FE;&#x5757;&#x6216;&#x5BB6;&#x5177;&#xFF09;</b>&#x3002;
        <br
        /><em>&#x9700;&#x4FDD;&#x8BC1;<code>HasFront(xi, yi)</code>&#x4E3A;&#x771F;&#x3002;</em>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">MapUtils.RemoveFrontAndDrop(int xi, int yi, bool isDropOriginal = false,
        int dropFortune = 0, bool showEffect = true, bool playSound = true)</td>
      <td
      style="text-align:center">bool</td>
        <td style="text-align:left"><b>&#x79FB;&#x9664;</b>&#x6307;&#x5B9A;&#x683C;&#x5B50;&#x7684;<b>&#x524D;&#x666F;&#x65B9;&#x5757;&#xFF08;&#x524D;&#x666F;&#x56FE;&#x5757;&#x6216;&#x5BB6;&#x5177;&#xFF09;</b>&#xFF0C;&#x5E76;&#x751F;&#x6210;<b>&#x6389;&#x843D;&#x7269;</b>&#x3002;
          <br
          /><code>isDropOriginal</code>&#x8868;&#x793A;&#x662F;&#x5426;&#x7CBE;&#x51C6;&#x91C7;&#x96C6;&#xFF0C;<code>dropFortune</code>&#x8868;&#x793A;&#x65F6;&#x8FD0;&#x91CF;&#x3002;
          <br
          /><em>&#x9700;&#x4FDD;&#x8BC1;<code>HasFront(xi, yi)</code>&#x4E3A;&#x771F;&#x3002;</em>
        </td>
    </tr>
    <tr>
      <td style="text-align:left">MapUtils.RemoveWall(int xi, int yi, bool showEffect = false, bool playSound
        = false)</td>
      <td style="text-align:center">bool</td>
      <td style="text-align:left"><b>&#x79FB;&#x9664;</b>&#x6307;&#x5B9A;&#x683C;&#x5B50;&#x7684;<b>&#x80CC;&#x666F;&#x5899;&#x65B9;&#x5757;</b>&#x3002;
        <br
        /><em>&#x9700;&#x4FDD;&#x8BC1;<code>HasWall(xi, yi)</code>&#x4E3A;&#x771F;&#x3002;</em>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">MapUtils.RemoveWallAndDrop(int xi, int yi, bool isDropOriginal = false,
        int dropFortune = 0, bool showEffect = true, bool playSound = true)</td>
      <td
      style="text-align:center">bool</td>
        <td style="text-align:left"><b>&#x79FB;&#x9664;</b>&#x6307;&#x5B9A;&#x683C;&#x5B50;&#x7684;<b>&#x80CC;&#x666F;&#x5899;&#x65B9;&#x5757;</b>&#xFF0C;&#x5E76;&#x751F;&#x6210;<b>&#x6389;&#x843D;&#x7269;</b>&#x3002;
          <br
          /><code>isDropOriginal</code>&#x8868;&#x793A;&#x662F;&#x5426;&#x7CBE;&#x51C6;&#x91C7;&#x96C6;&#xFF0C;<code>dropFortune</code>&#x8868;&#x793A;&#x65F6;&#x8FD0;&#x91CF;&#x3002;
          <br
          /><em>&#x9700;&#x4FDD;&#x8BC1;<code>HasWall(xi, yi)</code>&#x4E3A;&#x771F;&#x3002;</em>
        </td>
    </tr>
    <tr>
      <td style="text-align:left">MapUtils.SetWall(int xi, int yi, int blockID, bool showEffect = false,
        bool playSound = false)</td>
      <td style="text-align:center">bool</td>
      <td style="text-align:left">
        <p>&#x5728;&#x6307;&#x5B9A;&#x683C;&#x5B50;<b>&#x5199;&#x5165;&#x80CC;&#x666F;&#x5899;</b>&#x3002;
          <br
          /><code>showEffect</code>&#x8868;&#x793A;&#x5199;&#x5165;&#x77AC;&#x95F4;&#x662F;&#x5426;&#x4EA7;&#x751F;&#x7C92;&#x5B50;&#x6548;&#x679C;&#x3002;<code>playSound</code>&#x8868;&#x793A;&#x5199;&#x5165;&#x77AC;&#x95F4;&#x662F;&#x5426;&#x64AD;&#x653E;&#x653E;&#x7F6E;&#x97F3;&#x6548;&#x3002;</p>
        <p><em>&#x9700;&#x4FDD;&#x8BC1;<code>CanSetWall(xi, yi, blockID)</code>&#x4E3A;&#x771F;&#x3002;</em>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">MapUtils.PlaceWall(int xi, int yi, int blockID, bool showEffect = true,
        bool playSound = true)</td>
      <td style="text-align:center">bool</td>
      <td style="text-align:left">
        <p>&#x5728;&#x6307;&#x5B9A;&#x683C;&#x5B50;<b>&#x653E;&#x7F6E;&#x80CC;&#x666F;&#x5899;</b>&#x3002;
          <br
          /><code>showEffect</code>&#x8868;&#x793A;&#x653E;&#x7F6E;&#x77AC;&#x95F4;&#x662F;&#x5426;&#x4EA7;&#x751F;&#x7C92;&#x5B50;&#x6548;&#x679C;&#x3002;<code>playSound</code>&#x8868;&#x793A;&#x653E;&#x7F6E;&#x77AC;&#x95F4;&#x662F;&#x5426;&#x64AD;&#x653E;&#x653E;&#x7F6E;&#x97F3;&#x6548;&#x3002;</p>
        <p><em>&#x9700;&#x4FDD;&#x8BC1;<code>CanPlaceWall(xi, yi, blockID)</code>&#x4E3A;&#x771F;&#x3002;</em>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">MapUtils.SetFront(int xi, int yi, int blockID, bool destroyFraglie = true,
        bool showEffect = false, bool playSound = false)</td>
      <td style="text-align:center">bool</td>
      <td style="text-align:left">
        <p>&#x5728;&#x6307;&#x5B9A;&#x683C;&#x5B50;<b>&#x5199;&#x5165;&#x524D;&#x666F;&#x65B9;&#x5757;&#xFF08;&#x524D;&#x666F;&#x56FE;&#x5757;&#x6216;&#x5BB6;&#x5177;&#xFF09;</b>&#x3002;
          <br
          /><code>showEffect</code>&#x8868;&#x793A;&#x5199;&#x5165;&#x77AC;&#x95F4;&#x662F;&#x5426;&#x4EA7;&#x751F;&#x7C92;&#x5B50;&#x6548;&#x679C;&#x3002;<code>playSound</code>&#x8868;&#x793A;&#x5199;&#x5165;&#x77AC;&#x95F4;&#x662F;&#x5426;&#x64AD;&#x653E;&#x653E;&#x7F6E;&#x97F3;&#x6548;&#x3002;</p>
        <p><em>&#x9700;&#x4FDD;&#x8BC1;<code>CanSetFront(xi, yi, blockID, destroyFraglie)</code>&#x4E3A;&#x771F;&#x3002;</em>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">MapUtils.PlaceFront(int xi, int yi, int blockID, bool destroyFraglie =
        true, bool showEffect = true, bool playSound = true)</td>
      <td style="text-align:center">bool</td>
      <td style="text-align:left">
        <p>&#x5728;&#x6307;&#x5B9A;&#x683C;&#x5B50;<b>&#x653E;&#x7F6E;&#x524D;&#x666F;&#x65B9;&#x5757;&#xFF08;&#x524D;&#x666F;&#x56FE;&#x5757;&#x6216;&#x5BB6;&#x5177;&#xFF09;</b>&#x3002;
          <br
          /><code>showEffect</code>&#x8868;&#x793A;&#x653E;&#x7F6E;&#x77AC;&#x95F4;&#x662F;&#x5426;&#x4EA7;&#x751F;&#x7C92;&#x5B50;&#x6548;&#x679C;&#x3002;<code>playSound</code>&#x8868;&#x793A;&#x653E;&#x7F6E;&#x77AC;&#x95F4;&#x662F;&#x5426;&#x64AD;&#x653E;&#x653E;&#x7F6E;&#x97F3;&#x6548;&#x3002;</p>
        <p><em>&#x9700;&#x4FDD;&#x8BC1;<code>CanPlaceFront(xi, yi, blockID, destroyFraglie)</code>&#x4E3A;&#x771F;&#x3002;</em>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">MapUtils.SetFrontTag(int xi, int yi, int tag)</td>
      <td style="text-align:center">bool</td>
      <td style="text-align:left">
        <p>&#x5728;&#x6307;&#x5B9A;&#x683C;&#x5B50;&#x5199;&#x5165;<b>&#x524D;&#x666F;&#x9644;&#x52A0;&#x503C;</b>&#x3002;</p>
        <p><code>tag</code>&#x8868;&#x793A;&#x524D;&#x666F;&#x7684;&#x9644;&#x52A0;&#x503C;&#x3002;</p>
        <p><em>&#x9700;&#x4FDD;&#x8BC1;<code>CanSetFrontTag(xi, yi)</code>&#x4E3A;&#x771F;&#x3002;</em>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">MapUtils.TriggerSignal(int xi, int yi, bool isOn)</td>
      <td style="text-align:center">bool</td>
      <td style="text-align:left">
        <p>&#x5728;&#x6307;&#x5B9A;&#x683C;&#x5B50;&#x5199;&#x5165;<b>&#x89E6;&#x53D1;&#x4E00;&#x4E2A;&#x7EA2;&#x77F3;&#x4FE1;&#x53F7;</b>&#x3002;</p>
        <p><code>isOn</code>&#x8868;&#x793A;&#x7EA2;&#x77F3;&#x4FE1;&#x53F7;&#x662F;&#x6FC0;&#x6D3B;&#x8FD8;&#x662F;&#x53D6;&#x6D88;&#x6FC0;&#x6D3B;&#x3002;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">MapUtils.DelayTriggerSignal(int xi, int yi, bool isOn, int delayTime)</td>
      <td
      style="text-align:center">bool</td>
        <td style="text-align:left">
          <p>&#x5728;&#x6307;&#x5B9A;&#x683C;&#x5B50;&#x7B49;&#x5F85;&#x6307;&#x5B9A;&#x5EF6;&#x8FDF;&#x65F6;&#x95F4;&#x540E;<b>&#x89E6;&#x53D1;&#x4E00;&#x4E2A;&#x7EA2;&#x77F3;&#x4FE1;&#x53F7;</b>&#x3002;</p>
          <p><code>isOn</code>&#x8868;&#x793A;&#x7EA2;&#x77F3;&#x4FE1;&#x53F7;&#x662F;&#x6FC0;&#x6D3B;&#x8FD8;&#x662F;&#x53D6;&#x6D88;&#x6FC0;&#x6D3B;&#xFF0C;<code>delayTime</code>&#x8868;&#x793A;&#x5EF6;&#x8FDF;&#x65F6;&#x95F4;&#x3002;</p>
        </td>
    </tr>
  </tbody>
</table>

#### 

