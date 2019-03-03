## 使用 docker

為了便於開發，建議使用x86 NextCloudPi docker容器。

安裝 docker、docker-compose 及(參照下面)

```
git clone https://github.com/nextcloud/nextcloudpi.git
cd nextcloudpi
docker-compose -f docker-compose-ncpdev.yml up
```
安裝完成後。我們將可以訪問網路介面了(`https://localhost:4443`)

我們將開始工作於 `ncp-web` 資料夾，並且從 repo 處理文件，這樣就不必兩邊互相複製了。

當然。我們可以修改任何 NCP 功能於`nextcloudpi-config.d`資料夾

## 使用 QEMU

請參見： [此說明](https://ownyourbits.com/2017/02/06/raspbian-on-qemu-with-network-access/)

```
sudo ./qemu-pi.sh NextCloudPi_03-13-17.img
```

## 使用 VirtualBox

請參見：[此說明](https://ownyourbits.com/2018/10/25/introducing-the-nextcloudpi-vm/)

## 使用 virt-manager

請參見：[此說明](https://ownyourbits.com/2018/10/25/introducing-the-nextcloudpi-vm/)
