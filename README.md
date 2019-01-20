Prusa I8 A (metal/aluminium) 
This worked for me with arduino 1.8.7 Latest Marlin cloned Jan20 2019
With coinfig from examples Prusa I3 B config.

Though the sensors and steps were not yet configured.
The bootloader and fuses were:


I bootloader it with usbasp i2c programmer hooked on the small LCD controller.

avrdude -p atmega1284p -c usbtiny -b 19200 -V -e -U lfuse:w:0xD6:m -U hfuse:w:0xDA:m -U efuse:w:0xFD:m -U flash:w:ATmegaBOOT_168_atmega1284p.hex:i
avrdude -v -patmega1284P -cusbasp-clone -U flash:w:./ATmegaBOOT_168_atmega1284p.hex

