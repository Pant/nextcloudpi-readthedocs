#### Install Docker
I used [the docker documentation](https://docs.docker.com/install/linux/docker-ce/debian/#install-using-the-repository) for Debian 9 that worked fine, but you'll find instructions for other linux flavor there too. 
#### Download and start 
The the x86 version of NextCloudPi docker container. It features the latest Nextcloud networking and system management extras.

Run it with

 > docker run -d -p 4443:4443 -p 443:443 -p 80:80 -v ncdata:/data --name nextcloudpi ownyourbits/nextcloudpi-x86 $DOMAIN

DOMAIN should be your trusted domain: the URL or IP that will be used to access.  Substitute _x86_ with _armhf_ if your on RaspberryPi or other armfs devices.

Any folder can be used instead of the volume ncdata to hold the Nextcloud data.

That's it. Visit https://yourIP/activation copy and save auto generated passwords, and start using your Nextcloud instance.

#### Check and manage

Check if running with:
 > docker ps

Update to latest NCP version with:
 > docker exec -it nextcloudpi ncp-update

Run NCP-config to access all NCP apps with:
 > docker exec -it nextcloudpi ncp-config

Make sure container re-start, unless manually stopped with:
 > docker update --restart=unless-stopped nextcloudpi

View other options with:
 > docker help

Start docker with custom storage volume with:
> sudo mkdir /media/ncdata

> docker run -d -p 4443:4443 -p 443:443 -p 80:80 -v /media/ncdata:/data --name nextcloudpi ownyourbits/nextcloudpi-x86 $sub.domain.tld 

Add IP or domain to trusted domains array with:
 > sudo /media/ncdata/data/bin/ncc config:system:set trusted_domains 9 --value="sub.domain.tld"

Reload apache2 webservice with:
 > docker exec -it nextcloudpi service apache2 reload
