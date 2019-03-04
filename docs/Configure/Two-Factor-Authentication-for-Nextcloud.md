## 雙重認證

若您需要使用雙重認證於 Nextcloud 中，請依照以下文件進行操作：

1. 安裝 `TOTP` 應用程式於 NextCloud
2. 啟用 `TOTP` on `Personal Settings`，under `TOTP second-factor auth` section. QR Code 將會出現於畫面中。
3. 安裝 `andOTP` 於你的 Android 手機中。(或者你有更好的雙重認證應用程式，也可以進行替換。`andOTP` 可以於 F-droid 找到)
4. 開啟 `andOTP` 並在第二步中掃描 QR Code 。
5. 接下來`andOTP` 將於 Nextcloud 進行連結，並於每30秒產生一個新 TOTP password 密碼。

現在，當您登入時，系統將會提示你輸入TOTP密碼。密碼位置於你的手機 `andOTP` 應用程式中。

## 應用程式(裝置)密碼

當你使用這個功能時，你必須新增 `應用程式密碼` 來使用 NextCloud 客戶端(任何) 。

例如：Nextcloud 桌面/手機客戶端、DavDroid、Notes等

請依照以下文件進行操作：

1. 開啟設定-->個人設定-->安全性-->Devices & sessions。此處可以看到所有訪問你的 NextCloud 裝置。

2. 在下方 `應用程式名稱` 填寫你所要使用的應用程式名稱。這只為了區分而已。

3. 點擊 `建立新的應用程式密碼`，現在使用權杖將顯示在你面前。你可以使用此權杖來登入應用程式。

*注意：當你確定之後，權杖可能永遠不會再顯示出來。建議你將權杖儲存在其它地方。
