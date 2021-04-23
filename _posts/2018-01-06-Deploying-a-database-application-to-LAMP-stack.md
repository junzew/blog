---
layout: post
title: "Deployment of a Laravel and MySQL Web Application to EC2"
meta : PHP MySQL Ubuntu EC2 LAMP
categories: PHP MySQL Ubuntu EC2 LAMP
---


As part of the UBC course CPSC 304 (Introduction to Relational Databases), I built an app PHPizza along with [@psiemens](https://github.com/psiemens), [@mattfung](https://github.com/mattfung), and [@sebysebyseby](https://github.com/sebysebyseby). PHPizza is an online pizza ordering system built with the PHP [Laravel](https://laravel.com) framework and MySQL database. In this post, I will write about how I deployed it to an AWS EC2 instance. The website is running now: http://35.153.63.255


# Prepare the LAMP stack

Login in to my Ubuntu 16.04 EC2 instance with `ssh -i`.

Install Apache, MySQL, and PHP:
```
sudo apt-get install apache2
sudo apt-get install mysql-server
sudo apt-get install php libapache2-mod-php php-mcrypt php-mysql
```

Accodring to the [Laravel installation page](https://laravel.com/docs/5.5/installation), 
the PHP extension Mbstring must also be installed

```sudo apt-get install php-mbstring```


# Configure Apache
- Change apache2 document root to the project `public` folder:
```
sudo vi /etc/apache2/sites-available/000-default.conf
```
and change `DocumentRoot /var/www/html`
```
sudo nano /etc/apache2/apache2.conf
```
and change `Directory /var/www/html/`

- Start Apache2
```
sudo systemctl start apache2
```

# Create and populate the database
```
mysql -u root
create database phpizza
use database phpizza
source ./createtables.sql
```

# Prepare the project
- Clone the project from github with `git clone`
- Install [Composer](https://getcomposer.org/download/)
```
php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
php -r "if (hash_file('SHA384', 'composer-setup.php') === '544e09ee996cdf60ece3804abc52599c22b1f40f4323403c44d44fdfdd586475ca9813a858088ffbc1f233e9b180f061') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
php composer-setup.php
php -r "unlink('composer-setup.php');"
```
- Install Laravel and project dependencies with
`php composer.phar install`

- Edit .env to set database environment variables
```
DB_CONNECTION=mysql
DB_HOST=
DB_PORT=
DB_DATABASE=phpizza
DB_USERNAME=root
DB_PASSWORD=
```

# Troubleshooting
Then I ran into some weird issues:

# Routing didn't work except the index page
- It turns out to be some issue with the ./public/.htaccess file being ignored.
Added the VirualHost section to `/etc/apache2/sites-available/000-default.conf`
according to [this Stack Overflow answer](https://stackoverflow.com/a/32617405/6374198).
- Also enabled `mod_rewrite` on apache2 accoding to Laravel [web server configuration suggestions](https://laravel.com/docs/5.5/installation#web-server-configuration) and [this post](https://www.digitalocean.com/community/tutorials/how-to-rewrite-urls-with-mod_rewrite-for-apache-on-ubuntu-16-04).
```
sudo a2enmod rewrite
sudo systemctl restart apache2
```

# Permission issues
According to the Laravel installation page:
> Laravel may require one set of permissions to be configured: folders within app/storage require write access by the web server.

Create these folders under storage/framework:

- sessions
- views
- cache 

`chmod 777 -R storage` and do the same for all three folders

# Database configurations
The configuration file is `/etc/mysql/my.cnf`
- Disable the option 'ONLY_FULL_GROUP_BY':

```
[mysqld]  
sql_mode = "STRICT_TRANS_TABLES,NO_ZERO_IN_DATE,NO_ZERO_DATE,ERROR_FOR_DIVISION_BY_ZERO,NO_AUTO_CREATE_USER,NO_ENGINE_SUBSTITUTION"
```

- Make table names case insensitive:

```
[mysqld]
lower_case_table_names = 1
```

- After configuration change, restart MySQL with `sudo systemctl restart mysql`


# References
https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu-16-04

https://askubuntu.com/questions/491629/how-to-install-php-mbstring-extension-in-ubuntu

https://stackoverflow.com/questions/5891802/how-do-i-change-the-root-directory-of-an-apache-server

https://stackoverflow.com/questions/8940230/how-can-i-run-a-sql-text-file-on-a-mysql-database

https://aws.amazon.com/premiumsupport/knowledge-center/set-change-root-linux/

https://stackoverflow.com/questions/41209349/requirevendor-autoload-php-failed-to-open-stream

https://stackoverflow.com/questions/38483837/please-provide-a-valid-cache-path

https://www.digitalocean.com/community/tutorials/how-to-rewrite-urls-with-mod_rewrite-for-apache-on-ubuntu-16-04

https://stackoverflow.com/questions/23921117/disable-only-full-group-by

https://dba.stackexchange.com/questions/59407/how-to-make-mysql-table-name-case-insensitive-in-ubuntu
