#### ALIASES  
```sudo nano .bashrc```  
```alias updateme='sudo apt-get update && sudo apt-get upgrade -y```  
#### STATIC IP
```sudo nano /etc/network/interfaces```
* iface eth0 inet static
    * address
    * netmask 
    * network
    * gateway 
    * dns-nameservers  
    
```sudo nano /etc/netplan/01-netcfg.yaml```  
* network:  
  * version: 2  
  * renderer: networkd  
  * ethernets:  
    * ens3:  
      * dhcp4: yes  

#### SSH / SFTP
```sudo apt-get install openssh-server```  
```sudo nano /etc/ssh/sshd_config```  
```sudo nano .ssh/authorized_keys```  

#### UFW
```sudo ufw status```  
```sudo ufw enable```  
```sudo ufw default allow/deny incoming/outgoing```  
```sudo ufw allow from 192.168.0.0/24```  
```sudo ufw allow/deny <port>```  
```sudo ufw show added```  

#### GNOME
``` ubuntu 16 gnome tweaks go here :p```
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

#### PRIVATE INTERNET ACCESS (headless)  
```sudo apt-get install openvpn```  
```cd /etc/openvpn```  
```sudo wget https://www.privateinternetaccess.com/openvpn/openvpn.zip```  
```sudo unzip openvpn.zip```  
```sudo cp Netherlands.ovpn pia-nl.conf```  
```sudo nano pia-nl.conf```  
```Change:```  
```auth-user-pass```  
```To:```  
```auth-user-pass login.conf```  
```sudo vi login.conf```  
```yourPIAusername```  
```yourPIApassword```  
```sudo vi /etc/default/openvpn```  
```AUTOSTART="pia-nl"```  
```wget -q -O - ipecho.net/plain```  
   
#### JAVA  
```sudo add-apt-repository ppa:webupd8team/java```  
```sudo apt install default-jre```  

### SCREEN  
```screen -S <id>```  
```ctrl+a+d: to detach from session```  
```screen -r <id>```  
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
* Mount remote directory with FSTAB/cifs:  
    ```  sudo nano /etc/fstab```   
    ``` sudo apt-get install cifs-utils```  
    ```  //remote-ip/share /mount/directory cifs guest,uid=1000,iocharset=utf8 0 0```  
    ```  sudo mount -a```  
  
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
``` adduser```  
```  deluser```  
  
#### MONITORING  
``` top```  
``` ps -e```  
```iotop```  
``` top | grep <program>```  
``` sudo tshark <port> and not arp```  
  
