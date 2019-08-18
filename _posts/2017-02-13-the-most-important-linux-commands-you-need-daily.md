---
layout: post
title:  "The most important Linux commands you need daily"
author: vijayan
categories: [ Linux ]
tags: [ Find, Linux Commands, Linux Tips, sudo, Tips and Tricks]
image: assets/images/2017/02/linux-commands.png
description: "Use this guide to most important Linux commands, utilities, and tools for beginners, enterprise administrators, and managers"
---
Use this guide to most important Linux commands, Utilities, and tools for beginners, enterprise administrators, and managers.

<h2>Directory Operations:</h2>

<table>
<tbody>
<tr>
<th>Command</th>
<th>Description</th>
</tr>
<tr>
<td>pwd</td>
<td>Show current directory</td>
</tr>
<tr>
<td>cd dir</td>
<td>Change to directory dir</td>
</tr>
<tr>
<td>mkdir dir</td>
<td>Create a new directory dir</td>
</tr>
<tr>
<td>rmdir dir</td>
<td>Delete directory dir</td>
</tr>
<tr>
<td>ls dir</td>
<td>List Contents directory dir</td>
</tr>
</tbody>
</table>

<strong>Example:</strong>

<pre class="lang:default decode:true" title="Directory Operations">vijayan@vijayan-VPCCA35FA:~$ pwd
/home/vijayan
vijayan@vijayan-VPCCA35FA:~$ cd Downloads/
vijayan@vijayan-VPCCA35FA:~/Downloads$ mkdir techpulsetoday
vijayan@vijayan-VPCCA35FA:~/Downloads$ ls techpulsetoday
vijayan@vijayan-VPCCA35FA:~/Downloads$ rmdir techpulsetoday/</pre>

<h2>Special Directories:</h2>

<table>
<tbody>
<tr>
<th>Command</th>
<th>Description</th>
</tr>
<tr>
<td>.</td>
<td>Current Directory</td>
</tr>
<tr>
<td>..</td>
<td>Up a Directory</td>
</tr>
<tr>
<td>~</td>
<td>Home Directory</td>
</tr>
<tr>
<td>/</td>
<td>Root Directory</td>
</tr>
<tr>
<td>-</td>
<td>Previous Directory</td>
</tr>
</tbody>
</table>

<strong>Example:</strong>

<pre class="lang:default decode:true" title="Special Directories">vijayan@vijayan-VPCCA35FA:~$ pwd
/home/vijayan
vijayan@vijayan-VPCCA35FA:~$ cd .
vijayan@vijayan-VPCCA35FA:~$ pwd
/home/vijayan
vijayan@vijayan-VPCCA35FA:~$ cd ..
vijayan@vijayan-VPCCA35FA:/home$ pwd
/home
vijayan@vijayan-VPCCA35FA:/home$ cd ~
vijayan@vijayan-VPCCA35FA:~$ pwd
/home/vijayan
vijayan@vijayan-VPCCA35FA:~$ cd /
vijayan@vijayan-VPCCA35FA:/$ pwd
/
vijayan@vijayan-VPCCA35FA:/$ cd -
/home/vijayan
vijayan@vijayan-VPCCA35FA:~$</pre>

<h2>ls Options:</h2>

<strong>Syntax:</strong>

<pre class="lang:default decode:true">ls [options] [file|dir]</pre>

