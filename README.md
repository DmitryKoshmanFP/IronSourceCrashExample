# IronSourceCrashExample

This repository is only created to demonstrate an Adnroid crash case in IronSource SDK 7.4.0.

There are only a few changes in the IS SDK demo that shouldn't be the cause of the crash, but for some reason it's much easier to reproduce this bug with them.

### Added
1. Adapters.
2. TestSuite button.
3. Network Tracking.
3. Automatic loading of interstitials after sdk initialization.

You can see all the changes related to the demo script in this [diff](https://github.com/DmitryKoshmanFP/IronSourceCrashExample/compare/ef2202d74d98b6d87b97d1dcfea97a59bd8e55ce...0c28afcca4ab3b6cea5c1363ef304f99b1988481).

### Our steps to reproduce
1. Configure IronSource. (Api key, Adapters, AdMob key)
2. Build an app.
3. Install app.
4. Run other game/application to reduce device resources.
5. Turn off internet.
6. Open IS demo app.
7. Wait for a few seconds.
8. Turn on internet.

This case works for low-end devices.
In my case it is Xiaomi Redmi Note 4 (Android 7.0, 3 GB RAM).

Also judging by the crash statistics from prod application, more often appeared Xiaomi Redmi 9A device.
The crash happens in the UnityCallbackTh thread, when the SDK is trying to invoke an event from the native Android SDK implementation.

You can find all logs related to this case in the [Logs](Builds/7.4.0/Logs) folder.

APK - [IS_7.4.0.apk](Builds/7.4.0/IS_7.4.0.apk)

SYMBOLS - [IS_7.4.0-1.0-v1.symbols.zip](Builds/7.4.0/IS_7.4.0-1.0-v1.symbols.zip)

Video *click*

[![Everything Is AWESOME](https://img.youtube.com/vi/p8N6j7zsVb8/0.jpg)](https://www.youtube.com/watch?v=p8N6j7zsVb8 "IS crash 7.4.0")
