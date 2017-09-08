[nc-wifi]: https://github.com/nextcloud/nextcloudpi/wiki/Configuration-Reference#nc-wifi

This guide will help you access NextCloudPi.

## Find the IP address of the Raspberry Pi
You need to find the local IP address of the Raspberry Pi in order to connect to it and configure it.

### From the screen
If you connect a monitor with HDMI cable to your Raspberry Pi, you will see the local IP address.

![screen-ip](https://ownyourbits.com/wp-content/uploads/2017/02/nextcloudpi_boot.jpg)

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

---

Now, you can start using Nextcloud! type the IP address in your browser.

Learn [how to configure NextCloudPi](https://github.com/nextcloud/nextcloudpi/wiki/How-to-configure-NextCloudPi).