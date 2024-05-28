### How to Install phpmyadmin with Nginx Web Server
- Install phpMyAdmin and Other Plugins
```sh
sudo apt update
sudo apt upgrade
sudo apt install phpmyadmin php-mbstring php-zip php-gd php-json php-curl
```
```sh
- php-mbstring: A module for managing non-ASCII strings with different encodings
- php-zip: An extension that facilitates uploading .zip files to phpMyAdmin
- php-gd: Enables support for GD graphics library
- php-json: Provides support for JSON serialization
- php-curl: Allows PHP to communicate with other servers
```
- Create a symbolic link from the installation files to Nginx’s document root directory:
sudo ln -s /usr/share/phpmyadmin /var/www/codesagar.com/phpmyadmin


NGINX Configurations:

location /phpmyadmin {
    root /var/www/codesagar.com;
    index index.php index.html index.htm;

    location ~ ^/phpmyadmin/(.+\.php)$ {
        try_files $uri =404;
        root /var/www/codesagar.com;
        fastcgi_pass unix:/run/php/php8.1-fpm.sock;
        fastcgi_index index.php;
        fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
        include /etc/nginx/fastcgi_params;
    }

    location ~* ^/phpmyadmin/(.+\.(jpg|jpeg|gif|css|png|js|ico|html|xml|txt))$ {
        root /var/www/codesagar.com;
    }
}

- Check Permissions:
sudo chown -R www-data:www-data /var/www/your_domain/phpmyadmin
sudo chmod -R 755 /var/www/your_domain/phpmyadmin


- Restart the nginx and PHP-FPM services:
sudo systemctl restart nginx
sudo systemctl restart php78.1-fpm

```
- Login to phpmyadmin using web browser
- If get warning e.g. "The $cfg['TempDir'] (/var/lib/phpmyadmin/tmp/) is not accessible." then run below commands
```sh
cd /var/lib/phpmyadmin
sudo chmod -R 775 tmp
sudo service nginx restart
```
