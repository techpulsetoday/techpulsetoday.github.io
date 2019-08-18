---
layout: post
title:  "How To Create Apache Virtual Host in Ubuntu"
author: vijayan
categories: [ Linux ]
tags: [ Apache, Linux Tips, Server, Virtual Host ]
image: assets/images/2017/03/vitual-host.png
description: "How To Create Apache Virtual Host in Ubuntu. This article will help you to create Virtual hosts in Apache2 server on Ubuntu systems."
---
<h2>Install the Apache Web Server</h2>
Before Create Apache Virtual Host files, we need to check in your system whether Apache Server installed or not. If it is installed no need to anything. If it is not installed type the following commands.

<pre class="lang:default decode:true" title="Install the Apache WebServer">sudo apt-get update
sudo apt-get install apache2</pre>

After installing Apache Server, Let's test whether the web server is working properly or not by navigating to the URL <strong><a href="https://www.techpulsetoday.com/">http://ip-address/</a> or <a href="https://www.techpulsetoday.com/">http://localhost/</a>. </strong>It will open Apache Ubuntu Default Page.

<h2>Create  a Virtual Directories</h2>

Create a directory in root folder (ie. public_html folder)

<pre class="lang:default decode:true" title="Create a Directories">cd /var/www/html/
sudo mkdir dev1.techpulsetoday.com
sudo mkdir dev2.techpulsetoday.com</pre>

<h2>Create a Demo Pages</h2>

Create an <strong>index.html</strong> file in nano or vim editor by typing,

<pre class="lang:default decode:true" title="Create an index.html">sudo nano dev1.techpulsetoday.com/index.html</pre>

<pre class="lang:default decode:true" title="html h1 tag">&lt;h1&gt;Good! dev1.techpulsetoday.com Virtual Host is Working fine!&lt;/h1&gt;</pre>

Do the same thing for Virtual Host Directory 2

<pre class="lang:default decode:true" title="Create an index.html">sudo nano dev2.techpulsetoday.com/index.html</pre>

<pre class="lang:default decode:true" title="html h1 tag">&lt;h1&gt;Good! dev2.techpulsetoday.com Virtual Host is Working fine!&lt;/h1&gt;</pre>

<h2>Give the Proper Ownership and Permissions</h2>

Navigate to corresponding Virtual Host Directory and then run the below commands.

ie. <em><strong>cd /var/www/html/dev1.techpulsetoday.com/ and cd /var/www/html/dev2.techpulsetoday.com/</strong></em>

<pre class="lang:default decode:true" title="Ownership and Permissions">sudo chown www-data:www-data -R *
sudo find . -type d -exec chmod 755 {} \;
sudo find . -type f -exec chmod 644 {} \;</pre>

<h2>Create Virtual Host Files</h2>

By default, Apache comes with a default virtual host file called <em><strong>000-default.conf</strong></em>. We will copy the <em><strong>000-default.conf</strong></em> file contents or Create a new Virtual Host files.

<pre class="lang:default decode:true" title="Diretory">vijayan@vijayan-VPCCA35FA:/var/www/html/dev1.techpulsetoday.com$ cd /etc/apache2/sites-available/
vijayan@vijayan-VPCCA35FA:/etc/apache2/sites-available$ pwd
/etc/apache2/sites-available
vijayan@vijayan-VPCCA35FA:/etc/apache2/sites-available$ ls
000-default.conf
vijayan@vijayan-VPCCA35FA:/etc/apache2/sites-available$</pre>

Now you are in this location -&gt; <em><strong>/etc/apache2/sites-available</strong></em>

<pre class="lang:default decode:true" title="Create Files">sudo touch dev1.techpulsetoday.com.conf
sudo touch dev2.techpulsetoday.com.conf</pre>

Make sure the Virtual Host files contains <em><strong>.conf</strong></em> extension at the end.

Now open <strong>dev1.techpulsetoday.com.conf, </strong>nano or vim editor by typing

