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


## UBUNTU 19
 #### SSH
* Disable password authentication
* SSH public/private keys on hostname basis
#### SFTP
* SFTP via openssh-server only, NO FTP via vsftpd
* Disable root login
#### UFW
* sudo ufw default deny incoming
* sudo ufw default allow outgoing
* ufw allow from 192.168.0.0/24

