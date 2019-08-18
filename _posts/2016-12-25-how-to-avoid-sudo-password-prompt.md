---
layout: post
title:  "How to avoid sudo password prompt"
author: vijayan
categories: [ Linux ]
tags: [Linux Tips, Password, sudo, Tips and Tricks]
image: assets/images/2016/12/using-sudo-with-a-password-in-one-line.png
description: "We can avoid prompts for passwords by giving the sudo password as a standard input to the sudo command. echo 'password' | sudo -S command"
---
Here is the simple tip which gets rid of this password prompt, follow these tweaks if you have a situation where you don’t want to enter the root password while running the sudo command as a non-root user. We can avoid prompts for passwords by giving the <em><strong>sudo </strong></em>password as a standard input to the <em><strong>sudo</strong></em> command, as shown below:
<pre class="lang:default decode:true">echo &lt;password&gt; | sudo -S &lt;command&gt;</pre>
For Example:
<pre class="lang:default decode:true ">echo 'password' | sudo -S cp wp-config.php bkp-wp-config.php</pre>
Here, the echo <strong>'<a href="https://www.techpulsetoday.com/">password</a>'</strong> will send a password to the output, where | will send this as standard input to the sudo command run with the <strong>-S</strong> parameter.

<strong>-S</strong> is -stdin, which reads, the password from the standard input.

for more information about sudo, type <em><strong>man sudo</strong></em>
<pre class="lang:default decode:true  ">man sudo</pre>