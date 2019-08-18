---
layout: post
title:  "How to Install WP-CLI on a linux"
author: vijayan
categories: [ Linux, WordPress ]
tags: [ Linux Tips, WordPress, WP-CLI ]
image: assets/images/2016/12/wp-cli.png
description: "How to Install WP-CLI is by downloading the Phar build, marking it executable, and placing it on your PATH. "
---
<h2 id="how-to-install-wp-cli">About WP-CLI</h2>
WP-CLI will be particularly useful if you are a WordPress developer, System Administrator or run a business built on WordPress. WP-CLI is an awesome command line tool for WordPress. It has a lot of commands that can help us installing plugins/themes, add posts, updating WordPress Core, taking backups, querying databases, import/export data quickly and easily. This command line tool will greatly help you do more in less time.
<h2>Download WP-CLI</h2>
First Connect your server through SSH. wp-cli.org recommended to install WP-CLI is by downloading the Phar file. The latest version WP-CLI installation file is available <a href="https://raw.github.com/wp-cli/builds/gh-pages/phar/wp-cli.phar">here</a>. You can download by using <em><strong>wget</strong></em> or <strong><em>curl</em></strong>. For Example:
<pre class="lang:default decode:true ">curl -O https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar</pre>
<img class="aligncenter size-full wp-image-268" src="/assets/images/2016/12/wp-cli-1.png" alt="wp-cli-1" width="941" height="187" />
<h2>Check if it works</h2>
Enter the following command to check if it works or not.
<pre class="lang:default decode:true ">php wp-cli.phar --info</pre>
<img class="aligncenter size-full wp-image-269" src="/assets/images/2016/12/wp-cli-2.png" alt="wp-cli-2" width="914" height="166" />
<h2>Creating executable files</h2>
Enter the following command to make it executable.
<pre class="lang:default decode:true ">chmod +x wp-cli.phar</pre>
<img class="aligncenter size-full wp-image-270" src="/assets/images/2016/12/wp-cli-3.png" alt="wp-cli-3" width="911" height="102" />
<h2>Move WP-CLI.PHAR File</h2>
We can move <strong>wp-</strong>cli<strong>.</strong>phar file to <strong><em>/</em>usr<em>/local/bin</em></strong> and rename it to <em><strong>wp</strong></em>. This will help us use the <strong>WP-CLI</strong> commands by just typing <em><strong>'wp'</strong></em> at the start of the commands. Type wp --info to check the status.
<pre class="lang:default decode:true ">sudo mv wp-cli.phar /usr/local/bin/wp</pre>
<img class="aligncenter size-full wp-image-271" src="/assets/images/2016/12/wp-cli-4.png" alt="wp-cli-4" width="942" height="218" />
<h2>WP-CLI Update</h2>
In future, you can update wp cli by entering the following command to update.
<pre class="lang:default decode:true">sudo wp cli update</pre>
<img class="size-full wp-image-272 aligncenter" src="/assets/images/2016/12/wp-cli-5.png" alt="wp-cli-5" width="458" height="56" />For more information about wp-cli installation <a href="https://wp-cli.org/docs/installing/">click here</a>.
<h2>wp-cli bash completion</h2>
The bash completion feature of WP-CLI allows you to see all the available commands on the fly.
<h3>Download the bash script in your home directory:</h3>
<pre class="lang:default decode:true " title="Download the bash script">cd ~/
wget https://github.com/wp-cli/wp-cli/raw/master/utils/wp-completion.bash</pre>
<h3>Edit the .bashrc file</h3>
Edit the file<code>.bashrc</code> so that it is loaded by the shell every time you log in. Open the file and add the following line in the editor:
<pre class="lang:default decode:true " title=".bashrc">source /home/$USER/wp-completion.bash</pre>
<h3>Run the following command to reload the bash profile:</h3>
<pre class="lang:default decode:true " title="Reload .bashrc">source ~/.bashrc</pre>
That’s it. Bash completion is now enabled. To test it, type <strong>wp theme<span style="font-family: monospace;"> </span></strong>(include the trailing space) and press <strong>Tab</strong> twice. You will see the list of available commands with <strong>wp theme</strong> again on the prompt.