By booting from USB instead of SD card, we can increase reliability over time in our storage device and take full advantage of the independant USB 3.1 channel in the RPI 4. Also, by installing a 64-bit version of Ubuntu-Server instead of 32-bit, an application can properly utilize the 8GB of RAM in the RPI4!

Pre-requisites: 
- Raspberry Pi 4 8GB model
- Micro SD Card with reader
- USB stick
- Keyboard
- Monitor and mini-HDMI cable
- Install [Raspberry Pi Imager](https://www.raspberrypi.org/software/)
- Install [SD Card Formatter](https://www.sdcard.org/downloads/formatter/)
- Download & extract [Ubuntu Server 64-bit for RPI4](https://www.raspberrypi.org/forums/viewtopic.php?t=278791)

Update Bootloader and enable USB Booting:  
- Plug your SD card into the reader and the reader into your PC, then open SD Card Formatter software and Quick-format your SD Card.
- Open Raspberry Pi Imager, click "Choose OS", go to "Misc Utilities", click "EEPROM Boot Recovery" and select the newly formated SD card. Then, click "Write".
- Eject the SD card from your PC and plug in your newly imaged SD card, mini-HDMI and power cord to the RPI4. Power on the monitor and RPI 4. Should show a green image on monitor and/or flash green indicator LED's if bootloader update was successful. Red screen if not.
- Power off RPI4 and remove SD card from RPI 4, you only need a bootable USB plugged in now!
- ([Source](https://webtechie.be/post/2020-09-29-64bit-raspbianos-on-raspberrypi4-with-usbboot/))  

Install 64-bit Ubuntu Server to RPI4:
- Plug your USB stick into your PC, then open SD Card Formatter and Quick-format your USB stick. Ensure it is formatted as ExFat, not NTFS. Format using Windows if so.
- Open Raspberry Pi Imager, click "Choose OS", select custom image and write the extracted 64bit ubuntu server "RPI USB Boot" .img file to your formatted USB.
- Eject the USB stick from your PC and plug in the newly imaged USB stick, mini-HDMI and power cord to the RPI4. Power on without an SD card inserted, just the USB stick.
- Login with `ubuntu` as user and password.
- You will then be prompted to change default ubuntu user password.
- Verify available disk space on USB: `df -h`
- Verify 64-bit: `uname -a`

OPTIONAL (create a new user, delete default user and change hostname):
- To do the following steps over SSH, plug in an ethernet cable and issue `ip addr` to find your ip address then log in with ubuntu as username and the password you just set upon first login using keybord.
- Add a new user: `sudo adduser jordan`  
- Make the new user a sudo user: `sudo usermod -aG sudo jordan`
- Login to new user: `su - jordan`
- Verify sudo priviledges of new user & reboot RPI 4 (if RPI4 restarts = success): `sudo reboot`
- Log back in with the new account and delete default ubuntu user account: `sudo deluser --remove-home ubuntu`
- Verify ubuntu user is deleted: `id ubuntu` & verify password is deleted `grep '^ubuntu' /etc/passwd` (no output = success)
- Type `sudo nano /etc/hostname` and change the default hostname to your preffered hostname.
- Find any occurance of the default hostname in `/etc/hosts` and change it to what is in `/etc/hostname`.
