Frequently Asked Questions
=========================

*1.Smart home features are not responding.*
 - Please use six AA batteries for power. Check that the battery charge is sufficient and ensure the battery voltage is above 7.5V.
 - Please check that the wiring is correct. The ESP32 development board does not come pre-installed with smart home software. You will need to upload the appropriate software to enable these features.
----

*2.The development board is not recognized or the program cannot be burned.*
 - Please make sure the CH340 driver is correctly installed on your computer.
 - Use a Type-C data cable （make sure it supports data transmission, not just charging）.
 - Open the Device Manager and check if the "USB-SERIAL CH340" device appears.
 - If the port number is occupied, reconnect the USB or restart the computer.

----

*3.If flashing the firmware using the Arduino IDE fails, please follow these steps to troubleshoot:*
 - Check the power supply and connections: Ensure the power supply is stable and the USB cable and interface are securely connected.
 - Confirm the development board model: Select the correct development board model in the menu - Tools → Board → ESP32 Dev Module.
 - Import necessary libraries: Ensure that all required libraries for the example programs are correctly imported.
 - Check the serial port settings: Select the correct serial port number （e.g., COM4） in Tools → Port.

----

*4.The serial monitor output is garbled.*
 - Please set the serial port baud rate to 115200 baud in the Arduino IDE.
 - If garbled characters persist, please confirm that the line "Serial.begin（115200）;" in the example code is consistent.

----

*5.Unable to connect to the App.*
 - Please make sure your phone and ESP32 are on the same Wi-Fi network.
 - Check that the IP address displayed on the LCD1602 screen matches the IP address entered in the app.
 - If the connection fails, try powering the ESP32 again; the IP address will be reassigned.
 - Check whether your router has a firewall or isolation mode enabled.
 - Enable the app's Internet access permission in "Settings → Wi-Fi & Cellular Data" on your phone.

----

*6.App operation delays or unresponsiveness.*
 - Please ensure a stable WiFi signal.
 - If the connection is poor, reconnect to WiFi or move closer to the router. It is recommended to use the kit within 3 meters of the router.
 - If the device remains unresponsive for an extended period, press the "RST" button on the ESP32 to reboot the system.

----

*7.The servo is not moving or is trembling.*
 - Confirm that the power supply is stable and the servo voltage should be 5V.
 - Avoid sharing USB power for multiple servos; use separate battery packs or external power supplies.
 - Check that the signal cables are correctly connected to the corresponding GPIOs （e.g., GPIO4 for window servos and GPIO13 for door servos）.

----

*8.If the sensor detects abnormal data, please check the following*
 - Confirm that the sensor's wiring port matches the pin number defined in the code.
 - Ensure that the sensor surface is free of dust, stains, or foreign objects. Keep it clean to ensure accurate detection.

----

*9.If the LCD1602 screen brightness is low or there is no display, please check the following.*
 - Use an external battery for power. USB power may cause insufficient voltage, resulting in low screen brightness or no display.
 - Ensure the battery voltage is above 7.5V. If the voltage is lower than this, it is recommended to replace the battery promptly to ensure normal operation of the system.

----

*10.Is the voice recognition module not recognizing your voice?*
 - Please make sure the voice recognition module is connected correctly.
 - The baud rate should be set to 115200.
 - Please use it in a quiet environment and ensure that it is within 0.5 meters of the microphone.
 - This module only supports fixed commands, such as "Light on," "Light off," "Fan on," and "Fan off."
 - Other unregistered voice commands will be invalid.

----

*11.The app cannot connect to the ESP32 development board/cannot be controlled using the app.*
 - If you are using the Arduino IDE to program:Please confirm that you have changed the WiFi name and password in the code to your own network information.
 - If you are using Espressif's official programming tool:Please confirm that you have correctly configured the WiFi according to the network configuration tutorial.
 - If you still cannot connect:It is recommended to power cycle the device and then try connecting again.

*If you encounter other problems or cannot solve them yourself, please contact the after-sales technical support team and we will provide you with assistance in a timely manner.*