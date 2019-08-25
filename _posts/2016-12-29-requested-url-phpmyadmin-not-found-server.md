---
layout: post
title:  "The requested url /phpmyadmin/ was not found on this server"
author: vijayan
categories: [ Linux ]
tags: [Apache, Linux Tips, PHPMyAdmin was not found]
image: assets/images/2016/12/phpmyadmin.png
description: "If you get a 404 error(the requested url /phpmyadmin was not found on this server.)upon visiting http://localhost/phpmyadmin: You will need to configure apache2.conf to work with PHPMyAdmin."
featured: true
hidden: true
rating: 5
toc: true
---
PHPMyAdmin is a free software tool written in PHP, intended to handle the administration of MySQL over the Web. PHPMyAdmin supports a wide range of operations on MySQL and MariaDB. Frequently used operations (managing databases, tables, columns, relations, indexes, users, permissions, etc) can be performed via the user interface, while you still have the ability to directly execute any SQL statement.

### Features

1. Intuitive web interface
2. Support for most MySQL features:
   * browse and drop databases, tables, views, fields and indexes
   * create, copy, drop, rename and alter databases, tables, fields, and indexes
   * maintenance server, databases, and tables, with proposals on server configuration
   * execute, edit and bookmark any SQL-statement, even batch-queries
   * manage MySQL user accounts and privileges
   * manage stored procedures and triggers
3. Import data from CSV and SQL
4. Export data to various formats: CSV, SQL, XML, PDF, ISO/IEC 26300 - OpenDocument Text and Spreadsheet, Word, LATEX, and others
5. Administering multiple servers
6. Creating graphics of your database layout in various formats
7. Creating complex queries using Query-by-example (QBE)
8. Searching globally in a database or a subset of it
9. Transforming stored data into any format using a set of predefined functions, like displaying BLOB-data as image or download-link
10. And much more...

If you get a 404 error (the requested url /phpmyadmin was not found on this server.) upon visiting [http://localhost/phpmyadmin](http://localhost/phpmyadmin): You will need to configure apache2.conf to work with PHPMyAdmin.

![Not Found](/assets/images/2016/12/phpmyadmin-not-found.png "Not Found"){: .shadow-lg }

### Edit apache2.conf

Open apache2.conf file with your favorite editor,

```bash
sudo nano /etc/apache2/apache2.conf
```

![Open apache2.conf](/assets/images/2016/12/apache2-config.png "apache2.conf"){: .shadow-lg }

### Include PHPMyAdmin configuration file

Then add the following line to the end of the file

```bash
Include /etc/phpmyadmin/apache.conf
```

![Include](/assets/images/2016/12/phpmyadmin-configuration.png "Include /etc/phpmyadmin/apache.conf"){: .shadow-lg }

Save and exit. or `(ctrl+o and ctrl+x)`.

### Restart Apache

```bash
sudo /etc/init.d/apache2 restart
```

or

```bash
sudo service apache2 restart
```

or

```bash
sudo systemctl restart apache2.service
```

or

```bash
sudo service apache2 reload
```

### Alternative method

Please follow the steps listed below,

```bash
sudo ln -s /etc/phpmyadmin/apache.conf /etc/apache2/conf-available/phpmyadmin.conf
sudo a2enconf phpmyadmin
sudo service apache2 reload
```
