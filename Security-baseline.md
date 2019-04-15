 
## Proxmox
* NO openssh-server / vsftp (DISABLES sftp, ftp, ssh)
* Root is only user/group
#### SSL
* on 8006
#### Fail2Ban
* listening on 8006
#### UFW
* ufw allow from localnetwork/24
* ufw default deny incoming
* ufw default allow outgoing
* deny port 20-22
#### Multi-factor Authentication
* OATP



## UBUNTU 16
* Put VM in DMZ if externally facing(?)
 #### SSH
* NON-standard port
* Disable password authentication, SSH keys only
#### SFTP
* NON-standard port
* Disable root login
#### UFW
* sudo ufw default deny incoming
* ufw allow from localnetwork/24
#### FAIL2BAN
* On SSH / FTP interface
#### Multi-Factor Authentication via libpam-google-authenticator

