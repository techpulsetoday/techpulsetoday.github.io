---
layout: post
title:  "How to fix the Unknown collation: ‘utf8mb4_unicode_ci’ error"
author: vijayan
categories: [ WordPress ]
tags: [ Linux Commands, MySQL, utf8mb4, WordPress ]
image: assets/images/2017/04/utf8mb4_unicode_ci.png
description: "utf8 values are stored as 3 bytes, where utf8mb4 are stored as 4 bytes. This new encoding (utf8mb4_unicode_ci) type was introduced in MySQL version 5.5.3."
toc: true
---
utf8 values are stored as 3 bytes, where utf8mb4 are stored as 4 bytes. This new encoding type was introduced in MySQL version 5.5.3. This can cause some issues if you’re attempting to migrate from 5.5.3+ to an older database.

## The utf8mb4 Upgrade

Since WordPress 4.2, they are upgrading tables to utf8mb4 Your site will only upgrade when the following conditions are met:

1. You're currently using the utf8 character set.
2. Your MySQL server is version 5.5.3 or higher (including all 10.x versions of MariaDB).
3. Your MySQL client libraries are version 5.5.3 or higher. If you're using mysqlnd, 5.0.9 or higher.

### Method 1

Log in to your database server using [phpMyAdmin](/requested-url-phpmyadmin-not-found-server/).

If you export normally, you’ll most likely get the error message of Unknown collation: ‘utf8mb4_unicode_ci’ when importing into an older MySQL database.

To export to older MySQL databases, follow these few steps:

1. Make sure you select your database and go to the "Export" tab
2. Select the "Custom" radio button
3. Go the section "Format-specific options" and in the setting for "Database system or older MySQL server to maximize output compatibility with:" select MYSQL40.
4. Scroll to the bottom and click GO.

![utf8mb4_unicode_ci](/assets/images/2017/04/utf8mb4_unicode_ci.png "utf8mb4_unicode_ci")

![utf8mb4_unicode_ci](/assets/images/2017/04/utf8mb4_unicode_ci-1.png "utf8mb4_unicode_ci")

### Method 2

For a command line export using mysqldump.

```bash
mysqldump -u root -p --compatible=mysql4 techpulsetoday > techpulsetoday.sql
```

```bash
sed -i 's/TYPE=InnoDB/ENGINE=InnoDB/g' techpulsetoday.sql
```

then restore techpulsetoday.sql

```bash
mysql -u root -p techpulsetoday < techpulsetoday.sql
```

### Method 3

Search and Replace through Terminal.

utf8_unicode_ci to utf8_general_ci (or) utf8mb4_unicode_ci to utf8mb4_general_ci

```bash
sed -i 's/utf8mb4/utf8/g' techpulsetoday.sql
sed -i 's/utf8_unicode_ci/utf8_general_ci/g' techpulsetoday.sql
sed -i 's/utf8_unicode_520_ci/utf8_general_ci/g' techpulsetoday.sql
```

then restore techpulsetoday.sql

```bash
mysql -u root -p techpulsetoday < techpulsetoday.sql
```

***Important Note:*** Converting from utf8mb4 to utf8 may cause loss of data. It is advisable to take a full database backup, before carrying out the steps below and inspect your site in full after the changes, to ensure there is no corruption.
