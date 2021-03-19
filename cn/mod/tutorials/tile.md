# 1.8 第一个图块TODO

## 创建方块文件夹

在_**contents**_文件夹中创建_**blocks**_文件夹作为方块文件夹。

## 创建一个图块（Tile）

我们希望木板可以被染色！那么我们加入一个黄色木板作为模组的第一个图块，id命名为`yellow_plank`。

![yellow\_plank\_icon.png](../../../.gitbook/assets/image%20%2817%29.png)

![yellow\_plank.png](../../../.gitbook/assets/image%20%2818%29.png)

在方块文件夹任意路径内添加`yellow_plank.png`、`yellow_plank_icon.png`作为贴图路径，并在同级文件夹创建`yellow_plank.json`文件作为JSON数据表文件。JSON文件为如下内容：

```text
{
  "block": {
    "yellow_plank": {
      "textureData": "yellow_plank.png",
      "color": [ 255, 255, 0 ],
      "renderMode": "RENDER_BORDER_CUT",
      "renderSortedInterval": 8,
      "type": "TILE",
      "group": "ARTIFICAL",
      "collision": "SOLID",
      "lightOpacity": 3,
      "toolType": "AXE",
      "mineGrade": "GRASS",
      "hardness": 100,
      "slipperiness": 1.0,
      "gravity": false,
      "allowSlope": false,
      "isWallDark": false,
      "wallCheck": "NO_GENERABLE",
      "soundGroupId": "wood",
      "stepSoundGroupId": "step_wood",
      "particleColor": [ 255, 173, 137, 80 ]
    }
  },
  "item": {
    "yellow_plank": {
      "type": "BLOCKS",
      "iconTextureData": "yellow_plank_icon.png",
      "group": "GROUP_WOODEN_PLANK",
      "oreDictionaries": [ "plank" ],
      "blockId": "yellow_plank",
      "fuelTime": 60
    }
  }
}
```



