---
layout: post
title:  "How to Delete all the Files in a Directory Recursively"
author: vijayan
categories: [ Linux ]
tags: [ Delete, Find, Linux Tips, Tips and Tricks]
image: assets/images/2016/12/linux-delete-all-files-in-a-directory-recursively.png
description: "Delete all the files in a directory recursively with a specific extension (e.g.txt) from current directory and all subfolders,use the find cmd"
---
Linux deletes all the files in a directory recursively. How do I delete folder recursively under Linux operating systems using a bash command line options? You need to use the rm command to remove files or directories (also known as folders) recursively. The <strong>rmdir</strong> command removes only empty directories.

Recursively delete all files with a specific extension (e.g. .txt) from current directory and all subfolders, use the find command.

I'm able to use the following to remove the target directory and recursively all of its subdirectories and contents. Before deleting, make a sure the list of files, first run this below command.

<h2>Create dummy files</h2>

For testing this command, Just create dummy text files by using this below command.

<pre class="lang:default decode:true ">touch bspl{0001..0100}.txt</pre>

<img class="aligncenter wp-image-220 size-full" src="/assets/images/2016/12/delete-1.png" width="600" height="75" />

<h2>Precaution test</h2>

Before deleting, make a sure the list of files, first run this below command.

<pre class="lang:default decode:true">find . -name "bspl000*.txt" -type f</pre>

<img class="aligncenter wp-image-219 size-full" src="/assets/images/2016/12/delete-2.png" width="600" height="133" />

<h2>Delete all files from directory and all subfolders</h2>

If you want to delete a file with start from <strong>bspl1000*.txt </strong>or delete all files with a specific extension (<strong>e.g. <code>.txt</code></strong>) from current directory and all subfolders, use the <code>find</code> command, you can safely delete.

Make sure that <a href="https://www.techpulsetoday.com/"><strong><code>-delete</code></strong></a> is the last argument in your command.

<pre class="lang:default decode:true ">find . -name "bspl000*.txt" -type f -delete</pre>

<img class="aligncenter wp-image-218 size-full" src="/assets/images/2016/12/delete-3.png" alt="Delete all files from directory and all subfolders" width="600" height="76" />

<h2>Delete Folder Recursively</h2>

You can also tell find to just find directories named <strong>.svn</strong> by adding a <strong><em>-type d</em></strong> check:

<pre class="lang:default decode:true  ">find . -name ".svn" -type d -exec rm -r "{}" \;</pre>