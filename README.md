# Anet-Z2-IO-Module
Work in progress...<br>
Attempt to add a 2nd Z driver and extra IO for an ANET A6 3D printer.<br>
The Anet A6 is a nice, relatively cheap, 3D printer. It has 2x Z steppers, plugged in parrallel into 1 Z-driver.<br>
The disadvantage is that the 2 Z-steppers can be very easily misalligned. I got fed-up with that and wanted to add at least a 2nd independant Z-driver.<br>

This project will:
- free up the I2C pins on the LCD plug and redirecting the encoder on the LCD board to the IO on an I2C MCP23017 IO controller.
- the FAN control pin is also re-used, 1 small cut in a trace on the main board.
- an IC2 PWM chip PCA9685 is used for outputs. 1 output will drive the FAN output on the mainboard.
- The 3 freed-up pins on the uC are then used to directly drive the 2nd Z driver.#

Limitations:
- The ANet board uses the ATMEGA1284P uC and has only 1 free pin in the standard configuration.
- The ATMEGA1284P has a very limited program memory. Using some extra's like manual bedlevel LCD menu and custom startup logo, takes up about 97% of prog mem already.

Done:
- Schematic and electronics are done.
- Created an additional board in local Marlin version, based on the Anet_10 board.
- Initial checks seems to be able to put all this extra in the limited available program memory.

To do is:
- The logical addressing of the IO pins on the I2C chips in the Marlin firmware.
- Possibly rewriting the MCP23017 and PCA9685 Arduino libraries for use with Marlin.
