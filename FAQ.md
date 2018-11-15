### What is NextCloudPi?

NCP an officially recognized Nextcloud community project that provides a working Nextcloud instance out of the box in the form of SD card image for the Raspberry Pi, Odroid HC1 and other boards, x86 and ARM docker containers, and an installer for any Debian-based system.

### How do I install NextCloudPi on a Raspberry Pi?

Follow the guide [How to install NextCloudPi](https://github.com/nextcloud/nextcloudpi/wiki/How-to-install-NextCloudPi).

### I get stuck at "NC not yet initialized..." / Nextcloud is so slow / failing randomly / getting server errors even with a fresh image?

Most commonly these things are caused by hardware problems.

 - **Check your SD card**: take it out, copy the whole image to your computer and then copy it back to the SD. Assert that there are no read/write errors. You can also check the md5sum after reading it again and assert that it matches the md5sum of the image that you just copied.
 - **Check your power supply**. Many cheap power supplies are not stable enough for reliable functioning. Also try to have external supplies for your external HDDs.

### How can I access from outside my home network?

See [this guide](https://github.com/nextcloud/nextcloudpi/wiki/How-to-access-from-outside-your-network)

### I have been updating through `nc-update` but why isn't Nextcloud on the latest version?

`nc-update` only updates NextCloudPi related stuff. In order to upgrade the Nextcloud instance itself you use `nc-update-nextcloud`.

### Do I have to configure every entry in the WebUI and the TUI?

No. You only need to run the Wizard to have a working Nextcloud instance. Everything else is optional.

### Can I use an external USB drive with NTFS/FAT filesystem?

No. These do not support the linux user/permission system.

You can read/write to NTFS/FAT filesystems, but the permissions need to be set for the whole drive, which leads to many problems.

Secondly, the performance can be really bad in linux, and this is very noticeable on the pi.

For this reasons, this is not supported. Do it at your own risk.

### How do I connect with SSH to NextCloudPi?

There are three ways.

1. From ncp-web, activate SSH from the `SSH` option.
2. (Rpi only) You can place an empty file named `ssh` in the boot partition of the sd card (so `/boot/ssh`)
3. (Rpi only) You can connect a keyboard and screen to the Raspberry Pi, log in and activate it typing `sudo raspi-config`, then go to the option 'Interfacing Options' > 'SSH'

### Is there a changelog?

Yes, it's [here](https://github.com/nextcloud/nextcloudpi/blob/master/changelog.md)

### What are pre-set users/passwords on NextCloudPi?

There are no pre-set passwords, the following are randomly generated upon first access during activation.

* For terminal `pi`/`raspberry` (`root`/`1234` on Armbian)
* For SSH: generated on demand on ncp-web `SSH` section.
* For nextcloudpi.local:4443 `ncp`/`<random>`  
* For nextcloudpi.local `ncp`/`<random>`
* For Database user is `ncadmin`/`<random in /root/.my.cnf>`

### What user/permissions should I have to the external USB drive mount point, the ncdata and ncdatabase directory?

| Directory | User | Group | Permissions | Permission mask |
|---|---|---|---|---|
| Mount Point | root | root | drwxr-x--x | 751 |
| ncdata | www-data | www-data | drwxr-x--- | 750 |
| ncdatabase | mysql | mysql | drwxr-xr-x | 755 |

### Why does NextCloudPi uses Apache and not Nginx?

Read the blog [post](https://ownyourbits.com/2017/06/12/why-nextcloudpi-uses-apache-and-not-nginx/).

### Why is my md5sum of the image file different than the md5sum on the site?

The md5sum on the site is the md5sum of the `tar.bz2` file that you get after you download, not the image's one.

### Why `dd` command doesn't burn the sd card correctly?

In `dd` command you need to specify the block device, not the partition. E.x.:

```
sudo dd bs=4M if=NextCloudPi_xx-yy-zz.img of=/dev/sda status=progress && sync
```
### Can I boot NextCloudPi from a USB drive instead of the SD card?

Yes, it can be done following [this guide](https://www.raspberrypi.org/documentation/hardware/raspberrypi/bootmodes/msd.md)

### What if my ISP doesn't allow me to open ports 80 and/or 443?

You can change the port in the apache virtual host files ( in `/etc/apache2/sites-available` ), but the Let's Encrypt authentication process won't work for you.

### How do I set up Let's Encrypt with blocked ports?

 - If you only have port 443 available, you can use the following workaround: copy that code and after that try again from the web interface or `nextcloudpi-config`

```
sudo wget https://raw.githubusercontent.com/nextcloud/nextcloudpi/beb9bc1ee2909a1ab6bfde7398ddf19a50d02478/etc/nextcloudpi-config.d/letsencrypt.sh -O /usr/local/etc/nextcloudpi-config.d/letsencrypt.sh
```

- If you don't have port 443 available, you will have to do it manually. You can use the Let's Encrypt DNS challenge authentication for this ( [wiki entry](https://github.com/nextcloud/nextcloudpi/wiki/How-to-get-certificate-with-Letsencrypt-using-DNS-to-verify-domain) ).

Also, see [this page](https://github.com/nextcloud/nextcloudpi/wiki/Why-is-my-Pi-so-slow%3F) on performance tips.