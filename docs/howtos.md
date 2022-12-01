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

## Dockers on VOXL

### Switching the Docker Directory to the SD Card

Follow the instructions in [this guide](https://docs.modalai.com/docker-on-voxl/#move-docker-image-from-data-to-mntsdcard). But you can also follow the instructions below.

1. Format the microSD card using the `ext4` format, and insert the SD card into the drone.
2. Log into the drone.
3. Open the file `docker-daemon.service`.
```
vi /etc/systemd/system/docker-daemon.service
```
4. Change the line starting with `ExecStart` to `ExecStart=/usr/bin/docker daemon -g /mnt/sdcard`.
5. Restart the docker service using the following command and run additional commands that follow.
```
systemctl restart docker-daemon.service
```
6. Delete the previous directories:
```
cd /data
rm -rf containers linkgraph.db overlay tmp volumes graph network repositories-overlay trust
```
7. Reconfigure docker on VOXL:
```
voxl-configure-docker-support.sh
```

### Building a Dockerfile

Use the following command to build a dockerfile on VOXL:
```
docker build -t <name:tag> -f <dockerfile> .
```
The name and tag combo can be something like `focal:barebones`, meaning this dockerfile was derived from Ubuntu Focal and it installs the barebone packages needed for your project.
