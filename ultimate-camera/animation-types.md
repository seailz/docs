---
title: Animation Types
category: API Usage
order: 5
---


Ultimate Camera has two types of animations available in the API:

- **Runtime Animations**: These contain the complete keyframe path from before the animation starts. Ultimate Camera uploads a few keyframes to start, then continues uploading keyframes while the animation runs. These can contain essentially unlimited keyframes.
- **Live Animations**: These work similarly to Runtime Animations. They require you to upload at least two keyframes to start, but you can upload new keyframes in real time while the animation is running. This is useful for paths generated from dynamic data, but you must upload keyframes slightly in advance to stay ahead of the client. Call `finish()` when no more keyframes will be added.

In most cases, you'll want to build a `RuntimeAnimation` then use `tryPlay(...)` or `play(...)` to begin it for the player. Use `LiveAnimation` only when the full keyframes are not known in advance.
