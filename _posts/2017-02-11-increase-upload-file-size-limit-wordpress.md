---
layout: post
title:  "How to increase upload file size limit in WordPress"
author: vijayan
categories: [ WordPress ]
tags: [ increase upload file size limit, WordPress ]
image: assets/images/2017/02/how-to-increase-upload-file-size-limit-in-wordpress.png
description: "Some host set the default upload size for WordPress to 2MB which is extremely low. This can cause an error when you try to upload files that are larger than this size."
---
Some host set the default upload size for WordPress to 2MB which is extremely low. This can cause an error when you try to upload files that are larger than this size. The error would see would be something like:

<blockquote>File exceeds the maximum upload size for this site.</blockquote>

<h3>php.ini Method</h3>

If you are using shared hosting like GoDaddy, Bluehost, you will not see a php.in file. Create a file called php.in and upload it in the root directory, then edit php.ini add the below code.

<pre class="lang:default decode:true"># Increase php memory limit
memory_limit = 256M
upload_max_size = 64M
post_max_size = 64M
upload_max_filesize = 64M
max_execution_time = 300
max_input_time = 1000</pre>

<h3>.htaccess Method</h3>

Open or create the .htaccess file in the root folder and add the following code.

<pre class="lang:default decode:true"># Increase php memory limit
php_value memory_limit 256
php_value upload_max_filesize 64M
php_value post_max_size 64M
php_value max_execution_time 300
php_value max_input_time 1000</pre>

<h3>wp-config.php Method</h3>

<pre class="lang:default decode:true">/**
 * Increase php memory limit: (Yes, "M", not "MB")
 * (you may need to do this for upload scripts or something)
 */
define( 'WP_MEMORY_LIMIT', '128M' );
define( 'WP_MAX_MEMORY_LIMIT', '256M' );</pre>

<h3>functions.php Method</h3>

<pre class="lang:default decode:true  ">/* Increase php memory limit */
@ini_set( 'upload_max_size' , '64M' );
@ini_set( 'post_max_size', '64M');
@ini_set( 'max_execution_time', '300' );</pre>

<h3>WordPress Multisite Method</h3>

If your website is a WordPress multisite installation and your php.ini is in OK but still unable to upload large files, follow the steps below.
Navigate to Settings &gt;&gt; Network Settings.
In Max upload file size under Upload Settings section, increase the field value to a higher kilobyte value. For example, inserting 9000 will increase the upload limit to 9 megabytes (MB).

<h3 class="related-posts-main-title">Suggested Read:</h3>

<h4 class="related-posts-main-title"><a title="Useful WordPress Functions" href="/useful-wordpress-functions/">Useful WordPress Functions</a></h4>

<h4 class="related-posts-main-title"><a title="Useful configuration steps for securing your wordpress site" href="/useful-configuration-steps-for-securing-your-wordpress-site/">Useful configuration steps for securing your WordPress site</a></h4>