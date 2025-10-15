# TODO

## Can Bus

The Can Bus is not coming up automatically
```
sudo systemctl status systemd-networkd
can0: Failed to set CAN interface configurations: Device doesn't support restart from Bus Off. Operation not supported
```

To start now
```
sudo service klipper stop
sudo ip link set up can0
sudo service klipper start
```
kernel version is 6.12.47 - could this be related https://lkml.rescloud.iu.edu/2507.2/00068.html

```
sudo systemctl disable klipper
sudo systemctl enable klipper
```


## Camera

For the camera I've commented out
`camera_auto_detect=1`
Under `/boot/firmware/config.txt`

This has stopped the spam under dmesg, but I need to check the camera still works under Klipper


## X Endstop

I think the X Endstop has been configured for sensorless
check the klipper config


## Door Bracket

Door bracket needs reprinting, apparantly there is an issue with these easily breaking

## Calibration

Once everything is updated add in some calibration steps from my own setup
