---
layout: post
title:  "How to Login WordPress with Email only no Username?"
author: vijayan
categories: [ WordPress ]
tags: [ Security, WordPress, WordPress Login with Email Only, WP Function ]
image: assets/images/2017/01/WordPress-Login-with-Email-Only.png
description: "How to Login WordPress with Email Only. Using email address to login to your WordPress account is the best solution to secure."
---
How to Login WordPress with Email Only. Now WordPress allows users to login with their username and Email, which is not recommended in all cases. So as an alternative, using the email address to login to your WordPress account is the best solution to secure your WordPress Website.

Open your themes `functions.php` file and add this code in it.

### Remove default authentication function

```php
/* ------------------------------------------------------------------------- *
 * Remove WordPress default authentication function
/* ------------------------------------------------------------------------- */
remove_filter('authenticate', 'wp_authenticate_username_password', 20);
```

### Add custom authentication function

```php
/* ------------------------------------------------------------------------- *
 * Add custom authentication function
/* ------------------------------------------------------------------------- */
add_filter('authenticate', function($user, $email, $password){

    //Check for empty fields
    if(empty($email) || empty ($password)){
        //create new error object and add errors to it.
        $error = new WP_Error();

        if(empty($email)){ //No email
            $error->add('empty_username', __('<strong>ERROR</strong>: Email field is empty.'));
        }
        else if(!filter_var($email, FILTER_VALIDATE_EMAIL)){ //Invalid Email
            $error->add('invalid_username', __('<strong>ERROR</strong>: Email is invalid.'));
        }

        if(empty($password)){ //No password
            $error->add('empty_password', __('<strong>ERROR</strong>: Password field is empty.'));
        }

        return $error;
    }

    //Check if user exists in WordPress database
    $user = get_user_by('email', $email);

    //bad email
    if(!$user){
        $error = new WP_Error();
        $error->add('invalid', __('<strong>ERROR</strong>: Either the email or password you entered is invalid.'));
        return $error;
    }
    else{ //check password
        if(!wp_check_password($password, $user->user_pass, $user->ID)){ //bad password
            $error = new WP_Error();
            $error->add('invalid', __('<strong>ERROR</strong>: Either the email or password you entered is invalid.'));
            return $error;
        }else{
            return $user; //passed
        }
    }
}, 20, 3);
```

### Change text "Username" in wp-login.php to "Email"

We can use [gettext](https://codex.wordpress.org/Plugin_API/Filter_Reference/gettext){: target="_blank"} filter to change text “Username” to “Email” without editing core files.

```php
/* ------------------------------------------------------------------------- *
 * Change text "Username" in wp-login.php to "Email"
/* ------------------------------------------------------------------------- */
add_filter('gettext', function($text){
    if(in_array($GLOBALS['pagenow'], array('wp-login.php'))){
        if('Username' == $text){
            return 'Email';
        }
    }
    return $text;
}, 20);

```

[Source](https://wordpress.stackexchange.com/questions/51678/how-to-login-with-email-only-no-username){: target="_blank"}
