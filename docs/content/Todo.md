# TODO

## Camera

Having issues getting the camera to work

```
# Command
v4l2-ctl --list-devices

# Output
unicam (platform:3f801000.csi):
        /dev/video0
        /dev/media3
```

```
# Command
dmesg

# Output
unicam 3f801000.csi: Failed to start media pipeline: -22
```


## Config

Config needs a workover, Homing doesn't work at least at the moment without massive stutter


## X Endstop

I think the X Endstop has been configured for sensorless
check the klipper config


## Door Bracket

Door bracket needs reprinting, apparantly there is an issue with these easily breaking

## Calibration

Once everything is updated add in some calibration steps from my own setup
