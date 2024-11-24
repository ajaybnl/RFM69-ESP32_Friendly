# ESP32-Friendly RFM69 Library

This library is a modified version of the [Lowpowerlab RFM69](https://www.lowpowerlab.com/blog/2014/06/22/introducing-the-rfm69/) library, specifically adapted to work seamlessly with the ESP32 platform. It allows easy integration of the RFM69 RF module with the ESP32, enabling reliable wireless communication.

## Features

- **ESP32 compatibility**: Easily configure SPI bus selection and Chip Select (CS) pin for the ESP32.
- **Flexible SPI selection**: Choose between HSPI (SPI2) or VSPI (SPI3) using different GPIO pins for the CS pin.
- **Simple setup**: Initialize the RFM69 with a few simple commands.

## How to Use with ESP32

### Step 1: Define SPI Bus and CS Pin

The ESP32 has multiple SPI buses, and the library allows you to specify which one you want to use by selecting the appropriate Chip Select (CS) pin.

- **For HSPI (SPI2)**: Use **GPIO 15** for the CS pin.
- **For VSPI (SPI3)**: Use **GPIO 5** for the CS pin.

The library will automatically select the correct SPI bus based on the CS pin you choose.

```cpp

RFM69 rfm;



#define NODE_ID 1 //My Node ID
#define RECEIVER_ID 2 //Receiver Node ID

#define NETWORKID 100 //the same on all nodes that talk to each other

#define FREQUENCY     RF69_433MHZ
//#define FREQUENCY     RF69_868MHZ
//#define FREQUENCY     RF69_915MHZ

#define ENCRYPTKEY "xxxxxxxxxxxxxxxx" //exactly the same 16 characters/bytes on all nodes!

//SPI1 is not usable in ESP32 Wroom
//#define CS SS

// For HSPI (SPI2) use GPIO 15 for CS
#define CS 15

// For VSPI (SPI3) use GPIO 5 for CS
//#define CS 5


  void setup() {  

    // Initialize the RFM69 module
    rfm.setCS(CS);             // Set the CS pin (Important)
    rfm.setIrq(IRQ);           // Set the IRQ pin (Important)
   rfm.initialize(FREQUENCY, NODE_ID, NETWORKID); // Set frequency (e.g., 433 MHz), node ID, network ID
   rfm.encrypt(ENCRYPTKEY);
  //rfm.spyMode(true); //Read All Packets

}
```





# Originally from : RFM69 Library
[![arduino-library-badge](https://www.ardu-badge.com/badge/RFM69_LowPowerLab.svg?)](https://www.ardu-badge.com/RFM69_LowPowerLab)
[![Build Status](https://app.travis-ci.com/LowPowerLab/RFM69.svg)](https://app.travis-ci.com/LowPowerLab/RFM69)
[![GitHub release](https://img.shields.io/github/release/LowPowerLab/RFM69.svg)](https://github.com/LowPowerLab/RFM69)
[![GitHub issues](https://img.shields.io/github/issues/LowPowerLab/RFM69.svg)](https://github.com/LowPowerLab/RFM69/issues)
[![GitHub pull requests](https://img.shields.io/github/issues-pr/LowPowerLab/RFM69.svg)](https://github.com/LowPowerLab/RFM69/pulls)
[![license](https://img.shields.io/github/license/LowPowerLab/RFM69.svg)](https://github.com/LowPowerLab/RFM69/blob/master/LICENSE.txt)

By Felix Rusu, [LowPowerLab.com](http://LowPowerLab.com)
<br/>
RFM69 library for RFM69W, RFM69HW, RFM69CW, RFM69HCW (semtech SX1231, SX1231H)
<br/>
The latest examples, new features and bug fixes are found in the [original repository](https://github.com/LowPowerLab/RFM69) of this library.
  
## License
GPL 3.0, please see the [License.txt](https://github.com/LowPowerLab/RFM69/blob/master/License.txt) file for details. Be sure to include the same license with any fork or redistribution of this library.
