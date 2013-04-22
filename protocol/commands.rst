RobotOpen Protocol
==================
The creation of the RobotOpen Protocol is an effort to design an open, standardized protocol for communication and control of hobbyist robots over an IP based network. It is designed for simple and lightweight two-way communication. This version of the RobotOpen protocol supersedes any prior documentation and is used in all current RobotOpen software.


Basics
-----------------
By default, any robot controller implementing the RobotOpen protocol should be disabled and inactive upon powerup. At any point that no packets are received for a timeout period (typically 100-200 milliseconds), the robot should also disable itself. All RobotOpen protocol data is currently intended to traverse an IP based network, specifically utilizing UDP on the transport layer. The RobotOpen protocol is stateless. Every packet should be treated individually and does not rely on any specific ordering.


Parameters
-----------------
Parameters are semi-permanent values intended to be stored in non-volatile EEPROM memory onboard the Robot. These values can be read from the robot and updated from the Driver Station when the robot controller is disabled. Currently RobotOpen protocol supports the following types listed below. Each parameter has a unique address assigned to it (a number between 0 and 99). Parameters are always transmitted as 4 bytes, even if their size is less than 4. Additional bytes should be set to 0. For instance a boolean that is true would be transmitted as 0xFF000000 in a parameter packet. Values are transmitted in big endian format (most significant byte first).


Parameter Types
~~~~~~~~~~~~~~~~~~~~~~
| Bool - 1 byte (0x00 false, 0xFF true)
| Char - 1 byte (signed)
| Int - 2 bytes (signed)
| Long - 4 bytes (signed)
| Float - 4 bytes (signed)


Driver Station to Robot Packets
-----------------
Currently the RobotOpen protocol supports up to four control devices (each having a fixed size of 24 bytes, totalling 96 bytes of control data) per packet. These 24 bytes have specified names but arbitrary data can be inserted and interpreted on the robot controller.


Joystick/Control Naming
~~~~~~~~~~~~~~~~~~~~~~
| Byte 0 - **Analog Left X Axis** (0x00-0xFF)
| Byte 1 - **Analog Left Y Axis** (0x00-0xFF)
| Byte 2 - **Analog Right X Axis** (0x00-0xFF)
| Byte 3 - **Analog Right Y Axis** (0x00-0xFF)
| Byte 4 - **Button A** (0x00 off, 0xFF on)
| Byte 5 - **Button B** (0x00 off, 0xFF on)
| Byte 6 - **Button X** (0x00 off, 0xFF on)
| Byte 7 - **Button Y** (0x00 off, 0xFF on)
| Byte 8 - **Left Shoulder** (0x00 off, 0xFF on)
| Byte 9 - **Right Shoulder** (0x00 off, 0xFF on)
| Byte 10 - **Left Trigger** (0x00-0xFF)
| Byte 11 - **Right Trigger** (0x00-0xFF)
| Byte 12 - **Select** (0x00 off, 0xFF on)
| Byte 13 - **Start** (0x00 off, 0xFF on)
| Byte 14 - **Left Stick Button** (0x00 off, 0xFF on)
| Byte 15 - **Right Stick Button** (0x00 off, 0xFF on)
| Byte 16 - **D-Pad Up** (0x00 off, 0xFF on)
| Byte 17 - **D-Pad Down** (0x00 off, 0xFF on)
| Byte 18 - **D-Pad Left** (0x00 off, 0xFF on)
| Byte 19 - **D-Pad Right** (0x00 off, 0xFF on)
| Byte 20 - **Aux 1** (0x00-0xFF)
| Byte 21 - **Aux 2** (0x00-0xFF)
| Byte 22 - **Aux 3** (0x00-0xFF)
| Byte 23 - **Aux 4** (0x00-0xFF)


Control (Enable) Packet
~~~~~~~~~~~~~~~~~~~~~~
A control packet must contain at least one controller's worth of data. This means that a control packet can be 27, 51, 75, or 99 bytes long. Control packets with no joystick data will be dropped on the robot side. A CRC-16 of the packet is calculated and appended on the end. When a valid control packet is received on the robot side, the robot will enable itself.