<table>
<tbody>
<tr>
<th>Command</th>
<th>Description</th>
</tr>
<tr>
<td>-a</td>
<td>All inc. hidden file</td>
</tr>
<tr>
<td>-l</td>
<td>Long Format</td>
</tr>
<tr>
<td>-i</td>
<td>List file's inode index number</td>
</tr>
<tr>
<td>-t</td>
<td>Sort by time &amp; date</td>
</tr>
<tr>
<td>-d</td>
<td>List directories  with ' */' [eg1. <strong>ls -d */</strong> ][eg2. <strong>ls -d $PWD/*</strong> ]</td>
</tr>
<tr>
<td>-s</td>
<td>List file size</td>
</tr>
<tr>
<td>-S</td>
<td>Sort by time</td>
</tr>
<tr>
<td>-r</td>
<td>Reverse order</td>
</tr>
<tr>
<td>-R</td>
<td>Recursive</td>
</tr>
<tr>
<td>-X</td>
<td>Sort by extension name</td>
</tr>
</tbody>
</table>

<strong>Example:</strong>

<pre class="lang:default decode:true" title="ls options">vijayan@vijayan-VPCCA35FA:~/Music/ringtone$ ls -lash
total 5.3M
4.0K drwxrwxr-x 2 vijayan vijayan 4.0K Jan  3 01:51 .
4.0K drwxr-xr-x 3 vijayan vijayan 4.0K Dec 31 22:53 ..
648K -rw-rw-r-- 1 vijayan vijayan 643K Dec 31 22:53 Aval Azhakai.mp3
564K -rw-rw-r-- 1 vijayan vijayan 557K Dec 31 22:54 Azhagiya Theeye.mp3
480K -rw-rw-r-- 1 vijayan vijayan 475K Dec 31 22:54 Azhagiya Theeye Whistle.mp3
680K -rw-rw-r-- 1 vijayan vijayan 675K Dec 31 22:55 Iru Vizhi unathu.mp3
624K -rw-rw-r-- 1 vijayan vijayan 617K Dec 31 22:55 Nenjai Poopoal.mp3
584K -rw-rw-r-- 1 vijayan vijayan 580K Dec 31 22:55 Pooppol Pooppol.mp3
540K -rw-rw-r-- 1 vijayan vijayan 536K Dec 31 22:55 Vaseegara Theme.mp3
620K -rw-rw-r-- 1 vijayan vijayan 613K Dec 31 22:55 Venmathi love fail.mp3
596K -rw-rw-r-- 1 vijayan vijayan 590K Dec 31 22:56 Verenna Verenna Male.mp3</pre>

<h2>File Operations:</h2>

<table>
<tbody>
<tr>
<th>Command</th>
<th>Descriptions</th>
</tr>
<tr>
<td>touch file</td>
<td>Create a new file</td>
</tr>
<tr>
<td>cp file1 file2</td>
<td>Copy file1 to file2</td>
</tr>
<tr>
<td>mv file1 file2</td>
<td>Move file1 to file2</td>
</tr>
<tr>
<td>rm file</td>
<td>Delete a file</td>
</tr>
<tr>
<td>cat file</td>
<td>Display content of a file</td>
</tr>
<tr>
<td>cat file1 file2</td>
<td>Cancatenate files</td>
</tr>
<tr>
<td>less file</td>
<td>Display file (paginated), q to quit</td>
</tr>
<tr>
<td>head file</td>
<td>Show first 10 lines</td>
</tr>
<tr>
<td>tail file</td>
<td>Show last 10 lines [-n N →N lines; -f → Continuos update]</td>
</tr>
</tbody>
</table>

<h2>File Searching:</h2>

<table>
<tbody>
<tr>
<th>Command</th>
<th>Descriptions</th>
</tr>
<tr>
<td>grep <em>pattern file</em></td>
<td>Searching for a line with <em>a pattern</em> in a file</td>
</tr>
<tr>
<td>grep -v</td>
<td>Inverted search</td>
</tr>
<tr>
<td>grep -r</td>
<td>Recursive search</td>
</tr>
<tr>
<td>grep -e <em><span style="background-color: #f5f6f5;">pattern</span></em> -e <em>pattern</em></td>
<td>Multiple patterns</td>
</tr>
<tr>
<td>locate <em>file</em></td>
<td>Quick search for <em>a file</em></td>
</tr>
<tr>
<td>which <em>cmd</em></td>
<td>Find locations of binary</td>
</tr>
<tr>
<td>find <em>dir</em> -name <em>pattern</em></td>
<td>Find a file with <em>a pattern</em> in <em>dir</em></td>
</tr>
</tbody>
</table>

<strong>Example:</strong>

<pre class="lang:default decode:true" title="File Searching">grep -rnw '/var/www/html/' -e "techpulsetoday"</pre>

<h2>Standard IO Streams:</h2>

<table>
<tbody>
<tr>
<th>Command</th>
<th>Descriptions</th>
</tr>
<tr>
<td>stdin</td>
<td>Input typed on the command line</td>
</tr>
<tr>
<td>stdout</td>
<td>Output on the screen</td>
</tr>
<tr>
<td>stderr</td>
<td>Errors output on the screen</td>
</tr>
<tr>
<td>echo string</td>
<td>Write a <em>string</em> to stdout</td>
</tr>
</tbody>
</table>

<strong>Example:</strong>

<pre class="lang:default decode:true " title="Standard IO String">echo 'password' | sudo -S cp wp-config.php bkp-wp-config.php</pre>

<h2>Redirection:</h2>

<table>
<tbody>
<tr>
<th>Command</th>
<th>Descriptions</th>
</tr>
<tr>
<td>cmd &gt; file</td>
<td>Output of <em>cmd</em> to file</td>
</tr>
<tr>
<td>cmd &lt; file</td>
<td><em>file</em> used as input to cmd</td>
</tr>
<tr>
<td>cmd &gt;&gt; file</td>
<td>Append output to <em>file</em></td>
</tr>
<tr>
<td>cmd 2&gt; file</td>
<td>Write errors to <em>file</em></td>
</tr>
<tr>
<td>cmd &amp;&gt; file</td>
<td>Errors and stdout to <em>file</em></td>
</tr>
</tbody>
</table>

<h2>Pipe Multiple Commands</h2>

<table>
<tbody>
<tr>
<th>Command</th>
<th>Descriptions</th>
</tr>
<tr>
<td>cmd1 | cmd2</td>
<td>Stdout of cmd1 is used as input to cmd2</td>
</tr>
<tr>
<td>cmd1 | &amp;cmd2</td>
<td>Stderr of cmd1 is used as input to cmd2</td>
</tr>
<tr>
<td>cmdpart1 \ cmdpart2</td>
<td>Continue command on next line</td>
</tr>
<tr>
<td>cmd1; cmd2</td>
<td>Execute cmd1 then cmd2</td>
</tr>
</tbody>
</table>

<h2>Processes:</h2>

<table>
<tbody>
<tr>
<th>Command</th>
<th>Descriptions</th>
</tr>
<tr>
<td>ps</td>
<td>Show processes of user</td>
</tr>
<tr>
<td>ps -e</td>
<td>Show all processes</td>
</tr>
<tr>
<td>ps -fA</td>
<td>Show all processes in detail</td>
</tr>
<tr>
<td>top</td>
<td>Show all processes in real-time</td>
</tr>
<tr>
<td>cmd &amp;</td>
<td>Run command in the background</td>
</tr>
<tr>
<td>Ctrl-c</td>
<td>Stop (kill) currently active process</td>
</tr>
<tr>
<td>Ctrl-z</td>
<td>Suspend currently active process</td>
</tr>
<tr>
<td>bg</td>
<td>Place suspended process in a background</td>
</tr>
<tr>
<td>fg</td>
<td>Bring background process to foreground</td>
</tr>
<tr>
<td>kill <em>pid</em></td>
<td>Kill process with process id PID</td>
</tr>
<tr>
<td>Kill -9 <em>pid</em></td>
<td>Kill process PID (ungraceful)</td>
</tr>
</tbody>
</table>

<h2>Bash Shortcuts:</h2>

<table>
<tbody>
<tr>
<th>Command</th>
<th>Descriptions</th>
</tr>
<tr>
<td>Ctrl-k</td>
<td>Cut line of text</td>
</tr>
<tr>
<td>Ctrl-y</td>
<td>Past line of text</td>
</tr>
<tr>
<td>Ctrl-e</td>
<td>Go to end of line</td>
</tr>
<tr>
<td>Ctrl-a</td>
<td>Go to start of line</td>
</tr>
<tr>
<td>TAB</td>
<td>Autocomplete command/file</td>
</tr>
<tr>
<td>TAB-TAB</td>
<td>Show list of possible autocompletes</td>
</tr>
<tr>
<td>up arrow</td>
<td>Scroll previous commands</td>
</tr>
<tr>
<td>down arrow</td>
<td>Scroll previous commands</td>
</tr>
<tr>
<td>histrory</td>
<td>List recent commands</td>
</tr>
<tr>
<td>!!</td>
<td>Repeat the last command</td>
</tr>
<tr>
<td>!N</td>
<td>Execute command N from history</td>
</tr>
<tr>
<td>!abc:p</td>
<td>Print the last command starting with abc</td>
</tr>
<tr>
<td>!abc</td>
<td>Execute the last command starting with abc</td>
</tr>
</tbody>
</table>

<h2>Text file operation:</h2>

<table>
<tbody>
<tr>
<th>Command</th>
<th>Descriptions</th>
</tr>
<tr>
<td>wc</td>
<td>Line, word and character count</td>
</tr>
<tr>
<td>sort file</td>
<td>Sort file, line by line</td>
</tr>
<tr>
<td>uniq file</td>
<td>Display only unique lines of a file</td>
</tr>
<tr>
<td>sed ‘s/abc/def/g’ file</td>
<td><a href="https://www.techpulsetoday.com/search-replace-string-file-name/">Replace</a> all occurrence of abc with def, out to stdout</td>
</tr>
<tr>
<td>cut -d “ “ -f N file</td>
<td>Display field N of space delimited file</td>
</tr>
<tr>
<td>cut -d “,” -f M-N file</td>
<td>Display field M-N of a comma delimited file</td>
</tr>
</tbody>
</table>

<h2>Tar Command:</h2>

<table>
<tbody>
<tr>
<th>Command</th>
<th>Descriptions</th>
</tr>
<tr>
<td>-c</td>
<td>Creates a new .tar archive file.</td>
</tr>
<tr>
<td>-x</td>
<td>To untar or extract a tar file</td>
</tr>
<tr>
<td>-v</td>
<td>Verbosely show the .tar file progress.</td>
</tr>
<tr>
<td>-f</td>
<td>File name type of the archive file.</td>
</tr>
<tr>
<td>-z</td>
<td>compressed gzip archive file</td>
</tr>
<tr>
<td>-r</td>
<td>To add files or directories to existing tar archive file</td>
</tr>
<tr>
<td>-j</td>
<td>To create a highly compressed tar file</td>
</tr>
<tr>
<td>-C</td>
<td>untar in a different directory</td>
</tr>
<tr>
<td>-t</td>
<td>viewing content of archive file</td>
</tr>
<tr>
<td>-W</td>
<td>Verify an archive file</td>
</tr>
</tbody>
</table>

<strong>Example:</strong>

<h2>How to create a tar.gz file</h2>

To create a tar.gz archive from a given folder you can use the following command

<pre class="lang:default decode:true" title="To create a tar.gz archive from a given folder">tar -zcvf tar-archive-name.tar.gz source-folder-name</pre>

<h2>How to extract a tar.gz file</h2>

To extract a tar.gz compressed archive you can use the following command

<pre class="lang:default decode:true" title="To extract a tar.gz compressed archive">tar -zxvf tar-archive-name.tar.gz</pre>

<h2>How to extract specific file(s) from tar.gz</h2>

<pre class="lang:default decode:true" title="To extract specific file(s) from tar.gz">tar -zxvf &lt;tar filename&gt; &lt;file you want to extract&gt;</pre>

<h2>Proper file Permissions for WordPress</h2>

<pre class="lang:default decode:true">sudo chown www-data:www-data -R *
sudo find . -type d -exec chmod 755 {} \;
sudo find . -type f -exec chmod 644 {} \;
sudo chmod 444 wp-config.php
sudo chmod 444 .htaccess
</pre>

<h2>Three-digit permissions specified in octal</h2>

<pre class="lang:default decode:true">stat -c "%a %n" *</pre>

<img class="aligncenter size-full wp-image-437" src="/assets/images/2017/05/octal-three-digit-permissions.png" alt="octal-three-digit-permissions" width="593" height="285" />

<h2>How to find recently modified files</h2>

see all files that were modified during the last 2 days

<pre class="lang:default decode:true">find . -mtime -2 -ls</pre>

<h2>How can I monitor the progress of an import of a large .sql file?</h2>

If you're just importing from a dump file from the CLI on *nix, e.g.

<pre class="lang:default decode:true">mysql -uxxx -pxxx dbname &lt; /sqlfile.sql</pre>

then first install pipe viewer on your OS then try something like this:

<pre class="lang:default decode:true">pv sqlfile.sql | mysql -uxxx -pxxxx dbname
</pre>

<h2>How to convert ppk file from pem file?</h2>

Make sure puttygen installed on your computer. If it is not installed, type the below command,

<pre class="lang:default decode:true">sudo apt-get install putty-tools</pre>

<pre class="lang:default decode:true">puttygen keyfile.pem -O private -o avdev.ppk</pre>

<h2>How to download YouTube Playlist</h2>

The program '<strong>youtube-dl</strong>' is currently not installed. You can install it by typing:

<pre class="lang:default decode:true">sudo apt install youtube-dl</pre>

<pre class="lang:default decode:true">youtube-dl -o '%(playlist)s/%(playlist_index)s - %(title)s.%(ext)s' https://www.youtube.com/playlist?list=PLtaXuX0nEZk9MKY_ClWcPkGtOEGyLTyCO</pre>