# 实体API

全局表名称：entity

| API | 返回值 | 可用 | 描述 |
| :--- | :---: | :---: | :--- |
| entity.x\(\) | double | C/S | 返回实体左上角横坐标。 |
| entity.y\(\) | double | C/S | 返回实体左上角纵坐标。 |
| entity.setX\(double x\) | void | S | 设置实体左上角横坐标。 |
| entity.setY\(double y\) | void | S | 设置实体左上角纵坐标。 |
| entity.speedX\(\) | double | C/S | 返回实体横向速度。 |
| entity.speedY\(\) | double | C/S | 返回实体纵向速度。 |
| entity.setSpeedX\(double spx\) | void | S | 设置实体横向速度。 |
| entity.setSpeedY\(double spy\) | void | S | 设置实体纵向速度。 |
| entity.width\(\) | int | C/S | 返回实体碰撞箱宽度。 |
| entity.height\(\) | int | C/S | 返回实体碰撞箱高度。 |
| entity.centerX\(\) | double | C/S | 返回实体正中间横坐标。 |
| entity.centerY\(\) | double | C/S | 返回实体正中间纵坐标。 |
| entity.rightX\(\) | double | C/S | 返回实体最右侧横坐标。 |
| entity.bottomY\(\) | double | C/S | 返回实体最底部纵坐标。 |
| entity.hitbox\(\) | Hitbox | C/S | 返回实体与坐标轴对齐的碰撞箱。 |
| entity.randX\(\) | double | C/S | 返回实体横向投影上的随机横坐标。 |
| entity.randY\(\) | double | C/S | 返回实体纵向投影上的随机纵坐标。 |
| entity.angleTo\(double desX, double desY\) | double | C/S | 返回实体中心点到目标点的角度。 |
| entity.angleFrom\(double srcX, double srcY\) | double | C/S | 返回来源点到实体中心点的角度。 |
| entity.distance\(double otherX, double otherY\) | double | C/S | 返回实体中心到指定点的距离。 |
| entity.rotateAngle\(\) | double | C/S | 返回实体旋转角度。 |
| entity.setRotateAngle\(double angle\) | void | C/S | 设置实体旋转角度。 |
| entity.rotate\(double angle\) | void | C/S | 在原有角度基础上继续旋转指定角度。 |



