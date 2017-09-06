# What is NextCloudPi?

NextCloudPi is a ready to use image for Raspberry Pi.
This code also generates the [NextCloudPi ARM docker image](https://hub.docker.com/r/ownyourbits/nextcloudpi/).

# How do I install NextCloudPi on a Raspberry Pi?

Follow the guide [How to install NextCloudPi on a Raspberry Pi](https://github.com/nextcloud/nextcloudpi/wiki/How-to-install-NextCloudPi-on-a-Raspberry-Pi). Don't forget the [Required Tasks](https://github.com/nextcloud/nextcloudpi/wiki/Required-Tasks-for-NextCloudPi).

# Why do I need to run the [Required Tasks](https://github.com/nextcloud/nextcloudpi/wiki/Required-Tasks-for-NextCloudPi)?

You only need to do that in order to make Nextcloud accessible from the outside of your house.

# Do I have to configure every entry in the WebUI and the TUI?

No. You only need to run the [Required Tasks](https://github.com/nextcloud/nextcloudpi/wiki/Required-Tasks-for-NextCloudPi). Everything else is optional.

# Can I use an external USB drive with NTFS/FAT filesystem?

No. These do not support the linux user/permission system.

# How do I connect with SSH to the Raspberry Pi?

You need to place a file named "SSH" in the boot partition of the sd card.

# What user/permissions should I have to the external USB drive mount point, the ncdata and ncdatabase directory?

| Directory | User | Group | Permissions | Permissions (numbers) |
|---|---|---|---|---|
| Mount Point | root | root | drwxr-x--x | 751 |
| ncdata | www-data | www-data | drwxr-x--- | 750 |
| ncdatabase | mysql | mysql | drwxr-x--- | 750 |

# Why NextCloudPi uses Apache and not Nginx

Read the blog [post](https://ownyourbits.com/2017/06/12/why-nextcloudpi-uses-apache-and-not-nginx/).

# Why my md5sum of the image file is different that the md5sum on the site?

The md5sum on the site is the md5sum of the tar.bz2 file that you get after you download, not the image's one.

# dd command doesn't burn the sd card correctly.

In dd command you need to specify the block device, not the partition. E.x.:

```
sudo dd bs=4M if=NextCloudPi_xx-yy-zz.img of=/dev/sda status=progress && sync
```

# How can I install Plex with NextCloudPi

First install plex, after configure NextCloudPi, upgrades, etc.

