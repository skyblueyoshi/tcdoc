# 物品API

## 物品格类（ItemSlot Class）

**物品格（ItemSlot）**类表示拥有物品格子基本信息的类对象。

物品格可能包含某种类型的物品，也可能不包含任何物品，即**空物品格**。

以Minecraft为例，下图描述了有物品和无物品的两种物品格：

![&#x5305;&#x542B;&#x201C;&#x6CB3;&#x8C5A;&#x201D;&#x7269;&#x54C1;&#x7684;&#x7269;&#x54C1;&#x683C;](../../../.gitbook/assets/item_slot_has_item.png)

![&#x4E0D;&#x5305;&#x542B;&#x7269;&#x54C1;&#x7684;&#x7A7A;&#x7269;&#x54C1;&#x683C;](../../../.gitbook/assets/item_slot_empty.png)

**在对物品格进行相关物品操作时必须预先判断当前物品格是否包含物品。**

### **类成员属性**

| 属性 | 类型 | 描述 |
| :--- | :--- | :--- |
| ItemSlot.hasItem | bool | **【只读】**当前物品格是否包含物品。 |
| ItemSlot.id | int | **【只读】**若物品格不为空，表示包含的物品ID，否则总是为0。 |
| ItemSlot.count | int | **【只读】**若物品格不为空，表示包含的物品数量，否则总是为0。 |
| ItemSlot.maxCount | int | **【只读】**若物品格不为空，表示包含的物品最大允许数量，否则总是为0。 |
| ItemSlot.type | [ItemType](datatypes-enums-constants.md#itemtype) | **【只读】**若物品格不为空，表示内置物品类型，否则总是为`ITEM_TYPE_NONE`。 |

### 类成员函数

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
      <td style="text-align:left">ItemSlot:Create(int itemID, int count = 1)</td>
      <td style="text-align:center">bool</td>
      <td style="text-align:left">
        <p>&#x82E5;&#x7269;&#x54C1;&#x683C;&#x4E3A;&#x7A7A;&#xFF0C;&#x521B;&#x5EFA;&#x65B0;&#x7684;&#x6307;&#x5B9A;&#x7269;&#x54C1;&#xFF0C;&#x8FD4;&#x56DE;true&#x3002;</p>
        <p>&#x82E5;&#x7269;&#x54C1;&#x683C;&#x4E0D;&#x4E3A;&#x7A7A;&#xFF0C;&#x5148;&#x9500;&#x6BC1;&#x539F;&#x5305;&#x542B;&#x7269;&#x54C1;&#xFF0C;&#x518D;&#x521B;&#x5EFA;&#x65B0;&#x7684;&#x6307;&#x5B9A;&#x7269;&#x54C1;&#xFF0C;&#x8FD4;&#x56DE;true&#x3002;</p>
        <p>&#x82E5;itemID&#x975E;&#x6CD5;&#x6216;count&#x975E;&#x6B63;&#x6570;&#xFF0C;&#x9500;&#x6BC1;&#x539F;&#x5305;&#x542B;&#x7269;&#x54C1;&#x5E76;&#x8FD4;&#x56DE;false&#x3002;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">ItemSlot:Replace(ItemSlot slot)</td>
      <td style="text-align:center">void</td>
      <td style="text-align:left">&#x5C06;&#x5F53;&#x524D;&#x7269;&#x54C1;&#x683C;&#x66FF;&#x6362;&#x4E3A;&#x6307;&#x5B9A;&#x7269;&#x54C1;&#x683C;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">ItemSlot:Swap(ItemSlot slot)</td>
      <td style="text-align:center">void</td>
      <td style="text-align:left">&#x5C06;&#x5F53;&#x524D;&#x7269;&#x54C1;&#x683C;&#x4E0E;&#x53E6;&#x4E00;&#x4E2A;&#x7269;&#x54C1;&#x683C;&#x4EA4;&#x6362;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">ItemSlot:Clear()</td>
      <td style="text-align:center">void</td>
      <td style="text-align:left">&#x9500;&#x6BC1;&#x5185;&#x90E8;&#x7684;&#x5168;&#x90E8;&#x7269;&#x54C1;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">ItemSlot:RemoveOne()</td>
      <td style="text-align:center">bool</td>
      <td style="text-align:left">
        <p>&#x82E5;&#x7269;&#x54C1;&#x683C;&#x4E0D;&#x4E3A;&#x7A7A;&#xFF0C;&#x79FB;&#x9664;&#x5185;&#x90E8;1&#x4E2A;&#x7269;&#x54C1;&#x3002;</p>
        <p>&#x82E5;&#x64CD;&#x4F5C;&#x540E;&#x7269;&#x54C1;&#x683C;&#x7269;&#x54C1;&#x683C;&#x4E3A;&#x7A7A;&#xFF0C;&#x8FD4;&#x56DE;true&#x3002;&#x82E5;&#x7269;&#x54C1;&#x683C;&#x4ECD;&#x7136;&#x5B58;&#x5728;&#x7269;&#x54C1;&#xFF0C;&#x8FD4;&#x56DE;false&#x3002;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">ItemSlot:MoveFrom(ItemSlot slot)</td>
      <td style="text-align:center">int</td>
      <td style="text-align:left">
        <p>&#x5C06;&#x6307;&#x5B9A;&#x7269;&#x54C1;&#x683C;&#x7684;&#x5185;&#x5BB9;&#x7269;&#x54C1;&#x79FB;&#x5165;&#x5230;&#x5F53;&#x524D;&#x7269;&#x54C1;&#x683C;&#x3002;&#x8FD4;&#x56DE;&#x6210;&#x529F;&#x79FB;&#x5165;&#x7684;&#x7269;&#x54C1;&#x4E2A;&#x6570;&#x3002;</p>
        <p>&#x8F6C;&#x79FB;&#x89C4;&#x5219;&#x89C1;&#xFF1A;<a href="wu-pin-api.md#wu-pin-zhuan-yi-gui-ze">&#x7269;&#x54C1;&#x8F6C;&#x79FB;&#x89C4;&#x5219;</a>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">ItemSlot:MoveTo(ItemSlot slot)</td>
      <td style="text-align:center">int</td>
      <td style="text-align:left">
        <p>&#x5C06;&#x5F53;&#x524D;&#x7269;&#x54C1;&#x683C;&#x7684;&#x5185;&#x5BB9;&#x7269;&#x79FB;&#x51FA;&#x5230;&#x6307;&#x5B9A;&#x7269;&#x54C1;&#x683C;&#x3002;&#x8FD4;&#x56DE;&#x6210;&#x529F;&#x79FB;&#x51FA;&#x7684;&#x7269;&#x54C1;&#x4E2A;&#x6570;&#x3002;</p>
        <p>&#x8F6C;&#x79FB;&#x89C4;&#x5219;&#x89C1;&#xFF1A;<a href="wu-pin-api.md#wu-pin-zhuan-yi-gui-ze">&#x7269;&#x54C1;&#x8F6C;&#x79FB;&#x89C4;&#x5219;</a>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">ItemSlot:SetCount(int count)</td>
      <td style="text-align:center">int</td>
      <td style="text-align:left">
        <p>&#x82E5;&#x7269;&#x54C1;&#x683C;&#x4E0D;&#x4E3A;&#x7A7A;&#xFF0C;&#x8BBE;&#x7F6E;&#x5305;&#x542B;&#x7684;&#x7269;&#x54C1;&#x6570;&#x91CF;&#xFF0C;&#x8FD4;&#x56DE;&#x8BBE;&#x7F6E;&#x540E;&#x7269;&#x54C1;&#x6570;&#x91CF;&#x3002;</p>
        <p>&#x82E5;&#x7269;&#x54C1;&#x683C;&#x4E3A;&#x7A7A;&#xFF0C;&#x4E0D;&#x8FDB;&#x884C;&#x4EFB;&#x4F55;&#x64CD;&#x4F5C;&#x5E76;&#x8FD4;&#x56DE;0&#x3002;</p>
        <p>&#x8BBE;&#x5B9A;&#x89C4;&#x5219;&#x89C1;&#xFF1A;<a href="wu-pin-api.md#wu-pin-shu-liang-she-ding-yuan-ze">&#x7269;&#x54C1;&#x6570;&#x91CF;&#x8BBE;&#x5B9A;&#x89C4;&#x5219;</a>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">ItemSlot:AddCount(int addCount)</td>
      <td style="text-align:center">int</td>
      <td style="text-align:left">
        <p>&#x82E5;&#x7269;&#x54C1;&#x683C;&#x4E0D;&#x4E3A;&#x7A7A;&#xFF0C;&#x4E3A;&#x5305;&#x542B;&#x7684;&#x7269;&#x54C1;&#x6DFB;&#x52A0;&#x6570;&#x91CF;&#xFF0C;&#x8FD4;&#x56DE;&#x6DFB;&#x52A0;&#x540E;&#x7269;&#x54C1;&#x6570;&#x91CF;&#x3002;</p>
        <p>&#x82E5;addCount&#x4E3A;&#x6B63;&#x6570;&#xFF0C;&#x8868;&#x793A;&#x6DFB;&#x52A0;&#x7269;&#x54C1;&#x6570;&#x91CF;&#x3002;&#x82E5;addCount&#x4E3A;&#x8D1F;&#x6570;&#xFF0C;&#x8868;&#x793A;&#x51CF;&#x5C11;&#x7269;&#x54C1;&#x6570;&#x91CF;&#x3002;</p>
        <p>&#x82E5;&#x7269;&#x54C1;&#x683C;&#x4E3A;&#x7A7A;&#xFF0C;&#x4E0D;&#x8FDB;&#x884C;&#x4EFB;&#x4F55;&#x64CD;&#x4F5C;&#x5E76;&#x8FD4;&#x56DE;0&#x3002;</p>
        <p>&#x8BBE;&#x5B9A;&#x89C4;&#x5219;&#x89C1;&#xFF1A;<a href="wu-pin-api.md#wu-pin-shu-liang-she-ding-yuan-ze">&#x7269;&#x54C1;&#x6570;&#x91CF;&#x8BBE;&#x5B9A;&#x89C4;&#x5219;</a>
        </p>
      </td>
    </tr>
  </tbody>
</table>

## 物品数量设定规则

在物品格包含物品的情况下，若设定数量在区间**\[1, 最大允许数量\]**，则设定数量合法，直接将物品数量设为指定数量。否则：

1. 若设定数量超过最大允许数量，将物品数量设为最大允许数量。
2. 若设定数量非正数，清除内部包含的物品。

## 物品转移规则

将一个物品格的物品转移至另一个物品格时，若两个物品格的物品不是同类物品，不会进行转移。若物品格转移达到最大允许数量，则终止转移。





