# 语言API

## 语言通用模块（LangUtils）

注意：该模块返回的所有字符串为_**UTF8格式**_，用于兼容多国语言。

| 函数 | 返回值 | 描述 |
| :--- | :---: | :--- |
| LangUtils.ModText\(string key\) | string | 根据key值返回Mod在当前语言的**自定义文本**。 |
| LangUtils.BuffName\(int buffID\) | string | 根据BUFF的ID返回**BUFF**在当前语言的名称。 |
| LangUtils.EnchantmentName\(int enchantmentID\) | string | 根据附魔的ID返回**附魔**在当前语言的名称。 |
| LangUtils.NpcName\(int npcID\) | string | 根据NPC的ID返回**NPC**在当前语言的名称。 |



