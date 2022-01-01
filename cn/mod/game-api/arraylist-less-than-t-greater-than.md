---
description: 数组，封装自std::vector<T>，一般用于返回值。
---

# ArrayList\<T>

## 属性

| 属性                                                        |
| --------------------------------------------------------- |
| <p>int length<br><strong>【只读】</strong>数组长度。</p>           |
| <p>T [index]<br>读取或写入指定下标的数组元素。index有效区间为[1, length]。</p> |

## 使用

```lua
for i = 1, arrayList.length do
    local element = arrayList[i]
    -- do something on this element
end
```
