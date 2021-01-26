# 音效表（sounds.json）

## JSON格式：

```text
[
    {
        <音效ID名称>: {
            "tcResource": <布尔值>,
            "path": <路径>
        }
    },
    ...
]
```

| 标志 | 默认值 | 描述 |
| :--- | :--- | :--- |
| tcResource | false | 音效的绝对路径是否使用游戏assets主文件夹。若为false，则使用模组文件夹。 |
| path | **必填** | 音效文件路径。 |



