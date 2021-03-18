# 特效API

## 钩子函数（特效脚本：contents/effect\_ai/...）

### void Init\(\)

```lua
function Init()
    
end
```

特效生成时调用一次该函数。

### void Update\(\)

```lua
function Update()
    
end
```

特效每帧运行时调用，您可以在该函数内编写运动等逻辑。

### void OnDraw\(\)

```lua
function OnDraw()
    
end
```

特效每帧绘制前调用，在该函数内编写自定义绘制属性。不使用该钩子函数时采取默认处理方式。

## 特效通用模块（EffectUtils）

| 函数 | 返回值 | 描述 |
| :--- | :---: | :--- |
| EffectUtils.Create\(int id, double centerX, double centerY, double speedX = 0.0, double speedY = 0.0, double rotateSpeed = 0.0, double scale = 1.0, double alpha = 1.0\) | Effect | 创建一个特效实体，返回创建好的特效实体。 `id`：特效ID。`centerX`和`centerY`：创建特效的中心点。`speedX`和`speedY`：初始运动速度。`rotateSpeed`：初始旋转速度。`scale`：初始缩放尺寸比例，有效区间为\(0, +∞\)。`alpha`：初始不透明度，有效区间为\[0, 1\]。 |
| EffectUtils.SendFromServer\(int id, double centerX, double centerY, double speedX = 0.0, double speedY = 0.0, double rotateSpeed = 0.0, double scale = 1.0, double alpha = 1.0\) | Effect | 在服务端发送一个特效实体到所有可见该特效的客户端。 |
| EffectUtils.CreateExplosion\(double centerX, double centerY\) | void | 创建一个爆炸特效。 |

## 特效类（Effect Class，继承自Entity Class）

特效（Effect）类表示具有粒子客户端效果的实体类。

### 父类

该类的父类为[Entity类](entity.md#shi-ti-lei-entity-class)。可直接使用该父类的类成员属性与类成员函数。

### 类成员属性

| 属性 | 类型 | 描述 |
| :--- | :---: | :--- |
| Effect.id | int | **【只读】**当前特效的动态ID。 |
| Effect.decSpeed | double | 当前特效的运动减速度。 |
| Effect.decRotateSpeed | double | 当前特效的旋转角减速度。 |
| Effect.decScale | double | 当前特效的每帧尺寸缩小量。 |
| Effect.decAlpha | double | 当前特效的每帧不透明度缩小量。 |
| Effect.scale | double | 当前特效的放缩量。 |
| Effect.alpha | double | 当前特效的不透明度。 |
| Effect.rotateSpeed | double | 当前特效的旋转速度。 |
| Effect.modData | ExData | 特效当前模组自定义模组数据。 |

### 类成员函数

| 函数 | 返回值 | 描述 |
| :--- | :--- | :--- |
| Effect:Kill\(\) | void | 清除当前特效实体。 |



