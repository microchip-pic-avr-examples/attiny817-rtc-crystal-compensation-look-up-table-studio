<!-- Please do not change this html logo with link -->
<a href="https://www.microchip.com" rel="nofollow"><img src="images/microchip.png" alt="MCHP" width="300"/></a>

# RTC Crystal Compensation Look-Up Table

This example uses a look-up table to do temperature compensation. The look-up table is built from the manufacturers data on temperature drift. As the values are symmetrical around 25C (parabolic curve), only values for 25C and higher are used, to reduce data size. There are two tables included in this example, one using 8-bit data, and one with 16-bit data. 8-bit data offers reduced datasize, but it gives lower accuracy. There are also two defined values associated with the table.

The application sets up the ADC to read the internal temperature sensor. The resulting temperature value is used to pick a correction value from the look-up table, which is added to the accumulated error.

The RTC is configured to give an interrupt every second. In the RTC ISR the correction is applied. When the accumulated error is larger that one (or more) 32.768 kHz clock cycle, the RTC period is reduced by one (or more). Any remaining error unaccounted for is kept until the next correction cycle.

This example is based on the Application Note [AN2711 - Real-Time Clock Calibration and Compensation on AVR® Microcontrollers](https://www.microchip.com/DS00002711), which should be referred to for a more detailed understanding of the concepts.

## Related Documentation

- [AN2711 - Real-Time Clock Calibration and Compensation on AVR® Microcontrollers](https://www.microchip.com/DS00002711)
- [ATtiny817 Device Page](https://www.microchip.com/wwwproducts/en/ATTINY817)

## Software Used

- [Atmel Studio](https://www.microchip.com/mplab/avr-support/atmel-studio-7) 7.0.2397 or later
- [ATtiny DFP](http://packs.download.atmel.com/) 1.6.316 or later
- AVR/GNU C Compiler (Built-in compiler) 5.4.0 or later


## Hardware Used

- [ATtiny817 Xplained Pro](https://www.microchip.com/DevelopmentTools/ProductDetails/attiny817-xpro)
- Micro-USB cable (Type-A/Micro-B)

## Setup

1. The crystal on the ATtiny817 Xplained Pro board is by default not connected to the TOSC pins, as they are used for UART communication. To connect the pins, remove resistors R307 and R308 and place them on the footprints of R312 and R313. Refer to [ATtiny817 Xplained Pro User's Guide](https://www.microchip.com/DS50002684) for more information on how to do this.

## Operation

1. Connect the board to the PC.

2. Download the zip file or clone the example to get the source code.

3. Open the .atsln file with Atmel Studio.

4. Build the solution and program the ATtiny817. Press *Start without debugging* or use CTRL+ALT+F5 hotkeys to run the application for programming the device.

## Conclusion

This example has now illustrated a way of doing temperature compensation by using look-up tables.
