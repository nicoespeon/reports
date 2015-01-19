# CodeFest Intel (FR/EN)

Tour d'horizon sur le XDK d'Intel pour développer des applications cross-platform.

## Why HTML5 on mobile?

Common base to all mobile OS.
Possibility to deploy one app on multiple OS.
Large community.

Problem of performance and compatibility.
Issue with distribution.

## Native vs. Hybrid

Hybride = appli native + couche HTML5 (web view) qui va être chargée dans l'application pour la distribuer nativement.

## XDK is...

... a set of tools:

- Code editor
- App designor
- Emulator
- Debugger
- Packager

... a set of APIs:

- Cordova
- AppFramework
- XDK
- AppMobi

... based on well-known tools:

- Brackets
- Ripple
- Chrome debug tools
- Cordova

## XDK Tools

Can emulate, debug and profile almost everything (geolocation, acceleration, network, etc.).

We have access to the Chrome DevTools directly with the emulation. We alse can still working on our HTML5 project with ST2 and our own workflow, just using the XDK to debug and build for mobile supports.

Then, we can build our application for a bunch of supports.

We can use the App Preview to upload code in the cloud and run demos on our own device.

## XDK APIs

1. Add `<script src="intelxdk.js" />`
2. Wait for `intel.xdk.device.ready`
3. Have fun with object `intel.xdk`

This is a JavaScript API which covers a lot of native stuff:

- Accelerometer
- Cache
- Cameras
- OAuth
- ...

Example to use the camera to take a picture:

    intel.xdk.camera.takePicture(50, false, "jpg");

    document.addEventListener("xdk.intel.camera.picture.add", function(event) {
      var imgUrl = intel.xdk.camera.getPictureUrl(event.filename);
      document.getElementById("picturePlace").url = imgUrl;
    });

That's almost straightforward JavaScript!

The `App.Framework` can replace `jQuery UI` (just in case). Its far more powerful for building hybrid apps.
