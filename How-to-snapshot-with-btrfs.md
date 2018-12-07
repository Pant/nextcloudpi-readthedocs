For now all info on this subject is [here](https://ownyourbits.com/category/btrfs/)

In order to restore the data from a snapshot, you replace the ncdata subvolume, as **for example**:

### To remove datadir
`sudo btrfs subvolume delete /media/USBdrive/ncdata` 

### To restore old copy
`sudo btrfs subvolume snapshot /media/USBdrive/ncp-snapshots/daily-xxxxx /media/USBdrive/ncdata`

### To update NC database with the new/old files                    
`nc-scan`                                       
