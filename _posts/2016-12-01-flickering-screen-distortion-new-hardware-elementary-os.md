---
layout: post
title:  "Flickering and Screen distortion with new Hardware on elementary OS"
author: vijayan
categories: [ Linux ]
tags: [ Elementary OS, Tips and Tricks]
image: assets/images/2016/12/elementaryos.png
description: "Flickering/Blinking with your elementary OS, and If you have an Intel chipset you can try this, your problem will be solved."
---
Flickering/Blinking with your elementary OS, and If you have an Intel chipset you can try this, your problem will be solved.

## Get information about your graphics card

### Step 1

Open the Applications launcher and open System Settings, When the window appears, scroll down until you see the About icon under the System category. Click it and some information about your operating system and a computer will appear. Under hardware, there is a line starting with Graphics. Next to it is the information about your graphics card.

![elementary OS](/assets/images/2016/12/elementaryos-1-519x365-1.png "elementary OS")

### Step 2

Using terminal to get information on Graphic card, Just type this command in terminal

```bash
lspci | grep VGA
```

### Step 3

More detail Information

```bash
sudo lshw -C video
```

![More detail Information](/assets/images/2016/12/elementaryos-2-1-600x324-1.png "More detail Information")

If you have an Intel chipset you can try this, your problem will be solved.

```bash
sudo apt-get install mesa-utils
sudo mkdir /etc/X11/xorg.conf.d/
echo -e 'Section "Device"\n Identifier "Intel Graphics"\n Driver "Intel"\n Option "AccelMethod" "sna"\n Option "TearFree" "true"\nEndSection' | sudo tee /etc/X11/xorg.conf.d/20-intel.conf
sudo reboot
```
