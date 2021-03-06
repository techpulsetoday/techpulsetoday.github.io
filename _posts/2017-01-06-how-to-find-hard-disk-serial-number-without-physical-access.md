---
layout: post
title:  "How to Find Hard Disk Serial Number without Physical Access to it"
author: vijayan
categories: [ Linux ]
tags: [Linux Tips, Tips and Tricks]
image: assets/images/2017/01/how-to-find-hard-disk-serial-number-without-physical-access.png
description: "How to find hard disk serial number in Linux when physical access to the disk is not possible. You need to run 'hdparm -I /dev/sda'"
---
There's a very small chance that the laptop's manufacturer recorded the hard disk's serial number as correlated with the laptop serial number while it was being assembled, and that their customer service department could tell you if you asked them. In some cases you can run a software program that can retrieve and report the serial number of the disk without physically getting access to the drive. However, the most surefire way is to directly look at the product label on the drive itself. How to find hard disk serial number in Linux when physical access to the disk is not possible. You need to run the following command in the terminal to get these details:

```bash
sudo hdparm -I /dev/sda
```

To get only the serial number, you can run the following command:

```bash
sudo hdparm -I /dev/sda | grep Serial
```

![find-hard-disk-serial-number-without-physical-access](/assets/images/2017/01/find-hard-disk-serial-number-without-physical-access.png "find-hard-disk-serial-number-without-physical-access")
