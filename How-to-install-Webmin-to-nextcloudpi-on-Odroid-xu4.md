This guide will help you to install Webmin to nextcloudpi on Odroid XU4.

I tried to install webmin to nextcloudpi on odroid xu4 and I had some troubles, so I decided to write an short guide how to do it. Maybe the same problems are existing on some of the other images of nextcloudpi.

At first I started with official guide for debian 9 here: http://www.webmin.com/deb.html, but without success.

After several attempt I found the next implementation, that work for me:

Go to terminal and login as root user:

**nano /etc/apt/sources.list**
   
and add this:

**deb https://download.webmin.com/download/repository sarge contrib**

Save and close file. Install GPG key with which the repository is signed, with the commands :

**cd /root**

**wget http://www.webmin.com/jcameron-key.asc**

**apt-key add jcameron-key.asc**

To overcome the problem with installing apt-show-versions, removed all installation files:

**apt-get purge apt-show-versions**

**rm /var/lib/dpkg/info/apt-show***

Set on the fly option for apt:

**apt-get -o Acquire::GzipIndexes=false update**

Now install apt-show-versions and webmin:

**apt-get update**

**apt-get install apt-show-versions webmin**

If UFW firewall is active, open 10000 port to be able to access Webmin web panel:

**ufw allow 10000/tcp**

Now go to https://your-nextcloudpi-ip:10000 and log in with your root user name and password.