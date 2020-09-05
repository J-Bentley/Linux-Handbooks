A security baseline is a list of OS configurations that must be made on a *per OS basis* before the OS should be put in production/exposed to public. Meaning, all ubuntu VMs must be setup as defined below and any new OS's used must have a secure baseline created and implemented.
 
## Proxmox
* NO openssh-server / vsftp (this ensures SFTP, FTP, SSH are not installed, should still deny packets tho)
* Root is only user/group.
#### SSL
* Proxmox's web panel port 8006.
#### Fail2Ban
* Listening on Proxmox's web panel port 8006.
#### UFW
* `sudo ufw default deny incoming`
* `sudo ufw default allow outgoing`
* `sudo ufw deny port 20-22` (only use web panel for Proxmox access)
* `sudo ufw allow from localnetwork/24`
#### Multi-factor Authentication
* OATP.


## UBUNTU 19
 #### SSH
* Disable password authentication.
* SSH public/private keys created per hostname.
#### SFTP
* SFTP via openssh-server only, NO FTP via vsftpd.
* Disable root login.
* Triple check anonymous-login is disabled.
#### UFW
* `sudo ufw default deny incoming`
* `sudo ufw default allow outgoing`
* `sudo ufw allow from localnetwork/24`

