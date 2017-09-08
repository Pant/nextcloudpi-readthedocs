[nc-wifi]: https://github.com/nextcloud/nextcloudpi/wiki/Configuration-Reference#nc-wifi

This guide will help you access NextCloudPi.

## Find the IP address of the Raspberry Pi
You need to find the local IP address of the Raspberry Pi in order to connect to it and configure it.

### From the screen
If you connect a monitor with HDMI cable to your Raspberry Pi, you will see the local IP address.

### From your home Router Web Interface
Note: *Routers do not share the same Web User Interface.*  
1. Open a Web Browser, like Firefox.
2. Visit your home Router IP address. It is written at the bottom of your Router. Normally it will be 192.168.1.1
3. Log in with your credentials
4. Navigate to an entry in your menu that shows your Network Map and find a list that shows the IPs of the connected devices. The Raspberry Pi's IP address should be listed there.

### Linux / Mac
1. Install `nmap` from your package manager.
2. Open a terminal 
3. Run the command `nmap -sP '192.168.0.*'`, where you have to replace the network IP (192.168.0) with yours.
You will see something like this:
```
Nmap scan report for 192.168.0.131 (192.168.0.131)
Host is up (0.016s latency).
MAC Address: AA:BB:CC:11:22:33 (Raspberry Pi Foundation)
```

The local IP address of this Raspberry Pi is `192.168.0.131`

### Windows
1. Install "Angry IP Scanner" from [it's website](http://angryip.org/).
2. Run "Angry IP Scanner" and put your network range and netmask. For example "From: 192.168.0.0 To: 192.168.0.255 Netmask: /24".
3. Hit start.

You will get a list of all connected devices on your network. For more info look at the [FAQ](http://angryip.org/faq/) of Angry IP Scanner.

## Choose an User Interface
You can configure the NextCloudPi instance from the TUI or from the WebUI. 
Note: *The backend is the same.*

### TUI
NOTE: *You need to have ssh enabled on your Raspberry Pi. For more info look [here](https://github.com/nextcloud/nextcloudpi/wiki/How-to-install-NextCloudPi-on-a-Raspberry-Pi#first-steps)*

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

You now have connected to the NextCloudPi Shell. You can run the command `nextcloud-config` to open the TUI.

### WebUI
If you want to configure NextCloudPi with the WebUI:
1. Open a web browser.
2. Write in the URL "https://"raspberryPiAddress":4443", where "raspberryPiAddress" (without quotes) should be replaced with your Raspberry Pi's IP Address.
3. There should be an message saying that the address you are visiting is not secure. You should accept the self-signed certificate. After this you should be able to see the Web Panel.

From here you can configure everything that you need.
