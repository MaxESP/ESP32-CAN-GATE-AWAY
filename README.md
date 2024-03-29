# ESP32-CAN-GATE-AWAY
NMEA 2000 NMEA 0183 GATE away

I have started this project a few years ago for boat the goal was to implement a small factor pc connected to nmea (2000 and 0183) to display data on a smart touch  display on the console of the boat.

I have seen a lot of example using raspberry pi but for my goal the graphic power of a pi was not enough to power a large display like photo below.

![boat 2023](https://user-images.githubusercontent.com/41333143/217280431-9ed467c4-3f9a-4ce4-accd-00c1c4b01b3c.png)

So the first step  was to find a library to read nmea 2000 ; I think that Timo Lappalainen was the men witch provide the most used nmea 2000 library based on reverse engineering.

2 step was to design a pcb based on ESP32 with a good advise of Timo about isolated 5v dc like photo below

![ESP32 NMEA 2000 READER SENDER](https://user-images.githubusercontent.com/41333143/217289512-3714985d-d79b-4abf-a835-e54730c2ac6e.jpg)

I have had in my design a mcp 2515 to free out the integrated CAN controler of the esp32 for a futur goal . the resulting device is an isolated NMEA 2000 gateway that will both read and write NMEA 2000 packets and allow your computer to interface with your boat electronics.

The test on Actisence reader sofware is ok you can download on this page https://actisense.com/downloads/?download_type&range=2608 them using the example of Timo library

https://github.com/ttlappalainen/NMEA2000/blob/master/Examples/MessageSender/MessageSender.ino

Just Adding this header below #include <Arduino.h>

#define USE_N2K_CAN 1 // Force mcp_can
#define N2k_SPI_CS_PIN 5 // Pin for SPI CAN Select

3 For GPS data on main screen i have connected  a 0183 GPS to the PC by serial com and used and give thanks to https://github.com/jamesp/node-nmea

for his node js nmea library . The main screen is an Electron Node JS app that provide  on main screen SAT in view, LAT and LONG AND COG.

For Sensor data I have used the famous MPU 6050 linked with Heading Compass to make a tilt Compass .



![ELECTRONIC Tilt Gyro Compass](https://github.com/MaxESP/ESP32-CAN-GATE-AWAY/assets/41333143/a4d379c6-4a95-4f7a-9324-8442a2d0151d)

The new Tilt Compass Gyro is launched.
Hardware
ESP32
LSM303DLH compass + mpu6050
RS485  board + CP2102 serial

![back pcb](https://github.com/MaxESP/ESP32-CAN-GATE-AWAY/assets/41333143/76101a8e-e447-40bf-9596-0d4b6ae38cae)


I have found a magic IC CH344Q to connect to my computer USB to Quad Serial Ports Chip CH344 it's perfect to receive rs485 or nmea 2000 sensors to my pc dash board above 







![usb serial x4 hub](https://github.com/MaxESP/ESP32-CAN-GATE-AWAY/assets/41333143/e34f9870-eacd-4ba0-a408-ee9e14ba09e3)
