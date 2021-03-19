# 模组配置表（tcmod.json）

```text
{
  "modid": <string>,
  "displayName": <string>,
  "description": <string>,
  "version": <string>,
  "tcVersion": <string>,
  "useSaver": <bool>,
  "authorList": [
    <string>, ...
  ],
  "credits": <string>
}
```

| 内容 | 描述 | 默认值 |
| :---: | :---: | :---: |
| modid | 当前模组的命名空间ID，模组包的唯一标识符，模组发布后不可再修改。见下面关于命名空间的概念解释。只能由小写字母、数字、下划线组成 |  |
| displayName | 游戏中对玩家可见的模组名称 |  |
| description | 游戏中对玩家可见的模组描述 | 空 |
| version | 模组版本号，每次更新模组时需要更新该版本号，版本号必须为4个数字并以英文点号分隔，并且更新版本时数字应该依次累加 |  |
| tcVersion | TerraCraft游戏本体的版本号，请准确填写以便存档版本检测 |  |
| authorList | 开发当前模组的作者名称，可以设置多个作者名称 |  |
| credits | 感谢信息 |  |
| useSaver | 模组是否使用存档，一般填true |  |



