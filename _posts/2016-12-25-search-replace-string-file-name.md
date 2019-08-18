---
layout: post
title:  "How to search for and replace a string in the file name"
author: vijayan
categories: [ Linux ]
tags: [Linux Tips, Tips and Tricks]
image: assets/images/2016/12/search-for-and-replace-a-string.png
description: "You may sometimes want to rename a file in a directory by substituting certain string in the name.Search for and replace a string in the file."
---
As a developer, you may sometimes want to rename a file in a directory by substituting certain string in the name. The following one line tip in the Linux shell will help you to achieve this.
<pre class="lang:default decode:true">for file in $LIST; do newname=`echo $file|sed s/oldname/newname/g`; echo "change $file to $newname";mv $file $newname; done;</pre>
Here, '<strong>oldname</strong>' is the search string and '<strong>newname</strong>' is the replacement string.

The <em><strong>for loop </strong></em>will iterate and file the '<strong>file</strong>' variable with every instance of the files founds. The '<strong>sed</strong>' command will replace the found string with a replacement string, and pass it as the second parameter for the '<strong>mv</strong>' <a href="https://www.techpulsetoday.com/">command</a>.

Here is an example of how to rename all files that have the strings '<em><strong>oldname</strong></em>' in their file names, which need to be replaced with '<em><strong>newname</strong></em>'.
<h2>Create dummy a file</h2>
<pre class="lang:default decode:true">touch oldname.txt oldname.c oldname-test.c test-oldname.c</pre>
<h2>Search for and replace a string</h2>
<pre class="lang:default decode:true ">export LIST=`ls`
for file in $LIST; do newname=`echo $file|sed s/oldname/newname/g`; echo "change $file to $newname";mv $file $newname; done;</pre>
<h2>Search-Replace Examples</h2>
<pre class="lang:default decode:true">vijayan@vijayan-Lenovo-E40-80:~/Downloads/techpulsetoday$ touch oldname.txt oldname.c oldname-test.c test-oldname.c
vijayan@vijayan-Lenovo-E40-80:~/Downloads/techpulsetoday$ ls
oldname.c  oldname-test.c  oldname.txt  test-oldname.c
vijayan@vijayan-Lenovo-E40-80:~/Downloads/techpulsetoday$ export LIST=`ls`
vijayan@vijayan-Lenovo-E40-80:~/Downloads/techpulsetoday$ for file in $LIST; do newname=`echo $file|sed s/oldname/newname/g`; echo "change $file to $newname";mv $file $newname; done;
change oldname.c to newname.c
change oldname-test.c to newname-test.c
change oldname.txt to newname.txt
change test-oldname.c to test-newname.c
vijayan@vijayan-Lenovo-E40-80:~/Downloads/techpulsetoday$ ls
newname.c  newname-test.c  newname.txt  test-newname.c
vijayan@vijayan-Lenovo-E40-80:~/Downloads/techpulsetoday$ ls -lash
total 8.0K
4.0K drwxrwxr-x  2 vijayan vijayan 4.0K Dec 25 20:48 .
4.0K drwxr-xr-x 19 vijayan vijayan 4.0K Dec 25 20:47 ..
   0 -rw-rw-r--  1 vijayan vijayan    0 Dec 25 20:48 newname.c
   0 -rw-rw-r--  1 vijayan vijayan    0 Dec 25 20:48 newname-test.c
   0 -rw-rw-r--  1 vijayan vijayan    0 Dec 25 20:48 newname.txt
   0 -rw-rw-r--  1 vijayan vijayan    0 Dec 25 20:48 test-newname.c
vijayan@vijayan-Lenovo-E40-80:~/Downloads/techpulsetoday$</pre>
&nbsp;

&nbsp;

&nbsp;