---
layout: post
title:  "Useful Configuration Steps for Securing Your WordPress Site"
author: vijayan
categories: [ WordPress ]
tags: [ Security, Tips and Tricks, WordPress]
image: assets/images/2016/12/wp-config.png
description: "wp-config file is a heart of your website, specify how your WordPress site should operate. And make wp-config file becomes inaccessible."
---
<h3><span id="Security_Keys" class="mw-headline">Security Keys:</span></h3>
You don't have to remember the keys, just make them long, random and complicated that's it. You can generate a new set of security keys using the WordPress <a href="https://api.wordpress.org/secret-key/1.1/salt/">Security Key Generator</a>. You can change these at any time to invalidate all existing cookies. This does mean that all users will have to log in again. Copy the new key and paste it.
<pre class="lang:default decode:true" title="Authentication Unique Keys and Salts">/* Authentication Unique Keys and Salts. */
define('AUTH_KEY',         '{|N7L~yMsLjtE7vc[[|4I*VaS*b~]KPAx{aW|kfSSPr.H;h&lt;oo]%98GR024DnH6y');
define('SECURE_AUTH_KEY',  'T%8i4Mhmd!t=-R}i;-IyeR_eCI#z|s~v$;%Ebg Mz&gt;(n(@LYKG-syN;Z%G`lE/ H');
define('LOGGED_IN_KEY',    '!Gsl1yz=&gt;jAnVYW=N@*,:B&gt;(?[Wq-1-~]vV|GO?h5Lk6HYF,m|&lt;k2+((A,qNe 5&amp;');
define('NONCE_KEY',        'SWvS4ci1Yg}B7v*akN~rlQz)na;#=#az-.meU*N$`$+&lt;ft|y7aQv+_b]?31.@^4{');
define('AUTH_SALT',        'Yxql4ZOJuBumiTxi*(KPxb[PD]v-&amp;lb;7$e[9L&lt;t`kvqwD;{xd#,v0WZr|wNR}YZ');
define('SECURE_AUTH_SALT', 'v.CJ=@C598Ea&lt;wf%p]6q]=BEB.l&gt;u) drC-#56&gt;^K2NvY.s+TD7CdzO#G^ :L3gF');
define('LOGGED_IN_SALT',   'YxG!au&amp;?EQ{&amp;Qn &lt;{n9jM-n,^BXgr2BiSqY+n~7kHwyYq-eJ|eL(RYq@H9lmj%)}');
define('NONCE_SALT',       '}*=b2NECH xd^|U1&amp;}_(}+:-#FJERDN1oFv2yY%iqPl18a&amp;k;}&lt;M)FO|U;v|=5_n');</pre>
<h3><span id="table_prefix" class="mw-headline">MySQL database table prefix:</span></h3>
A table_prefix is placed in front of your database tables. By default, it’s set to <strong>wp_</strong>, change to something <strong>6dRxWf_</strong> like this. For the securing purpose, please try to change <strong>user_table</strong> and <strong>user_meta_table</strong> names. Please remember when you are using table prefix use only numbers, letters, and underscores.
<pre class="lang:default decode:true" title="MySQL database table prefix">/* MySQL database table prefix. */
$table_prefix = '6dRxWf_';
define( 'CUSTOM_USER_TABLE',      $table_prefix . 'brandname_user' );
define( 'CUSTOM_USER_META_TABLE', $table_prefix . 'brandname_usermeta' );</pre>
<h3><span id="Moving_wp-content_folder" class="mw-headline">Moving and rename the wp-content folder:</span></h3>
The wp-content directory will store all your theme files, plugin files, and images. Why Move The wp-content Folder The best reason to move the wp-content is for security if you move this to an unexpected location any hackers looking to target this area won't be able to find it, or it will make it more difficult to find.
<pre class="lang:default decode:true" title="Custom WordPress URL">/* Custom WordPress URL. */
define ('WP_CONTENT_FOLDERNAME', 'brandname');
define ('WP_CONTENT_DIR', ABSPATH . WP_CONTENT_FOLDERNAME) ;
define('WP_SITEURL', 'http://' . $_SERVER['HTTP_HOST'] . '/');
define('WP_CONTENT_URL', WP_SITEURL . WP_CONTENT_FOLDERNAME);</pre>
<h3>Move the WordPress Plugin Directory:</h3>
<ol>
 	<li>Set <tt>WP_PLUGIN_DIR</tt> to the full <b>local path</b> of this directory (no trailing slash)</li>
 	<li> Set <tt>WP_PLUGIN_URL</tt> to the full <b>URI</b> of this directory (no trailing slash)</li>
