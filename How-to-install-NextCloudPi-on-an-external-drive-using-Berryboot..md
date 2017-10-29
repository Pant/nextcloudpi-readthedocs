A step by step guide to installing NextCloudPi to an external drive using Berryboot.
In first place we need to install Berryboot, a bootloader and management tool for OS installations on your Raspberry Pi. You will choose where your NextCloud installation will reside in this part.  In second place we will use specially formatted image to install the NextCloudPi

Part 1: First time boot and choosing device to install Nextcloud to.

1. Download [berryboot-20170527-pi2-pi3.zip](http://downloads.sourceforge.net/project/berryboot/berryboot-20170527-pi2-pi3.zip) if you have a quadcore RPI. Download [berryboot-20170527-pi0-pi1-pi2-pi3.zip](http://downloads.sourceforge.net/project/berryboot/berryboot-20170527-pi0-pi1-pi2-pi3.zip) singlecore RPI.
2. Unzip the file into an empty fat32 formatted (micro) SD card.
3. Insert the SD card into your RPI and power it up for first boot.
4. You'll be presented with following screen:
![BerrybootWelcomScreen](https://pi3.ovps.nl:1443/index.php/s/Nm065jBJsG6MgW5) In this first screen you can enable or disable overscan, check your network connection, set your time-zone and keyboard layout.If your Pi is connected to the Internet BerryBoot will try to detect your location based on your IP-address, and set the right timezone automatically. Verify that it is correct and press “ok”
5. In the next screen: ![Choosing were to install screen](https://pi3.ovps.nl:1443/index.php/s/uTvViX4zHOb94e0) Select where you want to store the operating system files, and press “format”
You can choose to install the operating system files: 
- on the SD card itself
- on an external USB stick/disk.
- on networked storage (for more information see: storing your files on a Synology NAS)
Be aware that if you choose an external drive, the files of the operating system will be stored there, but you still need to keep the SD card in the Pi to boot from.

WARNING: all existing files on the disk will be erased.
