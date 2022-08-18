# DIY e-bike documentation

The goal of this repo is to keep DIY e-bike related information that could be of public use

## Useful links
- [TSDZ2 6-pin cable pinout](https://github.com/OpenSourceEBike/TSDZ2_wiki/wiki/Wire-KT-LCD3-to-TSDZ2)
- [Bafang 850C Display firmware update](https://github.com/OpenSourceEBike/TSDZ2_wiki/wiki/Flash-the-firmware-on-850C-using-SWD)
- [STM32 ST-LINK Utility](https://www.st.com/en/development-tools/stsw-link004.html)
- [KT-LCD3 firware flashing issues](kt-lcd3-versions.md)

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

### 850C flashing firmware
According to this link [Bafang 850C Display firmware update](https://github.com/OpenSourceEBike/TSDZ2_wiki/wiki/Flash-the-firmware-on-850C-using-SWD) you need to use [STM32 ST-LINK Utility](https://www.st.com/en/development-tools/stsw-link004.html) to flash the display, but there are some issues:
- it is marked obsolete, replaced with [STM32CubeProg](https://www.st.com/en/development-tools/stm32cubeprog.html)
- if you install the ST-LINK Utility it might not start. 
For me it refused to start on one laptop (Win 11) complaining about some missing vcredist related dlls. 
Installing vcredist and rebooting, reinstalling the tool - nothing helped, could not get it running. 
But just installing it on another laptop (also Win 11) worked from the get go, no issues.
Flashing the display with STM32CubeProg went through after some tinkering, but the display did not boot afterwards. I am pretty sure this is a user error and not the software fault.
Flashing with ST-LINK Utility was succesful.

Also flashing instructions are not really clear, at least not for someone inexperienced with flashing microcontrollers. 
I will try creating a more thorough guide for this, but in short the steps are as follows:
- connect your display to ST-LINK V2 USB dongle
Note: you don't need any voltage boosters, nor connecting the bike battery to the display, just plain st-link to display SWD pins as described in [Bafang 850C Display firmware update](https://github.com/OpenSourceEBike/TSDZ2_wiki/wiki/Flash-the-firmware-on-850C-using-SWD)
Also you don't need to turn the display on in order to flash it (and you can't do this anyway with described wiring arrangement) so you just flas it and then go ahead and connect to the bike as usual
- plug the dongle into computer
- in ST-LINK Utility go to settings and make sure your dongle was recognized (it will display the serial number and allow changing some settings; I have left all settings stock)
- click "connect" in the top toolbar
- full chip erase (if fails see the next step)
- open **option byte** view and turn off all read/write protection flags you see there; apply; repeat full chip erase if it failed before
- open your firmware file 
(there are 2 versions: bootloader and regular, non-bootloader; at this point I am not sure what bootloader is, but if I understand correctly when flashing via ST-LINK you need a regular, non-bootloader version)
- flash the firmware (should take about 10-20 seconds, you'll see the progress bar as it goes)
- you're done

If at some point you see complaints about read or write failure - just tinker with erasing the chip and setting the option bytes to remove write protection, you'll get there.
