## NFS
Configure a NFS network file system server (for Linux LAN)

## dnsmasq
Configure DNS server with cache

## fail2ban
From [https://www.fail2ban.org](https://www.fail2ban.org) 
> Fail2ban scans log files (e.g. /var/log/apache/error_log) and bans IPs that show the malicious signs -- too many password failures, seeking for exploits, etc.

### Features of Fail2ban in NextCloudPi
- SSH jail
- Nextcloud login jail

### How to activate
Run the TUI (`nextcloud-config`) or use the WebUI.
1. Change "ACTIVE" to "yes"
2. Change (optional) "NCLOG" to the nextcloud.log. Default: /var/www/nextcloud/data/nextcloud.log. **Important Note:** Change the log address if you have changed the data directory of nextcloud ([nc-datadir](#nc-datadir))
3. Change (optional) BANTIME in seconds. Default: 600 (10mins)
4. Change (optional) "FINDTIME" in seconds. Default: 600 (10mins)
5. Change (optional) "MAXRETRY" in retries. Default 6 retries.
6. Change (optional) "EMAIL" with your personal email to receive ban notifications.
7. Change (optional) "MAILALERTS" to activate/deactivate email notifications.
8. Click Run or Start

## freeDNS
[FreeDNS](https://freedns.afraid.org/) client.

Most home users do not have a static IP but rather a dynamic IP that changes from time to time. in order for you to be able to access your Nextcloud instance, from outside of your house, without typing an IP address you need a DDNS service which tracks IP changes and updates the DNS records. 

You need to register an account on [FreeDNS](https://freedns.afraid.org/) and setup a (sub)Domain Name.

### How to activate
Run the TUI (`nextcloud-config`) or use the WebUI.
Log in to freedns.afraid.com and click "Dynamic DNS". Right click on "Direct URL" next to your record. Paste it in a text editor and select only the hash (the letters after the "?").
1. Navigate to "freeDNS" in the TUI or the WebUI.
2. Change "ACTIVE" to "yes"
3. Change the "UPDATEHASH" with yours (delete the example and paste with ctrl+shift+V)
4. Change "DOMAIN" with your Domain Name you have registered.
5. (Optional) Change the "UPDATEINTERVAL" to the interval time you want the client to update your IP (Dynamic IPs do not change that often so you can leave the default (5mins)).
6. Click Run or Start.

## letsencrypt

In order to trust a connection to a website and send your user name and password, you need a SSL certificate. The SSL certificate ensures that the communication is encrypted, so everything you send can only be viewed by the server and not someone who impersonates him. By default NextCloudPi provides a self signed SSL certificate in order to encrypt your communication but it is strongly recomended that you use a certificate from a certificate authority. The NextCloudPi can run the Let's Encrypt client which gets a certificate from https://letsencrypt.org for your (sub)Domain Name. NextCloudPi also configures the web server to use it and renews the certificate once a month.

### Configure
1. Navigate to "letsencrypt" in the TUI or the WebUI.
2. Change the DOMAIN with your (sub)Domain Name.
3. Change the "EMAIL" with your Email address. (It is recomended to use a valid Email address)
4. Click Run or Start.


## modsecurity
Web Application Firewall for extra security (experimental)

## nc-automount
Enable this feature if you want the Rasperry Pi to automount usb drives.

### How to enable
1. Navigate to "nc-automount" in the TUI or the WebUI.
2. Change "ACTIVE" to yes

## nc-autoupdate-ncp
Auto update NextCloudPi

## nc-backup-auto
Perform automatic backups.

## nc-backup
Perform a backup.

## nc-database
Enable if you want to change the Nextcloud database location (e.x. to a usb drive)

> **Note** that non Unix filesystems such as NTFS are not supported because they do not provide a compatible user/permissions system 

>You need to use a USB drive that is permanently on and is responsive or the database will fail.     

> ** If it ever fails with a white page, move the database back to the SD **

### How to configure
1. Navigate to "nc-database" in the TUI or the WebUI.
2. Change "DBDIR" to your database location.
3. Click Run or Start.

## nc-datadir
Change the "data" folder location of Nextcloud.

> **Note** that non Unix filesystems such as NTFS are not supported because they do not provide a compatible user/permissions system  

### How to configure
1. Navigate to "nc-datadir" in the TUI or the WebUI.
2. Change "DATADIR" to your data location.
3. Click Run or Start.

## nc-format-USB
Do this if you want to format your USB Drive and make it compatible with linux user/permissions system

> Make sure that **ONLY** the USB drive that you want to format is plugged in. 

>Be careful, this will destroy **ALL** data in the USB drive

>** YOU WILL LOSE ALL YOUR USB DATA **   

### How to run
1. Navigate to "nc-format-USB" in the TUI or the WebUI.
2. Change "LABEL" to a label you like.
3. Click Run or Start.

## nc-forward-ports
NextCloudPi has implemented a UPnP client to be able to configure the Router to port forward to your Raspberry Pi.

### Requirements
You need to enable UPnP on your Router. Also disable it after you configure port forwarding.

### How to configure
1. Navigate to "nc-forward-ports" in the TUI or the WebUI.
2. Set the ports your Nextcloud runs on. (It is recomended that you use the defaults)

## nc-httpsonly
Force HTTPS

## nc-init
(Re)initiate Nextcloud to a clean configuration.

## nc-limits
Configure system limits for NextCloudPi

## nc-nextcloud
Configure Nextcloud.

## nc-notify-updates
Get notified for updates (Pending or Installed).

## nc-ramlogs
Enable mounting logs in RAM to prevent SD degradation (faster, consumes more RAM)

## nc-restore
Restore from a backup.

## nc-scan-auto
Automate a Nextcloud scan for user files.

## nc-scan
Perform a Nextcloud scan for user files.

## nc-swapfile
Change the location and the size of the swap file.

## nc-update
Perform a manual update

## nc-webui
Enable or disable the WebUI

## no-ip

Run the TUI (`nextcloud-config`) or use the WebUI.
1. Navigate to "no-ip" in the TUI or the WebUI.
2. Change "ACTIVE" to "yes".
3. Change "USER" with your user name.
4. Change "PASS" with your password.
5. Change "DOMAIN" with your (sub)Domain Name.
6. Change "TIME" with the interval time you want to update the DNS record. Default 30mins.
7. Click Run or Start.

## samba
Configure SMB/CIFS file server (for Mac/Linux/Windows)

## unattended-upgrades
Enable Automatic installation of security updates. Keep your cloud safe
