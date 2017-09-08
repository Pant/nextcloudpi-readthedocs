### What is NextCloudPi?

NextCloudPi is a ready to use image for Raspberry Pi.
This code also generates the [NextCloudPi ARM docker image](https://hub.docker.com/r/ownyourbits/nextcloudpi/).

### How do I install NextCloudPi on a Raspberry Pi?

Follow the guide [How to install NextCloudPi on a Raspberry Pi](https://github.com/nextcloud/nextcloudpi/wiki/How-to-install-NextCloudPi-on-a-Raspberry-Pi). Don't forget the [Required Tasks](https://github.com/nextcloud/nextcloudpi/wiki/Required-Tasks-for-NextCloudPi).

### Why do I need to run the [Required Tasks](https://github.com/nextcloud/nextcloudpi/wiki/Required-Tasks-for-NextCloudPi)?

You only need to do that in order to make Nextcloud accessible from the outside of your house.

### Do I have to configure every entry in the WebUI and the TUI?

No. You only need to run the [Required Tasks](https://github.com/nextcloud/nextcloudpi/wiki/Required-Tasks-for-NextCloudPi). Everything else is optional.

### Can I use an external USB drive with NTFS/FAT filesystem?

No. These do not support the linux user/permission system.

### How do I connect with SSH to the Raspberry Pi?

There are two ways.

1. You can place an empty file named `ssh` in the boot partition of the sd card (so `/boot/ssh`)
2. You can connect a keyboard and screen to the Raspberry Pi, log in and activate it typing `sudo raspi-config`, then go to the option 'Interfacing Options' > 'SSH'

### What user/permissions should I have to the external USB drive mount point, the ncdata and ncdatabase directory?

| Directory | User | Group | Permissions | Permission mask |
|---|---|---|---|---|
| Mount Point | root | root | drwxr-x--x | 751 |
| ncdata | www-data | www-data | drwxr-x--- | 750 |
| ncdatabase | mysql | mysql | drwxr-xr-x | 755 |

### Why NextCloudPi uses Apache and not Nginx

Read the blog [post](https://ownyourbits.com/2017/06/12/why-nextcloudpi-uses-apache-and-not-nginx/).

### Why my md5sum of the image file is different that the md5sum on the site?

The md5sum on the site is the md5sum of the `tar.bz2` file that you get after you download, not the image's one.

### `dd` command doesn't burn the sd card correctly.

In `dd` command you need to specify the block device, not the partition. E.x.:

```
sudo dd bs=4M if=NextCloudPi_xx-yy-zz.img of=/dev/sda status=progress && sync
```
### Can I boot NextCloudPi from a USB drive instead of the SD card?

Yes, it can be done following [this guide](https://www.raspberrypi.org/documentation/hardware/raspberrypi/bootmodes/msd.md)

### My ISP doesn't allow me to open ports 80 and/or 443

You can change the port in the apache virtual host files ( in `/etc/apache2/sites-available` ), but the Let's Encrypt authentication process won't work for you.

### How to set up Let's Encrypt with blocked ports?

 - If you only have port 443 available, you can use the following workaround: copy that code and after that try again from the web interface or `nextcloudpi-config`

```
sudo wget https://raw.githubusercontent.com/nextcloud/nextcloudpi/beb9bc1ee2909a1ab6bfde7398ddf19a50d02478/etc/nextcloudpi-config.d/letsencrypt.sh -O /usr/local/etc/nextcloudpi-config.d/letsencrypt.sh
```

- If you don't have port 443 available, you will have to do it manually. You can use the Let's Encrypt DNS challenge authentication for this.

### Nextcloud is too slow / I get random failures / I get server errors even with a fresh image

Most commonly these things are caused by hardware problems.

 - Check your SD card: take it out, copy the whole image to your computer and then copy it back to the SD. Assert that there are no read/write errors
 - Check your power supply. Many cheap power supplies are not stable enough for reliable functioning. Also try to have external supplies for your external HDDs.

### How can I install Plex with NextCloudPi

First install plex, after configure NextCloudPi, upgrades, etc.

