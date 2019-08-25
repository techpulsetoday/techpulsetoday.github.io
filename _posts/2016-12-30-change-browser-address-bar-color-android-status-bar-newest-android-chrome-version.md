---
layout: post
title:  "How to Change Browser Address bar color and Android Status bar in newest Android Chrome version"
author: vijayan
categories: [ WordPress ]
tags: [ HTML, WordPress, Tips and Tricks]
image: assets/images/2016/12/change-browser-address-bar-color-1.png
description: "How to change browser address bar color and android status bar in newest android chrome version to match their WordPress theme."
---
Have you noticed that many popular websites like [Facebook](https://www.facebook.com/ "Facebook"){:target="_blank"}, [Desinema](http://desinema.com/ "Desinema"){:target="_blank"} use their own brand colors for the address bar in mobile browser. How to change the color of address bar in mobile browser to match their WordPress theme? In this article, we will show you how to change the color of address bar in mobile browser to match your WordPress site.

![Before](/assets/images/2016/12/change-browser-address-bar-color-before.png "Before") ![After](/assets/images/2016/12/change-browser-address-bar-color.png "After")

### Change browser address bar color

You need to place the below code inside `<head></head>` tags.

Most of the WordPress themes have a default option to add scripts in the header. In case if you don’t have such option in your theme, Go to Appearance > Editor and add the code in header.php

In blogger or static sites, you can directly add this into your XML/HTML template.

### Meta tag to be added

```html
<!-- Chrome, Firefox OS and Opera -->
<meta name="theme-color" content="#08426E">
<!-- Windows Phone -->
<meta name="msapplication-navbutton-color" content="#08426E">
<!-- iOS Safari -->
<meta name="apple-mobile-web-app-status-bar-style" content="#08426E">
```

If you are using [WordPress Child Theme](/useful-wordpress-functions/), just add this below code in functions.php file.

```php
<?php
/* ------------------------------------------------------------------------- *
 * Change the color of header bar and address bar in newest Android Chrome version
/* ------------------------------------------------------------------------- */
add_action('wp_head', 'chrome_header_bar_color_change');
function chrome_header_bar_color_change() { ?>
<!-- Chrome, Firefox OS and Opera -->
<meta name="theme-color" content="#08426E">
<!-- Windows Phone -->
<meta name="msapplication-navbutton-color" content="#08426E">
<!-- iOS Safari -->
<meta name="apple-mobile-web-app-status-bar-style" content="#08426E">
<?php } ?>
```

### Notes

* Please change your HEX code as the content value
* It won’t work in Incognito windows.
