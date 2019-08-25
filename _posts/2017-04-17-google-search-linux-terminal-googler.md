---
layout: post
title:  "Google Search from Linux Terminal (Googler)"
author: vijayan
categories: [ Linux, Tech Tips ]
tags: [ googler, Linux Tips ]
image: assets/images/2017/04/googler.png
description: "You can now Google search through your Linux terminal, i.e., by using Googler. Here is the process of using it on Ubuntu."
---
You can now Google search through your Linux terminal, i.e., by using **Googler**. Here is the process of using it on Ubuntu.

To install it in Ubuntu, first make sure you have **Python** version 3.3 or later, by using the following command:

```bash
python3 --version
```

![python3-version-checking](/assets/images/2017/04/python3-version-checking.png "python3-version-checking")

If the version of Python is not correct, upgrade it. Googler requires Python 3.3+ to run.

Thought Googler is not available through the package repository on Ubuntu, we can easily install it from the GitHub repository. All we have to do is run the following set of commands:

```sh
cd /tmp
git clone https://github.com/jarun/googler/
cd googler
sudo make install
cd  auto-completion/bash/
sudo cp googler-completion.bash /etc/bash_completion.d/
sudo googler -u
```

![googler-installation](/assets/images/2017/04/googler-installation.png "python3-version-checking")

And that’s it. Googler is installed along with the command auto-completion feature.

After installing it, just run the command `‘googler’` and start searching on Google.

Reference: [google-cli](https://github.com/jarun/googler){: target="_blank"}
