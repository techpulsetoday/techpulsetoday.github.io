---
layout: post
title:  "How to check the number of protocol connections made in a server"
author: vijayan
categories: [ Linux ]
tags: [Linux Tips, Server, Tips and Tricks]
image: assets/images/2016/12/number-of-protocol-connections-made-in-a-server.png
description: "Protocol connections,netstat -an | grep :80. We know port 80 is used by the HTTP server and port 3306 is used by the MySQL server, by default."
---
Here is a simple tip to check the number of protocol connections made by HTTP or MySQL.
We know port 80 is used by the HTTP server and port 3306 is used by the MySQL server, by default. So here is the command to check the number of <a href="https://www.techpulsetoday.com/">connections</a>:
<pre class="lang:default decode:true ">netstat -an | grep :80 | wc -l</pre>
The above command is for the HTTP server. Similarly, type 3306 instead of 80 to know the connection made for the MySQL server.
To know the IP addresses that have made requests to port 80 of your server, run the following command:
<pre class="lang:default decode:true ">netstat -an | grep :80</pre>
&nbsp;