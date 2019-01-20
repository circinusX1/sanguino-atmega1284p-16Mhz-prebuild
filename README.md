===Prusa  A/B (metal/aluminium)===

==prebuild folder has prebuild images==

I am not maintaing this repo. I just put here what worked for me.
This worked for this board.


https://www.geeetech.com/geeetech-prusa-i3-aluminum-diy-3d-printer-only-accept-order-fr-p-944.html
http://domoticx.com/mechanica-hardware-sanguinololu-board/

This worked for me with arduino 1.8.7 Latest Marlin cloned Jan-20 2019
With coinfig from configs examples Prusa I3 / B configuration file.

Though the sensors and steps were not yet configured.
The bootloader and fuses were flashed with:

I bootloader-it with usbasp i2c programmer hooked on the small 9 pin's LCD pins.
I use a standard LCD text based the I8 dyo is shipped with.

Flashed the bootloader

    avrdude -v -patmega1284P -cusbasp-clone -U flash:w:./ATmegaBOOT_168_atmega1284p.hex
    avrdude -p atmega1284p -c usbtiny -b 19200 -V -e -U lfuse:w:0xD6:m -U hfuse:w:0xDA:m -U efuse:w:0xFD:m -U flash:w:ATmegaBOOT_168_atmega1284p.hex:i


On arduino Ide I added the json boards definition from: https://github.com/Lauszus/Sanguino
I selected Board Sanguino, Prosessor 1284P 16 Mhz

The boards.txt  (see where arduino puts this frm your installation. Mine keeps going in ~/.arduino15)
    <home/user>/.arduino15/packages/Sanguino/hardware/avr/1.0.2/boards.txt
has following content

Then 
 - the programmer I used is either USBTinyISP or AVRISP mkII
 - the board is sanguino
 - the processor is atmega 1284 p (16 Mhz)

```
menu.cpu=Processor

##############################################################

sanguino.name=Sanguino

sanguino.upload.tool=arduino:avrdude
sanguino.upload.protocol=arduino

sanguino.bootloader.tool=arduino:avrdude
sanguino.bootloader.low_fuses=0xFF
sanguino.bootloader.high_fuses=0xDE
sanguino.bootloader.extended_fuses=0xFD
sanguino.bootloader.unlock_bits=0x3F
sanguino.bootloader.lock_bits=0x0F

sanguino.build.board=AVR_SANGUINO
sanguino.build.core=arduino:arduino
sanguino.build.variant=sanguino

###### ATmega644x

## Sanguino W/ ATmega644 or ATmega644A (16MHz)
sanguino.menu.cpu.atmega644=ATmega644 or ATmega644A (16 MHz)

sanguino.menu.cpu.atmega644.upload.maximum_size=64512
sanguino.menu.cpu.atmega644.upload.maximum_data_size=4096
sanguino.menu.cpu.atmega644.upload.speed=38400

sanguino.menu.cpu.atmega644.bootloader.file=optiboot/optiboot_atmega644.hex

sanguino.menu.cpu.atmega644.build.mcu=atmega644
sanguino.menu.cpu.atmega644.build.f_cpu=16000000L

## Sanguino W/ ATmega644 or ATmega644A (8MHz)
sanguino.menu.cpu.atmega644_8m=ATmega644 or ATmega644A (8 MHz)

sanguino.menu.cpu.atmega644_8m.upload.maximum_size=64512
sanguino.menu.cpu.atmega644_8m.upload.maximum_data_size=4096
sanguino.menu.cpu.atmega644_8m.upload.speed=38400

sanguino.menu.cpu.atmega644_8m.bootloader.file=optiboot/optiboot_atmega644_8m.hex

sanguino.menu.cpu.atmega644_8m.build.mcu=atmega644
sanguino.menu.cpu.atmega644_8m.build.f_cpu=8000000L

## Sanguino W/ ATmega644P or ATmega644PA (16MHz)
sanguino.menu.cpu.atmega644p=ATmega644P or ATmega644PA (16 MHz)

sanguino.menu.cpu.atmega644p.upload.maximum_size=64512
sanguino.menu.cpu.atmega644p.upload.maximum_data_size=4096
sanguino.menu.cpu.atmega644p.upload.speed=115200

sanguino.menu.cpu.atmega644p.bootloader.file=optiboot/optiboot_atmega644p.hex

sanguino.menu.cpu.atmega644p.build.mcu=atmega644p
sanguino.menu.cpu.atmega644p.build.f_cpu=16000000L

## Sanguino W/ ATmega644P or ATmega644PA (8MHz)
sanguino.menu.cpu.atmega644p_8m=ATmega644P or ATmega644PA (8 MHz)

sanguino.menu.cpu.atmega644p_8m.upload.maximum_size=64512
sanguino.menu.cpu.atmega644p_8m.upload.maximum_data_size=4096
sanguino.menu.cpu.atmega644p_8m.upload.speed=38400

sanguino.menu.cpu.atmega644p_8m.bootloader.file=optiboot/optiboot_atmega644p_8m.hex

sanguino.menu.cpu.atmega644p_8m.build.mcu=atmega644p
sanguino.menu.cpu.atmega644p_8m.build.f_cpu=8000000L

###### ATmega1284x


## atmega1284.name=Sanguino W/ ATmega1284p 16mhz
## atmega1284.upload.protocol=stk500
## atmega1284.upload.maximum_size=131072
## atmega1284.upload.speed=57600

## Sanguino W/ ATmega1284 or ATmega1284P 16MHz
sanguino.menu.cpu.atmega1284p=ATmega1284 or ATmega1284P (16 MHz)

sanguino.menu.cpu.atmega1284p.upload.maximum_size=130072
sanguino.menu.cpu.atmega1284p.upload.maximum_data_size=16384
sanguino.menu.cpu.atmega1284p.upload.speed=57600
sanguino.menu.cpu.atmega1284p.protocol=stk500

sanguino.menu.cpu.atmega1284p.bootloader.file=optiboot/optiboot_atmega1284p.hex

sanguino.menu.cpu.atmega1284p.build.mcu=atmega1284p
sanguino.menu.cpu.atmega1284p.build.f_cpu=16000000L

## Sanguino W/ ATmega1284 or ATmega1284P 8MHz
sanguino.menu.cpu.atmega1284p_8m=ATmega1284 or ATmega1284P (8 MHz)

sanguino.menu.cpu.atmega1284p_8m.upload.maximum_size=130048
sanguino.menu.cpu.atmega1284p_8m.upload.maximum_data_size=16384
sanguino.menu.cpu.atmega1284p_8m.upload.speed=38400

sanguino.menu.cpu.atmega1284p_8m.bootloader.file=optiboot/optiboot_atmega1284p_8m.hex

sanguino.menu.cpu.atmega1284p_8m.build.mcu=atmega1284p
sanguino.menu.cpu.atmega1284p_8m.build.f_cpu=8000000L

############################################################
```

