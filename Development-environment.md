In order to facilitate development, the x86 NextCloudPi docker container can be used.

Install docker and docker-compose and

```
git clone https://github.com/nextcloud/nextcloudpi.git
cd nextcloudpi
docker-compose -f docker-compose-ncpdev.yml up
```

We can now access the interface at `https://localhost:4443`. 

We can start working in the folder `ncp-web` from the repo and refresh the browser to see the changes live.

In the same way, we can edit any NCP option in the folder `nextcloudpi-config.d`.

Changes can be made directly on the repo, no more copying files back and forth!