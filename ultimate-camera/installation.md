---
title: Installation
category: Getting started
order: 2
---

Ultimate Camera is compatible with the following versions of Paper:
- 26.3.x

## Plugin

Make sure to download the latest version of Ultimate Camera from [BuiltByBit](https://builtbybit.com/resources/ultimate-camera.116877/) and place it in your server's `plugins` folder. After the first startup, Ultimate Camera will automatically generate a `config.yml` file in the `plugins/UltimateCamera` folder.

## Resource Pack

Ultimate Camera relies on a resource pack to function.

The plugin will automatically attempt to apply the correct resource pack for each player who joins the server. Because the shaders which Ultimate Camera uses change often, it is important that the correct version is applied based on the player's Minecraft version.

If your server does not already have a resource pack, there is nothing else you need to do.

:::accordion What if my server already has a resource pack?

You will need to handle versioned resource packs yourself and disable the `automatic-packs` option in the `config.yml` file.

Ultimate Camera will publish updated versions of the resource pack for each Minecraft version on [GitHub](// todo), and you should make sure to update your server's resource pack whenever a new version is released by copying the `assets/minecraft/shaders/core` and `assets/minecraft/shaders/include` folders into your pack.

If your server supports multiple Minecraft versions, you will need to provide a separate resource pack for each version and make sure that only the correct version is applied to each player. You can use the `versioned-packs` option in the `config.yml` file to specify which resource pack should be applied for each Minecraft version.

For the following versions:

- Versions below 26.3-snapshot-3: Not supported by Ultimate Camera.
- 26.3 (and snapshots after snapshot-3): use the [`26.3-snapshot-3`](//todo) resource pack.

:::

## Datapack

Ultimate Camera includes and automatically enables the datapack required by the plugin. You do not need to download or install it separately.

After starting the server, check the console for the message `ACC datapack loaded successfully`. If the datapack cannot be loaded, Ultimate Camera will disable itself and print an error to the console.