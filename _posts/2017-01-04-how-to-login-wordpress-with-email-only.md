---
layout: post
title:  "How to Login WordPress with Email only no Username?"
author: vijayan
categories: [ WordPress ]
tags: [ Security, WordPress, WordPress Login with Email Only, WP Function ]
image: assets/images/2017/01/WordPress-Login-with-Email-Only.png
description: "How to Login WordPress with Email Only. Using email address to login to your WordPress account is the best solution to secure."
---
<h2>How to Login WordPress with Email Only</h2>
How to Login WordPress with Email Only. Now WordPress allows users to login with their username and Email, which is not recommended in all cases. So as an alternative, using the email address to login to your WordPress account is the best solution to secure your WordPress Website.

Open your themes <em>functions.php</em> file and add this code in it.
<h2>Remove default authentication function</h2>
<pre class="lang:default decode:true ">/* ------------------------------------------------------------------------- *
 * Remove WordPress default authentication function
/* ------------------------------------------------------------------------- */
remove_filter('authenticate', 'wp_authenticate_username_password', 20);</pre>
<h2>Add custom authentication function</h2>
<pre class="lang:default decode:true ">/* ------------------------------------------------------------------------- *
 * Add custom authentication function
/* ------------------------------------------------------------------------- */
add_filter('authenticate', function($user, $email, $password){

    //Check for empty fields
    if(empty($email) || empty ($password)){        
        //create new error object and add errors to it.
        $error = new WP_Error();

        if(empty($email)){ //No email
            $error-&gt;add('empty_username', __('&lt;strong&gt;ERROR&lt;/strong&gt;: Email field is empty.'));
        }
        else if(!filter_var($email, FILTER_VALIDATE_EMAIL)){ //Invalid Email
            $error-&gt;add('invalid_username', __('&lt;strong&gt;ERROR&lt;/strong&gt;: Email is invalid.'));
        }

        if(empty($password)){ //No password
            $error-&gt;add('empty_password', __('&lt;strong&gt;ERROR&lt;/strong&gt;: Password field is empty.'));
        }

        return $error;
    }

    //Check if user exists in WordPress database
    $user = get_user_by('email', $email);

    //bad email
    if(!$user){
        $error = new WP_Error();
        $error-&gt;add('invalid', __('&lt;strong&gt;ERROR&lt;/strong&gt;: Either the email or password you entered is invalid.'));
        return $error;
    }
    else{ //check password
        if(!wp_check_password($password, $user-&gt;user_pass, $user-&gt;ID)){ //bad password
            $error = new WP_Error();
            $error-&gt;add('invalid', __('&lt;strong&gt;ERROR&lt;/strong&gt;: Either the email or password you entered is invalid.'));
            return $error;
        }else{
            return $user; //passed
        }
    }
}, 20, 3);</pre>
<h2>Change text "Username" in wp-login.php to "Email"</h2>
We can use <a href="http://codex.wordpress.org/Plugin_API/Filter_Reference/gettext">gettext</a> filter to change text "Username" to "Email" without editing core files.
<pre class="lang:default decode:true ">/* ------------------------------------------------------------------------- *
 * Change text "Username" in wp-login.php to "Email"
/* ------------------------------------------------------------------------- */
add_filter('gettext', function($text){
    if(in_array($GLOBALS['pagenow'], array('wp-login.php'))){
        if('Username' == $text){
            return 'Email';
        }
    }
    return $text;
}, 20);</pre>
<a href="http://wordpress.stackexchange.com/questions/51678/how-to-login-with-email-only-no-username">Source</a>