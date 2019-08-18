---
layout: post
title:  "Flickering and Screen distortion with new Hardware on elementary OS"
author: vijayan
categories: [ Linux ]
tags: [ Elementary OS, Tips and Tricks]
image: assets/images/2016/12/elementaryos.png
description: "Flickering/Blinking with your elementary OS, and If you have an Intel chipset you can try this, your problem will be solved."
---
<h2>Flickering/Blinking</h2>

Flickering/Blinking with your elementary OS, and If you have an Intel chipset you can try this, your problem will be solved.

<h2>Get information about your graphics card</h2>

<h3>Step 1</h3>

Open the Applications launcher and open System Settings, When the window appears, scroll down until you see the About icon under the System category. Click it and some information about your operating system and a computer will appear. Under hardware, there is a line starting with Graphics. Next to it is the information about your graphics card.

<img class="aligncenter wp-image-221 size-full" src="/assets/images/2016/12/elementaryos-1-519x365-1.png" width="519" height="365" />

<h3>Step 2</h3>

Using terminal to get information on Graphic card, Just type this command in terminal

<pre class="lang:default decode:true ">lspci | grep VGA</pre>

<h3>Step 3</h3>

More detail Information

<pre class="lang:default decode:true ">sudo lshw -C video</pre>

<img class="aligncenter size-full wp-image-222" src="/assets/images/2016/12/elementaryos-2-1-600x324-1.png" alt="" width="600" height="324" />

If you have an Intel chipset you can try this, your problem will be solved.

<pre class="lang:default decode:true ">sudo apt-get install mesa-utils

sudo mkdir /etc/X11/xorg.conf.d/

echo -e 'Section "Device"\n Identifier "Intel Graphics"\n Driver "Intel"\n Option "AccelMethod" "sna"\n Option "TearFree" "true"\nEndSection' | sudo tee /etc/X11/xorg.conf.d/20-intel.conf

sudo reboot</pre>