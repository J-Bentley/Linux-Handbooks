Update Bootloader and enable USB BOOT:  
Requisites: SD Card.
- Write "EEPROM Boot Recovery" image to an SD card via [Raspberry Pi Imager](https://www.raspberrypi.org/software/). ([Source](https://webtechie.be/post/2020-09-29-64bit-raspbianos-on-raspberrypi4-with-usbboot/))
- Start pi, should show green screen and flash green leds if update was successful and USB booting is now enabled as a feature.
- Remove SD card from RPI4, don't need it again.

Install 64-bit Ubuntu Server to RPI4:  
Requisites: Monitor & keyboard.
- Format USB via SD Card Formatter.
- Write [ubuntu server 64 bit for RPI4 image](https://www.raspberrypi.org/forums/viewtopic.php?t=278791) to USB, plug into pi, power on pi.
- Login with credentials ubuntu:ubuntu 
- will be prompted to change default ubuntu user password, it doesnt matter, make it easy as we will delete this user account and make our own.
- Add a new user: `sudo adduser jordan`
- Make the new user a sudo user: `sudo usermod -aG sudo jordan`
- login to new user: `su - jordan`
- verify sudo priviledges with new user (should return a usage error, NOT permissions error): `sudo`
- delete default ubuntu user account: `sudo deluser --remove-home ubuntu`
- verify user is deleted: `id ubuntu` & `grep '^ubuntu' /etc/passwd`
