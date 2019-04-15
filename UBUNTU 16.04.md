#### STATIC IP
* sudo nano /etc/network/interfaces
* iface ens33 inet static
    * address 192.168.0.
    * netmask 255.255.255.0
    * network 192.168.0.0
    * gateway 192.168.0.1
    * dns-nameservers 192.168.0.1

SSH
sudo apt-get install openssh-server
sudo nano /etc/ssh/sshd_config
sudo nano .ssh/authorized_keys

FTP (not needed for SFTP)
sudo apt-get install vsftpd
sudo nano /etc/vsftpd.conf

UFW
sudo ufw default deny incoming
sudo ufw default allow outgoing
sudo ufw status
sudo ufw enable
sudo ufw allow from 192.168.0.0/24
sudo ufw allow/deny <port>
sudo ufw show added

FDISK
fdisk -l
fdisk /dev/sdx
d: delete partition
p: list partition
n: new partition
w: write changes

JAVA
sudo add-apt-repository ppa:webupd8team/java
sudo apt install oracle-java8-installer
sudo apt install default-jre

SCREEN
screen -S <id>
ctrl+a+d: detach
screen -r <id>
/var/run/screen/s-$USER: screen sessions

SYSTEMCTL
systemctl status/start/stop <service>.service
systemctl enable/disable <service>.service: starts service at boot
systemctl list-unit-files | grep enabled: shows enabled services 
(Enabled doesn't mean it's running & running doesn't mean it's enabled.)

PACKAGE MGMT
sudo apt-cache search <program>
sudo apt list --installed | grep -i <program>
sudo apt-remove --purge <program>

DPKG
-r <file.deb>: uninstall
-i: install
-l: list 

PYTHON
sudo add-apt-repository ppa:jonathonf/python-3.6
sudo apt-get install python3.6
sudo update-alternatives --install /usr/bin/python3 python3 /usr/bin/python3.5 1
sudo update-alternatives --install /usr/bin/python3 python3 /usr/bin/python3.6 2
sudo update-alternatives --config python3
python3 -V
[see:http://ubuntuhandbook.org/index.php/2017/07/install-python-3-6-1-in-ubuntu-16-04-lts/]

PIP
sudo apt install python3-pip
pip3 --version

LM-SENSORS
apt-get install lm-sensors
sensors detect
sensors / watch sensors

NO-IP
cd /usr/local/src/
wget http://www.no-ip.com/client/linux/noip-duc-linux.tar.gz
tar xf noip-duc-linux.tar.gz
cd noip-2.1.9-1/
make install
sudo apt install build-essential
sudo apt install gcc
/usr/local/bin/noip2 -C
/usr/local/bin/noip2

PLEX
wget https://downloads.plex.tv/plex-media-server/1.5.5.3634-995f1dead/plexmediaserver_1.5.5.3634-995f1dead_amd64.deb
sudo dpkg -i plexmediaserver*.deb
sudo systemctl enable plexmediaserver.service
sudo systemctl start/stop/status plexmediaserver.service

PLEX UNINSTALL:
1)Run 
sudo apt-get purge plexmediaserver
2) Remove bulk of plex files
sudo rm -rf /var/lib/plexmediaserver
3) Remove plex user (very important!)
sudo userdel plex
4) Remove both /etc/init/plexmediaserver.conf and /etc/default/plexmediaserver
sudo rm /etc/init/plexmediaserver.conf
sudo rm /etc/default/plexmediaserver

NMAP
nmap <targetip> -p <port[-port2]>
nmap 192.168.0.0/24 -sn

NEOFETCH
sudo add-apt-repository ppa:dawidd0811/neofetch
sudo apt update && sudo apt install neofetch
config file: ${HOME}/.config/neofetch/config.conf
disable motd display by editing these two files: /etc/pam.d/login, /etc/pam.d/sshd, comment out the line that has "pam_motd"

GPU DRIVER INSTALL
ubuntu-drivers devices: find model/driver (ex: GTX 450/nvidia-304)
sudo apt-get install <model>
or
sudo ubuntu-drivers autoinstall

XBOXDRV (PS3 controller)
apt-get install xboxdrv
sudo xboxdrv --detach-from-kernel --led 2 --silent
ctrl+c to cancel, leave console window open

SAMBA
apt-get install samba
sudo nano /etc/samba/smb.conf
Mount remote directory with FSTAB/cifs:
sudo nano /etc/fstab
sudo apt-get install cifs-utils
//remote-ip/share /mount/directory cifs guest,uid=1000,iocharset=utf8 0 0
sudo mount -a

SNAP
apt-get install snap
snap install <pkg>

DISCORD
sudo snap install discord --classic

MOONLIGHT
sudo snap install moonlight-qt

MISC
df -h: disk usage
pinky: users logged in
whoami
watch <cmd>: does command every 2 seconds
pwd
adduser
deluser

MONITORING
top
ps -e
iotop
top | grep <program>
sudo tshark <port> and not arp
