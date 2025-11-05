Course 1-Button_LED
====================

.. image:: _static/COURSE/1.ledbutton.png
    :alt: Arduino IDE official website
    :align: center

----

Learning Objectives
-------------------

1. Master the basic principles of ESP32 digital input/output; 
2. Build a web server based on ESP32 to achieve remote control via web page; 
3. Understand the synchronization mechanism between physical buttons and web page control; 
4. Be familiar with the interaction between the HTML + CSS + JavaScript front-end and the ESP32 back-end; 
5. Ultimately, complete a simple and aesthetically pleasing LED control system with real-time status updates.

----

Required Component
------------------

 - LED Module、Button Module

Working Principle
-----------------

 - LED Module：LED（Light Emitting Diode）is a semiconductor device that converts electrical energy into light energy. Its working principle is based on the electron-hole recombination effect when a PN junction is forward-biased, resulting in light emission.
 - Button Module：Structurally, it is a mechanical contact switch. When pressed, the two contacts close, and the circuit is completed; when released, the contacts open, and the circuit is broken.

Wiring
------

 - LED Module —— ESP32 IO26
 - Button Module —— ESP32 IO25

.. image:: _static/COURSE/2.ledwiring.png
    :alt: Arduino IDE official website
    :align: center

----

Example Code
------------

.. code-block:: cpp

   #include <Arduino.h>

   // LED configuration
   #define LED_PIN 26

   // Voice recognition
   #define VOICE_RX_PIN 16
   #define VOICE_TX_PIN 17
   #define VOICE_HEADER 0xAA          // Packet header
   #define VOICE_FOOTER 0xBB          // Packet footer
   #define VOICE_PACKET_LENGTH 3      // Packet length
   #define VOICE_KEY_LED_ON 0x03
   #define VOICE_KEY_LED_OFF 0x04

   HardwareSerial VoiceSerial(2);

   // Voice protocol parsing variables
   uint8_t voiceBuffer[VOICE_PACKET_LENGTH];
   int voiceBufferIndex = 0;
   bool voiceReceiving = false;
   unsigned long lastVoiceByteTime = 0;
   const unsigned long VOICE_TIMEOUT = 100; // Byte timeout in ms

   void setLedValue(int val) {
     digitalWrite(LED_PIN, val);
   }

   int getLedValue() {
     return digitalRead(LED_PIN);
   }

   // Validate command
   bool isValidVoiceCommand(uint8_t command) {
     return (command == VOICE_KEY_LED_ON || command == VOICE_KEY_LED_OFF);
   }

   // Process voice command
   void processVoiceCommand(uint8_t keyword) {
     if (keyword == VOICE_KEY_LED_ON) {
       setLedValue(HIGH);
       Serial.println("Voice Command: LED ON");
     } else if (keyword == VOICE_KEY_LED_OFF) {
       setLedValue(LOW);
       Serial.println("Voice Command: LED OFF");
     }
   }

   // Voice protocol parser
   void voiceSerialLoop() {
     // Check timeout
     if (voiceReceiving && millis() - lastVoiceByteTime > VOICE_TIMEOUT) {
       voiceBufferIndex = 0;
       voiceReceiving = false;
     }
     
     while (VoiceSerial.available() > 0) {
       uint8_t data = VoiceSerial.read();
       lastVoiceByteTime = millis();
       
       if (!voiceReceiving) {
         if (data == VOICE_HEADER) {
           voiceReceiving = true;
           voiceBufferIndex = 0;
           voiceBuffer[voiceBufferIndex++] = data;
         }
         continue;
       }
       
       if (voiceBufferIndex < VOICE_PACKET_LENGTH) {
         voiceBuffer[voiceBufferIndex++] = data;
         
         if (voiceBufferIndex == VOICE_PACKET_LENGTH) {
           if (voiceBuffer[0] == VOICE_HEADER && voiceBuffer[2] == VOICE_FOOTER) {
             uint8_t keyword = voiceBuffer[1];
             if (isValidVoiceCommand(keyword)) {
               processVoiceCommand(keyword);
             } else {
               Serial.print("Invalid command: 0x");
               Serial.println(keyword, HEX);
             }
           }
           voiceReceiving = false;
           voiceBufferIndex = 0;
         }
       } else {
         voiceReceiving = false;
         voiceBufferIndex = 0;
       }
     }
   }

   void setup() {
     Serial.begin(115200);
     VoiceSerial.begin(115200, SERIAL_8N1, VOICE_TX_PIN, VOICE_RX_PIN);
     pinMode(LED_PIN, OUTPUT);
     setLedValue(LOW);
     Serial.println("Voice-controlled LED system started");
   }

   void loop() {
     voiceSerialLoop();  // Handle voice commands
   }