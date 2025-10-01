# TODO

## Can Bus

After upgrading to a new mainsailos / klipper there are two things to look at
First the USB Can bus is not coming up automatically when called from systemd-networkd on bootup
```
sudo systemctl status systemd-networkd
can0: Failed to set CAN interface configurations: Device doesn't support restart from Bus Off. Operation not supported
```

Currently I have to startup the can bus manually with `sudo ip link set up can0`
kernel version is 6.12.47 - could this be related https://lkml.rescloud.iu.edu/2507.2/00068.html


## Main Controller

I think one of the USB sockets on the Pi3 is causing issues when used (board crashout)
mention to only use ones in the picture
Update - nope still crashes, try a pi4

To start now
```
sudo ip link set up can0
sudo service klipper start
```


## Camera

For the camera I've commented out
`camera_auto_detect=1`
Under `/boot/firmware/config.txt`

This has stopped the spam under dmesg, but I need to check the camera still works under Klipper



## X Endstop

I think the X Endstop has been configured for sensorless
check the klipper config

## Shutdown

Currently the shutdown button is missing on klipperscreen to cleanly shutdown the pi

## Updates

Need to check on compiling klipper for the different control boards / hardware
and add in any plugins from my own setup

## Door Bracket

Door bracket needs reprinting, apparantly there is an issue with these easily breaking

## Calibration

Once everything is updated add in some calibration steps from my own setup
