---
layout: post
title:  "How to Delete all the Files in a Directory Recursively"
author: vijayan
categories: [ Linux ]
tags: [ Delete, Find, Linux Tips, Tips and Tricks]
image: assets/images/2016/12/linux-delete-all-files-in-a-directory-recursively.png
description: "Delete all the files in a directory recursively with a specific extension (e.g.txt) from current directory and all subfolders,use the find cmd"
---
Linux deletes all the files in a directory recursively. How do I delete folder recursively under Linux operating systems using a bash command line options? You need to use the rm command to remove files or directories (also known as folders) recursively. The `rmdir` command removes only empty directories.

Recursively delete all files with a specific extension (e.g. .txt) from current directory and all subfolders, use the find command.

I'm able to use the following to remove the target directory and recursively all of its subdirectories and contents. Before deleting, make a sure the list of files, first run this below command.

### Create dummy files

For testing this command, Just create dummy text files by using this below command.

```bash
touch bspl{0001..0100}.txt
```

![Delete-1](/assets/images/2016/12/delete-1.png "Delete")

### Precaution test

Before deleting, make a sure the list of files, first run this below command.

```sh
find . -name "bspl000*.txt" -type f
```

![Delete-2](/assets/images/2016/12/delete-2.png "Delete")

### Delete all files from directory and all subfolders

If you want to delete a file with start from `bspl1000*.txt` or delete all files with a specific extension (e.g. `.txt`) from current directory and all subfolders, use the `find` command, you can safely delete.

Make sure that [-delete](/ "TechPulseToday") is the last argument in your command.

```bash
find . -name "bspl000*.txt" -type f -delete
```

![Delete all files from directory and all subfolders](/assets/images/2016/12/delete-3.png "Delete all files from directory and all subfolders")

### Delete Folder Recursively

You can also tell find to just find directories named `.svn` by adding a `-type d` check:

```bash
find . -name ".svn" -type d -exec rm -r "{}" \;
```
