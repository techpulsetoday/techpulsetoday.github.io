---
layout: post
title:  "How To Remove Shortcut Virus From Pendrives And Memory Cards"
author: vijayan
categories: [ Tech Tips ]
tags: [ Tips and Tricks, Windows ]
image: assets/images/2016/12/command.png
description: "Insert pen drives and memory card in USB port for the data transfer,then the files in your pen drive and memory cards turn into shortcut virus."
---
So many people are facing the same problem of the Shortcut Virus in their pen drive.  Sometimes when we insert pen drives and memory card in a USB port for the data transfer, then the files in your pen drive and memory cards turns into shortcut virus. This  is the most common problem for all. We see this virus in the systems which have anti-virus installed. When your PC, pen drive and memory cards got affected by any malware, then it will change all your original files into folders. So many people will face this problem. We can easily remove shortcut virus from [Pendrive](/), just follow the bellow steps.

Click on “Start” –>Run –> type cmd and click on OK.

Here I assume your pen drive letter as G:

Enter this command.

```sh
attrib -h -r -s /s /d g:\*.*
```

![Command](/assets/images/2016/11/command-600x304-1.png)

You can copy the above command –> Right-click in the Command Prompt and paste it.

Note : Don’t forget to replace the letter 'g' with your pen drive letter.

Now press “Enter”.

That’s it!!!!

Now check for your files and folder in Pen Drive.
