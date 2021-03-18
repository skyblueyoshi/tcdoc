# JSON API

## Json通用模块（JsonUtils）

| 函数 | 返回值 | 描述 |
| :--- | :---: | :--- |
| JsonUtils.SetItemSlot\(Json json, string key, ItemSlot itemSlot\) | void | 为指定JSON写入字符串键和物品格子数据。 |
| JsonUtils.SetItemSlot\(Json json, ItemSlot itemSlot\) | void | 为指定JSON写入物品格子数据。 |
| JsonUtils.GetItemSlot\(Json json, string key, ItemSlot itemSlot\) | void | 从指定JSON根据字符串键读取物品格子数据。 |
| JsonUtils.GetItemSlot\(Json json, ItemSlot itemSlot\) | void | 从指定JSON读取物品格子数据。 |

## Json类（Json Class）

**Json**类为标记化序列，是一个序列化的对象或数组，满足标准JSON语法规范。

### 静态函数

| 静态函数 | 返回值 | 描述 |
| :--- | :---: | :--- |
| Json:new\_local\(\) | Attack | 返回一个JSON类。 |

### 类成员函数

#### 对象写入操作

| 函数 | 返回值 | 描述 |
| :--- | :---: | :--- |
| Json:SetInt\(string key, int value\) | void | 写入字符串键和整数值。 |
| Json:SetInt\(int value\) | void | 写入整数。 |
| Json:SetDouble\(string key, double value\) | void | 写入字符串键和浮点数值。 |
| Json:SetDouble\(double value\) | void | 写入浮点数。 |
| Json:SetBoolean\(string key, bool value\) | void | 写入字符串键和布尔值。 |
| Json:SetBoolean\(bool value\) | void | 写入布尔值。 |
| Json:SetString\(string key, string value\) | void | 写入字符串键和字符串值。 |
| Json:SetString\(string value\) | void | 写入字符串。 |
| Json:SetJson\(string key, Json value\) | void | 写入字符串键和JSON值。 |
| Json:SetJson\(Json value\) | void | 写入JSON。 |
| Json:MoveSetJson\(string key, Json value\) | void | 写入字符串键和JSON值。**value使用移动构造方式加入，注意传参后value不允许再次使用。** |
| Json:MoveSetJson\(Json value\) | void | 写入JSON。**value使用移动构造方式加入，注意传参后value不允许再次使用。** |

#### 对象读取操作

| 函数 | 返回值 | 描述 |
| :--- | :---: | :--- |
| Json:GetInt\(string key\) | int | 由字符串键读取整数值，若键值对不存在或值非整数类型，总是返回0。 |
| Json:GetInt\(\) | int | 读取整数值，若不存在或非整数类型，总是返回0。 |
| Json:GetDouble\(string key\) | double | 由字符串键读取浮点数值，若键值对不存在或值非浮点数类型，总是返回0.0。 |
| Json:GetDouble\(\) | double | 由读取浮点数值，若不存在或非浮点数类型，总是返回0.0。 |
| Json:GetBoolean\(string key\) | bool | 由字符串键读取布尔值，若键值对不存在或值非布尔类型，总是返回false。 |
| Json:GetBoolean\(\) | bool | 由读取布尔值，若不存在或非布尔类型，总是返回false。 |
| Json:GetString\(string key\) | string | 由字符串键读取字符串值，若键值对不存在或值非字符串类型，总是返回空字符串。 |
| Json:GetString\(\) | string | 由读取字符串值，若不存在或非字符串类型，总是返回空字符串。 |
| Json:HasKey\(string key\) | bool | 判断当前JSON对象是否拥有指定键。 |
| Json:Dump\(\) | string | 返回当前JSON的 |

#### 数组操作

| 函数 | 返回值 | 描述 |
| :--- | :---: | :--- |
| Json:AddJson\(string key, Json value\) | void | 加入一个JSON到当前JSON指定键对应的数组。 |
| Json:MoveAddJson\(string key, Json value\) | void | 加入一个JSON到当前JSON指定键对应的数组。**value使用移动构造方式加入，注意传参后value不允许再次使用。** |
| Json:AddJson\(Json value\) | void | 加入一个JSON到当前JSON数组。 |
| Json:MoveAddJson\(Json value\) | void | 加入一个JSON到当前JSON数组。**value使用移动构造方式加入，注意传参后value不允许再次使用。** |
| Json:GetList\(\) | ArrayList&lt;Json&gt; | 返回当前JSON数组。 |

#### 编码与解码操作

| 函数 | 返回值 | 描述 |
| :--- | :---: | :--- |
| Json:Dump\(\) | string | 将当前JSON编码成文本。 |
| Json:Load\(string text\) | void | 将文本解码到当前JSON。 |



