---
title: Keyframes
category: API Usage
order: 3
---
A `Keyframe` defines the complete camera position at an absolute time.
- X, Y, Z
- Yaw
- Pitch
- Roll
- FOV (the default is 70)
- Easing
- Position space

You can create keyframes with `Keyframe.builder()`.

## Time
```java
.time(Duration.ofSeconds(3))
```
Keyframe times are absolute offsets from animation activation.
For example:
- Keyframe A: 0 seconds
- Keyframe B: 2 seconds
- Keyframe C: 5 seconds

This produces:
- A → B over 2 seconds
- B → C over 3 seconds

Make sure your first keyframe is at `Duration.ZERO`. A nonzero timestamp on that keyframe will not delay its activation. Ultimate Camera
supports precision of `0.01` seconds, and each individual gap between keyframes has a maximum of `655.35 seconds`. The complete animation,
however, can be much longer. If you want to represent a jump cut, create two keyframes in sequence with the same timestamp.

## Position
Position values are rounded to the nearest 1/16 block and must be between `-2048` and `2047.9375` inclusive. The meaning of the coordinates depends on the selected position space.
## Orientation
Yaw and pitch must be between `-180` and `180` degrees, and are rounded to the nearest `2` degrees.

Roll is rounded to the nearest `2` degrees, but may represent multiple revolutions. For example,
```java
.roll(720)
```
requests two complete revolutions. Ultimate Camera will automatically divide the extended roll into more keyframes when the animation runs.
This will increase the effective keyframe count and upload time. 

Ordinary angular interpolation takes the shortest route. If you require a particular yaw or pitch rotation direction, add intermediate keyframes before crossing 180 degrees.

## FOV
FOV must be between 1 and 170 degrees.
Examples:
- 30: strongly zoomed in
- 70: approximately normal
- 100: wide
- 150: extremely wide

If you go wider than the client's set FOV, you should expect graphical issues with terrain. So, wide FOVs are discouraged.

## Easing and position spaces
For info on how easing and position spaces work, see [Cutscenes](/docs/ultimate-camera/cutscenes).