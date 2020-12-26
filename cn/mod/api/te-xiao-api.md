# 特效API

## 特效通用模块（EffectUtils）

| 函数 | 返回值 | 描述 |
| :--- | :---: | :--- |
| EffectUtils.Create\(int id, double centerX, double centerY, double speedX = 0.0, double speedY = 0.0, double rotateSpeed = 0.0, double scale = 1.0, double alpha = 1.0\) | Effect | 创建一个特效实体，返回创建好的特效实体。 `id`：特效ID。`centerX`和`centerY`：创建特效的中心点。`speedX`和`speedY`：初始运动速度。`rotateSpeed`：初始旋转速度。`scale`：初始缩放尺寸比例，有效区间为\(0, +∞\)。`alpha`：初始不透明度，有效区间为\[0, 1\]。 |
| EffectUtils.CreateFromServer\(int id, double centerX, double centerY, double speedX = 0.0, double speedY = 0.0, double rotateSpeed = 0.0, double scale = 1.0, double alpha = 1.0\) | Effect | 在服务端创建一个特效实体并将该特效实体发送到所有可见该特效的客户端。 |
| EffectUtils.CreateExplosion\(double centerX, double centerY\) | void | 创建一个爆炸特效。 |

## 特效类（Effect Class）

特效（Effect）类表示具有粒子客户端效果的实体类。

### 父类

该类的父类为[Entity类](entity.md#shi-ti-lei-entity-class)。可直接使用该父类的类成员属性与类成员函数。

### 类成员函数

| 函数 | 返回值 | 描述 |
| :--- | :--- | :--- |
|  |  |  |



