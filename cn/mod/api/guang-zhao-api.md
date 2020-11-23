# 光照API

光照系统采取**光强等级**来表示光照的强弱。光强等级为整数，有效区间为\[0, 32\]，0为无光强，32为最大光强。

一个光源由如下四个光强分量来表示：

* `alpha`分量表示总光照强度。
* `red`分量表示光照中红色光的多少。
* `green`分量表示光照中绿色光的多少。
* `blue`分量表示光照中蓝色光的多少。

## 光照通用模块（LightingUtils）

| 函数 | 返回值 | 描述 |
| :--- | :---: | :--- |
| LightingUtils.Add\(int xi, int yi, int alpha, int red = 0, int green = 0, int blue = 0\) | void | 为指定格子添加一个光源。 |
| LightingUtils.AddDelay\(int xi, int yi, int delayTime, int alpha, int red = 0, int green = 0, int blue = 0\) | void | 为指定格子添加一个延迟光源。光源在`delayTime`时间内会逐渐延迟消失。 |


