---
description: >-
  光照系统采取光强等级来表示光照的强弱。光强等级为整数，有效区间为[0,
  32]，0为无光强，32为最大光强。一个光源由如下四个光强分量来表示：alpha分量表示总光照强度，red/green/blue分量表示光照中红/绿/蓝色光的多少。
---

# LightingUtils

光照系统采取光强等级来表示光照的强弱。光强等级为整数，有效区间为\[0, 32]，0为无光强，32为最大光强。一个光源由如下四个光强分量来表示：alpha分量表示总光照强度，red/green/blue分量表示光照中红/绿/蓝色光的多少。

## 函数

| 函数                                                                                                                                                                                            |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <p><strong>void LightingUtils.Add(int xi, int yi, int alpha, int red = 0, int green = 0, int blue = 0)</strong><br>为指定格子添加一个光源。</p>                                                           |
| <p><strong>void LightingUtils.AddDelay(int xi, int yi, int delayTime, int alpha, int red = 0, int green = 0, int blue = 0)</strong><br>为指定格子添加一个延迟光源。光源在<code>delayTime</code>时间内会逐渐延迟消失。</p> |
| <p><strong>void LightingUtils.SetState(LightingState state)</strong><br>设定客户端当前的光照状态。光照渲染完毕后恢复状态为<em><code>LIGHTING_STATE_NORMAL</code>。</em></p>                                             |

