# Instaling-SYSPASS-store-passwords


Enter the path /var/www/html and get the SYSPASS https://github.com/nuxsmin/sysPass/releases
```bash
wget https://github.com/nuxsmin/sysPass/archive/refs/tags/3.2.2.tar.gz
```

Unpack the file tar.gz
```bash
tar -xzvf  3.2.2.tar.gz
```

```bash
mv sysPass-3.2.2/ syspass
```

Configure permissions
```bash
chmod -R 750 /var/www/html/syspass/ ; chown -R apache /var/www/html/syspass
```

Install PHP 7.3

```bash
yum install -y http://rpms.remirepo.net/enterprise/remi-release-7.rpm
yum install https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
```


```bash
sudo yum -y install yum-utils
```


```bash
sudo yum-config-manager --enable remi-php73
```

```bash
sudo yum -y install php php-cli
```
```bash
yum install -y php php-mcrypt php-cli php-gd php-curl php-mysql php-ldap php-zip php-fileinfo 
```

```bash
yum install -y php-mbstring php-mysqlnd php-curl php-json php-gd php-xml php-mbstring php-intl php-readline php-ldap php-mcrypt unzip wget
```

enter the path /var/www/html/syspass and execute the script below

```bash
#!/bin/sh
EXPECTED_SIGNATURE="$(wget -q -O - https://composer.github.io/installer.sig)"
php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
ACTUAL_SIGNATURE="$(php -r "echo hash_file('sha384', 'composer-setup.php');")"

if [ "$EXPECTED_SIGNATURE" != "$ACTUAL_SIGNATURE" ]
then
    >&2 echo 'ERROR: Invalid installer signature'
    rm composer-setup.php
    exit 1
fi

php composer-setup.php --quiet
RESULT=$?
rm composer-setup.php
exit $RESULT


```


Install mariadb


```bash
yum install -y mariadb-server
```

```bash
systemctl enable mariadb ; systemctl start mariadb
```


```bash
mysql_secure_installation
```

Enter the path /var/www/html/syspass and execute the command below

```bash
php composer.phar install --no-dev
```



#Update syspass

Database process

```bash
create user 'syspass'@'localhost' identified by '123' ;
```

```bash
create user 'syspass'@'%' identified by '123' ;
```

```bash
create database syspass33 ;
```

```bash
grant all privileges on *.* to 'syspass'@'localhost' ;
```

```bash
grant all privileges on syspass33.* to 'syspass'@'localhost' ;
```

```bash
grant all privileges on syspass33.* to 'syspass'@'%' ;
```

```bash
grant all privileges on *.* to 'syspass'@'%' ;
```

```bash
scp root@OLDSYSPASS:/var/www/html/syspassOLD/app/config/config.xml /var/www/html/syspassNEW/app/config/
```

```bash
chmod -R 750 /var/www/html/syspassNEW/app/config/ ; chown -R apache /var/www/html/syspassNEW/app/config/
```
execute script

```bash

```bash
#!/bin/sh
EXPECTED_SIGNATURE="$(wget -q -O - https://composer.github.io/installer.sig)"
php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
ACTUAL_SIGNATURE="$(php -r "echo hash_file('sha384', 'composer-setup.php');")"

if [ "$EXPECTED_SIGNATURE" != "$ACTUAL_SIGNATURE" ]
then
    >&2 echo 'ERROR: Invalid installer signature'
    rm composer-setup.php
    exit 1
fi

php composer-setup.php --quiet
RESULT=$?
rm composer-setup.php
exit $RESULT

```

```bash
php composer.phar install --no-dev
```

```bash
systemctl restart httpd

```

# Install plugin double factor authentication

Install composer v2

```bash
php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
```
```bash
php composer-setup.php

```
```bash
chmod +x composer.phar
```
```bash
mv composer.phar /usr/bin
```
```bash
composer --version
```
Install Plugin, after that, enable plugin from front-end app
```bash
composer require syspass/plugin-authenticator:^v2.0
```










