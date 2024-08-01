# Camera Helper Documentation
Author: https://gist.github.com/kasuganosoras
Example Code: https://gist.github.com/kasuganosoras/006a2441ba35981697ba65914547ca4d

## Introduction
This Camera Helper script provides several utility functions to interact with the game camera in RedM. These functions allow you to get the camera's position and rotation, convert between different coordinate systems, and perform raycasting from the camera to detect entities.

## License
```
Copyright 2022 ZeroDream
Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:
The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.
THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
```

## Functions

### `CameraHelper.GetPosition()`
Returns the current position of the gameplay camera as a vector3.

**Usage:**
```lua
local cameraPosition = CameraHelper.GetPosition()
```

### `CameraHelper.GetRotation(unk)`
Returns the current rotation of the gameplay camera. The `unk` parameter is an unknown parameter, typically set to 2.

**Usage:**
```lua
local cameraRotation = CameraHelper.GetRotation(2)
```

### `CameraHelper.DegToRad(degs)`
Converts degrees to radians.

**Parameters:**
- `degs`: The angle in degrees.

**Returns:**
- The angle in radians.

**Usage:**
```lua
local radians = CameraHelper.DegToRad(90)
```

### `CameraHelper.RotationToDirection(rotation)`
Converts a rotation vector to a direction vector.

**Parameters:**
- `rotation`: The rotation vector.

**Returns:**
- The direction vector.

**Usage:**
```lua
local direction = CameraHelper.RotationToDirection(rotation)
```

### `CameraHelper.WorldToScreenRel(worldCoords)`
Converts world coordinates to screen relative coordinates.

**Parameters:**
- `worldCoords`: The world coordinates as a vector3.

**Returns:**
- A boolean indicating success, and the screen relative x and y coordinates.

**Usage:**
```lua
local success, screenX, screenY = CameraHelper.WorldToScreenRel(worldCoords)
```

### `CameraHelper.ScreenToWorld(giveX, giveY)`
Converts screen coordinates to world coordinates.

**Parameters:**
- `giveX`: The screen X coordinate.
- `giveY`: The screen Y coordinate.

**Returns:**
- The world coordinates as a vector3.

**Usage:**
```lua
local worldCoords = CameraHelper.ScreenToWorld(0.5, 0.5)
```

### `CameraHelper.RaycastForEntity(screenCoord, ignoreEntity, maxDistance)`
Performs a raycast from the screen position to detect entities.

**Parameters:**
- `screenCoord`: The screen coordinates as a vector2.
- `ignoreEntity`: The entity to ignore (e.g., the player).
- `maxDistance`: The maximum distance for the raycast.

**Returns:**
- The entity detected by the raycast.

**Usage:**
```lua
local entity = CameraHelper.RaycastForEntity(vec2(0.5, 0.5), PlayerPedId(), 10.0)
print(entity)
```

## Example
The following example demonstrates how to use the `RaycastForEntity` function to get the entity in the middle of the screen:

```lua
local entity = CameraHelper.RaycastForEntity(
  vec2(0.5, 0.5), -- Screen position vector2
  PlayerPedId(),  -- Ignore self
  10.0            -- Max distance
)
-- Print entity id
print(entity)
```

This function will return the entity ID of the entity in the middle of the screen within a 10 unit distance, ignoring the player entity.
