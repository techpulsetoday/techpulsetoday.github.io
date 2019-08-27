---
layout: post
title:  "Remove all spaces  or unwanted characters from the file name"
author: vijayan
categories: [ Linux ]
tags: [Linux Tips, Tips and Tricks]
image: assets/images/2017/01/Remove-all-spaces-or-unwanted-characters-from-the-file-name.png
description: "Remove all spaces or unwanted characters from the file name, and it becomes annoying to access these files from the terminal."
---
Often, there are multiple spaces or unwanted characters in the file name, and it becomes annoying to access these files from the terminal. We can remove spaces from file name manually, but it becomes a tedious task when there are a large number of files involved. Fortunately, GNU/Linux has a <a href="https://techpulsetoday.com/search-replace-string-file-name/">command</a> that solves this problem. This is the "<strong>rename</strong>" command, Which renames the filenames supplied according to the rule specified as the first argument. Let us understand this with a simple example.

Shown below are the files whose names contain spaces:
<pre class="lang:default decode:true">vijayan@vijayan-VPCCA35FA:~/Downloads/techpulsetoday$ ls -lash
total 5.3M
4.0K drwxrwxr-x 2 vijayan vijayan 4.0K Jan 10 23:46 .
4.0K drwxr-xr-x 8 vijayan vijayan 4.0K Jan 10 23:42 ..
648K -rw-rw-r-- 1 vijayan vijayan 643K Dec 31 22:53 Aval Azhakai.mp3
564K -rw-rw-r-- 1 vijayan vijayan 557K Dec 31 22:54 Azhagiya Theeye.mp3
480K -rw-rw-r-- 1 vijayan vijayan 475K Dec 31 22:54 Azhagiya Theeye Whistle.mp3
680K -rw-rw-r-- 1 vijayan vijayan 675K Dec 31 22:55 Iru Vizhi unathu.mp3
624K -rw-rw-r-- 1 vijayan vijayan 617K Dec 31 22:55 Nenjai Poopoal.mp3
584K -rw-rw-r-- 1 vijayan vijayan 580K Dec 31 22:55 Pooppol Pooppol.mp3
540K -rw-rw-r-- 1 vijayan vijayan 536K Dec 31 22:55 Vaseegara Theme.mp3
620K -rw-rw-r-- 1 vijayan vijayan 613K Dec 31 22:55 Venmathi love fail.mp3
596K -rw-rw-r-- 1 vijayan vijayan 590K Dec 31 22:56 Verenna Verenna Male.mp3
</pre>
<img class="aligncenter size-full wp-image-314" src="/assets/images/2017/01/Remove-all-spaces-or-unwanted-characters-from-the-file-name-1.png" alt="Remove all spaces or unwanted characters from the file name" width="644" height="200" />

Now, let us remove these spaces using the "<strong>rename</strong>" command as follows:
<pre class="lang:default decode:true">vijayan@vijayan-VPCCA35FA:~/Downloads/techpulsetoday$ rename 's/ //g' *.mp3</pre>
It's that simple, We are done. Now, Let us verify the results:
<pre class="lang:default decode:true">vijayan@vijayan-VPCCA35FA:~/Downloads/techpulsetoday$ rename 's/ //g' *.mp3
vijayan@vijayan-VPCCA35FA:~/Downloads/techpulsetoday$ ls -lash
total 5.3M
4.0K drwxrwxr-x 2 vijayan vijayan 4.0K Jan 10 23:45 .
4.0K drwxr-xr-x 8 vijayan vijayan 4.0K Jan 10 23:42 ..
648K -rw-rw-r-- 1 vijayan vijayan 643K Dec 31 22:53 AvalAzhakai.mp3
564K -rw-rw-r-- 1 vijayan vijayan 557K Dec 31 22:54 AzhagiyaTheeye.mp3
480K -rw-rw-r-- 1 vijayan vijayan 475K Dec 31 22:54 AzhagiyaTheeyeWhistle.mp3
680K -rw-rw-r-- 1 vijayan vijayan 675K Dec 31 22:55 IruVizhiunathu.mp3
624K -rw-rw-r-- 1 vijayan vijayan 617K Dec 31 22:55 NenjaiPoopoal.mp3
584K -rw-rw-r-- 1 vijayan vijayan 580K Dec 31 22:55 PooppolPooppol.mp3
540K -rw-rw-r-- 1 vijayan vijayan 536K Dec 31 22:55 VaseegaraTheme.mp3
620K -rw-rw-r-- 1 vijayan vijayan 613K Dec 31 22:55 Venmathilovefail.mp3
596K -rw-rw-r-- 1 vijayan vijayan 590K Dec 31 22:56 VerennaVerennaMale.mp3
vijayan@vijayan-VPCCA35FA:~/Downloads/techpulsetoday$</pre>
<img class="aligncenter size-full wp-image-315" src="/assets/images/2017/01/Remove-all-spaces-or-unwanted-characters-from-the-file-name-3.png" alt="Remove all spaces or unwanted characters from the file name" width="619" height="232" />

Indeed, it has worked. In the above example, the "<strong>rename</strong>" command specified the rule to replace the space with nothing, i.e., it just removes the space. In the above command, the "<strong>g</strong>" option implies "global", i.e., "<em>remove all spaces</em>". If you want to replace spaces with any other character  <strong><em>-</em></strong> for instance, an underscore <strong>_</strong> then use the following rule with the "<strong>rename</strong>" command:
<pre class="lang:default decode:true ">vijayan@vijayan-VPCCA35FA:~/Downloads/techpulsetoday$ rename 's/ /-/g' *.mp3</pre>
It's that simple, We are done. Now,
<pre class="lang:default decode:true">vijayan@vijayan-VPCCA35FA:~/Downloads/techpulsetoday$ rename 's/ /-/g' *.mp3
vijayan@vijayan-VPCCA35FA:~/Downloads/techpulsetoday$ ls -lash
total 5.3M
4.0K drwxrwxr-x 2 vijayan vijayan 4.0K Jan 10 23:46 .
4.0K drwxr-xr-x 8 vijayan vijayan 4.0K Jan 10 23:42 ..
648K -rw-rw-r-- 1 vijayan vijayan 643K Dec 31 22:53 Aval-Azhakai.mp3
564K -rw-rw-r-- 1 vijayan vijayan 557K Dec 31 22:54 Azhagiya-Theeye.mp3
480K -rw-rw-r-- 1 vijayan vijayan 475K Dec 31 22:54 Azhagiya-Theeye-Whistle.mp3
680K -rw-rw-r-- 1 vijayan vijayan 675K Dec 31 22:55 Iru-Vizhi-unathu.mp3
624K -rw-rw-r-- 1 vijayan vijayan 617K Dec 31 22:55 Nenjai-Poopoal.mp3
584K -rw-rw-r-- 1 vijayan vijayan 580K Dec 31 22:55 Pooppol-Pooppol.mp3
540K -rw-rw-r-- 1 vijayan vijayan 536K Dec 31 22:55 Vaseegara-Theme.mp3
620K -rw-rw-r-- 1 vijayan vijayan 613K Dec 31 22:55 Venmathi-love-fail.mp3
596K -rw-rw-r-- 1 vijayan vijayan 590K Dec 31 22:56 Verenna-Verenna-Male.mp3
</pre>
<img class="aligncenter size-full wp-image-316" src="/assets/images/2017/01/Remove-all-spaces-or-unwanted-characters-from-the-file-name-4.png" alt="Remove all spaces or unwanted characters from the file name" width="638" height="211" />