---
layout: post
title:  "Ubuntu 18.04.3, relocation error, error code (127) after last updates"
author: vijayan
categories: [ Tech Tips ]
tags: [ Tips and Tricks ]
image: assets/images/2019/09/recovery-mode.png
description: "Ubuntu 18.04.3, relocation error, error code (127) after last updates."
featured: true
hidden: true
rating: 4.5
toc: true
---
After the last update, I received the following updates

> libidn2-0 libnss-myhostname libnss-systemd libpam-systemd libsystemd0 libudev1 systemd systemd-sysv udev

This update is causing multiple programs to fail with error messages such as:
**"symbol _idn2_punycode_decode version IDN2_0.0.0 not defined in file libidn2.so.0 with link time reference"**

```sh
/usr/lib/apt/methods/http: relocation error: /usr/lib/x86_64-linux-gnu/libgnutls.so.30: symbol _idn2_punycode_decode version IDN2_0.0.0 not defined in file libidn2.so.0 with link time reference
/usr/lib/apt/methods/http: relocation error: /usr/lib/x86_64-linux-gnu/libgnutls.so.30: symbol _idn2_punycode_decode version IDN2_0.0.0 not defined in file libidn2.so.0 with link time reference
/usr/lib/apt/methods/http: relocation error: /usr/lib/x86_64-linux-gnu/libgnutls.so.30: symbol _idn2_punycode_decode version IDN2_0.0.0 not defined in file libidn2.so.0 with link time reference
/usr/lib/apt/methods/http: relocation error: /usr/lib/x86_64-linux-gnu/libgnutls.so.30: symbol _idn2_punycode_decode version IDN2_0.0.0 not defined in file libidn2.so.0 with link time reference
/usr/lib/apt/methods/http: relocation error: /usr/lib/x86_64-linux-gnu/libgnutls.so.30: symbol _idn2_punycode_decode version IDN2_0.0.0 not defined in file libidn2.so.0 with link time reference
/usr/lib/apt/methods/http: relocation error: /usr/lib/x86_64-linux-gnu/libgnutls.so.30: symbol _idn2_punycode_decode version IDN2_0.0.0 not defined in file libidn2.so.0 with link time reference
/usr/lib/apt/methods/http: relocation error: /usr/lib/x86_64-linux-gnu/libgnutls.so.30: symbol _idn2_punycode_decode version IDN2_0.0.0 not defined in file libidn2.so.0 with link time reference
/usr/lib/apt/methods/http: relocation error: /usr/lib/x86_64-linux-gnu/libgnutls.so.30: symbol _idn2_punycode_decode version IDN2_0.0.0 not defined in file libidn2.so.0 with link time reference
E: Method http has died unexpectedly!
E: Sub-process http returned an error code (127)
E: Method /usr/lib/apt/methods/http did not start correctly
E: Method http has died unexpectedly!
E: Sub-process http returned an error code (127)
E: Method /usr/lib/apt/methods/http did not start correctly
E: Method http has died unexpectedly!
E: Sub-process http returned an error code (127)
E: Method /usr/lib/apt/methods/http did not start correctly
E: Method http has died unexpectedly!
E: Sub-process http returned an error code (127)
E: Method /usr/lib/apt/methods/http did not start correctly
E: Method http has died unexpectedly!
E: Sub-process http returned an error code (127)
E: Method /usr/lib/apt/methods/http did not start correctly
E: Method http has died unexpectedly!
E: Sub-process http returned an error code (127)
E: Method /usr/lib/apt/methods/http did not start correctly
E: Method http has died unexpectedly!
E: Sub-process http returned an error code (127)
E: Method /usr/lib/apt/methods/http did not start correctly
E: Method http has died unexpectedly!
E: Sub-process http returned an error code (127)
E: Method /usr/lib/apt/methods/http did not start correctly
```

> This appears to only affect those using PHP from launchpad.net/~ondrej

## Temporary solution

1. Download [this file](http://ftp.us.debian.org/debian/pool/main/libi/libidn2/libidn2-0_2.0.5-1_amd64.deb "libidn2-0_2.0.5-1_amd64.deb") to the machine.
2. sudo dpkg -i <path/to/.deb>
3. sudo apt-mark hold libidn2-0

## If the system still doesn't boot, follow the below steps

1. Download [this file](http://ftp.us.debian.org/debian/pool/main/libi/libidn2/libidn2-0_2.0.5-1_amd64.deb "libidn2-0_2.0.5-1_amd64.deb") to a flashdrive.
2. Boot in recovery mode
   1. After restart, press `Esc` or `Shift` button immediately.
   2. Select `Advanced Options for Ubuntu`. It's the second option on the GRUB boot splash screen.
   3. Select `Ubuntu, with Linux x.xx.x 32 generic (recovery mode)`. This boots Ubuntu in Recovery Mode.
   4. Select `root Drop to root shell prompt`.
3. Copy files from flashdrive in recovery mode.
   1. Use `fdisk -l` to see if your USB-Drive is identified.
   2. Remember the device (/dev/sdX) Mount the USB-Drive manually with mount /dev/sdX1 /mnt
   3. copy the downloaded files from the flashdrive into the machine. `cp -a /mnt/libidn2-0_2.0.5-1_amd64.deb /home/<your_user>/Downloads/`
4. sudo dpkg -i <path/to/.deb>
5. sudo apt-mark hold libidn2-0

## How to get a list of installed packages held back from upgrade?

```sh
apt-mark showhold
```

## Permanent solution

Apparently it has already been fixed. Try running `sudo apt update` and then `apt policy libidn2-0` to see if you get the fixed version `2.2.0-2+ubuntu18.04.1+deb.sury.org+1`. Only run `sudo apt upgrade` (or `full-upgrade` or `dist-upgrade`) if you get that new version.

Looks like this issue [https://github.com/oerdnj/deb.sury.org/issues/1247](https://github.com/oerdnj/deb.sury.org/issues/1247).
