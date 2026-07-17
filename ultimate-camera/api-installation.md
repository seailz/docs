---
title: API Installation
category: API Usage
order: 1
---

Once you've installed Ultimate Camera, you can start using the API to create cutscenes programmatically in your own plugin. It's included in the Ultimate Camera plugin, so you don't need to install it separately.

The API provides:
- Three dimensional camera movement
- Yaw, pitch, and roll control
- Animated FOV/zoom
- Multiple easing curves
- World-space and origin-relative animations
- Predefined and dynamically generated animation paths (so you don't need to send all keyframes in advance)
- Optional Citizens player mimics
- Safe playback lifecycle and resource-pack checking

## Maven

Add the following to your `pom.xml` file. **Do not package or shade Ultimate Camera into your plugin.**

```xml
    <dependency>
        <groupId>com.seailz</groupId>
        <artifactId>advanced-camera-control</artifactId>
        <version>1.0.0</version>
        <scope>provided</scope>
    </dependency>
```

There is not a public Maven repository for Ultimate Camera, so you will need to install it into your local repoistory.

```shell
mvn install:install-file -Dfile="C:\path\to\UltimateCamera.jar" -DgroupId=com.seailz -DartifactId=advanced-camera-control -Dversion=1.0.0 -Dpackaging=jar
```

## plugin.yml
If you're using `paper-plugin.yml`, include the following:
```yaml
dependencies:
  server:
    UltimateCamera:
      load: BEFORE
      required: true
      join-classpath: true
```
Or if you're using `plugin.yml`, include the following:
```yaml
depend: [UltimateCamera]
```
