This document describes the workflow to building and testing NCP.

**Help is welcome and  needed! The more testers there are the less each single one of them has to work. Please, write us in the [forums](https://help.nextcloud.com/c/support/appliances-docker-snappy-vm) or [Telegram](https://t.me/NextCloudPi) if you are interested.**

## Procedure

@nachoparker is in change of batch building all the appliances. The build system automatically uploads the images to [downloads/testing](ownyourbits.com/downloads/testing).

When the images for a new release are ready, @nachoparker will create a post in the [forums](https://help.nextcloud.com/c/support/appliances-docker-snappy-vm), quoting all the volunteer testers in this document. They will receive an email notification.

At least one tester per board will respond in the forum thread with 'ack', meaning that they will assign themselves the testing of that board for this pre-release. Then, if everything is ok, they will create another comment saying 'ok'. After everything is tested, @nachoparker will move the images to [downloads](https://ownyourbits.com/downlads), and @nachoparker (or any volunteer) will anonunce the release.

Ideally we would have at least two volunteers per board, so nobody is pressured to do it in a short notice if they are busy with their life. A week would be a good period to wait to all images to be pretested before the official release announcement.

Initially just checking that the board boots, activation and wizard works, and nextcloud logs in should be enough. We will gradually replace this manual method for some automated testing scripts.

- rpi version @nachoparker @kanuahs 
- rpi berryboot version
- odroid version - @bit67 @nachoparker 
- rock64 version @nachoparker  
- bananapi version @theCalcaholic 
- orangepi version (new)
- docker version armhf @ushills 
- docker version x86 @ushills 
- curl installer (debian) @ovpso

---

## Test cases

Here we will list the test cases to be performed first manually, and we will gradually automate.

- Image boots
- Activation works
- Wizard works
- Nextcloud logs in, navigates to the 'admin' section and there are no warnings.

[add more]