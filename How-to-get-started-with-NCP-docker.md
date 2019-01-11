#### Install Docker
I used [the docker documentation](https://docs.docker.com/install/linux/docker-ce/debian/#install-using-the-repository) for Debian 9 that worked fine, but you'll find instructions for other linux flavor there too. 
#### Download and start 
The the x86 version of NextCloudPi docker container. It features the latest Nextcloud plus networking and system management extras.

Run it with

 > docker run -d -p 4443:4443 -p 443:443 -p 80:80 -v ncdata:/data --name nextcloudpi ownyourbits/nextcloudpi-x86 $DOMAIN

DOMAIN should be your trusted domain: the URL or IP that will be used to access.

Any folder can be used instead of the volume ncdata to hold the Nextcloud data.