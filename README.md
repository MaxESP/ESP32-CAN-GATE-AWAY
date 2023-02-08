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

for his node js nmea library . It's provide on main screen SAT in view, LAT and LONG AND COG



