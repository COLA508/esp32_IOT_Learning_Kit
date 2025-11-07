Frequently Asked Questions
==========================

**Need help? Please see here first**
 - To help you quickly resolve your issues, we have compiled frequently asked questions and troubleshooting methods below. Please try self-troubleshooting first, as this is usually the most efficient way to solve problems.
 - If you cannot find a solution here, please feel free to contact our after-sales team for further technical support.

----

**1.The device doesn't respond at all after powering on（no light, no operation）?**
 - This is normal, please don't worry! To maintain flexibility, our development boards are not pre-installed with functional programs. Simply follow our introductory tutorial to burn your first program and begin your creative journey.

----

**2.The development board is not recognized or the program cannot be burned.**
 - Please make sure the CH340 driver is correctly installed on your computer.Click here to view the installation tutorial. :ref:`install_ch340_driver`
 - Use a Type-C data cable （make sure it supports data transmission, not just charging）.
 - Open the Device Manager and check if the “USB-SERIAL CH340” device appears.
 - If the port number is occupied, reconnect the USB or restart the computer.

----

**3.If flashing the firmware using the Arduino IDE fails, please follow these steps to troubleshoot**
 - Check the power supply and connections: Ensure the power supply is stable and the USB cable and interface are securely connected.
 - Confirm the development board model: Select the correct development board model in the menu - Tools → Board → ESP32 Dev Module.
 - Import necessary libraries: Ensure that all required libraries for the example programs are correctly imported.
 - Check the serial port settings: Select the correct serial port number （e.g., COM4） in Tools → Port.

----

**4.Unable to open the web control interface**
 - Connect the development board to your computer, open the serial monitor in the Arduino IDE, and press the "RST" reset button on the development board. Observe the IP address in the serial port print information.
 - Ensure that the mobile phone or computer used to open the web page is connected to the development board on the same Wi-Fi network.
 - If the above steps do not resolve the issue, please refer to the detailed illustrated tutorial: "Network Configuration Tutorial"  :ref:`Configure network`

----

**5.Servo motor/fan not spinning, or LCD1602 screen showing no display/dim display**
 - These issues are often caused by insufficient power supply. Please ensure you use the battery box included with the kit, powered by 6 external AA batteries, and ensure the total battery voltage is not lower than 7.5V.
 - If the fan makes noise but the blades don't spin after powering on, try gently flicking the blades with your hand to start them.
 - If the screen is not lit or the content is unclear, check the potentiometer（backlight adjustment knob）on the back of the screen. Fine-tune it left or right to change the backlight brightness until the display is clear.

----
