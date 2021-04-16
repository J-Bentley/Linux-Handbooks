#### PUBLIC KEY AUTHENTICATION (Putty on Windows)  
Client: Generate a key pair with puttygen.exe (rsa-ssh2, min bit length: 1024 bits).  
Client: Copy the public key to clipboard, save private key as `rsa_id-hostname.ppk` and put it somewhere safe that it can stay, then close puttygen.  
Client: Load the private key in the PuTTY profile via `connection> ssh> auth` and make sure to save in `session`!   
Server: Create `~/.ssh/` directory if doesn't exist and paste the public key in `~/.ssh/authorized_keys`, should be all in one line (ssh-rsa your_public_key)  
```chmod 700 ~/.ssh```  
```chmod 600 ~/.ssh/authorized_keys```  
```chown $USER:$USER ~/.ssh -R```  

Open ```/etc/ssh/sshd_config```:  
- uncomment ``` AuthorizedKeysFile    /.ssh/authorized_keys```  
- uncomment and modify line to be ```PasswordAuthentication no```  
- more hardening tips in security baseline.  
```sudo service ssh restart```  
For troubleshooting ``` tail -f /var/log/auth.log```  
Note: Putty profiles are picky, ensure you are loading the profile and saving the changes you make. If you are having problems, this is prob it.    

#### Mount HDD  
```sudo lsblk```  
```sudo blkid```  
```sudo fdisk -l```  
```sudo mkfs.xfs /dev/sdx```  
```sudo mkdir /hdd```  
```sudo mount /dev/sdx /hdd```  
```sudo nano /etc/fstab:```  
```/dev/sdbx                   /hdd  xfs     defaults         0       0```  

#### ALIASES  
```sudo nano .bashrc```  
```alias updateme='sudo apt-get update && sudo apt-get upgrade -y```  

#### STATIC IP
16 :```sudo nano /etc/network/interfaces```     
18 - 20 :  
 - ```sudo nano /etc/netplan/*-netcfg.yaml```  
- ```      dhcp4: no```  
```      addresses:```  
```        - 192.168.0.2/24```  
```      gateway4: 192.168.0.1```  
```      nameservers:```  
```      addresses: [8.8.8.8]```  
 - ```sudo netplan --debug apply```    
 - ```sudo ip addr show```  
 
