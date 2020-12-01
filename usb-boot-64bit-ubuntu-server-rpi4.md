Update Bootloader and enable USB BOOT:  
Requisites: SD Card.
- Write "EEPROM Boot Recovery" image to an SD card via [Raspberry Pi Imager](https://www.raspberrypi.org/software/). ([Source](https://webtechie.be/post/2020-09-29-64bit-raspbianos-on-raspberrypi4-with-usbboot/))
- Start RPI, should show green screen and flash green LED's if update was successful and USB booting is now enabled as a feature.
- Remove SD card from RPI4, only need a bootable USB plugged in now!

Install 64-bit Ubuntu Server to RPI4:  
Requisites: Monitor & keyboard.
- Format a USB with FAT32 via [SD Card Formatter]().
- Download [Ubuntu Server 64-bit for RPI4](https://www.raspberrypi.org/forums/viewtopic.php?t=278791) and extract it.
- Using [Raspberry Pi Imager](https://www.raspberrypi.org/software/), select custom image and write the extracted img file to the the your formatted USB.
- Plug in the USB and power on RPI4 without an SD card.
- Login with `ubuntu` as user and password.
- You will then be prompted to change default ubuntu user password. See optionl steps for how to create a new user, delete default ubuntu user and change the hostname.
- Verify available disk space on USB: `df -h`
- Verify 64-bit: `uname -a`

OPTIONAL:
Requisites: Monitor & keyboard.
- Add a new user: `sudo adduser jordan`
- Make the new user a sudo user: `sudo usermod -aG sudo jordan`
- Login to new user: `su - jordan`
- Verify sudo priviledges of new user & reboot (if RPI4 restarts = success): `sudo reboot`
- Delete default ubuntu user account: `sudo deluser --remove-home ubuntu`
- Verify ubuntu user is deleted: `id ubuntu` & verify password is deleted `grep '^ubuntu' /etc/passwd` (no output = success)
