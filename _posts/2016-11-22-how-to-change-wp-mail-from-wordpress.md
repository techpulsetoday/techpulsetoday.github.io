---
layout: post
title:  "How to Change wp_mail_from and wp_mail_from_name WordPress"
author: vijayan
categories: [ WordPress ]
tags: [ WordPress ]
image: assets/images/2016/12/wp-mail-from.png
description: "The wp_mail_from filter modifies the 'from email address' used in an email sent using the wp_mail function."
toc: true
---
The **`wp_mail_from`** (an email address) filter modifies the “from email address” used in an email sent using the wp_mail function. When used together with the **`wp_mail_from_name`** (the real name given to the email address) filter, it creates a from address like “TechPulseToday <info@techpulsetoday.com>”. The filter should return an email address. Just adding this below code to functions.php of your WordPress theme will change the from address in your WordPress theme or You don’t even need to mess with a file editor and FTP for this.  I would simply go to the Appearance > Editor menu in the WP Admin Panel, then find ‘functions.php’ in the list of theme files on the right.  Add these filters and you are in business. Two Important notes,

1. Make sure the email is from the same domain
2. As your website to avoid being marked as spam.

### wp_mail_from

```php
// wp_mail_from
add_filter('wp_mail_from', 'from_mail');

function from_mail($original_email_address) {
    return 'info@techpulsetoday.com';
}
```

### wp_mail_from_name

```php
// wp_mail_from_name
add_filter('wp_mail_from_name', 'from_mail_name');

function from_mail_name($original_email_address_name) {
    return 'TechPulseToday';
}
```