<pre class="lang:default decode:true" title="Edit dev1.techpulsetoday.com.conf file">sudo nano dev1.techpulsetoday.com.conf</pre>

Copy paste bellow code.

<pre class="lang:default decode:true" title="Configuration">&lt;VirtualHost *:80&gt;
        ServerName dev1.techpulsetoday.com
        ServerAlias www.dev1.techpulsetoday.com
        ServerAdmin vijayan@techpulsetoday.com
        DocumentRoot /var/www/html/dev1.techpulsetoday.com
&lt;Directory "/var/www/html/dev1.techpulsetoday.com"&gt;
    AllowOverride All
    Order allow,deny
    Allow from all
&lt;/Directory&gt;
        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined
&lt;/VirtualHost&gt;</pre>

Likewise, open <strong>dev2.techpulsetoday.com.conf, </strong>nano or vim editor by typing

<pre class="lang:default decode:true" title="Edit dev2.techpulsetoday.com.conf file">sudo nano dev2.techpulsetoday.com.conf</pre>

Copy paste bellow code.

<pre class="lang:default decode:true" title="Configuration">&lt;VirtualHost *:80&gt;
        ServerName dev2.techpulsetoday.com
        ServerAlias www.dev2.techpulsetoday.com
        ServerAdmin vijayan@techpulsetoday.com
        DocumentRoot /var/www/html/dev2.techpulsetoday.com
&lt;Directory "/var/www/html/dev2.techpulsetoday.com"&gt;
    AllowOverride All
    Order allow,deny
    Allow from all
&lt;/Directory&gt;
        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined
&lt;/VirtualHost&gt;</pre>

<h2>Check Virtual Host Configuration Syntax</h2>

To check configuration files for syntax errors:

<pre class="lang:default decode:true" title="check configuration files for syntax errors"># Fedora, RHEL, CentOS, OSX
httpd -t

# Debian, Ubuntu
apache2ctl -t

# MacOS
apachectl -t</pre>

To list all Virtual Hosts and their locations:

<pre class="lang:default decode:true" title="list all Virtual Hosts and their locations"># Fedora, RHEL, CentOS, OSX
httpd -S

# Debian, Ubuntu
apache2ctl -S

# MacOS
apachectl -S</pre>

<h2>Enable the Newly Created Virtual Host Files</h2>

<pre class="lang:default decode:true" title="a2ensite files">sudo a2ensite dev1.techpulsetoday.com.conf
sudo a2ensite dev2.techpulsetoday.com.conf</pre>

After Enabling Virtual Host, you need to restart Apache Server.

<pre class="lang:default decode:true" title="Restart Apache"># In Ubuntu 15.10/15.04:
sudo systemctl restart apache2

# In Ubuntu 14.10 and earlier versions:
sudo service apache2 restart</pre>

<h2>Setup Local Host Files</h2>

Edit file, /etc/hosts,

<pre class="lang:default decode:true" title="Edit Local Host File">sudo nano /etc/hosts</pre>

Add the Virtual Domain Names one by one as shown below

<pre class="lang:default decode:true" title="Local Host File">#####################################
# Virtual Host
#####################################
127.0.1.1       dev1.techpulsetoday.com
127.0.1.1       dev2.techpulsetoday.com
</pre>

restart your apache if require.

<h2>Test your Results</h2>

Open your browser and type URL http://dev1.techpulsetoday.com/ and http://dev2.techpulsetoday.com/

<h3><span style="color: #073c65;">dev1.techpulsetoday.com Page</span></h3>

<img class="aligncenter size-full wp-image-368" src="/assets/images/2017/03/dev1.techpulsetoday.com_.png" alt="dev1.techpulsetoday.com" width="1365" height="208" />

<h3><span style="color: #073c65;">dev2.techpulsetoday.com Page</span></h3>

<img class="aligncenter size-full wp-image-369" src="/assets/images/2017/03/dev2.techpulsetoday.com_.png" alt="dev2.techpulsetoday.com" width="1365" height="197" />

If both of these sites work, you've successfully configured two Virtual Hosts on the same Server.