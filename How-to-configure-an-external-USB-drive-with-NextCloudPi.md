This guide will help you configure an external USB drive.

# Procedure
1. Format USB drive (optional but check note).
2. Enable automount.
3. Configure Nextcloud data to be on the USB drive.
4. Configure Database data to be on the USB drive (optional).
5. Configure Swap on the USB drive (optional).

# Format USB drive (optional)

"nc-format-USB" will format your external USB drive to EXT4, with the given Label. 

_**Note:**_  _In order for you to be able to use an external USB drive, the USB drive must not be formatted as NTFS/FAT as these do not support the user/permission system._

1. Navigate to "nc-format-USB" in the TUI or the WebUI.
2. Change the LABEL to a label you like. This is also the name of the directory that the USB drive will mount to (e.x. /media/"myLabel").
3. Click Run or Start.

# Enable automount

To enable automount follow the steps:

1. Navigate to "nc-automount" in the TUI or the WebUI.
2. Change "ACTIVE" to yes.
3. Click Run or Start.

# Configure Nextcloud data to be on the USB drive

To make Nextcloud data directory to be on the USB drive, follow the steps:

1. Navigate to "nc-datadir" in the TUI or the WebUI.
2. Change "DATADIR" to your data location in the mount point.
3. Click Run or Start.

# Configure Database data to be on the USB drive (optional).

To make Database data to be on the USB Drive, follow the steps:

1. Navigate to "nc-database" in the TUI or the WebUI.
2. Change "DBDIR" to your database location in the mount point.
3. Click Run or Start.

# Configure Swap on the USB drive (optional).

To configure Swap location and size, follow the steps:

1. Navigate to "nc-swapfile" in the TUI or the WebUI.
2. Change the SWAPFILE to the desired location in the mount point.
3. Change the SWAPSIZE to the desired size of Swap File (Default: "1024MB").

# Final Words

Now you have configured NextCloudPi to use an external USB drive for Nextcloud data, optionally Database data and Swap.
