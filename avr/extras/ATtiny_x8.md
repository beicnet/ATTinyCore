
### ATtiny 48/88
![x8 Pin Mapping](http://drazzy.com/e/img/PinoutT88x.jpg "Arduino Pin Mapping for ATtiny 88/48 in TQFP")
![x8 Pin Mapping](http://drazzy.com/e/img/PinoutT88-PU.jpg "Arduino Pin Mapping for ATtiny 88/48 in DIP")

### Clock options
The ATtiny x8 series of microcontrollers, in the interest of lowering costs, does not provide support for using an external crystal as a clock source, only the internal oscillator (at ~8 or ~1mhz) or an external *clock* source. The internal oscillator is only factory calibrated to +/- 10%, so for timing critical tasks, other arrangements (or a different chip) must be used. Note that using an external clock source is not an option in the board drop-down menus, so you cannot set it that way with "burn bootloader" from within the IDE - you must do it manually (this is to prevent new users from accidentally bricking their parts).

### I2C Support
There is full Hardware I2C support. Use the normal Wire library. 

### SPI Support
There is full Hardware SPI supply. Use the normal SPI library. 

### UART (Serial) Support
There is no hardware UART support (for cost saving). If running off the internal oscillator (since this chip does not support a crystal), you may need to calibrate it to get the speed close enough to the correct speed for UART communication to work. The core incorporates a built-in software serial named Serial - this uses the analog comparator pins, in order to use the Analog Comparator's interrupt, so that it doesn't conflict with libraries and applications that require PCINTs.  TX is AIN0, RX is AIN1. Although it is named Serial, it is still a software implementation, so it is recommended to keep the baud rate low, and you cannot send or receive at the same time. The SoftwareSerial library may be used; if it is used at the same time as the built-in software Serial, only one of them can send *or* receive at a time (if you need to be able to use both at the same time, or send and receive at the same time, you must use a device with a hardware UART). 

### ADC Reference Options
