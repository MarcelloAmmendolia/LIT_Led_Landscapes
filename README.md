# Led_micro_CTRL
Led_micro_CTRL is a repository about controlling ws2812b Led strips and arrays using microcontrollers
like Arduino, ESP and Teensy+.


HARDWARE:

Windows 10

Teensy 4.1 (arduino based MC with full usb speed serial communication)

Custom pcb

Any ws82-xxx led strip

Dependancy Libraries:

https://github.com/FastLED/FastLED/tree/FastLED3.1 14, 
https://github.com/PaulStoffregen/OctoWS2811 18



PROCESS:

1) Touch designer instance that manages the UI and animations created. This sends the animation data pre mapped in a table (3 rows, r/g/b, the number of columns equal the number of addressable led’s), out through a Touch Out DAT.
2) Second Touch designer instance receives the table dat, and focuses solely on formatting that table data into several compact byte strings that are sent using python and the serial.sendBytes() command.
[i]A side note here, I have to split the led bytes into chunks or packets of 255 or less due to a built in limit that sendBytes has. I’ve successfully sent entire byte strings using processing and it’s considerably faster (35-45 fps)
3) Byte string is received over serial comport by the teensy, at this point it’s premapped and each 3 values are applied to the led’s 1:1.


Many thanks to Lucas Morgan, http://www.enviral-design.com/


