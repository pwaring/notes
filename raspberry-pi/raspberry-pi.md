# Raspberry Pi

## Models

Two models available, similar except the Model B has an extra USB socket, an Ethernet socket, and 512MB of RAM.

## Architecture

The Pi contains a single BCM2835 processor, based on the ARM11 processor design and using the ARMv6 instruction set (incompatible with ARMv7, used in the ARM Cortex set of processors).

## USB

USB devices draw power, which can affect performance. If this is an issue, use a powered USB hub instead.

## Installation

Download latest Raspbian image from: http://www.raspberrypi.org/downloads

Copy using the following command:

```
sudo if=wheezy-raspbian.img of=/dev/sdX bs=2M
```

Replace `/dev/sdX` with the device name of the SD card, e.g. `/dev/sdb`. Check this before running `dd`, as using the wrong device name may result in your main disk being wiped. The command may take several minutes to complete.
