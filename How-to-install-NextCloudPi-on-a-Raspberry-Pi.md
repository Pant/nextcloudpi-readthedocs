This is the official guide on how to install NextCloudPi on a Raspberry Pi
## Download the Image
You will need to use a BitTorrent client like [Transmission](https://transmissionbt.com/download/)

Click on the torrent or the magnet link in [ownyourbits website](https://ownyourbits.com/2017/02/13/nextcloud-ready-raspberry-pi-image/)

## Installing
If your computer has a slot for SD cards, insert the card. If not, insert the card into an SD card reader, then connect the reader to your computer.

### Linux & Mac
1. Open a terminal and run the following commands.
2. Replace "user" with your user name and run command `cd /home/user/Downloads`.
3. Run command `tar -xvf NextCloudPi-lite_02-12-17.tar.bz2` to extract the image.
4. Run command `sudo dd bs=4M if=NextCloudPi-lite_02-12-17.img of=/dev/sdx`, where `/dev/sdx` is your sd card name. (For more info look [here](https://www.raspberrypi.org/documentation/installation/installing-images/linux.md))
4. Run command `sync`.

### Windows
1. Install Etcher from [their website](https://etcher.io/)
2. Install 7-Zip from [their website](http://www.7-zip.org/)
3. Run 7-Zip manager, find your downloaded file, select it and click the Extract icon.
4. Run Etcher and click "Select Image". Find your image you have just extracted and click "Open".
5. Etcher automaticaly detects the SD card, but verify that is the one you want the image to be installed on.
6. Click "Flash" in Ether.

## First steps
### Enable SSH (optional)
If you want to enable SSH, in order to connect to your Raspberry Pi's shell, create a file named `ssh` (without any extension) at the boot partition of your SD card. (More info [here](https://www.raspberrypi.org/documentation/remote-access/ssh/))

### Run NextCloudPi
Remove the SD card and insert it to the Raspberry Pi. Then connect it to your home Router with an UTP cable (Ethernet) and power on your Raspberry Pi.

---

Now you have Nextcloud up and running. Learn [how to access NextCloudPi](https://github.com/nextcloud/nextcloudpi/wiki/How-to-access-NextCloudPi)