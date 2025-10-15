# Head Board Klipper Firmware

The head board is a BTT EBB36
This operates over the CAN bus via a USB to CAN adapter

  * https://gist.github.com/jfryman/0c3827079e23d7bc55f9677d2c6b8bec
  * https://github.com/bigtreetech/EBB
  * STM32G0B1CBT6 64MHz

This assumes the bootloader is working / can be reached

## Building

To build the source

```
cd ~/klipper/
# Copy the config already setup for the EBB36
cp config-ebb36 .config
# Make changes to config if needed
make menuconfig
# Do the actual build
make clean
make
```

Config Options

  * Enable extra low-level configuration options: Enabled
  * Micro-controller Architecture: STM32
  * Processor model: STM32G0B1
  * Bootloader offset: 8KiB bootloader
  * Clock Reference: 8Mhz
  * Communication interface: (CAN bus (on PB0/PB1)
  * (1000000) CAN bus speed

## Flashing the Board

```bash
# stop Klipper
sudo service klipper stop
# Get the UUID of the board
python3 ~/katapult/scripts/flashtool.py -i can0 -q
# This reports bae8d370fb76 for us
# To flash the firmware
python3 ~/katapult/scripts/flash_can.py -i can0 -f ~/klipper/out/klipper.bin -u bae8d370fb76
# To start klipper
sudo service klipper start
```
