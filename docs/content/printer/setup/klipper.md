# Klipper Setup

## GUI URLs

  * http://192.168.111.71 - Mainsail (default)
  * http://192.168.111.71:81 - fluidd

Moonraker is the python web API that these front ends can connect to


## RPI Setup

First setup an SD card image with MainsailOS
Using Rpi Imager

  * https://github.com/raspberrypi/rpi-imager

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
