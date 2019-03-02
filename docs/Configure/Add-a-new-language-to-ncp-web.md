想為  _ncp-web_ 建立新語言嗎？請按照下列步驟操作。

- 建立開發環境 [development environment](https://github.com/nextcloud/nextcloudpi/wiki/Development-environment)

- 下載 [範本](https://ownyourbits.com/downloads/l10n_templates.zip)

※ _很抱歉的，我們的社區沒有足夠的時間維護翻譯範本，翻譯範本可能已經過時，我們正在努力製作新的範本 _

_若你在翻譯的時候遇到瓶頸，你可以查看中文翻譯，這是當前 ncp 翻譯最多的譯文，或者直接使用中文翻譯作為範本。_

- learn your language code [here](https://www.metamodpro.com/browser-language-codes)

- those files should be copied to `etc/ncp-config.d/l10n/<app>/<languagecode>.json`, except for `__core__.json`, which goes to `ncp-web/l10n/<languagecode>.json`. You can find the languagecode for your currently used language [here](http://mybrowserinfo.com/detail.asp), under 'User Language'. 

- edit those files to add the translation to your language. You can check the results in your browser at `https://localhost:4443`. Refresh to see any changes

- add the language code to `ncp-web/ncp-web.cfg`

- send a pull request with the changes to the _devel_ branch

Example: translate the original template of `nc-backup`

```
{
    "translations": {
        "BACKUPLIMIT": "BACKUPLIMIT",
        "Backup this NC instance to a file": "Backup this NC instance to a file",
        "COMPRESS": "COMPRESS",
        "DESTDIR": "DESTDIR",
        "INCLUDEDATA": "INCLUDEDATA",
        "nc-backup": "nc-backup"
    }
}
```

to German

```
{
    "translations": {
        "BACKUPLIMIT": "Maximale Anzahl", 
        "Backup this NC instance to a file": "Erstelle eine Backupdatei von dieser NC-Instanz", 
        "COMPRESS": "Kompression", 
        "DESTDIR": "Zielverzeichnis", 
        "INCLUDEDATA": "Inkl. Dateien", 
        "nc-backup": "Backup erstellen" 
    } 
}
