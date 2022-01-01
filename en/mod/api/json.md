# JSON

## JsonUtils

| Function                                                                                     | Returns | Description                                                                 |
| -------------------------------------------------------------------------------------------- | :-----: | --------------------------------------------------------------------------- |
| JsonUtils.SetItemSlot(Json json, string key, ItemSlot itemSlot)                              |   void  | 为指定JSON写入字符串键和物品格子数据。                                                       |
| JsonUtils.SetItemSlot(Json json, ItemSlot itemSlot)                                          |   void  | 为指定JSON写入物品格子数据。                                                            |
| JsonUtils.GetItemSlot(Json json, string key, ItemSlot itemSlot)                              |   void  | 从指定JSON根据字符串键读取物品格子数据。                                                      |
| JsonUtils.GetItemSlot(Json json, ItemSlot itemSlot)                                          |   void  | 从指定JSON读取物品格子数据。                                                            |
| JsonUtils.SetItemSlotArray(Json json, string key, ItemSlot itemSlotFirstElement, int length) |   void  | 为指定JSON写入字符串键和物品格子数组数据。`itemSlotFirstElement`表示物品格子数组的第一个元素，`length`表示数组长度。 |
| JsonUtils.SetItemSlotArray(Json json, ItemSlot itemSlotFirstElement, int length)             |   void  | 为指定JSON写入物品格子数组数据。                                                          |
| JsonUtils.GetItemSlotArray(Json json, string key, ItemSlot itemSlotFirstElement, int length) |   void  | 从指定JSON根据字符串键读取物品格子数组数据。                                                    |
| JsonUtils.GetItemSlotArray(Json json, ItemSlot itemSlotFirstElement, int length)             |   void  | 从指定JSON读取物品格子数组数据。                                                          |

## Json Class

The Json class is a serialized object or array that meets the standard JSON syntax specification.

### Static Function

| Function          | Returns | Description     |
| ----------------- | :-----: | --------------- |
| Json:new\_local() |   Json  | Returns a JSON. |

### Member Function

#### Object writing function

| Function                                 | Returns | Description                                                                                                                                                                                     |
| ---------------------------------------- | :-----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Json:SetInt(string key, int value)       |   void  | Write a key-value pair which value is integer.                                                                                                                                                  |
| Json:SetInt(int value)                   |   void  | Write an integer value.                                                                                                                                                                         |
| Json:SetDouble(string key, double value) |   void  | Write a key-value pair which value is double.                                                                                                                                                   |
| Json:SetDouble(double value)             |   void  | Write a double value.                                                                                                                                                                           |
| Json:SetBoolean(string key, bool value)  |   void  | Write a key-value pair which value is boolean.                                                                                                                                                  |
| Json:SetBoolean(bool value)              |   void  | Write a boolean value.                                                                                                                                                                          |
| Json:SetString(string key, string value) |   void  | Write a key-value pair which value is string.                                                                                                                                                   |
| Json:SetString(string value)             |   void  | Write a string value.                                                                                                                                                                           |
| Json:SetJson(string key, Json value)     |   void  | Write a key-value pair which value is JSON.                                                                                                                                                     |
| Json:SetJson(Json value)                 |   void  | Write a JSON value.                                                                                                                                                                             |
| Json:MoveSetJson(string key, Json value) |   void  | <p>Write a key-value pair which value is JSON using std::move(value) in C++.</p><p><em><strong>Note: the value is not allowed to be used again after the parameter is passed.</strong></em></p> |
| Json:MoveSetJson(Json value)             |   void  | <p>Write a JSON value using std::move(value) in C++.</p><p><em><strong>Note: same above.</strong></em></p>                                                                                      |

#### Object reading function

| Function                    | Returns | Description                                                           |
| --------------------------- | :-----: | --------------------------------------------------------------------- |
| Json:GetInt(string key)     |   int   | Read the integer value. Always returns 0 if does not exist.           |
| Json:GetInt()               |   int   | Read the integer value. Always returns 0 if does not exist.           |
| Json:GetDouble(string key)  |  double | Read the double value. Always returns 0.0 if does not exist.          |
| Json:GetDouble()            |  double | Read the double value. Always returns 0.0 if does not exist.          |
| Json:GetBoolean(string key) |   bool  | Read the boolean value. Always returns false if does not exist.       |
| Json:GetBoolean()           |   bool  | Read the boolean value. Always returns false if does not exist.       |
| Json:GetString(string key)  |  string | Read the string value. Always returns empty string if does not exist. |
| Json:GetString()            |  string | Read the string value. Always returns empty string if does not exist. |
| Json:HasKey(string key)     |   bool  | Returns whether the current JSON has the specified key.               |

#### Array function

| 函数                                       |        返回值       | 描述                                                             |
| ---------------------------------------- | :--------------: | -------------------------------------------------------------- |
| Json:AddJson(string key, Json value)     |       void       | 加入一个JSON到当前JSON指定键对应的数组。                                       |
| Json:MoveAddJson(string key, Json value) |       void       | 加入一个JSON到当前JSON指定键对应的数组。**value使用移动构造方式加入，注意传参后value不允许再次使用。** |
| Json:AddJson(Json value)                 |       void       | 加入一个JSON到当前JSON数组。                                             |
| Json:MoveAddJson(Json value)             |       void       | 加入一个JSON到当前JSON数组。**value使用移动构造方式加入，注意传参后value不允许再次使用。**       |
| Json:GetList()                           | ArrayList\<Json> | 返回当前JSON数组。                                                    |

#### Encoding and decoding

| Function               | Returns | Description                            |
| ---------------------- | :-----: | -------------------------------------- |
| Json:Dump()            |  string | Returns the current JSON encoded text. |
| Json:Load(string text) |   void  | Decode the text to the current JSON.   |
