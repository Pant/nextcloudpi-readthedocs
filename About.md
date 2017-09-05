#What is NextCloudPi

NextCloudPi is a ready to use Raspbian 9 image with the latest Nextcloud 12.

##Features
* Raspbian 9 stretch
* Nextcloud 12.0.2
* Apache 2.4.25, with HTTP2 enabled
* PHP 7.0 (double the speed of PHP5!)
* MariaDB 10
* 4.9 Linux Kernel ( NEW 03-13-2017 )
* nextcloudpi-config for easy setup ( RAM logs, USB drive and more )
* Automatic redirection to HTTPS
* ACPU PHP cache
* PHP Zend OPcache enabled with file cache
* HSTS
* Cron jobs for Nextcloud
* Sane configuration defaults
* Full emoji support ( NEW 05-24-2017 )
* Secure

##Extras
* NextCloudPi Web Panel ( NEW 07-24-2017 )
* Wi-Fi ready ( NEW 03-31-2017 )
* Automatic security updates, activated by default. ( NEW 03-21-2017 )
* Let’s Encrypt for trusted HTTPS certificates.(  NEW 03-16-2017 )
* Fail2Ban protection against brute force attacks. ( NEW 02-24-2017 )
* Dynamic DNS support for no-ip.org ( NEW 03-05-2017 )
* dnsmasq DNS server with DNS cache ( NEW 03-09-2017 )
* ModSecurity Web Application Firewall ( NEW 03-23-2017 )
* NFS ready to mount your files over LAN ( NEW 04-13-2017 )
* SAMBA ready to share your files with Windows/Mac/Linux ( NEW 04-16-2017 )
* USB automount ( NEW 05-24-2017 )
* Remote updates ( NEW 03-31-2017 )
* Autoupdates ( NEW 08-16-2017 )
* Update notifications ( NEW 08-16-2017 )
* NextCloud backup and restore ( NEW 05-24-2017 )
* NextCloud online installation ( NEW 05-24-2017 )
* Format USB drive to ext4 ( NEW 07-03-2017 )
* UPnP automatic port forwarding ( NEW 07-03-2017 )

You can activate Extras with the `nextcloudpi-config` or the webUI by visiting https://"serverIP":4443 (without quotes) with your browser.

## Docker Image
NextCloudPi is also available, for any arm board (which supports docker), as an arm docker image.

## Desktop Environment
At this moment, the images do not provide a desktop environment, though it can be added through apt.

## Ask for help
Please, report issues at NextCloudPi [Issues](https://github.com/nextcloud/nextcloudpi/issues) page.

*Please, before asking technical questions, look [here](https://github.com/nextcloud/nextcloudpi/issues?utf8=%E2%9C%93&q=%20label:question%20) if it has been asked before.*

Use the [official forums](https://help.nextcloud.com/c/support/appliances-docker-snappy-vm) to ask questions, opinions and participate.

We need your **help**! There are many easy things that you can do to [contribute](Contribute.md).