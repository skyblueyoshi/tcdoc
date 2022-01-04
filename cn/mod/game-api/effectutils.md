---
description: 特效通用模块。
---

# EffectUtils

## 函数

| <p><strong>Effect EffectUtils.Create(int id, double centerX, double centerY, double speedX = 0.0, double speedY = 0.0, double rotateSpeed = 0.0, double scale = 1.0, double alpha = 1.0)</strong><br>创建一个特效实体，返回创建好的特效实体。<br><code>id</code>：特效ID。<br><code>centerX</code>和<code>centerY</code>：创建特效的中心点。<br><code>speedX</code>和<code>speedY</code>：初始运动速度。<br><code>rotateSpeed</code>：初始旋转速度。<br><code>scale</code>：初始缩放尺寸比例，有效区间为(0, +∞)。<br><code>alpha</code>：初始不透明度，有效区间为[0, 1]。</p> |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <p><strong>Effect EffectUtils.SendFromServer(int id, double centerX, double centerY, double speedX = 0.0, double speedY = 0.0, double rotateSpeed = 0.0, double scale = 1.0, double alpha = 1.0)</strong><br>在服务端发送一个特效实体到所有可见该特效的客户端。</p>                                                                                                                                                                                                                                                  |
| <p><strong>void EffectUtils.CreateExplosion(double centerX, double centerY)</strong><br>创建一个爆炸特效。</p>                                                                                                                                                                                                                                                                                                                                                                                       |

