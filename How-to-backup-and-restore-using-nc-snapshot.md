# Goal

To fully backup and restore your NC instance containing:
1. NCP -configurations,
2. NC -configurations,
3. NC -database,
4. NC -data (ncdata contains all user`s files in cloud)

Snapshots are very fast and takes very little space because they are not duplicating your data while they are versioning it. In this backup strategy you use BTRFS -snapshots function included in NCP. In this setup snapshots only backs up your data -directory (4.), so you need to backup other things important to run your cloud (1, 2, 3) with using separate options that are included here. This guide is not including OS and and all apps running on it, like NCP app itself. For those you need a separate solution. But if you use SSD for OS drive its most likely more durable than HDD when it only runs OS and apps but does not store cloud data and backups. SSD running only OS and applications should last a lifetime if you look only the average read and write durability announced by manufacturer.

# Drives for this example

You can of course install your OS and all programs on one disk that also includes your Nextcloud instance with all your data and use one backupdrive for backing it up, but in this guide we use three different physical drives (HDD, SSD, thumb drive or SD):

1. OS drive for operating system (Debian strech) and programs on it named “NextcloudDrive0” and 
2. primary drive for Nextcloud instance named “NextcloudHDD1” and
3. secondary drive for Nextcloud instance backups “NextcloudHDD2”

# How to format drives

1. Partition tables: GPT
2. Encryption: LUKS (optional)
3. Filesystem: BTRFS

Big drives (bigger than 2 TB) needs to be partitioned with GPT.

Both NextcloudHDD1 and NextcloudHDD2 needs to be formatted to BTRFS to get backups working with snapshots. Using `nc-format-USB` will format the drive with the right settings. Beware that doing this will wipe out all existing data from the drive.

You may want to use LUKS full drive encryption so nobody gets your data by just taking your drive, but take into account that this could hurt performace, specially in slower boards. This can be easily done by using partitioning tools like Gnome disks or Gparted. Gnome disks might be the easiest tool for most of the people, it is usually preinstalled in Debian and Ubuntu desktop versions. 

In order to create a BTRFS partition from your PC you need to install `btrfs-tools`  

```
sudo apt install btrfs-tools
```

**NOTE**: Newest Ubuntu 18.04 LTS has support for formating drive to BTRFS with LUKS encryption in a simple way by GUI tools but for example Debian Strech Stable does not. You might be able to do it with Strech but its difficult get it working right. So use the most recent Debian based OS as you can for formatting the drives or find a guide for some more complicated way.

1. Create partition table GPT,
2. Format drive to BTRFS + LUKS by first choosing first format to btrfs and then checking the box that says use encryption. Choose your encryption pass phrase and save it to some place safe and when mounting the drive choose option to remember the passphrase.

# Steps to backup

1. For the first make scheduled BTRFS -snapshots running for your data by using NCP function `nc-snapshot-auto` for it.

     **Simple explanation**:
With the snapshots you get restore points for your data -directory, a bit similar way as you can have for your “Windows System Restore” or “Mac Time machine”. “Snapper” on linux is also using BTRFS -snapshots. Restore points with BTRFS -snapshots normally live inside the same drive as you have the data -directory to restore. Every single snapshot represents the state of the data -directory on one specific point of time. Snapshot contains the files that are deleted after one version earlier and links to all the files that where represented in that specific version of data -directory. When you run snapshots all your deleted data are stored in the snapshots for some specific retention time that is configured. In NCP you configure how many snapshots you keep before they are deleted. Because of this snapshots -directory as a whole can be defined as historical log of the original directory, but is containing also the deleted data. So running BTRFS -snapshots using NCP -functions protects you from data alteration or deletion on the data -directory, but it wont protect you from braking of the drive you run them in. So that’s why you need to also do the step 2.

2. Run the scheduled sync function for the BTRFS -snapshots to backup to the NextcloudHDD2 by using the NCP function nc-snapshot-sync for it.

     **Simple explanation**:
Scheduled syncing of the snapshots is periodically copying all your new snapshots to your NextcloudHDD2, so you get fully replicated snapshots including all your data in data -directory. So after this you have full backup of your data -directory with versioning but this data directory on backup drive is “invisible” for regular file explorer.


3. Make sheduled data less backup to the NextcloudHDD2 using NCP function nc-backup-auto.

     **Simple explanation**:
This is for backing up your NC -configurations and for your NC -database. Sheduled dataless backup means nc-backup-auto function in NCP when you do not choose to include data fom the options.

4. Make backup of your NCP -configurations to the NextcloudHDD2 using NCP function nc-export-ncp for it. This is the last step so you get the configurations you just made earlier saved to the first backup.

# Steps to restore after NextcloudHDD1 gets broken

1. Restore your NCP configurations using NCP function nc-import-ncp for it (not needed if NCP was not installed on NextcloudHDD1).

2. Restore your nextcloud configurations and database from data less backup by using NCP function nc-restore.

3. Restore your ncdata -directory from snapshots inside your backup drive

To restore inside backup drive:

 > sudo btrfs subvolume snapshot /media/NextcloudHDD2/ncp-snapshots/daily-xxxxx /media/NextcloudHDD2/ncdata

**NOTE**: like explained above the snapshots logs are linked to the hidden data on your NextcloudHDD2 so you have to restore from snapshots to inside the backupdrive not to the new replacement drive that replaces NextcloudHDD1.

4. Copy the just restored data -directory to the new replacement drive the new NextcloudHDD1, by these steps

Turn maintenance mode on:

 > ncc maintenance:mode –on

Delete manually the data -directory that has been created automatically to the new NextcloudHDD1. If there is already snapshots running on the new replacement drive delete the directory by:

 > sudo btrfs subvolume delete /media/NextcloudHDD1/ncdata

Copy manually the just restored data -directory (one version) from the NextcloudHDD2 to NextcloudHDD1
  
OR

You can also use btrfs-sync to copy the snapshots (all versions) from NextcloudHDD2 to NextcloudHDD1


 > btrfs-sync /media/NextcloudHDD2/.snapshots /media/NextcloudHDD1/snapshots


Turn the maintanence mode off:


 > ncc maintenance:mode –off


Make the Nextcloud instance aware of the restored data files by running the ncp-app `nc-scan`.