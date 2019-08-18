---
layout: post
title:  "Remove WordPress Logo From Admin Bar"
author: vijayan
categories: [ WordPress ]
tags: [ WordPress, WordPress Logo, WP Function ]
image: assets/images/2016/12/wordpress-logo.png
description: "Add this code to your functions.php file to remove the WordPress Logo on admin bar. It will remove WP Logo when your current theme is active."
---
<h2><span id="Remove_the_WordPress_Logo_from_the_Toolbar" class="mw-headline">Remove the WordPress Logo from the Toolbar:</span></h2>
Customize the admin bar and add or remove menu items as we require. Add this code to your functions.php file to remove the <a href="https://www.techpulsetoday.com/">WordPress</a> Logo on admin bar. Using this method will only remove the WordPress Logo when your current theme is active.
<pre class="lang:default decode:true" title="Remove WordPress Logo From Admin Bar">/* Remove WordPress Logo From Admin Bar */
add_action( 'admin_bar_menu', 'wordpress_logo_admin_bar_remove', 999 );

function wordpress_logo_admin_bar_remove( $wp_admin_bar ) {
	$wp_admin_bar-&gt;remove_node( 'wp-logo' );
}</pre>
To remove menu items you just need to add the following function to your functions.php file. Remove or comment out lines for menu items that you want to want to keep. Be careful by using this below wp functions.
<pre class="lang:default decode:true ">/* Remove menu items from wordpress admin bar */
function wcs_admin_bar_remove_menu_items() {
    global $wp_admin_bar;
    $wp_admin_bar-&gt;remove_menu( 'wp-logo' );          // Remove the wordpress logo
    $wp_admin_bar-&gt;remove_menu( 'about' );            // Remove the about link
    $wp_admin_bar-&gt;remove_menu( 'wporg' );            // Remove the wordpress.org link
    $wp_admin_bar-&gt;remove_menu( 'documentation' );    // Remove the documentation link
    $wp_admin_bar-&gt;remove_menu( 'support-forums' );   // Remove the support forums link
    $wp_admin_bar-&gt;remove_menu( 'feedback' );         // Remove the feedback link
    $wp_admin_bar-&gt;remove_menu( 'site-name' );        // Remove the site name link
    $wp_admin_bar-&gt;remove_menu( 'view-site' );        // Remove the view site link
    $wp_admin_bar-&gt;remove_menu( 'updates' );          // Remove the updates link
    $wp_admin_bar-&gt;remove_menu( 'comments' );         // Remove the comments link
    $wp_admin_bar-&gt;remove_menu( 'new-content' );      // Remove the content link
    $wp_admin_bar-&gt;remove_menu( 'my-account' );       // Remove the user details tab
}
add_action( 'wp_before_admin_bar_render', 'wcs_admin_bar_remove_menu_items' );</pre>
&nbsp;