#### SSH / SFTP
```sudo apt-get install openssh-server```  
Config: ```sudo nano /etc/ssh/sshd_config```  
(Hardening tips can be found in [security-baseline](https://github.com/J-Bentley/Linux-Handbooks/blob/master/Security-baseline.md))  
* Show config settings:``ssh -T``  

#### Add a new sudo user: 
``` sudo adduser jordan```  
``` sudo usermod -aG sudo jordan```  
#### Change hostname: 
``` sudo nano /etc/hostname```  

#### UFW
```sudo ufw status```  
```sudo ufw enable```  
```sudo ufw default allow/deny incoming/outgoing```  
```sudo ufw allow from 192.168.0.0/24```  
```sudo ufw allow/deny <port>```  
```sudo ufw show added```  

#### FDISK  
```fdisk -l```  
```fdisk /dev/sdx```  
```d: delete partition```  
```p: list partition```  
```n: new partition```  
```w: write changes```  
```Format Disk: sudo mkfs.ext4 /dev/sdx```  
```Mount Disk: sudo mount /dev/sda/ /mnt/sda```  
```Mount on reboot via fstab: sudo nano /etc/fstab /dev/sdb```  
```/mnt/sdb      ext4        defaults      0       0  ```
  
#### Headless Transmission with Web GUI  
`sudo apt-get install software-properties-common`  
https://help.ubuntu.com/community/TransmissionHowTo  

#### OPENVPN WITH PIA VPN 
https://www.thedallemagnes.com/2016/08/26/installing-private-internet-access-with-openvpn-on-ubuntu-server/
   
#### JAVA  
```sudo add-apt-repository ppa:webupd8team/java```  
```sudo apt install default-jre```  

### SCREEN  
```screen -S <id>```  
```ctrl+a+d: to detach from session```  
```screen -r <id>```  
```screen -S <id> -X quit```  
*/var/run/screen/s-$USER: a txt file is created for each session*  

#### SYSTEMCTL  
```systemctl status/start/stop <service>.service```  
```systemctl enable/disable <service>.service: starts service at boot```  
```systemctl list-unit-files | grep enabled: shows enabled services```  
*Enabled doesn't mean it's running & running doesn't mean it's enabled!*  

#### PACKAGE MGMT  
```sudo apt-cache search <program>```  
```sudo apt list --installed | grep -i <program>```  
```sudo apt-remove --purge <program>```  

#### DPKG  
```-r <file.deb>: uninstall```  
```-i: install```  
```-l: list```  

#### PIP (preinstalled on 18.04)
```sudo nano /etc/apt/sources.list```  
   * Add universe to end of lines  
```sudo apt update ```  
```sudo apt install python3-pip```  
``` pip3 --version```  

#### LM-SENSORS  
```apt-get install lm-sensors```  
```sensors detect```  
``` sensors / watch sensors```  

#### NO-IP
``` cd /usr/local/src/```  
``` wget http://www.no-ip.com/client/linux/noip-duc-linux.tar.gz```  
```  tar xf noip-duc-linux.tar.gz```  
```  cd noip-2.1.9-1/```  
```  make install```  
``` sudo apt install build-essential```  
```  sudo apt install gcc```  
```  /usr/local/bin/noip2 -C```  
```  /usr/local/bin/noip2```  
``` Auto start on boot:https://gist.github.com/NathanGiesbrecht/da6560f21e55178bcea7fdd9ca2e39b5```  

#### PLEX 
```  wget <latestfile>.deb```  
```  sudo dpkg -i plexmediaserver*.deb```  
``` sudo systemctl enable plexmediaserver.service```  
``` sudo systemctl start/stop/status plexmediaserver.service```  
allow updating with apt-get: 
```  echo deb https://downloads.plex.tv/repo/deb public main | sudo tee /etc/apt/sources.list.d/plexmediaserver.list```  
```  curl https://downloads.plex.tv/plex-keys/PlexSign.key | sudo apt-key add -```  
```  
    * PLEX UNINSTALL: 
    * 1)Run  
    * sudo apt-get purge plexmediaserver 
    * 2) Remove bulk of plex files 
    * sudo rm -rf /var/lib/plexmediaserver 
    * 3) Remove plex user (very important!)
    * sudo userdel plex
    * 4) Remove both /etc/init/plexmediaserver.conf and /etc/default/plexmediaserver
    * sudo rm /etc/init/plexmediaserver.conf
    * sudo rm /etc/default/plexmediaserver
```  
#### IPERF  
``` Client```  
``` Server```  

#### NMAP
```  nmap <targetip> -p <port[-port2]>```  
```  nmap 192.168.0.0/24 -sn```  

#### NEOFETCH
``` sudo add-apt-repository ppa:dawidd0811/neofetch```  
```  sudo apt update && sudo apt install neofetch```  
``` config file: ${HOME}/.config/neofetch/config.conf```  
*Disable motd display by editing these two files: /etc/pam.d/login, /etc/pam.d/sshd, comment out the line that has "pam_motd"*  

#### GPU DRIVER INSTALL
```  ubuntu-drivers devices: find model/driver (ex: GTX 450/nvidia-304)```  
```  sudo apt-get install <model>```  
or  
``` sudo ubuntu-drivers autoinstall```  

#### XBOXDRV (PS3 controller)  
* apt-get install xboxdrv  
* sudo xboxdrv --detach-from-kernel --led 2 --silent
* ctrl+c to cancel, leave console window open * 

#### SAMBA
```  apt-get install samba```  
```  sudo nano /etc/samba/smb.conf```  
`path = /media/PLEX`  
`writeable = yes`  
`browseable = yes`  
`public = yes`  
`guest only = yes`  
`guest ok = yes`  
`sudo chmod -R 777 /dir/to/share`  

* Mount remote directory with FSTAB/cifs:  
`IF in PVE container, ensure not unprivildged!`  
    ``` sudo apt-get install cifs-utils```  
    ```  sudo nano /etc/fstab```   
    ```  //remote-ip/share /mount/directory cifs guest,uid=1000,iocharset=utf8 0 0```  
    ```  sudo mount -a```  
    ``` df -h```
  
#### SNAP  
```  apt-get install snap```   
```  snap install <pkg>```   
 
#### DISCORD  
``` * sudo snap install discord --classic```   
  
#### MOONLIGHT  
```  sudo snap install moonlight-qt```  

#### MISC  
``` * df -h: disk usage```  
``` pinky: users logged in```  
```  whoami```  
```  watch <cmd>: does command every 2 seconds```  
```  pwd```  
``` adduser <username>```  
`usermod -aG sudo <username>`  
`su - <username>`  
```  deluser```  
  
#### MONITORING  
``` top```  
``` ps -e```  
```iotop```  
``` top | grep <program>```  
``` sudo tshark <port> and not arp```  
