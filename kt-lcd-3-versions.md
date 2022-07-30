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

**Uses SWD data interface, therefore SWIM support is not present and you can't flash it via ST-LINK**

# Data interfaces

## SWIM

The SWIM is a single wire interface based on asynchronous, high sink (8 mA), open-drain, bidirectional communication.

## SWD

SWD, also known as Serial Wire Debug is a 2-pin interface (SWDIO/SWCLK) of which it's also an alternative JTAG interface that has the same JTAG protocol. SWD uses an ARM CPU standard bi-directional wire protocol, defined in the ARM Debug programmer.
