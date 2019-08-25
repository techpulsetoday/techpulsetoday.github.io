---
layout: post
title:  "How to avoid sudo password prompt"
author: vijayan
categories: [ Linux ]
tags: [Linux Tips, Password, sudo, Tips and Tricks]
image: assets/images/2016/12/using-sudo-with-a-password-in-one-line.png
description: "We can avoid prompts for passwords by giving the sudo password as a standard input to the sudo command. echo 'password' | sudo -S command"
---
Here is the simple tip which gets rid of this password prompt, follow these tweaks if you have a situation where you don’t want to enter the root password while running the **sudo** command as a non-root user. We can avoid prompts for passwords by giving the **sudo** password as a standard input to the **sudo** command, as shown below:

```bash
echo <password> | sudo -S <command>
```

For Example:

```bash
echo 'password' | sudo -S cp wp-config.php bkp-wp-config.php
```

Here, the echo `‘password’` will send a password to the output, where `|` will send this as standard input to the sudo command run with the `-S` parameter.

`-S` is -stdin, which reads, the password from the standard input.

for more information about sudo, type man sudo

```bash
man sudo
```
