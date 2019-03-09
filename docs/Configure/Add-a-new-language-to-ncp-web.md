想為  _ncp-web_ 建立新語言嗎？請按照下列步驟操作。

- 建立開發環境 [development environment](https://github.com/nextcloud/nextcloudpi/wiki/Development-environment)

- 下載 [範本](https://ownyourbits.com/downloads/l10n_templates.zip)

※ _很抱歉的，我們的社區沒有足夠的時間維護翻譯範本，翻譯範本可能已經過時，我們正在努力製作新的範本_

_若你在翻譯的時候遇到瓶頸，你可以查看中文翻譯，這是當前 ncp 翻譯最多的譯文，或者直接使用中文翻譯作為範本。_

- 完成翻譯之後，你可以在[這裡](https://www.metamodpro.com/browser-language-codes)尋找並確認你的語言識別碼。

- 除了 `__core__.json`，其它的翻譯文件將會儲存到這裡： `etc/ncp-config.d/l10n/<app>/<languagecode>.json`。每個文件命名都是`languagecode`(語言識別碼)，若不是按照這個方式命名，翻譯檔案在顯示的時候可能會出錯。

- 請修改翻譯範本中的翻譯，修改成你的語言。你可以到 `https://localhost:4443` 這裡查看你的翻譯。

- 完成翻譯後，請至 `ncp-web/ncp-web.cfg` 新增語言識別碼(你的翻譯語言)，以利語言選擇欄有你的翻譯語言。

- 若要 Pull 任何的語言修改、新增要求，請要求 _devel_ 分支。

範例：翻譯原始範本 `nc-backup`

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

翻譯成德文

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

```

