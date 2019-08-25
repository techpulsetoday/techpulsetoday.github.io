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

**Step 1:**
You need to install figlet. So open the terminal and type the following command:

```bash
sudo apt-get install figlet
```

Then press Enter.

**Step 2:**
Open `.bashrc` in Vim editor and get into insert mode.

```bash
vim ~/.bashrc
```

**Step 3:**
Enter the following command in `.bashrc`:

```bash
figletx -c your-message
```

Save and exit.

**Step 4:**
Now, when you open your terminal, you can see your welcome message.

To make your message more interesting, try using ASCII art. I recommend this website to generate ASCII art – [ascii.mastervb.net](http://ascii.mastervb.net){:target="_blank"}
