---
title: Animations
category: API Usage
order: 4
---

## Runtime Animation

`RuntimeAnimation` is the recommended animation type when the complete path is known in advance.

```java
RuntimeAnimation animation = RuntimeAnimation.builder()
        .keyframe(first)
        .keyframe(second)
        .keyframe(third)
        .build();
```

You can then use `tryPlay` or `play` on the object depending on whether or not you would like to first validate
whether the player has installed the resource pack successfully.

### Animation Length

The client will retain 16 keyframes at once, but this is not a total limit, as Ultimate Camera reuses keyframes as the playhead passes them. Before accepting playback, Ultimate Camera verifies that the path can be uploaded quickly enough. A path with excessively dense keyframes may throw an `IllegalArgumentException`.

## Live Animation
`LiveAnimation` is intended for camera paths created while playback is already running.
A live animation needs at least two initial keyframes:
```java
LiveAnimation animation = LiveAnimation.builder()
        .keyframe(first)
        .keyframe(second)
        .build();
```

Then you can begin playback:
```java
AnimationPlayback.RequestResult result =
        animation.tryPlay(player, PlaybackOptions.DEFAULT);
```
And append future keyframes as you go:
```java
animation.append(Keyframe.builder()
        .time(Duration.ofSeconds(6))
        .xyz(10, 4, 16)
        .yawPitchRoll(80, -10, 0)
        .fov(70)
        .easing(Keyframe.Ease.SMOOTH)
        .positionSpace(Keyframe.PositionSpace.ORIGIN_RELATIVE)
        .build());
```


Appended timestamps must:
- Be in non-decreasing order
- Not precede the animation’s current final timestamp

Equal timestamps are allowed for cuts.

### Finishing
A live animation remains active when it reaches its latest available keyframe. It holds that pose and waits for more data.
Call `animation.finish();` to declare that no more keyframes will arrive. Playback will then end naturally after the final timestamp.

### Keeping ahead of the client
Keyframes must arrive before the client needs them. You can calculate the required lead you must maintain using
```java
Duration requiredLead =
        LiveAnimation.minimumLeadFor(pendingKeyframesToUpload);
```
The formula is:
```
500ms safety margin + 300ms per keyframe
```
So, you should maintain a lead of about `800ms` for 1 keyframe, `2000ms` for 5 keyframes, `3500ms` for 10, etc. This doesn't
take account for network latency, lag, or other factors (which is why the safety margin exists), so as a rule of thumb, it is
recommended to always maintain a lead of approximatley two seconds.

## Playback Options

`PlaybackOptions` controls how Ultimate Camera manages the player and animation origin during playback. For most animations, you can use the default options:

```java
animation.tryPlay(player, PlaybackOptions.DEFAULT);
```

Passing `null` as the options also uses `PlaybackOptions.DEFAULT`.

The default configuration:

- Uses the player’s rendered camera as the origin for origin-relative animations
- Fully locks the player during playback
- Does not create a mimic NPC
- Does not forward player input

Custom options can be created using the builder:

```java
PlaybackOptions options = PlaybackOptions.builder()
        .build();

animation.tryPlay(player, options);
```

### Custom Origin

When using `PositionSpace.ORIGIN_RELATIVE`, the origin normally comes from the player’s rendered camera immediately before playback begins. You can instead provide a fixed origin:

```java
Location origin = new Location(
        world,
        100,
        75,
        -40,
        90,
        -10
);

PlaybackOptions options = PlaybackOptions.builder()
        .originRelativeOrigin(origin)
        .build();

animation.tryPlay(player, options);
```

The origin’s coordinates, yaw and pitch determine where and in which direction the relative animation is placed.

### Player Mimics

A Citizens NPC can be created to represent the player during the animation. This is useful because the player cannot normally see their own body while using a first-person camera.

```java
PlaybackOptions options = PlaybackOptions.builder()
        .createMimicNpc(true)
        .build();
```

This feature requires Citizens to be installed on the server.

Player input can optionally be forwarded to the mimic:

```java
PlaybackOptions options = PlaybackOptions.builder()
        .createMimicNpc(true)
        .forwardInputToMimic(true)
        .build();
```

Input forwarding includes movement, looking, held-item changes, using items and attacking. It requires PacketEvents 2.13 or newer.

`forwardInputToMimic(true)` cannot be used unless `createMimicNpc(true)` is also enabled.

### Player Locking

Ultimate Camera currently requires the player to be fully locked during playback because it uses the physical player for render tracking. The full lock is enabled by default:

```java
PlaybackOptions options = PlaybackOptions.builder()
        .lockPlayer(PlayerLock.full())
        .build();
```

During playback, Ultimate Camera temporarily manages the player’s location, flight, visibility, collision and invulnerability. Their previous state is restored when the animation finishes or is stopped.
