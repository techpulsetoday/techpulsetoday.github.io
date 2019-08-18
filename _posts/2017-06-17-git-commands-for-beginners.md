---
layout: post
title:  "Git commands for beginners"
author: vijayan
categories: [ Tech Tips ]
tags: [ git, Linux Commands ]
image: assets/images/2017/06/Git-commands-for-beginners.png
description: "With multiple people working on a software project, co-ordination sometimes becomes difficult. Git commands for beginners"
---
With multiple people working on a software project, co-ordination sometimes becomes difficult. Git is a version control system (<a href="https://www.techpulsetoday.com/">VCS</a>) for tracing changes in computer files and coordinating&nbsp;work on these files. Given below are a few commands that can be commonly used while using this VCS.
<h2>Clone remote repo:</h2>
<pre class="lang:default decode:true">git clone [repository-url]</pre>
<h2>Refresh repo for the latest from remote repo:</h2>
<pre class="lang:default decode:true ">git pull</pre>
<h2>List all branches:</h2>
<pre class="lang:default decode:true ">git branch -a</pre>
<h2>Switch branch:</h2>
<pre class="lang:default decode:true ">git checkout [branch-name]</pre>
<h2>Check the status of the current repository:</h2>
<pre class="lang:default decode:true ">git status</pre>
<h2>Add new files:</h2>
<pre class="lang:default decode:true ">git add filename</pre>
<h2>Browse past commit information:</h2>
<pre class="lang:default decode:true ">git log</pre>
Browse past commit information by using the one line option:
<pre class="lang:default decode:true">git log --online</pre>
<h2>Check-in changes:</h2>
<pre class="lang:default decode:true ">git commit -m "Message to commit this file or directory" [directory-or-filename]</pre>
<h2>Compare file with past revision:</h2>
<pre class="lang:default decode:true ">git diff cf39cd1 filename</pre>
<h2>Reset current branch head (HEAD) to the specified state:</h2>
<pre class="lang:default decode:true">git reset &lt;paths&gt;</pre>