Calibrating Sensors on the VOXL Drone
===

This guide specifies the tools you need to calibrate sensors on a MODAL AI VOXL drone. Please note this setup guide was designed for an `m500` drone with a `VOXL Flight` onboard computer.

## Calibrating the Monocular Tracking Camera

The monocular tracking camera is the downward-facing (45-degree) camera. We will follow the `Calibrate Cameras` guide on the Modal AI website ([instructions here](https://docs.modalai.com/calibrate-cameras/)).

### Before you calibrate

1. Ensure you need the following items:

    - Installed on the drone:
        - VOXL Camera Calibration tool: `voxl-calibrate-camera`
        - VOXL Web Portal tool: `voxl-portal`

    - Printed checkboard pattern ([found here](/assets/images/camera_calib/checkboard.png))

2. Ensure the `adb` tool is installed on your computer. See the `Android Emulator` [instructions here](/docs/prereqs.md) if it is not installed.

3. Ensure the VOXL camera calibration tool is installed. You can install this tool using this command:
```
opkg install voxl-camera-calibration
```

4. Measure the side length of one of the square. Make sure your measurement is accurate as possible. Remember the side length in `meters`.

5. Fix the checkerboard pattern to a flat surface (such as a cardboard box).

6. Ensure your computer is on the same network as the drone (see [instructions here](/docs/howtos.md)).

7. Remove the removal plastic tube footing from the front of the drone. The front feet may get in the way when calibrating the camera.

### Calibrating the camera

1. Use the `adb` tool to log into the drone and start the `web-portal`. Ensure you are on the same network as the drone.
```
voxl-portal
```

2. Run the camera calibration command with the appropriate arguments:
```
voxl-calibrate-camera --fisheye --size <rows>x<columns> --length <sideLength> 
```

3. Go to the `Camera Calibrator Overlay` webpage via the `VOXL Web Portal` under the `Cameras` menu.

4. Use the checkboard to calibrate the camera.

    - Place the checkerboard pattern within the red box in the overlay. You should see rainbow colors across the checkboard (for example, [as seen here](https://docs.modalai.com/images/voxl-sdk/camera-calibration/tracking-cal.jpg)).
    - Move the checkboard within the red box until the box changes from red to green. Once the box turns green, the Total Collected status should increase by 25% and the box should move to another section of the overlay.
    - Repeat the two steps above until the Total Collected is 100%. Once finished, you should see a [Finished Sampling, Running Calibration](/assets/images/camera_calib/camera_calibrator_overlay_done.jpeg) status image display on your overlay.
    - Check your terminal for the camera intrinsic calibration matrix. The matrix should also be saved at the following location:
    `/data/modalai/opencv_tracking_intrinsics.yml`.