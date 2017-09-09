# **![Amiibomb](https://github.com/peacepenguin/AmiiBomb-uino/blob/master/logo.png) AmiiBomb**

AmiiBomb is a Windows tool built with cheap components for creating and cloning NTAG215 based-figures

## What you need?

- *1x* Windows PC   
- *1x* Arduino Uno R3 *(around $4)*  
   OR ESP32 DOIT DEVKIT V1 (any ESP32 dev board should work fine)    
- *1x* Arduino IDE with ESP32 Arduino core installed *(Only for ESP32)*
- *1x* *1x* USB Cable Type AB *(comes with Uno R3)* (Uno R3)   
   OR  USB to USB mini *(very common)* (ESP32)   
- *1x* RFID Module RC522 *(around $2)*  
- *7x* Pin Wire Male-Female *(around $1 for x20)* (Uno R3)   
   OR *7x* Pin Wire Female-Female *(around $1 for x20)* (ESP32)  
- *1x* Soldering Iron Kit *(and a little soldering skills)*  
- Many NTAG215 as you want NTAG215 based-figures *(around $34 for x100)*  



## What you have to do?

You have to solder the pins on the RC522 Module and connect them following this schematics. Connect the device to the PC by USB and that's all! (Guys with soldering skills already know that but I prefer explain for anyone!)


