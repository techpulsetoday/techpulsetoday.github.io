---
layout: post
title:  "How to make a folder Inaccessible and Undeletable"
author: vijayan
categories: [ Tech Tips ]
tags: [ Windows, Tips and Tricks ]
image: assets/images/2016/12/Undeletable.png
description: "You might want to argue that hiding you personal files and folders could solve the problem.Use Folder option in Windows explorer."
---
Most of the Peoples are not aware that it is possible to create Undeletable, Unrenamable folder in windows without any software. To Test, this concept just follows simple steps given below.

Try to make a new folder in some safe location on your local hard disk &amp; give it a name.

you won't be allowed to create a folder with con, aux, lpt1, lpt2, lpt3 up to lpt9 these names, Because they are reserved words in windows.

Open the <a href="https://www.techpulsetoday.com/how-to-remove-shortcut-virus-from-pendrives-and-memory-cards/">command prompt</a> in your system (Press Win key+R, type ‘cmd’ in the Run dialogue box and hit ‘Enter’).

Type the following syntax into the command prompt.
<pre class="lang:default decode:true ">cacls &lt;folder_name&gt; /e /c /d %username%</pre>
For instance, the command should be like this:
<pre class="lang:default decode:true ">cacls private /e /c /d %username%</pre>
It will make the folder ‘Private’ inaccessible as well as undeletable. If anybody tries to open or delete the folder, the following messages will be shown.

When you want to open that folder for your own need, type the following syntax in the command prompt and hit the ‘Enter’ key on your keyboard.
<pre class="lang:default decode:true ">cacls &lt;folder_name&gt; /e /c /g %username%:f</pre>
This will return the folder to its normal form. This trick works in Windows XP, Windows 7 and Windows vista as well. But, make sure that the file system is NTFS. Otherwise, this technique won’t work.