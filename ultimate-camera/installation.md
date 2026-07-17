---
title: Installation
category: Getting started
order: 2
---

Ultimate Camera is compatible with the following versions of Paper:
- 26.2

## Plugin

Make sure to download the latest version of Ultimate Camera from [BuiltByBit](https://builtbybit.com/resources/ultimate-camera.116877/) and place it in your server's `plugins` folder. After the first startup, Ultimate Camera will automatically generate a `config.yml` file in the `plugins/UltimateCamera` folder.

## Resource Pack

Ultimate Camera relies on a resource pack to function. Without it, cutscenes will not work properly.

The plugin will automatically attempt to apply the correct resource pack for each player who joins the server. Because the shaders which Ultimate Camera uses often change, it is important that the correct version is applied based on the player's Minecraft version.

If your server does not already have a resource pack, there is nothing else you need to do.

:::accordion What if my server already has a resource pack?

You will need to handle versioned resource packs yourself and disable the `automatic-resource-pack -> use-ultimate-camera-packs` option in the `config.yml` file.

Ultimate Camera will publish updated versions of the resource pack for each Minecraft version on [GitHub](https://github.com/seailz/ultimate-camera-packs/releases/latest) (they are also included in your BuiltByBit download), and you should make sure to update your server's resource pack whenever a new version is released by copying the `assets/minecraft/shaders/core` and `assets/minecraft/shaders/include` folders into your pack.
Make sure to download the correct version for your version of Ultimate Camera. You can find this by running `/version UltimateCamera` in-game.

If your server supports multiple Minecraft versions, you will need to provide a separate resource pack for each version and make sure that only the correct version is applied to each player. Ultimate Camera can help you do this automatically if you set `alternative-packs` in your `config.yml` for each version, including the URL and hash of the resource pack.


For the following versions:

- Versions below 26.2: Not supported by Ultimate Camera.
- 26.2.x: use the 26.2 resource pack.
:::

## Datapack

Ultimate Camera includes and automatically enables the datapack required by the plugin. You do not need to download or install it separately.

After starting the server, check the console for the message `ACC datapack loaded successfully`. If the datapack cannot be loaded, Ultimate Camera will disable itself and print an error to the console.