## Arduino UNO R3 - RC522 Pins
![Arduino / RC255 PinOut](https://github.com/peacepenguin/AmiiBomb-uino/blob/master/arduino-uno-r3--rfid-rc522.png)  
  
Signal    | RC522 Pin | Uno R3 Pin  
--------- | --------- | -----------  
RST/Reset | RST       | 9  
SPI SS    | SDA(SS)   | 10  
SPI MOSI  | MOSI      | 11 / ICSP-4   
SPI MISO  | MISO      | 12 / ICSP-1   
SPI SCK   | SCK       | 13 / ICSP-3   
VCC       | 3.3V      | 3.3V  

## ESP32 PinOut - RC522 Pins  
![ESP32-DOIT-V1 / RC255 PinOut](https://github.com/peacepenguin/AmiiBomb-uino/blob/master/esp32-doit-devkit-v1--rfid-rc522.PNG)  
  
Signal    | RC522 Pin | ESP32 Pin  
--------- | --------- | -----------  
SPI SS    | SDA(SS)   | 5  
SPI SCK   | SCK       | 18  
SPI MOSI  | MOSI      | 23  
SPI MISO  | MISO      | 19  
~         | IRQ       | ~  
GND       | GND       | GND  
RST/Reset | RST       | 22  
VCC       | 3.3V      | 3.3V  
  

## Flash Amiibombuino Firmware to ESP32

ESP32 only: Configure the ESP32 device to work with the Arduino IDE by installing the ESP32 Arduino Core  
(this link is the official ESP32 Arduino core repository):  
https://github.com/espressif/arduino-esp32  
  
Download the GIT repository/folder containing the esp32 version of Amiibombuino: "AmiiBombuino-esp32.ino" from:  
  
https://github.com/peacepenguin/AmiiBomb-uino/tree/master/AmiiBombuino  
  
Use the Arduino IDE:  
set the board to "ESP32 Dev Module"  
set the COM port  
open and "upload" AmiiBombuino-esp32.ino  

The ESP32 is now ready to use in Amiibomb on windows. Don't attempt to flash amiibombuino from within amiibomb to an ESP32 board. 

Pre-compiled builds for flashing within amiibomb may be added eventually, for now though the ESP32 must have AmiiBombuino firmware flashed onto them using the Arduino IDE with the ESP32 core added.


## And when the hardware is ready?
 
You have to run AmiiBomb, Set a working folder (*.bin files), select the Keys, flash the AmiiBombuino Firmware to the Arduino, and you are ready to Read and Write NTAG215 based-figures.


 - ***.bin folder**

It's the folder where you can put your NTAG215 based-figure dumps (previously dumped with AmiiBomb or found on internet, Google is your friend for that).  
You can save the read NTAG215 based-figures here too, to write it back to another NTAG. You don't have to re-execute AmiiBomb, it's looking for folder changes automatically.

 - **Keys**

You probably already have them if you know a little how NTAG215 based-figures cloning works. If not, a little helper is here in AmiiBomb. Due to Copyright reason, we can't distribute them, but there is many place to found them. AmiiBomb send you to the right website, you just have to highlight the keys chars and copy them to your Clipboard, AmiiBomb check if the valid keys was inside, and ask you if you want to save them. If you have already them, you just have to select the keys file.

- **AmiiBombuino Firmware**

Just an Arduino program who communicate with AmiiBomb, You can flash it through avrdude by yourself or using the Internal Flasher in AmiiBomb or using XLoader. amiibomuino can also be compiled and installed manually using the Arduino IDE.

## Overview

![](http://i68.tinypic.com/dwe7g6.png) 
![](http://i67.tinypic.com/4sjvd3.png) 
![](http://i66.tinypic.com/21mtao8.jpg) 
![](http://i66.tinypic.com/1z6z0o1.png) 

  
## What is done?  
Grab info of an Amiibo Dump via http://Amiibo.life website.  
Cache system for Amiibo Dump informations in a file.  
Enable/Disable and Reset Informations Caching files.  
Reconize encrypted/decrypted Amiibo Dump.  
Decrypt/Encrypt Amiibo Dump.  
Able to fix the incorrect size of one type of Amiibo Dump (Power Saves or N2? I don't know:/)  
Dump and Write AppData of an Amiibo Dump.  
Help to found Amiibo Keys and Autodetect them in Clipboard for save them in file.  
Multilanguages.  
Read a NTAG215 and save it to an Amiibo Dump file.  
Write an Amiibo Dump file to an NTAG215.  
Flash AmiiBombuino Firmware inside AmiiBomb.  
Get Amiibo Tag Basic Informations.  
and more...  
  
## What's Next?
Many little things to do AmiiBomb more User Friendly.  
Clean the code.  
It's work really fine with an NTAG215 but I don't know if it's work with an Amiibo ^^'!  
AppData editor (for SSB Amiibo or any others who have interesting things inside).  
Support PN532 NFC Module in AmiiBombuino.  
Improve the docs.  
Release  
  
## ChangeLog 
v0.3 Alpha:  
Fix:  
Fix bug of AmiiBombuino check on busy COM port. (Thanks dtomcat)  
Detect when Tag is not compatible. (Suggest by YozenPL)  
Add a forget message when delete cache files is done.  
Change way to detect if .bin file is encrypted.  
  
Improvement:  
Increase AmiiBombuino RxGain to read Boxed Amiibo. (Thanks StandardBus)  
Add folders browsing inside the Bin Folder. (Suggest by donator TerryG)  
Add ability to search Amiibo files. (Suggest by Zarklord)  
Keyboard Shortcuts added. (Suggest by YozenPL)  
Add Donators to the About windows.  
  
New:  
Add Spoof UID of .bin file (For N2/PowerTag).  
Add Support AmiiboAPI to get Amiibo informations. (Thanks N3evin - AmiiboAPI owner)  
Add Twilight Princess Wolf AppData Editor.  
Add Support of PowerSaves for Dump (Thanks ConsoleX for donate PowerSaves/PowerTag)   
  
Translation:  
Russian translation added. (Thanks Chrushev)  
Netherlands translation added. (Thanks DjoeN)  

## Build Instructions (Advanced Users, Bug Testers, and Developers Only)
For Amiibomb Executable on Windows (this does not yet auto-compile the arduino hex files!)  
Prereqs:  
Windows 7 or higher (most testing was done in Windows 10 Pro x64, 1703)  
.net 4.6.1 (or higher, Win 10 has 4.7 by default)  
Install Visual Studio 2017 Community Edition  
Install "GIT for Windows" (visual studio can install this for you, or install it manually)  
Open "GIT BASH", then run these commands:  
cd /c  
mkdir Amiibomb  
cd Amiibomb  
git clone https://github.com/peacepenguin/AmiiBomb-uino.git  
Open the AmiiBomb.sln file using Visual Studio. (C:\Amiibomb\Amiibomb-uino\Amiibomb.sln)  
Click "Build" -> "Rebuild Solution"  
Compilation should occur, the resulting EXE file can be found and launched from:  
c:\Amiibomb\Amiibomb-uino\Amiibomb\bin\Debug\  


