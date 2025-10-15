# Klipper Setup

## GUI URLs

  * http://192.168.111.71 - Mainsail (default)
  * http://192.168.111.71:81 - fluidd

Moonraker is the python web API that these front ends can connect to

## RPI Setup

First setup an SD card image with MainsailOS
Using Rpi Imager

  * https://github.com/raspberrypi/rpi-imager

## RPI3 USB Fix

In the case of the RPI3 there's an option we need to add to the boot config
otherwise traffic over the USB Bus to the control cards will cause the Pi to lock up

Add the following line to `/boot/firmware/config.txt`
```bash
dtoverlay=dwc2
```

## USB to Can Adapter Fix

With the default setup there can be an issue getting the USB-Can Adapter to work
In that it fails to come up on a reboot, to fix this

within the file `nano /etc/systemd/network/25-can.network`  
comment out the line starting with RestartSec
```
[CAN]
BitRate=1M
# RestartSec=0.1s
```

## KAuth Setup

Next we're going to install KAuth for updating and managing klipper

  * https://github.com/dw-0/kiauh

Download kiauth
```sh
sudo apt-get update && sudo apt-get install git -y
cd ~ && git clone https://github.com/dw-0/kiauh.git
```

When launching kauth it will auto prompt for updates if there are any
If asked about version 6, say yes for the latest

```sh
./kiauh/kiauh.sh
```

## KAuth Setup

Install the following

Main Install Options:
  * Fluidd - alternative interface
  * Crowsnest

Extensions:
  * G-Code Shell Command
    This should provide an example - shell_command.cfg
    For setting up a macro to run shell commands
