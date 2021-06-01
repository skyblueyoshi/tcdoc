# Entity

## Entity Class

The Entity class represents an object with basic properties related to graphics and collision detection.

### Member

#### Coordinates and Graphics Member 

_note: all members read only when the entity is a player._

| Member | Type | Description |
| :--- | :---: | :--- |
| Entity.x | double | The x coordinate of the upper left corner of the entity. |
| Entity.y | double | The y coordinate of the upper left corner of the entity. |
| Entity.centerX | double | **\[ Read-only \]** Returns the center x coordinate of the entity. |
| Entity.centerY | double | **\[ Read-only \]** Returns the center y coordinate of the entity. |
| Entity.centerXi | int | **\[ Read-only \]** Returns the center grid x index of the entity. |
| Entity.centerYi | int | **\[ Read-only \]** Returns the center grid y index of the entity. |
| Entity.rightX | double | **\[ Read-only \]** Returns the x coordinate of the right border of entity. |
| Entity.bottomY | double | **\[ Read-only \]** Returns the y coordinate of the bottom border of entity. |
| Entity.speedX | double | The horizontal speed of the entity. |
| Entity.speedY | double | The vertical speed of the entity. |
| Entity.gravity | double | The gravitational acceleration of the entity. |
| Entity.width | int | **\[ Read-only \]** Returns the width of the hitbox. |
| Entity.height | int | **\[ Read-only \]** Returns the height of the hitbox. |
| Entity.direction | bool | Facing right if true, otherwise facing left. |
| Entity.rotateAngle | double | The rotation angle of the hitbox. |
| Entity.speedAngle | double | **\[ Read-only \]** Returns the vector angle of the current speed. |
| Entity.randX | double | **\[ Read-only \]** Return the random coordinates of the entity on the x-axis projection. |
| Entity.randY | double | **\[ Read-only \]** Return the random coordinates of the entity on the y-axis projection. |
| Entity.shape | Shape | **\[ Read-only \]** Returns the shape of the hitbox. |

#### Collision Member

_note: all members read only when the entity is a player._

| Member | Type | Description |
| :--- | :---: | :--- |
| Entity.stand | bool | **\[ Read-only \]** Returns whether the entity is standing. |
| Entity.isCollisionTop | bool | **\[ Read-only \]** Returns whether the top of the entity collides with the map. |
| Entity.isCollisionLeft | bool | **\[ Read-only \]** Returns whether the left of the entity collides with the map. |
| Entity.isCollisionRight | bool | **\[ Read-only \]** Returns whether the right of the entity collides with the map. |
| Entity.isCollisionStuck | bool | **\[ Read-only \]** Returns whether the entity is stuck inside the block. |
| Entity.isNoCollision | bool | **\[ Read-only \]** Returns whether the entity has not collided in any form. |
| Entity.onSlope | bool | **\[ Read-only \]** Returns whether the entity is standing on the slope. |
| Entity.hitbox | Hitbox | **\[ Read-only \]** If the entity is an axis-aligned rectangle, returns an axis-aligned hitbox, otherwise returns a rotating rectangular collision box. |
| Entity.aabb | Hitbox | **\[ Read-only \]** The axis-aligned hitbox when rotation angle is 0. |
| Entity.minAABB | Hitbox | **\[ Read-only \]** The smallest axis-aligned hitbox that completely wraps the entity. |
| Entity.allowCheckCollision | bool | Decide whether to check collision detection with the map. |

#### Rendering Related Member

_note: all members read only when the entity is a player._

| Member | Type | Description |
| :--- | :---: | :--- |
| Entity.spriteDefaultWidth | int | **\[ Read-only \]** The default drawing width of the entity. |
| Entity.spriteDefaultHeight | int | **\[ Read-only \]** The default drawing height of the entity. |
| Entity.spriteRect | Rectangle | Represents the clipping area of the target texture when the entity is drawn. |
| Entity.spriteEx | SpriteEx | Sprite extension information when the entity is drawn. |
| Entity.spriteOffsetX | int | \[ default `0.0` \] The horizontal offset of the entity drawing. |
| Entity.spriteOffsetY | int | \[ default `0.0` \] The vertical offset of the entity drawing. |
| Entity.color | Color | \[ default `COLOR_WHITE` \] The color of the entity when it is drawn. |
| Entity.frameTickTime | int | The frame timer for entity drawing, increments by 1 every update tick. |
| Entity.frameIndex | int | **\[ Read-only \]** The frame index. Which is `(frameTickTime / frameSpeed) % frames` in C++. |
| Entity.frameStyles | int | **\[ Read-only \]** The total of entity frame styles. |
| Entity.frames | int | **\[ Read-only \]** The total of entity frames in one loop. |
| Entity.frameSpeed | int | **\[ Read-only \]** How many ticks to switch frames. |

#### Other Member

| Member | Type | Description |
| :--- | :---: | :--- |
| Entity.tickTime | int | **\[ Read-only \]** The actual survival time of the entity, increments by 1 every update tick when survival. |
| Entity.randSeed | int | **\[ Read-only \]** The random seed of current entity. |

### Member Function

| Function | Returns | Description |
| :--- | :---: | :--- |
| Entity:SetCenterX\(double newCenterX\) | void | Set the x coordinate of the center of the entity. |
| Entity:SetCenterY\(double newCenterY\) | void | Set the y coordinate of the center of the entity. |
| Entity:GetAngleTo\(double desX, double desY\) | double | Returns the angle from the center point of the entity to the target point. |
| Entity:GetAngleFrom\(double srcX, double srcY\) | double | Returns the angle from the source point to the center point of the entity. |
| Entity:GetDistance\(double otherX, double otherY\) | double | Returns the distance from the center of the entity to the specified point. |
| Entity:Rotate\(double angle\) | void | Continue to rotate the specified angle based on the original angle. |
| Entity:RotateSpeed\(double angle\) | void | Continue to rotate the specified speed angle based on the original speed angle. |

