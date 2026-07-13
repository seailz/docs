---
title: Installation
category: Getting started
order: 2
---

Ultimate Camera is compatible with the following versions of Minecraft Java:
- 26.3.x

## Plugin

Make sure to download the latest version of Ultimate Camera from [BuiltByBit](https://builtbybit.com/resources/ultimate-camera.116877/) and place it in your server's `plugins` folder. Once the server is started, Ultimate Camera will automatically generate a `config.yml` file in the `plugins/UltimateCamera` folder.

## Resource Pack

Ultimate Camera relies on a resource pack to function.

Ultimate Camera will automatically attempt to apply the correct resource pack for each player who joins the server. Because the shaders which Ultimate Camera uses change often, it is important that the correct version is applied based on the player's Minecraft version.

:::accordion What if my server already has a resource pack?

You will need to handle versioned resource packs yourself and disable the `automatic-packs` option in the `config.yml` file.

Ultimate Camera will publish updated versions of the resource pack for each Minecraft version on [GitHub](// todo), and you should make sure to update your server's resource pack whenever a new version is released by copying the `assets/minecraft/shaders/core` and `assets/minecraft/shaders/include` foldersi nto your pack.

:::

## Datapack

Ultimate Camera automatically applies a datapack to the server which is required for the plugin to function. This is packaged with the plugin.
