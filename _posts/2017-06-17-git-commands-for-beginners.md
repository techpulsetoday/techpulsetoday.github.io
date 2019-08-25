---
layout: post
title:  "Git commands for beginners"
author: vijayan
categories: [ Tech Tips ]
tags: [ git, Linux Commands ]
image: assets/images/2017/06/Git-commands-for-beginners.png
description: "With multiple people working on a software project, co-ordination sometimes becomes difficult. Git commands for beginners"
toc: true
---
With multiple people working on a software project, co-ordination sometimes becomes difficult. Git is a version control system (VCS) for tracing changes in computer files and coordinating work on these files. Given below are a few commands that can be commonly used while using this VCS.

### Clone remote repo

```bash
git clone [repository-url]
```

### Refresh repo for the latest from remote repo

```bash
git pull
```

### List all branches

```bash
git branch -a
```

### Switch branch

```bash
git checkout [branch-name]
```

### Check the status of the current repository

```bash
git status
```

### Add new files

```bash
git add filename
```

### Browse past commit information

```bash
git log
```

Browse past commit information by using the one line option:

```bash
git log --online
```

### Check-in changes

```bash
git commit -m "Message to commit this file or directory" [directory-or-filename]
```

### Compare file with past revision

```bash
git diff cf39cd1 filename
```

### Reset current branch head (HEAD) to the specified state

```bash
git reset <paths>
```
