To configure the NextCloudPi you can use the TUI (Terminal User Interface) or the WebUI.
## TUI
NOTE: *You need to have ssh enabled on your Raspberry Pi. For more info look [here](How to install NextcloudPIon a Raspberry Pi.md#First Steps)*

### Linux / Mac
1. Open a terminal
2. Connect to your Raspberry Pi with ssh. You can do that using the command `ssh pi@"localIPAdress"`, where "localIPAdress" (without the quotes) is the Pi's local ip address.
3. Enter the password "raspberry"


### Windows
1. Install Putty from [it's website](http://www.putty.org/)
2. Run Putty and write the IP address of your Raspberry Pi in the "Host Name" box.
3. Select "SSH" from the "Connection type" buttons. The port number should now change to "22".
4. Click "Open" on the bottom right.
5. Enter password "raspberry"

## WebUI
Note: *The WebUI is not accessible from outside at the momment.*
1. Open a web browser, like Firefox.
2. Type in the URL bar `https://"raspberryPiAddress":4443`, where "raspberryPiAddress" (without quotes) is the Raspberry Pi's IP address