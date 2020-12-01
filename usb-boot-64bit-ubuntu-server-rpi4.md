By booting from USB instead of SD card, we can increase reliability over time in our storage device and take full advantage of the independant USB 3.1 channel in the RPI 4.
Requisites: 
- SD Card
- SD reader
- USB stick
- Keyboard
- Monitor
- Install [Raspberry Pi Imager](https://www.raspberrypi.org/software/)
- Install [SD Card Formatter](https://www.sdcard.org/downloads/formatter/)
- Download & extract [Ubuntu Server 64-bit for RPI4](https://www.raspberrypi.org/forums/viewtopic.php?t=278791)

Update Bootloader and enable USB Booting:  
- Quick-format your SD Card using SD Card Formatter software.
- Open Raspberry Pi Imager, click "Choose OS", go to Misc Utilities, write "EEPROM Boot Recovery" OS to the SD card.
- Plug in SD card and monitor. Power on RPI 4, should show a green image on monitor and/or flash green indicator LED's if bootloader update was successful. Red screen if not.
- Remove SD card from RPI 4, you only need a bootable USB plugged in now!
- ([Source](https://webtechie.be/post/2020-09-29-64bit-raspbianos-on-raspberrypi4-with-usbboot/))  

Install 64-bit Ubuntu Server to RPI4:  
- Format USB stick with FAT32 using SD Card Formatter software.
- Open Raspberry Pi Imager, click "Choose OS", select custom image and write the extracted 64bit ubuntu server "RPI USB Boot" .img file to the the your formatted USB.
- Plug in the USB and power on RPI4 without an SD card.
- Login with `ubuntu` as user and password.
- You will then be prompted to change default ubuntu user password. See optionl steps for how to create a new user, delete default ubuntu user and change the hostname.
- Verify available disk space on USB: `df -h`
- Verify 64-bit: `uname -a`

OPTIONAL:  
- Add a new user: `sudo adduser jordan`  
- Make the new user a sudo user: `sudo usermod -aG sudo jordan`
- Login to new user: `su - jordan`
- Verify sudo priviledges of new user & reboot (if RPI4 restarts = success): `sudo reboot`
- Delete default ubuntu user account: `sudo deluser --remove-home ubuntu`
- Verify ubuntu user is deleted: `id ubuntu` & verify password is deleted `grep '^ubuntu' /etc/passwd` (no output = success)
- Type `sudo nano /etc/hostname` and change the default hostname to your preffered hostname.
- Find any occurance of the default hostname in `/etc/hosts` and change it to what is in `/etc/hostname`.
