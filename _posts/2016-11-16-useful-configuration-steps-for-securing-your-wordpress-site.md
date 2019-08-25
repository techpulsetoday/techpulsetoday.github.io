---
layout: post
title:  "Useful Configuration Steps for Securing Your WordPress Site"
author: vijayan
categories: [ WordPress ]
tags: [ Security, Tips and Tricks, WordPress]
image: assets/images/2016/12/wp-config.png
description: "wp-config file is a heart of your website, specify how your WordPress site should operate. And make wp-config file becomes inaccessible."
toc: true
---
wp-config file is a heart of your website, specify how your WordPress site should operate. And make wp-config file becomes inaccessible.

### Security Keys

You don’t have to remember the keys, just make them long, random and complicated that’s it. You can generate a new set of security keys using the WordPress [Security Key Generator](https://api.wordpress.org/secret-key/1.1/salt/){:target="_blank"}. You can change these at any time to invalidate all existing cookies. This does mean that all users will have to log in again. Copy the new key and paste it.

```php
/* Authentication Unique Keys and Salts. */
define('AUTH_KEY',         'v>shDt{Dt{<u)0eA^JD-O7,n;%9OCAtm0`9Go(+J&Y:nd>bn85jV->cZsRON@~/!');
define('SECURE_AUTH_KEY',  'LbS#C4+HZnO%+u>SvoAXgpd0-+2BOfoB8OP|}FmJb^a*M{CpN}:7PO)>3N1[M)XY');
define('LOGGED_IN_KEY',    'Ww;*o+oB(~c%1QyMdPM>*I|$K43*hSALeg#ZY%[+U7zvs~?^b#Pc-}~,8o(~*m~2');
define('NONCE_KEY',        'ksd;Xfe+($8p^Gole|u#PGn/b|P&Qy_!VS;[OZbV;NA{rqG1$3sI0u2wBr+]Sp2<');
define('AUTH_SALT',        'M=5>A`R!7mdu|+qD3G[BBSVX*vH|5nQFSl+HF[R+l<DI|x>+*B[a5|9`/HM-Y8w9');
define('SECURE_AUTH_SALT', '^WmzY$oD(kK`>i]i-V+ZCT#%p(a-+@1h5)>2~V`g,|xVLyy-bdjUlB&HBoM|b^1g');
define('LOGGED_IN_SALT',   '#pP@,DJ9.Z0=Lp U2s8W!jIM+2<Q+dsM9[yB-;/|KL?Fh(zgAk/H6reA&N?W<&wQ');
define('NONCE_SALT',       'k_4S=+$O+#y#[K9%/W*tb>E2`-EX#&Q*!4Y fCnew]-,K</~`lUJ6LnsV:dmKmF_');
```

### MySQL database table prefix

A table_prefix is placed in front of your database tables. By default, it’s set to **`wp_`**, change to something **`6dRxWf_`** like this. For the securing purpose, please try to change **`user_table`** and **`user_meta_table`** names. Please remember when you are using table prefix use only numbers, letters, and underscores.

```php
/* MySQL database table prefix. */
$table_prefix = '6dRxWf_';
define( 'CUSTOM_USER_TABLE',      $table_prefix . 'brandname_user' );
define( 'CUSTOM_USER_META_TABLE', $table_prefix . 'brandname_usermeta' );
```

### Moving and rename the wp-content folder

The wp-content directory will store all your theme files, plugin files, and images. Why Move The wp-content Folder The best reason to move the wp-content is for security if you move this to an unexpected location any hackers looking to target this area won’t be able to find it, or it will make it more difficult to find.

```php
/* Custom WordPress URL. */
define ('WP_CONTENT_FOLDERNAME', 'brandname');
define ('WP_CONTENT_DIR', ABSPATH . WP_CONTENT_FOLDERNAME) ;
define('WP_SITEURL', 'http://' . $_SERVER['HTTP_HOST'] . '/');
define('WP_CONTENT_URL', WP_SITEURL . WP_CONTENT_FOLDERNAME);
```

### Move the WordPress Plugin Directory

1. Set WP_PLUGIN_DIR to the full **`local path`** of this directory (no trailing slash)
2. Set WP_PLUGIN_URL to the full **`URI`** of this directory (no trailing slash)

```php
/* Move the WordPress Plugin Directory */
define( 'WP_PLUGIN_DIR', dirname(__FILE__) . '/brandname/foldername/plugins' );
define( 'WP_PLUGIN_URL', 'http://' . $_SERVER['HTTP_HOST'] . '/brandname/foldername/plugins' );
```

### Move the WordPress Theme folder

You cannot move the themes folder because its path is hard coded relative to the wp-content folder.

```php
$theme_root = WP_CONTENT_DIR . '/themes';
```

### Move Uploads Directory

```php
/* Move Uploads Directory */
define( 'UPLOADS', 'brandname/media');
```

This path can not be absolute. It is always relative to ABSPATH, therefore does not require a leading slash. Add the define just after this:

```php
/** Absolute path to the WordPress directory. */
if ( !defined('ABSPATH') )
    define('ABSPATH', dirname(__FILE__) . '/');
```

### Install plugins on localhost

In some cases, you are not able to update/upgrade your WordPress plugins to a newer version without providing your FTP connection information. This is a common issue whereby the WordPress system can’t write to your **`/wp-content`** folder directly.

To solve this issue you need to define the FTP details. So WordPress will remember it. Alternatively, you may also provide WordPress with write access to your **`/wp-content`** folder by accessing the FTP root file and changing the folder file permission (CHMOD) to 775 rather than the default 755 and 644.

There is, however, an easier way to deal with this; by defining constant, **`FS_METHOD`** in your **`wp-config.php`** file. This bypasses WordPress’s recurring prompts and allows auto-updates of your files to happen. And it takes only 1 line of code to do this.

```php
/* Unable to install plugins on localhost */
define('FS_METHOD','direct');
```

### Disable Post Revisions

Defaults WordPress WP_POST_REVISIONS to true (enable post revisions). If you want to disable the feature, use this setting:

```php
/* Disable Post Revisions. */
define( 'WP_POST_REVISIONS', false );
```

or

```php
/* Disable Post Revisions. */
define( 'WP_POST_REVISIONS', 3 );
```

### Media Trash

This constant controls the number of days before WordPress permanently deletes posts, pages, attachments, and comments, from the trash bin. The default is 30 days:

```php
/* Media Trash. */
define( 'MEDIA_TRASH', true );
/* Trash Days. */
define( 'EMPTY_TRASH_DAYS', '7' );
```

### WordPress debug mode for developers

```php
/* WordPress debug mode for developers. */
define( 'WP_DEBUG',         false );
define( 'WP_DEBUG_LOG',     true );
define( 'WP_DEBUG_DISPLAY', false );
define( 'SCRIPT_DEBUG',     true );
define( 'SAVEQUERIES',      false );
```

### Save queries for analysis

If “SAVEQUERIES” is true your website performance is getting slow, better we can turn off this if you are not debugging or troubleshooting.

```php
define( 'SAVEQUERIES', true );
```

Then in the footer of your theme put this:

```php
<?php
if ( current_user_can( 'administrator' ) ) {
    global $wpdb;
    echo "<pre>";
    print_r( $wpdb->queries );
    echo "</pre>";
}
?>
```

### PHP Memory

```php
/* PHP Memory */
define( 'WP_MEMORY_LIMIT', '128' );
define( 'WP_MAX_MEMORY_LIMIT', '256' );
```

### Compression

```php
/* Compression */
define( 'COMPRESS_CSS',        true );
define( 'COMPRESS_SCRIPTS',    true );
define( 'CONCATENATE_SCRIPTS', true );
define( 'ENFORCE_GZIP',        true );
```

### Updates

```php
/* Updates */
define( 'WP_AUTO_UPDATE_CORE', true );
define( 'DISALLOW_FILE_MODS', true );
define( 'DISALLOW_FILE_EDIT', true );
```

### Automatic Database Optimizing

The script can be found at `{$your_site}/wp-admin/maint/repair.php`

```php
/* Automatic Database Optimizing */
define( 'WP_ALLOW_REPAIR', true );
define( 'DO_NOT_UPGRADE_GLOBAL_TABLES', true );
```

### Block External URL Requests

Block external URL requests by defining WP_HTTP_BLOCK_EXTERNAL as true and this will only allow localhost and your blog to make requests. The constant WP_ACCESSIBLE_HOSTS will allow additional hosts to go through for requests. The format of the WP_ACCESSIBLE_HOSTS constant is a comma separated list of hostnames to allow, wildcard domains are supported.

```php
/* Blok External URL Requests */
define( 'WP_HTTP_BLOCK_EXTERNAL', true );
define( 'WP_ACCESSIBLE_HOSTS', 'api.wordpress.org,techpulsetoday.com' );
```

### Cleanup-Image Edits

By default, WordPress creates a new set of images every time you edit an image and when you restore the original, it leaves all the edits on the server. Defining IMAGE_EDIT_OVERWRITE as true changes this behavior. Only one set of image edits are ever created and when you restore the original, the edits are removed from the server.

```php
/* Cleanup-Image Edits */
define( 'IMAGE_EDIT_OVERWRITE', true );
```

### Override of default file permissions

```php
/* Override of default file permissions */
define( 'FS_CHMOD_DIR', ( 0755 & ~ umask() ) );
define( 'FS_CHMOD_FILE', ( 0644 & ~ umask() ) );
```

### View All Defined Constants

It returns an array of all the currently defined constants with their values.

```php
print_r( @get_defined_constants() );
```
