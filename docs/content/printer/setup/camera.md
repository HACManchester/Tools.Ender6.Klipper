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

## TODO

This command works
```
rpicam-still -t 2000 -o test.jpg --width 1920 --height 1080
```

But crowsnest is having issues


unicam 3f801000.csi: Failed to start media pipeline: -22

http://172.16.0.172/webcam/?action=snapshot
http://172.16.0.172/webcam/webrtc



https://www.teamfdm.com/forums/topic/2231-crowsnest-pi-cam-with-raspi-sbc-setup-quirk


Issue seems to be webrtc on opera but not chrome?
http://172.16.0.172/webcam/webrtc

try some different options
