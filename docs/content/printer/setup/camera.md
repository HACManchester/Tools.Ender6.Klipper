# Camera Setup

Currently we're using a ov5647 camera attached to the CSI port of the Rpi
Make sure to add the following to the /boot/firmware/config.txt file
```
camera_auto_detect=0
dtoverlay=ov5647
```

## Listing Cameras

To list the attached cameras
```
# install the camera apps for testing
apt install libcamera-apps
# List Cameras
rpicam-hello --list-cameras
v4l2-ctl --list-devices
```

## Opera Browser Fix

For some reason the opera browser can have issues viewing the video stream

  * Browse to opera://settings/?search=WebRTC
  * Select "Use any suitable network interface (recommended)"
    (instead of Disable non-proxied UDP)

## Mainsail setup

The settings to use for mainsail

  * Name: MainCam
  * URL Stream: /webcam/webrtc
  * URL Snapshot: /webcam/?action=snapshot
  * Service: WebRTC (camera-streamer)

## Crowsnest Setup

The available resolutions / max fps are

  * 640x480 58.92 Fps
  * 1296x972 46.34fps
  * 1920x1080 32.81 fps
  * 2592x1944 15.63 fps

```ini
[crowsnest]
log_path: /home/hacman/printer_data/logs/crowsnest.log
log_level: verbose                      # Valid Options are quiet/verbose/debug
delete_log: true                        # Deletes log on every restart, if set to true
no_proxy: false

[cam 1]
mode: camera-streamer                   # ustreamer - Provides mjpg and snapshots. (All devices)
                                        # camera-streamer - Provides webrtc, mjpg and snapshots. (rpi + Raspi OS based only)
enable_rtsp: true                       # If camera-streamer is used, this enables also usage of an rtsp server
rtsp_port: 8554                         # Set different ports for each device!
port: 8080                              # HTTP/MJPG Stream/Snapshot Port
device: /base/soc/i2c0mux/i2c@1/ov5647@36

# widthxheight format
#resolution: 640x480
resolution: 1296x972
# resolution: 1920x1080
# resolution: 2592x1944

# If Hardware Supports this it will be forced, otherwise ignored/coerced.
max_fps: 15
max_fps: 30
#custom_flags:                          # You can run the Stream Services with custom flags.
v4l2ctl: AfMode=2                       # Add v4l2-ctl parameters to setup your camera, see Log what your cam is capable of.
```

## Other Tests

This command works
```
rpicam-still -t 2000 -o test.jpg --width 1920 --height 1080
```

Also should be visible under

  * http://172.16.0.172/webcam/webrtc
