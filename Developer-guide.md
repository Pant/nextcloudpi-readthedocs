This section explains the basics for creating a new functionality that will show up in nextcloudpi-config and ncp-web.

## Anatomy of a NextCloudPi option

An option, such as `nc-datadir`, consists of a single bash _.sh_ file that lives in `/usr/local/etc/nextcloudpi-config.d`.

In order to be launched from the web interface, it needs a permission mask 660 and ownership root:www-data

```
chown -R root:www-data /usr/local/etc/nextcloudpi-config.d 
chmod 660 /usr/local/etc/nextcloudpi-config.d/*
```

### Steps
It needs to have three functions or _steps_ called install(), configure() and cleanup()

 - The _install_ step is run during the build process and also during ncp-update if it hasn't been installed before.
 - The _configure_ step is run when 
    - launched from ncp-web ,or nextcloudpi-config
    - during installation ( during build, or from ncp-update ) if it has a field `ACTIVE_=yes`
 - The _cleanup_ step will be run during the image building process only, to leave the system as clean as possible after installation

### Public fields
"Fields" that will show up in ncp-web and nextcloudpi-config for the user to modify are only bash variables with a special name. If a variable ends in underscore `_`, then it will be modifiable by the user. The original value will be left as a suggestion or default.

For instance, the top of the [nc-backup-auto](https://github.com/nextcloud/nextcloudpi/blob/master/etc/nextcloudpi-config.d/nc-backup-auto.sh) option shows the following variables

```
ACTIVE_=yes
DESTDIR_=/media/USBdrive
INCLUDEDATA_=yes
BACKUPDAYS_=7
BACKUPLIMIT_=4
DESCRIPTION="Periodic backups"
```

And looks like this

![nc-backup-auto](https://ownyourbits.com/wp-content/uploads/2017/08/ncp-web2.jpg)

### Special fields
There's two fields that have a special behaviour

 - `DESCRIPTION` is used to show a little explanation in the webUI or TUI and is a mandatory field.
 - `ACTIVE_` will show a ✓ next to the option when it has the value `yes`

Also, any field that reads `yes` or `no` will be displayed as a checkbox in the web interface.
