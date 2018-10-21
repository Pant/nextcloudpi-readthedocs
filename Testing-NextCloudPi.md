This document describes the workflow to building and testing NCP.

**Help is welcome and  needed! The more testers there are the less each single one of them has to work. Please, write us in the [forums](https://help.nextcloud.com/c/support/appliances-docker-snappy-vm) or [Telegram](https://t.me/NextCloudPi) if you are interested.**

## Procedure

@nachoparker is in change of batch building all the appliances. The build system automatically uploads the images to [downloads/testing](https://ownyourbits.com/downloads/testing).

When the images for a new release are ready, @nachoparker will create a post in the [forums](https://help.nextcloud.com/c/support/appliances-docker-snappy-vm), quoting all the volunteer testers in this document. They will receive an email notification.

At least one tester per board will respond in the forum thread with 'ack', meaning that they will assign themselves the testing of that board for this pre-release. Then, if everything is ok, they will create another comment saying 'ok'. After everything is tested, @nachoparker will move the images to [downloads](https://ownyourbits.com/downlads), and @nachoparker (or any volunteer) will anonunce the release.

Ideally we would have at least two volunteers per board, so nobody is pressured to do it in a short notice if they are busy with their life. A week would be a good period to wait to all images to be pretested before the official release announcement.

Initially just checking that the board boots, activation and wizard works, and nextcloud logs in should be enough. We will gradually replace this manual method for some automated testing scripts.

- rpi version @nachoparker @kanuahs 
- rpi berryboot version @ovpso alias @Oliver_Van
- odroid version - @bit67 @nachoparker @kunibert
- rock64 version @nachoparker  
- bananapi version @theCalcaholic 
- orangepi version (new)
- docker version armhf @ushills 
- docker version x86 @ushills @not_real_name
- curl installer (debian) @ovpso alias @Oliver_Van

## Testing the curl installer from the `devel` branch

```
wget https://raw.githubusercontent.com/nextcloud/nextcloudpi/devel/install.sh
chmod +x install.sh
sed -i 's|^BRANCH=master|BRANCH=devel|' install.sh ncp.sh
./install.sh
```

## Test cases

In the `tests` folders there are several tests that can be performed to thoroughly verify the build.

- Flash image
- Image boots
- Run automated tests

### Automated tests

The tests are located in the [tests](https://github.com/nextcloud/nextcloudpi/tree/master/tests) folder. You can download them directly from github, or clone the repo

```
git clone git@github.com:nextcloud/nextcloudpi.git
cd nextcloudpi/tests
```

### System tests

There are different tests available. We need python 3 and python selenium installed. The test results will be saved in `test_log.txt`

```
./system_tests.py [user@ip]
```
![ncp_system_tests](https://user-images.githubusercontent.com/21343324/47269139-58909780-d549-11e8-9686-69122d986b51.png)

This test can be run from the board or from our computer. If we don't specify arguments it will try to guess if the NCP instance is local, is a local docker container, or a remote instance at `pi@nextclodpi.local`. It will make sure that everything is installed and running.

### Activation tests

```
./activation_tests [ip]
```
![ncp_activation_tests](https://user-images.githubusercontent.com/21343324/47269157-95f52500-d549-11e8-8253-9450ef4d2f49.png)

This test will go through the activation process and verify it. It will save the random credentials in `test_cfg.txt` and subsequent tests will use those credentials if found. If no IP is provided it will try `localhost`.

### Nextcloud tests

```
./nextcloud_tests [--new] [ip]
```
![ncp_nextcloud_tests](https://user-images.githubusercontent.com/21343324/47269138-57f80100-d549-11e8-933a-ff37160bc862.png)

This test will make sure that Nextcloud works and is well configured. It will use the random credentials in `test_cfg.txt`, or ask for credentials if not found. Use `--new` if you don't want to use the stored credentials. If no IP is provided it will try `localhost`.

## Writing automated tests

If you feel that you can help with some **Python/Bash/Expect automated tests**, please **contribute** to the code in the [tests](https://github.com/nextcloud/nextcloudpi/tree/master/tests) folder of this repo.

The following technologies are suggested, but other suggestions are welcome.

- [TAP](https://testanything.org) Test anything protocol. A standard testing protocol with bindings for [Jenkins](https://wiki.jenkins.io/display/JENKINS/TAP+Plugin) and many [programming languages](https://testanything.org/producers.html).
- [BATS](https://github.com/sstephenson/bats) - a Bash testing suite that supports the TAP protocol
- [python selenium](https://selenium-python.readthedocs.io/) - tool to test web based interfaces in python.
- expect, pexpect...