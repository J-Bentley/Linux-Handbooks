A security baseline is a list of OS configurations that must be made on a *per OS basis* meaning, all ubuntu VMs must be setup as defined below and any new OS's used must have a secure baseline created and implemented.
 
## Proxmox
* NO openssh-server / vsftp (DISABLES sftp, ftp, ssh)
* Root is only user/group
#### SSL
* on proxmox's port 8006
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
* SFTP via openssh-server only, no FTP via vsftpd
* NON-standard port
* Disable root login
#### UFW
* sudo ufw default deny incoming
* ufw allow from 192.168.0.0/24
#### FAIL2BAN
* On SSH / FTP interface
#### Multi-Factor Authentication via libpam-google-authenticator

