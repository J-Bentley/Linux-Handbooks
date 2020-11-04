### QM
* list: find vm ids
* start/stop/destroy <vmid>
* config <vmid>: see vm performance

### ADD NEW DISK
* fdisk -l
* fdisk /dev/sdX (x = disk ID)
* d, delete all partitions, g for GPT label if disk over 2 TB, n new partition, w write partition
* pvcreate /dev/sdX[Y] (include partion number)
* vgcreate newdrivename /dev/sdX[Y]
* Datacentre > Stroage > Add > LVM
