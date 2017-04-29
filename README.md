# microbit-I2C-EEPROM-24LCxxx-Read-Write
Example Micro:bit functions to read and write to a Microchip I2C EEPROM

A very simple example function for writing and reading data to an I2C EEPROM chip. The one I used was a Microchip 24LC128 - others in the same range should work too. I *think* I2C EEPROMS of other makes may work, but that is untested at time of writing.

This is actually an offshoot of a Nokia 5110 LCD library I wrote (https://github.com/matneee/microbit-nokia5110-PCD8544-lcd). A full font of 5x8 pixel characters, or a full screen bitmap, take up around half a kilobyte of memory. As free memory on the Micro:bit implementation of Micropython is limited to roughly 9K, that's a comparatively large amount to spend. Moving the data to files in flash storage would still use memory opening the files, and would also require drag/dropping them back to the microbit whenever it is reflashed. 
Using EEPROM as storage is cheap (as in about 30p per chip cheap), and because it is non-volatile the microbit can be reflashed without erasing your dataset. This makes it ideal for storing data that isn't going to change during your program - It could arguably be used as general purpose read/write storage during live operations, but bare in mind that the write cycle takes 5ms, and the chips lifespan is rated at 1,000,000 erase/write cycles.

Note that standard micropython has a function called Frozen Bytecode - the inspiration for this was that the Micro:bit lacks this and I was trying to come up with a relatively practical alternative.

#Pin configuration for EEPROM -> microbit:
#1 -> GND
#2 -> GND
#3 -> GND
#4 -> GND
#5 -> 20 (SDA)
#6 -> 19 (SCL)
#7 -> GND
#8 -> 3V
