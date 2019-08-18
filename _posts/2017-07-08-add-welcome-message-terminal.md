---
layout: post
title:  "Add a welcome message to your terminal"
author: vijayan
categories: [ Linux, Tech Tips ]
tags: [Linux Tips, Tips and Tricks]
image: assets/images/2017/07/add-welcome-message-to-your-terminal.png
description: "This tip will show you how you can easily add a welcome message to your terminal. This message will be displayed at the start, whenever you open your terminal."
---
This tip will show you how you can easily add a welcome message to your terminal. This message will be displayed at the start, whenever you open your terminal.

Here are the steps to follow:

Step 1:
You need to install figlet. So open the terminal and type the following command:

<strong>sudo apt-get install figlet</strong>

Then press Enter.

Step 2:
Open <strong><em>.bashrc</em></strong> in Vim editor and get into insert mode.

<strong>vim ~/.bashrc</strong>

Step 3:
Enter the following command in <em><strong>.bashrc</strong></em>:

<strong>figletx -c your-message</strong>

Save and exit.

Step 4:
Now, when you open your terminal, you can see your welcome message.

To make your message more interesting, try using ASCII art. I recommend this website to generate ASCII art – <a href="http://ascii.mastervb.net">ascii.mastervb.net</a>