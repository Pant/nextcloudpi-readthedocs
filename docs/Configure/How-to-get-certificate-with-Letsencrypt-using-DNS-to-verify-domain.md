若你在使用 Letsencrypt 取得 SSL 證書時，80、443連接埠無法驗證、使用時，我們必須使用 certbot Letsencrypt `--manual`、`--preffered-challenges dns`指令來取得證書。

在使用這個指令之前，你必須先擁有一個域名，並在 DNS 頁面中加入 TXT 紀錄：`acme-challenge.yourNCP.yourdomain.tld`。在運行指令時，certbot 將以此紀錄做為域名擁有權的依據。

1. `sudo apt install certbot python-certbot-apache`
安裝 certbot Letsencrypt、apache module (apache 尚未測試)
2. `sudo nano /etc/hosts`
Add a line with your local IP hostname.domain.tld
1. `sudo certbot -d yourNCP.domain.tld --manual --preferred-challenges dns certonly`
This, interactively, generates all the required files and the certificate after providing challenge value for DNS TXT record and succesfully reading the DNS record.
1. `sudo nano /etc/apache2/sites-enabled/nextcloud.conf`
Edit to look like this, certbot provides these locations 
SSLCertificateFile      /etc/letsencrypt/live/yourNCP.domain.tld/fullchain.pem
SSLCertificateKeyFile	/etc/letsencrypt/keys/0000_key-certbot.pem
1. `sudo nano /var/www/nextcloud/config/config.php`
Edit config.php trusted_domains array by replacing the localhost in 0 => 'localhost' with yourNCP.domain.tld:port 
1. `sudo service php7.0-fpm restart`
To restart php7.0-fpm
1. `sudo service apache2 restart`
To restart apache2

You should now be able to access your NCP at https://yourNCP.domain.tld:portnr

I have my test NCP running on port 2443external/443internal, so I have a NAT/port forward accordingly. You are free to access your NCP on any port, now that domain and certificate are verified and installed.
