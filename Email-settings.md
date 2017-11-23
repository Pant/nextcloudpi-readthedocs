If you want to receive emails for password recovery and notifications, you have to set up the email settings in Nextcloud.

Email settings for Nextcloud are located in Admin -> Additional Settings -> Email server. There are 2 recommended ways to set the email address that mails come from:

1. PHP (postfix)
2. SMTP

The differences between them are that in PHP mode, sent emails pass through the ncp mail server named `postfix`, as opposed in SMTP mode where the email get passed through your email provider(Gmail, Yahoo, etc). With SMTP emails are saved in `Sent` folder of your account. Finally with SMTP it is required that you have a registered account with your provider.
## PHP (postfix)

In `Email server` area of `Additional settings` select `PHP` as the `Send mode` and simply add the email of which you want to shown as the sender of the receiving emails.

## SMTP

In `Email server` area of `Additional settings` add the following:

1. Sent mode `SMTP`, Encryption `STARTTLS`
2. From address `your_email`@`your_provider`
3. Authentication method `Login`, Authentication required `Checked`
4. Server address `your_provider_smtp_address`, : `your_provider_port`
5. Credentials: `email_address`, `email_password`
6. Click `Store Credentials`

You can now click `Send email` to test your settings. the administrator user will receive a test email.
