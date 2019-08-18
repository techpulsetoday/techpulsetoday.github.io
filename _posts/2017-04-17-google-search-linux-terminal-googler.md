---
layout: post
title:  "Google Search from Linux Terminal (Googler)"
author: vijayan
categories: [ Linux, Tech Tips ]
tags: [ googler, Linux Tips ]
image: assets/images/2017/04/googler.png
description: "You can now Google search through your Linux terminal, i.e., by using Googler. Here is the process of using it on Ubuntu."
---
You can now Google search through your Linux terminal, i.e., by using <strong>Googler</strong>.&nbsp;Here is the process of using it on Ubuntu.

To install it in Ubuntu, first make sure you have <strong>Python</strong> version 3.3 or later, by using the following command:

<pre class="lang:default decode:true " title="Check python3 Version">python3 --version</pre>

<img class="aligncenter size-full wp-image-412" src="/assets/images/2017/04/python3-version-checking.png" alt="python3-version-checking" width="612" height="109">If the version of Python is not correct, upgrade it. Googler requires Python 3.3+ to run.

Thought Googler is not available through the package repository on Ubuntu, we can easily install it from the GitHub repository. All we have to do is run the following set of commands:

<pre class="lang:default decode:true " title="Googler Instalation">$ cd /tmp
$ git clone https://github.com/jarun/googler/
$ cd googler
$ sudo make install
$ cd  auto-completion/bash/
$ sudo cp googler-completion.bash /etc/bash_completion.d/
$ sudo googler -u</pre>

<img class="aligncenter size-full wp-image-413" src="/assets/images/2017/04/googler-installation.png" alt="googler-installation" width="937" height="413">And that's it. Googler is installed along with the command <a href="/how-to-install-wp-cli-on-linux/" rel="noopener noreferrer"><strong>auto-completion</strong></a> feature.

After installing it, just run the command 'googler' and start searching on Google.

Reference:&nbsp;<a href="https://github.com/jarun/googler" target="_blank" rel="noopener noreferrer">google-cli</a>