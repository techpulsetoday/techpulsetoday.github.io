---
title: How to Manually Upgrade phpMyAdmin on Ubuntu
layout: post
author: vijayan
categories:
- Linux
tags:
- Linux-Tips
image: assets/images/2019/09/phpmyadmin-4-9-0-1.png
description: phpMyAdmin is a most popular MySQL client to access and manage your database.
  The phpMyAdmin installation via apt package manager create multiple directories.
featured: true
hidden: true
rating: 5
toc: true
---

phpMyAdmin is a most popular MySQL client to access and manage your database. The phpMyAdmin installation via apt package manager create multiple directories (`sudo apt-get install phpmyadmin`).

1. /usr/share/phpmyadmin – Main phpMyAdmin installation
2. /var/lib/phpmyadmin – Library and tmp directries
3. /etc/phpmyadmin – Configuration files

## Backup phpMyAdmin

We have to take a backup of current phpMyAdmin folder. I have just run the below command to rename phpMyAdmin folder in the same directory.

```sh
CURRENTDATE=`date +%Y_%m_%d_%H_%M_%S`
sudo mv /usr/share/phpmyadmin/ /usr/share/phpmyadmin_bak_${CURRENTDATE}
```

## Download Latest phpMyAdmin

```sh
wget --no-check-certificate --content-disposition https://www.phpmyadmin.net/downloads/phpMyAdmin-latest-all-languages.zip -P /tmp
```

## Unzip the file

```sh
unzip -qq /tmp/phpMyAdmin-*-all-languages.zip -d /tmp
```

## Move phpMyAdmin folder

```sh
sudo mv /tmp/phpMyAdmin-*-all-languages /usr/share/phpmyadmin
```

## Update the configuration file

Edit vendor_config.php file.

```sh
sudo vim /usr/share/phpmyadmin/libraries/vendor_config.php
```

and update the following values.

```sh
define('TEMP_DIR', '/var/lib/phpmyadmin/tmp/');
define('CONFIG_DIR', '/etc/phpmyadmin/');
```

## Easiest method to update the configuration file

```sh
sed -i "s+'TEMP_DIR', ROOT_PATH . 'tmp/'+'TEMP_DIR', '/var/lib/phpmyadmin/tmp/'+g" /usr/share/phpmyadmin/libraries/vendor_config.php
sed -i "s+'CONFIG_DIR', ROOT_PATH+'CONFIG_DIR', '/etc/phpmyadmin/'+g" /usr/share/phpmyadmin/libraries/vendor_config.php
```

You don't need to install anything. Just execute bash script from a remote site.

```sh
bash <(curl -Ls https://gist.githubusercontent.com/techpulsetoday/b138b94295d19115d7afffc10abeba8e/raw/)
```

{% gist b138b94295d19115d7afffc10abeba8e %}
