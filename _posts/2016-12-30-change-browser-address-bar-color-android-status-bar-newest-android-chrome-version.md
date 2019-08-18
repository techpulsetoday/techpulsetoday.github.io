---
layout: post
title:  "How to Change Browser Address bar color and Android Status bar in newest Android Chrome version"
author: vijayan
categories: [ WordPress ]
tags: [ HTML, WordPress, Tips and Tricks]
image: assets/images/2016/12/change-browser-address-bar-color-1.png
description: "How to change browser address bar color and android status bar in newest android chrome version to match their WordPress theme."
---
Have you noticed that many popular websites like <a href="http://www.facebook.com/">Facebook</a>, <a href="http://desinema.com/">Desinema</a> use their own brand colors for the address bar in mobile browser. How to change the color of address bar in mobile browser to match their WordPress theme? In this article, we will show you how to change the color of address bar in mobile browser to match your WordPress site.

<img class="wp-image-241 size-large alignleft" src="/assets/images/2016/12/change-browser-address-bar-color-before.png" alt="change browser address bar color before" width="250" height="445" /><img class="wp-image-240 size-large alignnone" src="/assets/images/2016/12/change-browser-address-bar-color.png" alt="change browser address bar color" width="250" height="445" />
<h2>Change browser address bar color</h2>
You need to place the below code inside &lt;head&gt;&lt;/head&gt; tags.

Most of the WordPress themes have a default option to add scripts in the header. In case if you don’t have such option in your theme, Go to Appearance &gt; Editor and add the code in header.php

In blogger or static sites, you can directly add this into your XML/HTML template.
<h2>Meta tag to be added</h2>
<pre class="lang:default decode:true ">&lt;!-- Chrome, Firefox OS and Opera --&gt;
&lt;meta name="theme-color" content="#08426E"&gt;
&lt;!-- Windows Phone --&gt;
&lt;meta name="msapplication-navbutton-color" content="#08426E"&gt;
&lt;!-- iOS Safari --&gt;
&lt;meta name="apple-mobile-web-app-status-bar-style" content="#08426E"&gt;</pre>
If you are using <a href="https://www.techpulsetoday.com/useful-wordpress-functions/">WordPress Child Theme</a>, just add this below code in functions.php file.
<pre class="lang:default decode:true">&lt;?php
/* ------------------------------------------------------------------------- *
 * Change the color of header bar and address bar in newest Android Chrome version
/* ------------------------------------------------------------------------- */
add_action('wp_head', 'chrome_header_bar_color_change');
function chrome_header_bar_color_change() { ?&gt;
&lt;!-- Chrome, Firefox OS and Opera --&gt;
&lt;meta name="theme-color" content="#08426E"&gt;
&lt;!-- Windows Phone --&gt;
&lt;meta name="msapplication-navbutton-color" content="#08426E"&gt;
&lt;!-- iOS Safari --&gt;
&lt;meta name="apple-mobile-web-app-status-bar-style" content="#08426E"&gt;
&lt;?php } ?&gt;</pre>
<h2>Notes</h2>
<ul>
 	<li>Please change your HEX code as the content value</li>
 	<li>It won’t work in Incognito windows.</li>
</ul>
&nbsp;