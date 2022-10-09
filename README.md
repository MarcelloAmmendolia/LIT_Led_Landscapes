Within LED_Landscapes, the light installations can show animations, react to sound, person movement, react to data coming from external API's and from many other sources. From a technical point of view, the goal of Led_landscapes was to create a system able to address every pixel of an hypotetic long LED strip chain, changing color (rgb) and brightness of the pixels with different types of sensors or pre-defined commands, leaving it open for future applications that may require a different number of LEDs, a different configuration, or different interaction elements.
<br/> 
<br/> 

--> GENERAL SETUP:

Windows 10 <br/> Teensy 4.1 (arduino based MC with full usb speed serial communication) <br/> Custom pcb <br/> Any ws82-xxx led strip <br/> Derivative Touchdesigner

Dependancy Libraries:

https://github.com/FastLED/FastLED/tree/FastLED3.1,  <br/> https://github.com/PaulStoffregen/OctoWS2811
<br/> 
<br/> 
--> GENERAL PROCESS:

1) Touch designer instance that manages the UI and animations created. This sends the animation data pre mapped in a table (3 rows, r/g/b, the number of columns equal the number of addressable led’s), out through a Touch Out DAT.
2) Second Touch designer instance receives the table dat, and focuses solely on formatting that table data into several compact byte strings that are sent using python and the serial.sendBytes() command.
[i]A side note here, I have to split the led bytes into chunks or packets of 255 or less due to a built in limit that sendBytes has. I’ve successfully sent entire byte strings using processing and it’s considerably faster (35-45 fps)
3) Byte string is received over serial comport by the teensy, at this point it’s premapped and each 3 values are applied to the led’s 1:1.
4) <img width="887" alt="image" src="https://user-images.githubusercontent.com/82780678/194755092-7109ca6e-daba-45f6-a830-a2a3d325795b.png">
5) <img width="887" alt="MAKING OF- 2" src="https://user-images.githubusercontent.com/82780678/194755103-5baf4dae-91f5-4c04-80ac-c617e8ad5461.png">




Many thanks to Lucas Morgan, http://www.enviral-design.com/


