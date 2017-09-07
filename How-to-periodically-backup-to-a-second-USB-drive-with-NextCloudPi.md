This guide will help you set up automatic backup to a second USB drive.

## Procedure
1. Complete at least steps 2 and 3 of the [[Guide to configure an external USB drive with NextCloudPi|How-to-configure-an-external-USB-drive-with-NextCloudPi]].
2. Format second USB drive with "[[nc-format-USB|Configuration-Reference#nc-format-usb]]" (optional but see Note).
3. Configure and activate "[[nc-backup-auto|Configuration-Reference#nc-backup-auto]]" to the second USB drive".

## Complete required steps from the [[Guide to configure an external USB drive with NextCloudPi|How-to-configure-an-external-USB-drive-with-NextCloudPi]]

You first need to configure this guide. "[[nc-backup-auto|Configuration-Reference#nc-backup-auto]]" is going to retrieve Nextcloud directory and database and backup them.

## Format second USB drive with "[[nc-format-USB|Configuration-Reference#nc-format-usb]]" (optional but see Note)

**IMPORTANT:** To format the second USB drive with "[[nc-format-USB|Configuration-Reference#nc-format-usb]]" you first need to remove the first USB drive!

> **Note: _The disk must not be formated as NTFS/FAT as these do not support the user/permission system.

1. Remove the first USB drive.
2. Navigate to "[[nc-format-USB|Configuration-Reference#nc-format-usb]]" in the TUI or the WebUI.
3. Change the "LABEL" to a label you like. This is also the name of the directory that the USB drive will mount to (e.x. /media/"myLabel"). **Do not use the same Label to both USB drives!**
4. Click Run or Start.

## Confi"nc-format-USB"gure and activate "[[nc-backup-auto|Configuration-Reference#nc-backup-auto]]" to the second USB drive

1. Navigate to "[[nc-backup-auto|Configuration-Reference#nc-backup-auto]]" in the TUI or the WebUI.
2. Change "ACTIVE" to "yes".
3. Change "DESTDIR" to the mount point of the second USB drive.
4. Change "ICLUDEDATA" to "yes" if you want to backup Nextcloud data as well (optional).
5. Change "BACKUPDAYS" to a desired number of days to take each backup.
6. Change "BACKUPLIMIT" to a desired amount of backup limit. This means that for example if you set to 3 and time comes to take an other backup, the first back up will be removed and replaced with the new one.

## Final words

This is what you have to do to enable Auto Backups.
