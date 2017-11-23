In Nextcloud, there is the option to set up Two Factor Authentication. The steps you have to follow in order to use it are the following:

1. Install `TOTP` app on Nextcloud.
2. Enable `TOTP` on `Personal Settings`. A QR code will show up.
3. Install `andOTP` on your android phone (you can use any TOTP client you want, `andOTP` is available in f-droid)
4. Scan the QR code that is shown in step 2 with `andOTP.
5. `andOTP` and Nextcloud are merged and now every 30 seconds a new TOTP password is generated.

Now when you log in you will be prompted to type a TOTP password. Type the password shown in the `andOTP` app.

You now should add `App passwords` for every app that needs access to your Nextcloud account.