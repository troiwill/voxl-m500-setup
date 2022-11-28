Quick How-To Guide
===

This guide provides a set of quick how-to's to use the drone.

## Connecting with the Drone

### Connect via USB

Run the following commands to connect to the drone via USB:
```
# First run:
adb shell

# Then run:
bash
```

### Connect via Wi-Fi

Ensure the drone is in `station mode` and is connected to the Wi-Fi. Then determine the drone's IP address via `adb shell`. Finally, remote log into the drone via `ssh`:
```
ssh root@<drone IP address>
```

## Networking

### Connect the Drone to an Existing Wi-Fi

Use the `adb shell` to log into the drone. Then run the command:
```
voxl-wifi station <ssid> <password>
```
Then run `ifconfig` a few seconds afterward to ensure the drone has an IP address for its wireless interface (usually called `wlan0`).