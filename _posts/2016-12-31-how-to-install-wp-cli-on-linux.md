---
layout: post
title:  "How to Install WP-CLI on a linux"
author: vijayan
categories: [ Linux, WordPress ]
tags: [ Linux Tips, WordPress, WP-CLI ]
image: assets/images/2016/12/wp-cli.png
description: "How to Install WP-CLI is by downloading the Phar build, marking it executable, and placing it on your PATH. "
---
WP-CLI will be particularly useful if you are a WordPress developer, System Administrator or run a business built on WordPress. WP-CLI is an awesome command line tool for WordPress. It has a lot of commands that can help us installing plugins/themes, add posts, updating WordPress Core, taking backups, querying databases, import/export data quickly and easily. This command line tool will greatly help you do more in less time.

### Download WP-CLI

First Connect your server through SSH. wp-cli.org recommended to install WP-CLI is by downloading the Phar file. The latest version WP-CLI installation file is available [here](https://raw.github.com/wp-cli/builds/gh-pages/phar/wp-cli.phar). You can download by using `wget` or `curl`. For Example:

```bash
curl -O https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar
```

![wp-cli-1](/assets/images/2016/12/wp-cli-1.png "wp-cli-1")

### Check if it works

Enter the following command to check if it works or not.

```bash
php wp-cli.phar --info
```

![wp-cli-2](/assets/images/2016/12/wp-cli-2.png "wp-cli-2")

### Creating executable files

Enter the following command to make it executable.

```bash
chmod +x wp-cli.phar
```

![wp-cli-3](/assets/images/2016/12/wp-cli-3.png "wp-cli-3")

### Move WP-CLI.PHAR File

We can move `wp-cli.phar` file to `/usr/local/bin` and rename it to `wp`. This will help us use the `WP-CLI` commands by just typing `‘wp’` at the start of the commands. Type wp –info to check the status.

```bash
sudo mv wp-cli.phar /usr/local/bin/wp
```

![wp-cli-4](/assets/images/2016/12/wp-cli-4.png "wp-cli-4")

### WP-CLI Update

In future, you can update wp cli by entering the following command to update.

```bash
sudo wp cli update
```

![wp-cli-5](/assets/images/2016/12/wp-cli-5.png "wp-cli-5")

For more information about wp-cli installation [click here](https://wp-cli.org/#installing "wp-cli installing"){: target="_blank"}.

### wp-cli bash completion

The bash completion feature of WP-CLI allows you to see all the available commands on the fly.

### Download the bash script in your home directory

```bash
cd ~/
wget https://github.com/wp-cli/wp-cli/raw/master/utils/wp-completion.bash
```

### Edit the .bashrc file

Edit the file `.bashrc` so that it is loaded by the shell every time you log in. Open the file and add the following line in the editor:

```bash
source /home/$USER/wp-completion.bash
```

### Run the following command to reload the bash profile

```bash
source ~/.bashrc
```

That’s it. Bash completion is now enabled. To test it, type `wp theme` (include the trailing space) and press Tab twice. You will see the list of available commands with `wp theme` again on the prompt.