| Byte 0 - 0x63
| (Controller 1 Bytes 0-23)
| (Controller 2 Bytes 0-23) - optional
| (Controller 3 Bytes 0-23) - optional
| (Controller 4 Bytes 0-23) - optional
| 2nd to Last Byte - CRC-16 Low Byte
| Last Byte - CRC-16 High Byte


Heartbeat (Disable) Packet
~~~~~~~~~~~~~~~~~~~~~~
Heartbeat packets are used to disable the robot but keep communications active. All heartbeat packets are 3 fixed bytes, show below.

| Byte 0 - 0x68
| Byte 1 - 0xEE
| Byte 2 - 0x01


Set Parameter Packet
~~~~~~~~~~~~~~~~~~~~~~
The robot must be disabled for the parameters to be successfully set. Multiple parameters may be transmitted in each set parameter packet. Each parameter will consume 5 bytes (address + 4 data bytes).

| Byte 0 - 0x73
| ...
| (Parameter Address (0x00-0x63)
| Val1
| Val2
| Val3
| Val4
| ...
| 2nd to Last Byte - CRC-16 Low Byte
| Last Byte - CRC-16 High Byte


Get Parameters Packet
~~~~~~~~~~~~~~~~~~~~~~
A get parameters packet requests the robot controller to transmit all current parameters and their values back to the Driver Station. All get parameters packets are 3 fixed bytes, shown below.

| Byte 0 - 0x67
| Byte 1 - 0xEA
| Byte 2 - 0x41


Robot to Driver Station Packets
-----------------
Robot to Driver Station packets can be transmitted at any time. While a robot controller is disabled (heartbeat packets being sent), it should continue to receive debug and dashboard packets regularly. Parameter packets will be received any time requested.

Debug Packet
~~~~~~~~~~~~~~~~~~~~~~
Debug packets allow for arbitrary ASCII data to be sent to the Driver Station (a sort of remote serial console). Debug packets begin with the byte 0x70 followed by a variable number of ascii bytes.

| Byte 0 - 0x70
| (ascii bytes of variable length)


Dashboard Packet
~~~~~~~~~~~~~~~~~~~~~~
A dashboard packet contains values that a user has published from their robot code so that they can monitor them remotely on their Driver Station. The supported types can be seen above. Unlike parameters, dashboard values are exactly their specified length in the packet. Every dashboard value in a dashboard packet begins with a length (the length of that dashboard value including the length byte). The type will be one of the type codes listed below. The appropriate number of bytes will follow based on the value's type. The ID is a variable length ascii name for the value.

| Byte 0 - 0x64
| ...
| Length
| Type
| Val1
| Val2 (optional)
| Val3 (optional)
| Val4 (optional)
| ID (variable length)
| ...


Dashboard Types
~~~~~~~~~~~~~~~~~~~~~~
| Char - 1 byte (unsigned) - (type code: 0x63)
| Int - 2 bytes (signed) - (type code: 0x69)
| Long - 4 bytes (signed) - (type code: 0x6C)
| Float - 4 bytes (signed) - (type code: 0x66)


Parameters Packet
~~~~~~~~~~~~~~~~~~~~~~
A parameters packet is sent back upon the reception of a get parameters packet. Each parameter in the parameters packet begins with a length (the length of the parameter including the length byte). This is followed by the unique parameter address (0-99). The type follows that (reference the parameter type codes below). 4 bytes will follow, however based on the type the non-used bytes will be zeroes. The ID is a variable length ascii name for the parameter.

| Byte 0 - 0x72
| ...
| Length
| Parameter Address (0x00-0x63)
| Type
| Val1
| Val2
| Val3
| Val4
| ID (variable length)
| ...


Parameter Type Codes
~~~~~~~~~~~~~~~~~~~~~~
| Bool - 0x62
| Char - 0x63
| Int - 0x69
| Long - 0x6C
| Float - 0x66