</ol>
<pre class="lang:default decode:true" title="Move the WordPress Plugin Directory">/* Move the WordPress Plugin Directory */
define( 'WP_PLUGIN_DIR', dirname(__FILE__) . '/brandname/foldername/plugins' );
define( 'WP_PLUGIN_URL', 'http://' . $_SERVER['HTTP_HOST'] . '/brandname/foldername/plugins' );</pre>
<h3><span id="Moving_themes_folder" class="mw-headline">Move the WordPress Theme folder:</span></h3>
You cannot move the themes folder because its path is hard coded relative to the <tt>wp-content</tt> folder.
<pre class="lang:default decode:true" title="Move the WordPress Theme folder">$theme_root = WP_CONTENT_DIR . '/themes';</pre>
<h3>Move Uploads Directory:</h3>
<pre class="lang:default decode:true" title="Move Uploads Directory">/* Move Uploads Directory */
define( 'UPLOADS', 'brandname/media');</pre>
This path can not be absolute. It is always relative to ABSPATH, therefore does not require a leading slash. Add the define just after this:
<pre class="lang:default decode:true " title="Absolute path to the WordPress directory">/** Absolute path to the WordPress directory. */
if ( !defined('ABSPATH') )
	define('ABSPATH', dirname(__FILE__) . '/');</pre>
<h3 class="entry-title">Install plugins on localhost:</h3>
In some cases, you are not able to update/upgrade your WordPress plugins to a newer version without providing your FTP connection information. This is a common issue whereby the WordPress system can’t write to your <code>/wp-content</code> folder directly.

To solve this issue you need to define the FTP details. So WordPress will remember it. Alternatively, you may also provide WordPress with write access to your <code>/wp-content</code> folder by accessing the FTP root file and changing the folder file permission (CHMOD) to 775 rather than the default 755 and 644.

