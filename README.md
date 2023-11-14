# Quick Start

- [BluetoothMe-Library](https://github.com/BluetoothMe/BluetoothMe)  
- [Examples](https://github.com/BluetoothMe/BluetoothMe/tree/main/examples)  


## App
The app supports `Bluetooth Classic` and `BLE (Bluetooth Low Energy)`. 

With the help of the application, you can create your own user interfaces - `Controllers`, which contain various types of control elements - `Widgets`:
- `EMPTY` is an empty widget with no control (can be used as a plug).
- `BUTTON` is a non-latching button that has two states: pressed and released.
- `SWITCH` is a two-position switch with locking.
- `SLIDER` is an element for changing values in a certain range (similar to a scroll bar).
- `TEXT` is a field for entering text from the keyboard.

It is also possible to activate additional tools that will be displayed on the toolbar:
- `withVoiceInput` is a button for entering text using the voice recognition function.
- `withRefresh` is a refresh button to get the current state (when clicked, sends a message with a tag `get/`).

The application also has `Chat`, where you can see all sent and received messages.


## Library
BluetoothMe library is required for proper interaction with Arduino. It helps recognize commands sent from the application.  
Each command consists of a `tag` and a `value`, separated by a `/` character and a `\n` character at the end (eg `tag/value` `\n`):
- `tag` is a command identifier that helps group commands by topic (eg `led` to control the state of an LED).  
- `value` is the meaningful payload of the command (eg `1` or `0` to turn the LED on or off respectively).  

So, the command to turn on the LED will be `led/1` `\n`, and to turn it off `led/0` `\n`.  

The library provides support for all Arduino-compatible Bluetooth modules using a different implementation of the `IBluetoothAdapter` interface.
- `HardwareSerialAdapter` for adapters that connect to the hardware serial port (`Serial` on Arduino Uno and Nano).
- `SoftwareSerialAdapter` for adapters that connect to the software serial port (the `SoftwareSerial.h` library is used).
- `AsyncHardwareSerialAdapter` to asynchronously read data without blocking from a hardware serial port (`Serial` on Arduino Uno and Nano).
- `AsyncSoftwareSerialAdapter` to asynchronously read data without blocking from a software serial port (the `SoftwareSerial.h` library is used).
