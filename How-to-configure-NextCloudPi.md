## Choose an User Interface
You can configure the NextCloudPi instance from the TUI or from the WebUI. 
Note: *The backend is the same.*

### TUI

To access the terminal, you need to have ssh enabled on your Raspberry Pi. For more info look [here](https://github.com/nextcloud/nextcloudpi/wiki/How-to-install-NextCloudPi-on-a-Raspberry-Pi#first-steps).

Alternatively, you can plug in a keyboard and HDMI screen to access the terminal.

#### Raspberry Pi
1. Connect keyboard and HDMI screen.
2. Turn on Raspberry Pi with NextCloudPi SD card image.
3. Login with user `pi` and password `raspberry`.
4. (optional) type `sudo raspi-config` and enable SSH in `Interfacing Options".
5. (optional) type `sudo nextcloudpi-config` and use [`nc-wifi`][nc-wifi] to connect to your WLAN.

#### Linux / Mac
1. Open a terminal.
2. Connect to your Raspberry Pi with `ssh`. You can do that using the command `ssh pi@"localIPAdress"`, where "localIPAdress" (without the quotes) is the Pi's local IP address.
3. Enter the password `raspberry`


#### Windows
1. Install Putty from [it's website](http://www.putty.org/)
2. Run Putty and write the IP address of your Raspberry Pi in the "Host Name" box.
3. Select "SSH" from the "Connection type" buttons. The port number should now change to "22".
4. Click "Open" on the bottom right.
5. Enter password `raspberry`

You now have connected to the NextCloudPi Shell. You can run the command `nextcloudpi-config` to open the TUI.

### WebUI
If you want to configure NextCloudPi with the WebUI:
1. Open a web browser.
2. Write in the URL "https://"raspberryPiAddress":4443", where "raspberryPiAddress" (without quotes) should be replaced with your Raspberry Pi's IP Address.
3. There should be an message saying that the address you are visiting is not secure. You should accept the self-signed certificate. After this you should be able to see the Web Panel.

---

From here you can configure everything that you need. See the [configuration reference](https://github.com/nextcloud/nextcloudpi/wiki/Configuration-Reference) for an explanation of all the options.

You can follow these [steps to access from outside](https://github.com/nextcloud/nextcloudpi/wiki/How-to-access-from-outside).

You can follow these [steps to host your data in a USB drive](https://github.com/nextcloud/nextcloudpi/wiki/How-to-configure-an-external-USB-drive-with-NextCloudPi).
