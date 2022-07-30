I've tried to flash KT-LCD3 using these [flashing instructions](https://github.com/OpenSourceEBike/TSDZ2_wiki/wiki/How-to-flash-the-Flexible-OpenSource-firmware-on-KT-LCD3) but could not get STVP to establish SWIM connection. Judging by some comments online I'm not the only one facing this issue. This document sums up the results of my research on why does this happen.

# KT-LCD3 versions

So far I've seen several revisions of KT-LCD3:
- KT-LCD3-E
- KT-LCD3-E2
- KT-LCD3-M1

I own both ´E´ and ´M1´ versions and can verify that these commonly used [flashing instructions](https://github.com/OpenSourceEBike/TSDZ2_wiki/wiki/How-to-flash-the-Flexible-OpenSource-firmware-on-KT-LCD3) only work for ´E´ variant. Reasons are explained below.

## KT-LCD3-E

Has an ST Microelectronics STM8S105 microcontroller inside

[Description](https://www.st.com/en/microcontrollers-microprocessors/stm8s105c6.html)

[Datasheet](https://www.st.com/resource/en/datasheet/stm8s105c6.pdf)

Uses SWIM interface, PD1 Pin is assigned to SWIM data interface

## KT-LCD3-M1

Has a Mind Motion MM32SPIN 25PF microcontroller inside

[Description](https://www.mindmotion.com.cn/en/products/mm32mcu/mm32spin/mm32spin_specific_mcu/mm32spin2x/)

[Datasheet](https://www.mindmotion.com.cn/download/products/DS_MM32SPIN2x_p_EN.pdf)

**Uses SWD data interface, therefore SWIM support is not present and you can't flash as per instructions mentioned above**

# Conclusion

I know nothing about microcontrollers, so probably stating the obvious, but it looks like existing OSF builds are compiled for STM8, not STM32/MM32. 
So even if you get the flashing setup right - you still need firmware binaries built specifically for MM32.

If I understand correctly this more or less rules out possibilities of flashing KT-LCD3-M1 at this point. 
Annoyingly it is not possible to tell by the looks / markings on the outside of the display, which revision it is (I have one marked _KT-LCD3 V3.0 7J 24/36/48_ with KT-LCD3-E board 
and another one _KT-LCD3 V3.0 1K 24/36/48_ with KT-LCD3-M1
