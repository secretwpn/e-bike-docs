# SWIM

The SWIM is a single wire interface based on asynchronous, high sink (8 mA), open-drain, bidirectional communication.

# SWD

SWD, also known as Serial Wire Debug is a 2-pin interface (SWDIO/SWCLK) of which it's also an alternative JTAG interface that has the same JTAG protocol. SWD uses an ARM CPU standard bi-directional wire protocol, defined in the ARM Debug programmer.

# KT-LCD3-E

Has an ST Microelectronics STM8S105 microcontroller inside

[Description](https://www.st.com/en/microcontrollers-microprocessors/stm8s105c6.html)

[Datasheet](https://www.st.com/resource/en/datasheet/stm8s105c6.pdf)

Uses SWIM interface, PD1 Pin is assigned to SWIM data interface

# KT-LCD3-M1

Has a Mind Motion MS32SPIN 25PF microcontroller inside

[Description](https://www.mindmotion.com.cn/en/products/mm32mcu/mm32spin/mm32spin_specific_mcu/mm32spin2x/)

[Datasheet](https://www.mindmotion.com.cn/download/products/DS_MM32SPIN2x_p_EN.pdf)

Uses SWD data interface, therefore SWIM support is not present and you can't flash it via ST-LINK