---
layout: post
title:  "How to fix the Unknown collation: &#8216;utf8mb4_unicode_ci&#8217; error"
author: vijayan
categories: [ WordPress ]
tags: [ Linux Commands, MySQL, utf8mb4, WordPress ]
image: assets/images/2017/04/utf8mb4_unicode_ci.png
description: "utf8 values are stored as 3 bytes, where utf8mb4 are stored as 4 bytes. This new encoding (utf8mb4_unicode_ci) type was introduced in MySQL version 5.5.3."
---
utf8 values are stored as 3 bytes, where utf8mb4 are stored as 4 bytes. This new encoding type was introduced in MySQL version 5.5.3. This can cause some issues if you're attempting to migrate from 5.5.3+ to an older database.
<h2>The utf8mb4 Upgrade:</h2>
Since WordPress 4.2, they are upgrading tables to utf8mb4
Your site will only upgrade when the following conditions are met:
<ol>
 	<li>You're currently using the utf8 character set.</li>
 	<li>Your MySQL server is version 5.5.3 or higher (including all 10.x versions of MariaDB).</li>
 	<li>Your MySQL client libraries are version 5.5.3 or higher. If you're using mysqlnd, 5.0.9 or higher.</li>
</ol>
<h2>Method 1:</h2>
Log in to your database server using <strong><a href="https://www.techpulsetoday.com/requested-url-phpmyadmin-not-found-server/">phpMyAdmin</a>.</strong>

If you export normally, you'll most likely get the error message of Unknown collation: 'utf8mb4_unicode_ci' when importing into an older MySQL database.

To export to older MySQL databases, follow these few steps:
<ol>
 	<li>Make sure you select your database and go to the "<strong>Export"</strong>&nbsp;tab</li>
 	<li>Select the "<strong>Custom"</strong>&nbsp;radio button</li>
 	<li>Go the section "<strong>Format-specific options</strong>" and in the setting for "Database system or older MySQL server to maximize output compatibility with:" select <strong>MYSQL40</strong>.</li>
 	<li>Scroll to the bottom and click <strong>GO</strong>.</li>
</ol>
<img class="aligncenter size-full wp-image-418" src="/assets/images/2017/04/utf8mb4_unicode_ci.png" alt="utf8mb4_unicode_ci" width="1036" height="387">

<img class="aligncenter size-full wp-image-419" src="/assets/images/2017/04/utf8mb4_unicode_ci-1.png" alt="utf8mb4_unicode_ci" width="714" height="413">
<h2>Method 2:</h2>
For a command line export using mysqldump.
<pre class="lang:default decode:true" title="MySQL Dump">mysqldump -u root -p --compatible=mysql4 techpulsetoday &gt; techpulsetoday.sql</pre>
<pre class="lang:default decode:true " title="Engine Type">sed -i 's/TYPE=InnoDB/ENGINE=InnoDB/g' techpulsetoday.sql</pre>
then restore techpulsetoday.sql
<pre class="lang:default decode:true">mysql -u root -p techpulsetoday &lt; techpulsetoday.sql</pre>
<h2>Method 3:</h2>
Search and Replace through Terminal.

utf8_unicode_ci to utf8_general_ci (or) utf8mb4_unicode_ci to utf8mb4_general_ci
<pre class="lang:default decode:true" title="Search and Replace">sed -i 's/utf8mb4/utf8/g' techpulsetoday.sql
sed -i 's/utf8_unicode_ci/utf8_general_ci/g' techpulsetoday.sql
sed -i 's/utf8_unicode_520_ci/utf8_general_ci/g' techpulsetoday.sql</pre>
then restore techpulsetoday.sql
<pre class="lang:default decode:true">mysql -u root -p techpulsetoday &lt; techpulsetoday.sql</pre>
<strong>Important Note:</strong> Converting from utf8mb4 to utf8 may cause loss of data. It is advisable to take a full database backup, before carrying out the steps below and inspect your site in full after the changes, to ensure there is no corruption.