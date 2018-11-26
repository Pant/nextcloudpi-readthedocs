If you want to receive emails for password recovery and notifications, you have to set up the email settings in Nextcloud.

Email settings for Nextcloud are located in Admin -> Additional Settings -> Email server. There are 2 recommended ways to set the email address that mails come from:

1. PHP (postfix)
2. SMTP

PHP is the most simple and easier to configure.

The differences between them are that in PHP mode, sent emails pass through the ncp mail server named `postfix`, as opposed in SMTP mode where the email get passed through your email provider(Gmail, Yahoo, etc). With SMTP emails are saved in `Sent` folder of your account. 

For SMTP it is required that you have a registered account with your provider, and to know the details such as port, authentication method and credentials.

## PHP (postfix)

In `Email server` area of `Additional settings` select `PHP` as the `Send mode` and simply add the email of which you want to shown as the sender of the receiving emails.

## SMTP

This is the example setup for Gmail. For other services, the configuration may vary.

In `Email server` area of `Additional settings` add the following:

1. Sent mode `SMTP`, Encryption `STARTTLS`
2. From address `your_email`@`your_provider`
3. Authentication method `Login`, Authentication required `Checked`
4. Server address `your_provider_smtp_address`, : `your_provider_port`
5. Credentials: `email_address`, `email_password`
6. Click `Store Credentials`

You can now click `Send email` to test your settings. the administrator user will receive a test email.

## SSMTP

There is a third way to set up your email, if the first two did not get the job done.

For this to work you need to install and configure **ssmtp** and **bsd-mailx**, which also installs the required libraries. It will also remove Postfix if it is installed.
 
`sudo apt-get install ssmtp bsd-mailx`
 
Files created manually:
/root/.forward   #used nano to add; pi@localhost
Files edited:
/etc/ssmtp/revaliases
#used nano to add: root:my@gmail.com:smtp.gmail.com:587
/etc/ssmtp/ssmtp.conf
#mine looks like this:
#
# Config file for sSMTP sendmail
#
#The person who gets all mail for userids < 1000
#Make this empty to disable rewriting.
root=my@gmail.com

#The place where the mail goes. The actual machine name is required no
#MX records are consulted. Commonly mailhosts are named mail.domain.com
mailhub=smtp.gmail.com:587
AuthUser=my@gmail.com
AuthPass=**********
UseTLS=Yes
UseSTARTTLS=Yes


#Where will the mail seem to come from?
rewriteDomain=my.tld

#The full hostname
hostname=myhostname

#Are users allowed to set their own From: address?
#YES - Allow the user to specify their own From: address
#NO - Use the system generated From: address
FromLineOverride=YES

To protect your account info:

`sudo chgrp pi /etc/ssmtp/ssmtp.conf`
`sudo chmod 640 /etc/ssmtp/ssmtp.conf`
