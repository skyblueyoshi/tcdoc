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
| entity.applyUserInt\(\) | int | C/S | 申请一个用户自定义的整型数据，初始值为0，返回指向该数据的索引。 |
| entity.applyUserDouble\(\) | int | C/S | 申请一个用户自定义的浮点型数据，初始值为0.0，返回指向该数据的索引。 |
| entity.applyUserBool\(\) | int | C/S | 申请一个用户自定义的布尔型数据，初始值为false，返回指向该数据的索引。 |
| entity.userInt\(int index\) | int | C/S | 根据索引index返回用户自定义整型数据，若索引无效或指向的数据不是整型数据，返回0。 |
| entity.userDouble\(int index\) | double | C/S | 根据索引index返回用户自定义浮点型数据，若索引无效或指向的数据不是浮点型数据，返回0.0。 |
| entity.userBool\(int index\) | bool | C/S | 根据索引index返回用户自定义布尔型数据，若索引无效或指向的数据不是布尔型数据，返回false。 |
| entity.setUserInt\(int index, int value\) | bool | C/S | 根据索引index设置用户自定义整型数据，若设置成功返回true，若索引无效或指向的数据不是整型数据，返回false。 |
| entity.setUserDouble\(int index, double value\) | bool | C/S | 根据索引index设置用户自定义浮点型数据，若设置成功返回true，若索引无效或指向的数据不是浮点型数据，返回false。 |
| entity.setUserBool\(int index, bool value\) | bool | C/S | 根据索引index设置用户自定义布尔型数据，若设置成功返回true，若索引无效或指向的数据不是布尔型数据，返回false。 |
|  |  |  |  |
|  |  |  |  |
|  |  |  |  |
|  |  |  |  |