There is, however, an easier way to deal with this; by defining constant, <code>FS_METHOD</code> in your <code>wp-config.php</code> file. This bypasses WordPress’s recurring prompts and allows auto-updates of your files to happen. And it takes only 1 line of code to do this.
<pre class="lang:default decode:true" title="Unable to install plugins on localhost">/* Unable to install plugins on localhost */
define('FS_METHOD','direct');</pre>
<h3>Disable Post Revisions:</h3>
Defaults WordPress <tt>WP_POST_REVISIONS</tt> to <i>true</i> (enable post revisions). If you want to disable the feature, use this setting:
<pre class="lang:default decode:true" title="Disable Post Revisions">/* Disable Post Revisions. */
define( 'WP_POST_REVISIONS', false );</pre>
or
<pre class="lang:default decode:true" title="Disable Post Revisions">/* Disable Post Revisions. */
define( 'WP_POST_REVISIONS', 3 );</pre>
<h3>Media Trash:</h3>
This constant controls the number of days before WordPress permanently deletes posts, pages, attachments, and comments, from the trash bin. The default is 30 days:
<pre class="lang:default decode:true" title="Media Trash">/* Media Trash. */
define( 'MEDIA_TRASH', true );
/* Trash Days. */
define( 'EMPTY_TRASH_DAYS', '7' );</pre>
<h3>WordPress debug mode for developers:</h3>
<pre class="lang:default decode:true" title="WordPress debug mode for developers">/* WordPress debug mode for developers. */
define( 'WP_DEBUG',         false );
define( 'WP_DEBUG_LOG',     true );
define( 'WP_DEBUG_DISPLAY', false );
define( 'SCRIPT_DEBUG',     true );
define( 'SAVEQUERIES',      false );
</pre>
<h3><span id="Save_queries_for_analysis" class="mw-headline">Save queries for analysis:</span></h3>
If "SAVEQUERIES" is <strong>true</strong> your website performance is getting slow, better we can turn off this if you are not debugging or troubleshooting.
<pre class="lang:default decode:true" title="Save queries for analysis">define( 'SAVEQUERIES', true );</pre>
Then in the footer of your theme put this:
<pre class="lang:default decode:true">&lt;?php
if ( current_user_can( 'administrator' ) ) {
    global $wpdb;
    echo "&lt;pre&gt;";
    print_r( $wpdb-&gt;queries );
    echo "&lt;/pre&gt;";
}
?&gt;</pre>
<h3>PHP Memory:</h3>
<pre class="lang:default decode:true" title="PHP Memory">/* PHP Memory */
define( 'WP_MEMORY_LIMIT', '128' );
define( 'WP_MAX_MEMORY_LIMIT', '256' );</pre>
<h3>Compression:</h3>
<pre class="lang:default decode:true" title="Compression">/* Compression */
define( 'COMPRESS_CSS',        true );
define( 'COMPRESS_SCRIPTS',    true );
define( 'CONCATENATE_SCRIPTS', true );
define( 'ENFORCE_GZIP',        true );</pre>
<h3>Updates:</h3>
<pre class="lang:default decode:true" title="Updates">/* Updates */
define( 'WP_AUTO_UPDATE_CORE', true );
define( 'DISALLOW_FILE_MODS', true );
define( 'DISALLOW_FILE_EDIT', true );</pre>
<h3><span id="Automatic_Database_Optimizing" class="mw-headline">Automatic Database Optimizing:</span></h3>
The script can be found at <tt>{$your_site}/wp-admin/maint/repair.php</tt>
<pre class="lang:default decode:true" title="Automatic Database Optimizing">/* Automatic Database Optimizing */
define( 'WP_ALLOW_REPAIR', true );
define( 'DO_NOT_UPGRADE_GLOBAL_TABLES', true );</pre>
<h3><span id="Block_External_URL_Requests" class="mw-headline">Block External URL Requests</span></h3>
Block external URL requests by defining WP_HTTP_BLOCK_EXTERNAL as true and this will only allow localhost and your blog to make requests. The constant WP_ACCESSIBLE_HOSTS will allow additional hosts to go through for requests. The format of the WP_ACCESSIBLE_HOSTS constant is a comma separated list of hostnames to allow, wildcard domains are supported.
<pre class="lang:default decode:true" title="Blok External URL Requests">/* Blok External URL Requests */
define( 'WP_HTTP_BLOCK_EXTERNAL', true );
define( 'WP_ACCESSIBLE_HOSTS', 'api.wordpress.org,techpulsetoday.com' );</pre>
<h3><span id="Cleanup_Image_Edits" class="mw-headline">Cleanup-Image Edits:</span></h3>
By default, WordPress creates a new set of images every time you edit an image and when you restore the original, it leaves all the edits on the server. Defining IMAGE_EDIT_OVERWRITE as true changes this behavior. Only one set of image edits are ever created and when you restore the original, the edits are removed from the server.
<pre class="lang:default decode:true" title="Cleanup-Image Edits">/* Cleanup-Image Edits */
define( 'IMAGE_EDIT_OVERWRITE', true );</pre>
<h3><span id="Override_of_default_file_permissions" class="mw-headline">Override of default file permissions:</span></h3>
<pre class="lang:default decode:true" title="Override of default file permissions">/* Override of default file permissions */
define( 'FS_CHMOD_DIR', ( 0755 &amp; ~ umask() ) );
define( 'FS_CHMOD_FILE', ( 0644 &amp; ~ umask() ) );</pre>
<h3><span id="View_All_Defined_Constants" class="mw-headline">View All Defined Constants:</span></h3>
it returns an array of all the currently defined constants with their values.
<pre class="lang:default decode:true " title="View All Defined Constants">print_r( @get_defined_constants() );</pre>