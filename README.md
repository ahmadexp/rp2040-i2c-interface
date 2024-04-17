# I2C interface

Modified to work with the SparkFun Pro Micro - RP2040

This RP2040 firmware implements the USB protocol expected by the I2C-Tiny-USB kernel driver, allowing the use of a Raspberry Pi Pico as USB to I2C adapter.

The original I2C-Tiny-USB project can be found at https://github.com/harbaum/I2C-Tiny-USB, this firmware is a complete re-implementation of the firmware for use with the RP2040.

More testing is needed to verify that the firmware works correctly, this project currently has proof of concept status.

## Pinout

for Generic RP2040
* I2C1
* SDA (i2c data): GPIO 2
* SCL (i2c clock): GPIO 3

for Sparkfun
* I2C0
* SDA (i2c data): GPIO 16
* SCL (i2c clock): GPIO 17

for Adafruit KB2040
* I2C0
* SDA (i2c data): GPIO 12
* SCL (i2c clock): GPIO 13

## Installation:

Make sure you have a clone of the PICO_SDK
https://github.com/raspberrypi/pico-sdk
```
cd ~
git clone https://github.com/raspberrypi/pico-sdk.git
git submodule update --init
```

clone this repo
```
cd ~
git clone https://github.com/ahmadexp/rp2040-i2c-interface.git
```

make sure you apply the necessary changes based on your board on the CMakeLists.txt file and main.c
For the CMakeLists.txt should specify the board and on the main.c you should select the right pins for SDA, SCL and the i2c device (0 or 1).

create a build folder, link the pico-sdk and run cmake from it
```
cd ~
cd rp2040-i2c-interface
mkdir build
cd build
export PICO_SDK_PATH=~/pico-sdk
cmake ..
```

build

```
make
```

copy the i2c_adapter.uf2 file to your RP2040 by dropping it on the drive it shows when turning it on by holding the boot button.

