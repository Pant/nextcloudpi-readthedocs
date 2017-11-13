## Download the Image
If you are comfortable using BitTorrent please use and share the Torrent files to save us some server traffic, thank you!
You can use a BitTorrent client like [Transmission](https://transmissionbt.com/download/).
You  find the torrent link as well as a magnet link and a direct download at [ownyourbits.com](https://ownyourbits.com/2017/02/13/nextcloud-ready-raspberry-pi-image/)

## Installing

You can run NextCloudPi from an SD card or from a USB drive.

### Option 1: Run from SD card

If your computer has a slot for SD cards, insert the card. If not, insert the card into an SD card reader, then connect the reader to your computer.

#### Linux & Mac
1. Open a terminal and run the following commands.
2. Replace "user" with your user name and run command `cd /home/user/Downloads` (or any other folder you've saved the files to).
3. Replace XX-XX-XX with the version you downloaded and run the command `tar -xvf NextCloudPi_XX-XX-XX.tar.bz2` to extract the image.
4. Run command `sudo dd bs=4M if=NextCloudPi_XX-XX-XX.img of=/dev/sdx`, where `/dev/sdx` is your sd card name. (For more info look [here](https://www.raspberrypi.org/documentation/installation/installing-images/linux.md))
4. Run command `sync`.

#### Windows
1. Install Etcher from [their website](https://etcher.io/)
2. Install 7-Zip from [their website](http://www.7-zip.org/)
3. Run 7-Zip manager, find your downloaded .tar.bz2 file, right click and choose "extract here". Next select the .tar file you just extracted, right click and choose "extract here" again. You should now see an .img file.
4. Run Etcher and click "Select Image". Find your image (the .image file) you have just extracted and click "Open".
5. Etcher automatically detects the SD card, but verify that is the one you want the image to be installed on.
6. Click "Flash" in Ether.

### Option 2: Run from USB drive

Follow [these steps](https://www.raspberrypi.org/documentation/hardware/raspberrypi/bootmodes/msd.md)

## First steps
### Enable SSH (optional)
If you want to enable SSH, in order to connect to your Raspberry Pi's shell, create a file named `ssh` (without any extension) at the boot partition of your SD card. (More info [here](https://www.raspberrypi.org/documentation/remote-access/ssh/))

### Run NextCloudPi
Remove the SD card and insert it to the Raspberry Pi. Then connect the Raspberry Pi to your home router with an ethernet cable and power on your Raspberry Pi.

---

Now you have Nextcloud up and running. Learn [how to access NextCloudPi](https://github.com/nextcloud/nextcloudpi/wiki/How-to-access-NextCloudPi)