# DIY e-bike documentation

The goal of this repo is to keep DIY e-bike related information that could be of public use

Useful links:
- [TSDZ2 6-pin cable pinout](https://github.com/OpenSourceEBike/TSDZ2_wiki/wiki/Wire-KT-LCD3-to-TSDZ2)
- [Bafang 850C Display disassembly](https://github.com/OpenSourceEBike/TSDZ2_wiki/wiki/Flash-the-firmware-on-850C-using-SWD#How_to_open_the_LCD)
- [STM32 ST-LINK Utility](https://www.st.com/en/development-tools/stsw-link004.html)

## Notes:

### 850C disassembly

Disassembling 850C display without breaking anything is pretty tricky. 

On the face side of the display you have 2 parts:
- "glass"
- surrounding frame 

You have to unclip the frame first, but it sits very tight and it is also made of very fragile plastic. Try using thin hard plastic spatulas. Like the ones you find in phone repair kits. put it between the frame and the main body and slowly twist near every clip location. There are 2 clips per side + some guiding pins. But you will likely crack that frame anyway, so be ready to glue up afterwards.

Once you've unclipped that stubborn frame you need to remove the "glass". 
'This is tricky too because it sits slightly nested into thin surrounding plastic of the main body AND it is attached with 2 sided tape all around. 
Use the same plastic spatula, squeeze it in between the body and the glass and twist, the sticky tape will start unsticking from the main body (if you're lucky it will stay on the glass) - go all around the glass and remove it. Heat gun or hair dryer might ease this step quite a bit.

The rest is simple - 2 screws in the bottom part of the display and you are done.
Instead of using header pins you can use a short length of some interface cable. I have used the display extension cable cut in half and soldered one half to the SWD pins on the display logic board (had to drill a small hole in a lower back side of the display enclosure to pass the cable in.
