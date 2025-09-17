# Head Board Bootloader

The head board is a BTT EBB36
This operates over the CAN bus via a USB to CAN adapter

  * https://gist.github.com/jfryman/0c3827079e23d7bc55f9677d2c6b8bec
  * https://github.com/bigtreetech/EBB
  * STM32G0B1CBT6 64MHz

## Checks

To check the CAN port is up and running
```
ifconfig can0
```

To check the existing katapult device is reachable over the CAN bus
```sh
python3 ~/katapult/scripts/flash_can.py -i can0 -q
```

## Katapult boot loader

Originally these board used to use some software called CanBoot to act as a firmware loader
this has now been renamed to Katapult

  * https://github.com/Arksine/katapult

Strictly speaking normally we shouldn't need to update this that often

To Build
```
cd ~
git clone https://github.com/Arksine/katapult
cd katapult
make menuconfig
make clean
make
```

The configuration options are

  * MCU: STM32
  * Model: STM32G0B1
  * Build Katapult deployment application: 8KiB bootloader
  * Clock Reference: 8 MHz crystal
  * Communication interface: CAN bus (on PB0/PB1)
  * Enable Status LED: check
  * Status LED GPIO Pin: PA13

TODO
I've not actually updated this on the board we have
as it's a hassle to get it into DFU mode with the switches
also the existing bootloader seems ok
