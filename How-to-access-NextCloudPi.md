[nc-wifi]: https://github.com/nextcloud/nextcloudpi/wiki/Configuration-Reference#nc-wifi

This guide will help you access NextCloudPi.

## Access directly
The default DNS address is `nextcloudpi.local`.

![](https://ownyourbits.com/wp-content/uploads/2017/09/local-access1.jpg)

If you are using Windows you may have to install [Bonjour Services for Windows](https://support.apple.com/kb/DL999)  to make the .local domains work.

Your initial nextcloud installation should be readily accessible simply under https://nextcloudpi.local, otherwise you need to find out its IP address through one of the following ways.

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
1. Install `Angry IP Scanner` from [it's website](http://angryip.org/).
2. Run `Angry IP Scanner` and put your network range and netmask. For example `From: 192.168.0.0` `To: 192.168.0.255` `Netmask: /24`.
3. Hit start.

You will get a list of all connected devices on your network. For more info look at the [FAQ](http://angryip.org/faq/) of Angry IP Scanner.

## Access from outside home

See [this guide](https://github.com/nextcloud/nextcloudpi/wiki/How-to-access-from-outside)

## Using your DDNS domain inside and outside home

Most probably, you will want to use the same DDNS domain inside your house that you setup to use [from outside](https://github.com/nextcloud/nextcloudpi/wiki/How-to-access-from-outside).

That way, your phone, tablet and laptop can seamlessly access your cloud regardless where you are. If your router doesn't support _NAT loopback_, you might have to setup and use a local DNS server.

1 ) First, try to access using your working DDNS domain, for instance _mycloud.freeDNS.org_

2 ) If it doesn't work, probably you need to setup [dnsmasq](https://github.com/nextcloud/nextcloudpi/wiki/Configuration-Reference#dnsmasq) in the NextCloudPi configuration. Just enter your registered domain, and if you know your ISP DNS also type it in the box, otherwise leave the default.

3 ) Finally, we have to setup or computers and devices to use that DNS server when we are connected inside our house.

  3.1 ) Some routers allow to configure this in the DNS configuration section for all devices in the house

  3.2 ) Otherwise, we will have to configure each device to use our NextCloudPi DNS. For more in depth information on this see [this post](https://ownyourbits.com/2017/03/09/dnsmasq-as-dns-cache-server-for-nextcloudpi-and-raspbian/)

---

Now, you can start using Nextcloud! type the IP address in your browser.

The default user is `admin` and the default password is `ownyourbits`. You should now change the default password in settings/personal or in settings/users.

![](https://user-images.githubusercontent.com/21343324/30252853-f31d11bc-9679-11e7-9591-df42c9fd13be.png)



Learn [how to configure NextCloudPi](https://github.com/nextcloud/nextcloudpi/wiki/How-to-configure-NextCloudPi).