# JSON API

## JsonUtils

| Function | Returns | Description |
| :--- | :---: | :--- |
| JsonUtils.SetItemSlot\(Json json, string key, ItemSlot itemSlot\) | void | 为指定JSON写入字符串键和物品格子数据。 |
| JsonUtils.SetItemSlot\(Json json, ItemSlot itemSlot\) | void | 为指定JSON写入物品格子数据。 |
| JsonUtils.GetItemSlot\(Json json, string key, ItemSlot itemSlot\) | void | 从指定JSON根据字符串键读取物品格子数据。 |
| JsonUtils.GetItemSlot\(Json json, ItemSlot itemSlot\) | void | 从指定JSON读取物品格子数据。 |
| JsonUtils.SetItemSlotArray\(Json json, string key, ItemSlot itemSlotFirstElement, int length\) | void | 为指定JSON写入字符串键和物品格子数组数据。`itemSlotFirstElement`表示物品格子数组的第一个元素，`length`表示数组长度。 |
| JsonUtils.SetItemSlotArray\(Json json, ItemSlot itemSlotFirstElement, int length\) | void | 为指定JSON写入物品格子数组数据。 |
| JsonUtils.GetItemSlotArray\(Json json, string key, ItemSlot itemSlotFirstElement, int length\) | void | 从指定JSON根据字符串键读取物品格子数组数据。 |
| JsonUtils.GetItemSlotArray\(Json json, ItemSlot itemSlotFirstElement, int length\) | void | 从指定JSON读取物品格子数组数据。 |

## Json Class

The Json class is a serialized object or array that meets the standard JSON syntax specification.

### Static Function

| Function | Returns | Description |
| :--- | :---: | :--- |
| Json:new\_local\(\) | Json | Returns a JSON. |

### Member Function

#### Object writing function

<table>
  <thead>
    <tr>
      <th style="text-align:left">Function</th>
      <th style="text-align:center">Returns</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">Json:SetInt(string key, int value)</td>
      <td style="text-align:center">void</td>
      <td style="text-align:left">Write a key-value pair which value is integer.</td>
    </tr>
    <tr>
      <td style="text-align:left">Json:SetInt(int value)</td>
      <td style="text-align:center">void</td>
      <td style="text-align:left">Write an integer value.</td>
    </tr>
    <tr>
      <td style="text-align:left">Json:SetDouble(string key, double value)</td>
      <td style="text-align:center">void</td>
      <td style="text-align:left">Write a key-value pair which value is double.</td>
    </tr>
    <tr>
      <td style="text-align:left">Json:SetDouble(double value)</td>
      <td style="text-align:center">void</td>
      <td style="text-align:left">Write a double value.</td>
    </tr>
    <tr>
      <td style="text-align:left">Json:SetBoolean(string key, bool value)</td>
      <td style="text-align:center">void</td>
      <td style="text-align:left">Write a key-value pair which value is boolean.</td>
    </tr>
    <tr>
      <td style="text-align:left">Json:SetBoolean(bool value)</td>
      <td style="text-align:center">void</td>
      <td style="text-align:left">Write a boolean value.</td>
    </tr>
    <tr>
      <td style="text-align:left">Json:SetString(string key, string value)</td>
      <td style="text-align:center">void</td>
      <td style="text-align:left">Write a key-value pair which value is string.</td>
    </tr>
    <tr>
      <td style="text-align:left">Json:SetString(string value)</td>
      <td style="text-align:center">void</td>
      <td style="text-align:left">Write a string value.</td>
    </tr>
    <tr>
      <td style="text-align:left">Json:SetJson(string key, Json value)</td>
      <td style="text-align:center">void</td>
      <td style="text-align:left">Write a key-value pair which value is JSON.</td>
    </tr>
    <tr>
      <td style="text-align:left">Json:SetJson(Json value)</td>
      <td style="text-align:center">void</td>
      <td style="text-align:left">Write a JSON value.</td>
    </tr>
    <tr>
      <td style="text-align:left">Json:MoveSetJson(string key, Json value)</td>
      <td style="text-align:center">void</td>
      <td style="text-align:left">
        <p>Write a key-value pair which value is JSON using std::move(value) in C++.</p>
        <p><em><b>Note: the value is not allowed to be used again after the parameter is passed.</b></em>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Json:MoveSetJson(Json value)</td>
      <td style="text-align:center">void</td>
      <td style="text-align:left">
        <p>Write a JSON value using std::move(value) in C++.</p>
        <p><em><b>Note: same above.</b></em>
        </p>
      </td>
    </tr>
  </tbody>
</table>

#### Object reading function

| Function | Returns | Description |
| :--- | :---: | :--- |
| Json:GetInt\(string key\) | int | Read the integer value. Always returns 0 if does not exist. |
| Json:GetInt\(\) | int | Read the integer value. Always returns 0 if does not exist. |
| Json:GetDouble\(string key\) | double | Read the double value. Always returns 0.0 if does not exist. |
| Json:GetDouble\(\) | double | Read the double value. Always returns 0.0 if does not exist. |
| Json:GetBoolean\(string key\) | bool | Read the boolean value. Always returns false if does not exist. |
| Json:GetBoolean\(\) | bool | Read the boolean value. Always returns false if does not exist. |
| Json:GetString\(string key\) | string | Read the string value. Always returns empty string if does not exist. |
| Json:GetString\(\) | string | Read the string value. Always returns empty string if does not exist. |
| Json:HasKey\(string key\) | bool | Returns whether the current JSON has the specified key. |

#### Array function

| 函数 | 返回值 | 描述 |
| :--- | :---: | :--- |
| Json:AddJson\(string key, Json value\) | void | 加入一个JSON到当前JSON指定键对应的数组。 |
| Json:MoveAddJson\(string key, Json value\) | void | 加入一个JSON到当前JSON指定键对应的数组。**value使用移动构造方式加入，注意传参后value不允许再次使用。** |
| Json:AddJson\(Json value\) | void | 加入一个JSON到当前JSON数组。 |
| Json:MoveAddJson\(Json value\) | void | 加入一个JSON到当前JSON数组。**value使用移动构造方式加入，注意传参后value不允许再次使用。** |
| Json:GetList\(\) | ArrayList&lt;Json&gt; | 返回当前JSON数组。 |

#### Encoding and decoding

| Function | Returns | Description |
| :--- | :---: | :--- |
| Json:Dump\(\) | string | Returns the current JSON encoded text. |
| Json:Load\(string text\) | void | Decode the text to the current JSON. |

