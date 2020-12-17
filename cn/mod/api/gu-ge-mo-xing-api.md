# 骨骼模型API

### 类成员函数

| 函数 | 返回值 | 描述 |
| :--- | :---: | :--- |
| Skeleton:FixJointAngle\(int skJointID, double angle, bool noFlip = false\) | void | 将骨骼模型关节强制旋转固定到指定角度。`skJointID`表示骨骼模型的关节ID，`angle`表示目标角度，`noFlip`表示在整个骨骼模型左右翻转时所设定的角度不会被翻转。 |
| Skeleton:FixJointToAngle\(int skJointID, double toAngle, double fixValue = 0.0625f, bool noFlip = false\) | void | 将骨骼模型关节渐进旋转到指定角度。`skJointID`表示骨骼模型的关节ID，`toAngle`表示目标角度，`fixAngle`表示单次渐进旋转角度，`noFlip`表示在整个骨骼模型左右翻转时所设定的角度不会被翻转。 |
| Skeleton:SetItemJoint\(int skJointID, ItemSlot itemSlot, int holdOffsetX = 0, int holdOffsetY = 0\) | void | 将骨骼模型物品关节绑定指定格子的物品。`skJointID`表示骨骼模型的关节ID，`itemSlot`表示待绑定的物品，`holdOffsetX`和`holdOffsetX`表示物品绑定点的偏移量。 |
| Skeleton:ClearItemJoint\(int skJointID\) | void | 清除骨骼模型物品关节绑定的物品数据。 |
| Skeleton:SetFlip\(bool flip\) | void | 决定是否将当前骨骼模型进行翻转。 |



