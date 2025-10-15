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

## Other Tests

This command works
```
rpicam-still -t 2000 -o test.jpg --width 1920 --height 1080
```

Also should be visible under

  * http://172.16.0.172/webcam/webrtc
