# 基本JSON类型

## 脚本JSON格式

```text
{
    "path": <lua file path>,
    "requires": [
        [ <module name>, <lua module file path> ],
        ...
    ]
}
```

| 内容 | 类型 | 描述 | 默认值 |
| :---: | :---: | :---: | :---: |
| path | string | 所执行脚本的lua文件路径。 |  |
| requires | list | 当前lua文件所使用的所有外部模块。 | 空 |
| &lt;模块名称&gt; | string | 模块名称。lua中请使用`require(模块名称)`来加载指定模块。 |  |
| &lt;lua模块文件路径&gt; | string | 模块对应的lua文件路径。 |  |

## 物品格子JSON格式



