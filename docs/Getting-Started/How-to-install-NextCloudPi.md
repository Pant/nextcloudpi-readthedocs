## Скачивание образа для вашего устройство

Если вам удобно использовать BitTorrent-клиент, пожалуйста, выберите этот способ для получения файлов. Это поможет нам сэкономить немного трафика на сервере. Воспользуйтесь  BitTorrent клиентом [Transmission](https://transmissionbt.com/download/) и оставайтесь на раздаче как можно дольше, после загрузки торрента.

Ссылки на скачивание образов NextCloudPi и .torrent файлы находятся на странице [nextcloudpi.com](https://ownyourbits.com/nextcloudpi/#download). Нажмите иконку загрузки и увидите список директорий, содержащих ссылки на .torrent и .tar.bz файлы.


## Проверка целостности загруженных файлов

В терминале (GNU/Linux & macOS) наберите

```bash
md5sum FILE_PATH
```

Либо в командной строке Windows

    certutil -hashfile  <path to the file>\<filename> MD5

И сравните полученное значение со значением в файле md5sum, который находится радом с .torrent и .tar.bz в директории загрузки.

## Установка

Вы можете записать образ NextCloudPi на SD-карту или USB-накопитель.

### Вариант 1: Запуск с SD-карты

Если ваш компьютер оснащён слотом для SD-карт, то вставьте карту в этот слот. Если слота нет, то вставьте карту в картридер, затем подключите картридер к компьютеру.

#### GNU/Linux & macOS

##### Графический интерфейс

1. Скачайте NextCloudPi с сайта [nextcloudpi.com](https://ownyourbits.com/nextcloudpi/#download):
2. Скачайте balenaEtcher с [официального сайта](https://www.balena.io/etcher/)
3. Распакуйте `.zip` файл
4. Дважды кликните на файл `.AppImage` для запуска balenaEtcher
5. Нажмите "Select Image" в окне balenaEtcher и выберите файл с образом NextCloudPi ( `.tar.bz2` можно не распаковывать) и нажмите "Open".
6. balenaEtcher автоматически определит SD-карту. Нажмите "Flash" в balenaEtcher.

##### Терминал

1. Откройте терминал.
2. Выполните команду `cd /home/${USER}/Downloads` (или другая директория, в которую вы загрузили файл).
3. Проверьте целостность файл (опционально). Выполните команду `md5sum NextCloudPi_XX-XX-XX.tar.bz2` и сравните с хэшем в файле `md5sum`, который вы найдёте на странице загрузки.
4. Замените XX-XX-XX на версию, которую вы загрузили и запустите команду `tar -xvf NextCloudPi_XX-XX-XX.tar.bz2` для распаковки образа.
5. Выполните команду `sudo dd bs=4M if=NextCloudPi_XX-XX-XX.img of=/dev/sdx`, где `/dev/sdx` это имя вашей SD-карты. (Более подробная инструкция на английском языке [здесь](https://www.raspberrypi.org/documentation/installation/installing-images/linux.md))
6. Выполните команду `sync`.

#### Windows
1. Скачайте balenaEtcher с [официального сайта](https://www.balena.io/etcher/)
2. Запустите balenaEtcher и нажмите "Select Image". выберите файл с образом NextCloudPi ( `.tar.bz2` можно не распаковывать) и нажмите "Open".
3. balenaEtcher автоматически определит SD-карту. Нажмите "Flash" в balenaEtcher.


### Вариант 2: Гибридный (/boot раздел на SD-карту, / раздел на USB-накопителе)

После установки NextCloudPi на SD-карту (вариант 1), для уменьшения количества ошибок, которые обычно происходят во время эксплуатации, переместите [корневой раздел с SD-карты на HD или SSD](https://elinux.org/Transfer_system_disk_from_SD_card_to_hard_disk). Если вы используете образ, основанный на Armbian, то установите специальный инструмент для этого: `apt install armbian-config`.

Внимание! Требуется помощь добровольцев для заполнения этого раздела документации.

### Вариант 3: Запуск с USB-накопителя

Если вы хотите попробовать, то лучше начать с [этого руководства на английском языке](https://www.raspberrypi.org/documentation/hardware/raspberrypi/bootmodes/msd.md)

Внимание! Требуется помощь добровольцев для заполнения этого раздела документации.

### Вариант 4: Установка NextCloudPi на SD-карту или USB-накопитель через Berryboot 

[Внимание! Требуется помощь добровольцев для перевода этой страницы документации.](http://docs.nextcloudpi.com/en/latest/Getting-Started/Berryboot-install-NextCloudPi-on-an-external-drive-step-by-step/)


## Первые шаги

### SSH (опционально)

Безопасная оболочка (SSH) позволяет производить удалённое администрирование NextCloudPi продвинутым пользователям. Если вы хотите просто использовать NextCloudPi, то, возможно, вам это никогда не потребуется.

#### Перед первым запуском

Если вам нужен SSH доступ к NextCloudPi, то перед первым запуском, создайте файл с именем `ssh` (без расширения) в загрузочном разделе SD-карты. (Более подробно об этом написано [на английском языке здесь](https://www.raspberrypi.org/documentation/remote-access/ssh/))

К сожалению, этот способ не работает для Odroid. 

#### После запуска NextCloudPi

1. [Запустите WebUI или TUI](https://docs.nextcloudpi.com/ru/latest/Configure/How-to-configure-NextCloudPi/).
2. Выберите [`SSH`][ssh] из списка.
3. Измените `Enabled` на `yes`.
4. Задайте имя пользователя в поле `USER`.
5. Задайте пароль в поле `PASS`.
6. Повторите пароль в поле `Confirm`.
7. Нажмите Run или Start.

### Запуск NextCloudPi
Вставьте SD-карту в Raspberry Pi (или другую плату), затем подключите Raspberry Pi к роутеру через кабель и включите питание.
