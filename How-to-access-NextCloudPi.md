[nc-wifi]: https://github.com/nextcloud/nextcloudpi/wiki/Configuration-Reference#nc-wifi

This guide will help you access NextCloudPi.

# Access

## Instant Domain Name Access
When up and running, your device should become accessible at [https://nextcloudpi](https://nextcloudpi) or [https://nextcloudpi.local](https://nextcloudpi.local).

![](https://ownyourbits.com/wp-content/uploads/2017/09/local-access1.jpg)

If you are using Windows you may have to install [Bonjour Services for Windows](https://support.apple.com/kb/DL999)  to make it discover the .local domains. If your Browser redirects you to some search engine, you may try pasting the whole adress (including https://) at once.

If this does not work, try the following to discover your Pi's IP address directly.

## Find the IP address of the Raspberry Pi
You need to find the local IP address of the Raspberry Pi in order to connect to it and configure it.

### From the screen
If you connect a monitor with a HDMI cable to your Raspberry Pi, you will see the local IP address.

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

## Access from outside home network

See [this guide](https://github.com/nextcloud/nextcloudpi/wiki/How-to-access-from-outside-your-network)

## Using your DDNS domain inside and outside home

Most probably, you will want to use the same DDNS domain inside your house that you setup to use [from outside](https://github.com/nextcloud/nextcloudpi/wiki/How-to-access-from-outside-your-network).

That way, your phone, tablet and laptop can seamlessly access your cloud regardless where you are. If your router doesn't support _NAT loopback_, you might have to setup and use a local DNS server.

1 ) First, try to access using your working DDNS domain, for instance _mycloud.freeDNS.org_

2 ) If it doesn't work, probably you need to setup [dnsmasq](https://github.com/nextcloud/nextcloudpi/wiki/Configuration-Reference#dnsmasq) in the NextCloudPi configuration. Just enter your registered domain, and if you know your ISP DNS also type it in the box, otherwise leave the default.

3 ) Finally, we have to setup our computers and devices to use that DNS server when we are connected inside our house.

  3.1 ) Some routers allow to configure this in the DNS configuration section for all devices in the house

  3.2 ) Otherwise, we will have to configure each device to use our NextCloudPi DNS. For more in depth information on this see [this post](https://ownyourbits.com/2017/03/09/dnsmasq-as-dns-cache-server-for-nextcloudpi-and-raspbian/)

---

# Activation

Now, we can start using NextCloudPi! first type the IP address or domain in your browser, then we have to activate NCP.

We will be presented with an activation page. Print the page or copy the passwords, and hit 'Activate'. We can change these passwords later with `nc-admin` and `nc-passwd`.

![](https://ownyourbits.com/wp-content/uploads/2018/04/ncp-activation.gif)

We will be redirected to ncp-web where we can run the first run Wizard.

![](https://ownyourbits.com/wp-content/uploads/2017/10/wizard-demo1.gif)

From this point we can access Nextcloud by the IP address, nextcloudpi.local or the DDNS domain name we have registered. We can access the web panel at port 4443, for example https://nextcloudpi.local:4443

Next, learn [how to configure NextCloudPi](https://github.com/nextcloud/nextcloudpi/wiki/How-to-configure-NextCloudPi).