# 皮肤表（skins.json）

## JSON格式

```text
[
    {
        <皮肤ID名称>: {
            "isFemale": <布尔值>,
            "headTexture": <贴图文件路径>,
            "bodyTexture": <贴图文件路径>,
            "legTexture": <贴图文件路径>,
            "hairTexture": <贴图文件路径>,
            "clothTexture": <贴图文件路径>,
            "pantTexture": <贴图文件路径>
        }
    },
    ...
]
```

| 标志 | 类型 | 默认值 | 描述 |
| :--- | :---: | :---: | :--- |
| &lt;皮肤ID名称&gt; | 字符串 | 必填 | 注册到游戏中的皮肤ID名称。 |
| isFemale | 布尔值 | false | 皮肤是否表示女性角色。 |
| headTexture | 字符串 | 必填 | 头的贴图文件路径。 |
| bodyTexture | 字符串 | 必填 | 身体的贴图文件路径。 |
| legTexture | 字符串 | 必填 | 腿的贴图文件路径。 |
| hairTexture | 字符串 | 必填 | 头发的贴图文件路径。 |
| clothTexture | 字符串 | 必填 | 衣服的贴图文件路径。 |
| pantTexture | 字符串 | 必填 | 裤子的贴图文件路径。 |

