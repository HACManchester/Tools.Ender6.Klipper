# Mainboard Updates

The main control board is a BTT SKR Mini E3 V3.0 located underneath the printer

  * https://docs.vorondesign.com/build/software/miniE3_v30_klipper.html

## Build

The configuration should be stored within `config-mainboard`  
This is taken from the above weblink  
To start the build
```
cd ~/klipper/
cp config-mainboard .config
make clean
make
```

The built firmware ends up in `/home/pi/klipper/out/klipper.bin`

## Flashing the Firmware

To get a list of attached usb devices that match the main control board
```
ls /dev/serial/by-id/*
```

To Flash the main board
```
# Stop Klipper
sudo service klipper stop
# Try to flash via the USB ID
make flash FLASH_DEVICE=/dev/serial/by-id/usb-Klipper_stm32g0b1xx_180049001450415833323520-if00
# The flashing might complain afterwards but it's probably run fine.
# If this fails try and flash via the USB number ID
make flash FLASH_DEVICE=0483:df11
# Restart klipper
sudo service klipper start
```

Check if the device can be reached
```sh
cd ~/klipper
~/klippy-env/bin/python3 ./klippy/console.py /dev/serial/by-id/usb-Klipper_stm32g0b1xx_180049001450415833323520-if00
```

This should show something like the following

```sh
==================== attempting to connect ====================
INFO:root:Starting serial connect
Loaded 130 commands (v0.12.0-404-g80d185c94 / gcc: (15:8-2019-q3-1+b1) 8.3.1 20190703 (release) [gcc-8-branch revision 273027] binutils: (2.35.2-2+14+b2) 2.35.2)
MCU config: ADC_MAX=4095 BUS_PINS_i2c1=PB6,PB7 BUS_PINS_i2c1a=PB8,PB9 BUS_PINS_i2c2=PB10,PB11 BUS_PINS_i2c3=PA8,PC9 BUS_PINS_sdio=PC12,PD2,PC8,PC9,PC10,PC11 BUS_PINS_spi1=PA6,PA7,PA5 BUS_PINS_spi1a=PB4,PB5,PB3 BUS_PINS_spi2=PB14,PB15,PB13 BUS_PINS_spi2a=PC2,PC3,PB10 BUS_PINS_spi3=PB4,PB5,PB3 BUS_PINS_spi3a=PC11,PC12,PC10 BUS_PINS_spi4=PE13,PE14,PE12 CLOCK_FREQ=180000000 INITIAL_PINS=PE1 MCU=stm32f446xx PWM_MAX=255 RESERVE_PINS_USB=PA11,PA12 RESERVE_PINS_crystal=PH0,PH1 STATS_SUMSQ_BASE=256 STEPPER_BOTH_EDGE=1
====================       connected       ====================
001.941: stats count=331 sum=421677 sumsq=3123766
006.941: stats count=61 sum=34937 sumsq=114331
011.941: stats count=61 sum=34778 sumsq=112299
016.941: stats count=61 sum=34775 sumsq=112267
021.941: stats count=61 sum=34775 sumsq=112267
```

Restart klipper
```
sudo service klipper start
```
