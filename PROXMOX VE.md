### Format and mount a disk permanently using its's UUID
* find disk name and uuid `lsblk`  
* format `mkfs.ext4 /dev/sdX`  
* mount `mkdir /mnt/sdX/;mount /dev/sdX /mnt/sdX/`  
* auto mount at boot via fstab `UUID=XXXX-XXXX-XXXX-XXXX-XXXX     /archive ext4 errors=remount-ro 0 1`    
### QM
* list: find vm ids
* start/stop/destroy <vmid>
* config <vmid>: see vm performance

### STORAGE
* pvcreate /dev/sdx[y] (include partion number)
* vgcreate name /dev/sdx[y]
https://proxmoxve.blogspot.com/2013/12/how-to-add-extra-storage-in-proxmox-ve.html

### pveperf
* test system perforamnce
