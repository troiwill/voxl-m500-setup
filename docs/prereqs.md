Setup for the Modal AI VOXL Drone
===

This guide specifies the tools you need to install to work with a MODAL AI VOXL drone. Please note this setup guide was designed for an `m500` drone with a `VOXL Flight` onboard computer.

## Installing Android Emulator

We need to install the Android emulator command line tools to use the `Android Debug Bridge (ADB) tool` on a host computer. Follow the instructions for your respective host computer:

- For an Apple Mac with an M1 chip, use [these instructions](https://bajtos.net/posts/2021-12-17-apple-m1-android-emulator/). Do the following sections:

    1. Install Java runtime.
    2. Install Android SDK. You can find the command line tools [here](https://developer.android.com/studio).
    3. Install `platform-tools` which contains interfaces such as `adb` and `fastboot`. To install `platform-tools`, run `sdkmanager "platform-tools"` in the terminal.

- For a PC running Ubuntu, use [these instructions](https://docs.modalai.com/setup-adb/). Run the commands under `Host Computer Setup`.
