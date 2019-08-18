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
rating: 4.5
---

<h2>About</h2>
PHPMyAdmin is a free software tool written in PHP, intended to handle the administration of MySQL over the Web. PHPMyAdmin supports a wide range of operations on MySQL and MariaDB. Frequently used operations (managing databases, tables, columns, relations, indexes, users, permissions, etc) can be performed via the user interface, while you still have the ability to directly execute any SQL statement.
<h2>Features</h2>
<ul>
 	<li>Intuitive web interface</li>
 	<li>Support for most MySQL features:
<ul>
 	<li>browse and drop databases, tables, views, fields and indexes</li>
 	<li>create, copy, drop, rename and alter databases, tables, fields, and indexes</li>
 	<li>maintenance server, databases, and tables, with proposals on server configuration</li>
 	<li>execute, edit and bookmark any SQL-statement, even batch-queries</li>
 	<li>manage MySQL user accounts and privileges</li>
 	<li>manage stored procedures and triggers</li>
</ul>
</li>
 	<li>Import data from CSV and SQL</li>
 	<li>Export data to various formats: CSV, SQL, XML, PDF, ISO/IEC 26300 - OpenDocument Text and Spreadsheet, Word, LATEX, and others</li>
 	<li>Administering multiple servers</li>
 	<li>Creating graphics of your database layout in various formats</li>
 	<li>Creating complex queries using Query-by-example (QBE)</li>
 	<li>Searching globally in a database or a subset of it</li>
 	<li>Transforming stored data into any format using a set of predefined functions, like displaying BLOB-data as image or download-link</li>
 	<li>And much more...</li>
</ul>
If you get a 404 error (the requested url /phpmyadmin was not found on this server.) upon <a href="https://www.techpulsetoday.com/">visiting</a> http://localhost/phpmyadmin: You will need to configure apache2.conf to work with PHPMyAdmin.

<img class="aligncenter size-full wp-image-231" src="/assets/images/2016/12/phpmyadmin-not-found.png" alt="phpmyadmin-not-found" width="1366" height="768">
<h2>Edit apache2.conf</h2>
Open apache2.conf file with your&nbsp;favorite editor,
<pre class="lang:default decode:true ">sudo nano /etc/apache2/apache2.conf</pre>
<img class="aligncenter size-full wp-image-229" src="/assets/images/2016/12/apache2-config.png" alt="apache2.config" width="1365" height="177">
<h2>Include PHPMyAdmin configuration file</h2>
Then add the following line to the end of the file
<pre class="lang:default decode:true ">Include /etc/phpmyadmin/apache.conf</pre>
<img class="aligncenter size-full wp-image-230" src="/assets/images/2016/12/phpmyadmin-configuration.png" alt="phpmyadmin-configuration" width="1366" height="768">

Save and exit. or (ctrl+o and ctrl+x).
<h2>Restart Apache</h2>
<pre class="lang:default decode:true ">sudo /etc/init.d/apache2 restart</pre>
or
<pre class="lang:default decode:true ">sudo service apache2 restart</pre>
or
<pre class="lang:default decode:true ">sudo systemctl restart apache2.service</pre>
or
<pre class="lang:default decode:true ">sudo service apache2 reload</pre>
<h2>Alternative method</h2>
Please follow the steps listed below,
<pre class="lang:default decode:true">sudo ln -s /etc/phpmyadmin/apache.conf /etc/apache2/conf-available/phpmyadmin.conf
sudo a2enconf phpmyadmin
sudo service apache2 reload</pre>