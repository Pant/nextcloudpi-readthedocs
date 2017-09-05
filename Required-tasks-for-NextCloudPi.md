Here are the required tasks you have to run for a complete setup of NextCloudPi.

## Find the IP address of the Raspberry Pi
You need to find the local IP address of the Raspberry Pi in order to connect to it and configure it.

### From the screen
If you connect a monitor with HDMI cable to your Raspberry Pi, you will see the local IP address.

### From your home Router Web Interface
Note: *Routers do not share the same Web User Interface.*  
1. Open a Web Browser, like Firefox.
2. Visit your home Router IP address. It is writen at the bottom of your Router. Normally it will be 192.168.1.1
3. Log in with your credentials
4. Navigate to an entry in your menu that shows your Network Map and find a list that shows the IPs of the connected devices. The Raspberry Pi's IP address should be listed there.

### Linux / Mac
1. Install nmap from your package manager.
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

## Choose an interface
You can configure the NextCloudPi instance from the TUI or from the WebUI. 
Note: *The backend is the same.*

### TUI
NOTE: *You need to have ssh enabled on your Raspberry Pi. For more info look [here](How to install NextcloudPIon a Raspberry Pi.md#First Steps)*

#### Raspberry Pi
1. Connect keyboard and HDMI screen
2. Turn on Raspberry Pi with NextCloudPi SD card image
3. Login with user "pi" and password "raspberry"
4. (optional) type "sudo raspi-config" and enable SSH in "Interacing Options"
5. (optional) type "sudo nextcloudpi-config" and use "nc-wifi" to connect to your WLAN

#### Linux / Mac
1. Open a terminal
2. Connect to your Raspberry Pi with ssh. You can do that using the command `ssh pi@"localIPAdress"`, where "localIPAdress" (without the quotes) is the Pi's local ip address.
3. Enter the password "raspberry"


#### Windows
1. Install Putty from [it's website](http://www.putty.org/)
2. Run Putty and write the IP address of your Raspberry Pi in the "Host Name" box.
3. Select "SSH" from the "Connection type" buttons. The port number should now change to "22".
4. Click "Open" on the bottom right.
5. Enter password "raspberry"

You now have connected to the NextCloudPi Shell. You can run the command `nextcloud-config` to open the TUI.

### WebUI
If you want to configure NextCloudPi with the WebUI:
1. Open a web browser.
2. Write in the URL "https://"raspberryPiAddress":4443", where "raspberryPiAddress" (without quotes) should be replaced with your Raspberry Pi's IP Address.
3. There should be an message saying that the address you are visiting is not secure. You should accept the self-signed certificate. After this you should be able to see the Web Panel.

From here you can configure everything that you need.

## Required Configurations
The following are the bare minimum configurations you need to do to have a complete Nextcloud Instance. You can do them ether from the TUI or from the WebUI.

### Access from the outside.
Most home Routers come with a firewall installed which blocks outside requests to inside computers. In order for you to access your Nextcloud from the outside of your house, you need to allow ports 80 and 443 and forward them to your Raspberry Pi. For that reason NextCloudPi has an UPnP client which does just that in an easy way.

Note: *You need UPnP enabled in your Router. It is recomended that you disable it after you run the command to port forward.*

#### Port Forward with UPnP
1. Navigate to "nc-forward-ports" in the TUI or the WebUI.
2. Set the ports your Nextcloud runs on. (It is recomended that you use the defaults)

#### DDNS
In order to access Nextcloud from outside of your house you need a Domain Name (e.x. cloud.com) or a sub-Domain Name (cloud.example.com). Domain Names are names that are pointing to your IP address. But in most cases, home users do not have a static IP address. You probably have a dynamic IP address, which means that changes from time to time. For that reason, in order to keep your (sub)Domain Name always pointing to your IP address, you need a DDNS (Dynamic DNS) service.

NextCloudPi has two different DDNS clients for two different DDNS providers([FreeDNS](http://freedns.afraid.org/), [No-IP](https://www.noip.com)). You have to register an account from their website. There you can create a subdomain for free, or connect a Domain Name you have purchached.

Note: You only need one DDNS service.

##### FreeDNS (freedns.afraid.com)
Run the TUI (`nextcloud-config`) or use the WebUI.
Log in to freedns.afraid.com and click "Dynamic DNS". Right click on "Direct URL" next to your record. Paste it in a text editor and select only the hash (the letters after the "?").
1. Navigate to "freeDNS" in the TUI or the WebUI.
2. Change "ACTIVE" to "yes"
3. Change the "UPDATEHASH" with yours (delete the example and paste with ctrl+shift+V)
4. Change "DOMAIN" with your Domain Name you have registered.
5. (Optional) Change the "UPDATEINTERVAL" to the interval time you want the client to update your IP (Dynamic IPs do not change that often so you can leave the default (5mins)).
6. Click Run or Start.

Now try visit your (sub)Domain Name that you have registered with your browser. It should navigate to the Nextcloud instance.

##### No-IP (www.noip.com)
Run the TUI (`nextcloud-config`) or use the WebUI.
1. Navigate to "no-ip" in the TUI or the WebUI.
2. Change "ACTIVE" to "yes".
3. Change "USER" with your user name.
4. Change "PASS" with your password.
5. Change "DOMAIN" with your (sub)Domain Name.
6. Change "TIME" with the interval time you want to update the DNS record. Default 30mins.
7. Click Run or Start.

Now try visit your (sub)Domain Name that you have registered with your browser. It should navigate to the Nextcloud instance.

#### Automatic signed SSL certificates 
In order to trust a connection to a website and send your user name and password, you need a SSL certificate. The SSL certificate ensures that the communication is encrypted, so everything you send can only be viewed by the server and not someone who impersonates him. By default NextCloudPi provides a self signed SSL certificate in order to encrypt your communication but it is strongly recomended that you use a certificate from a certificate athority. The NextCloudPi can run the Let's Encrypt client which gets a certificate from https://letsencrypt.org for your (sub)Domain Name. NextCloudPi also configures the web server to use it and renews the certificate once a month.

To configure automatic signed SSL certificates (run the TUI (`nextcloud-config`) or use the WebUI):
1. Navigate to "letsencrypt" in the TUI or the WebUI.
2. Change the DOMAIN with your (sub)Domain Name.
3. Change the "EMAIL" with your Email address. (It is recomended to use a valid Email address)
4. Click Run or Start.
