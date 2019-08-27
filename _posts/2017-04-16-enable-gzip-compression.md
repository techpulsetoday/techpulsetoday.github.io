---
layout: post
title:  "How to enable Gzip compression"
author: vijayan
categories: [ Linux ]
tags: [ Apache, gzip compression, Nginx]
image: assets/images/2017/04/gzip-compression.jpg
description: "GZip compression all files like HTML, JS and CSS files while serving the request to the browser it doesn't make any difference what the file type is or the encoding."
toc: true
---
GZip Compression (compress) all files like HTML, JS and CSS files while serving the request to the browser; it doesn’t make any difference what the file type is or the encoding. As a size of the file is reduced it is served to the user in a faster manner. Not all the browser support compression but now all the modern browser support. It is highly recommended, but only one part is that it increases the CPU usages of the server which may be concern sometime. Using Gzip with client side caching will help in increasing the performance.

### How to enable Gzip compression

Here are the most common ways to enable gzip compression including **.htaccess**, **[Apache](/create-apache-virtual-host-ubuntu/)**, and **Nginx** web servers.

### For Apache

1. mod_deflate (recommended way)
2. mod_gzip

You will need to add the following lines to your **`.htaccess`** file:

#### mod_deflate Method

```bash
<IfModule mod_deflate.c>
  # Compress HTML, CSS, JavaScript, Text, XML and fonts
  AddOutputFilterByType DEFLATE application/javascript
  AddOutputFilterByType DEFLATE application/rss+xml
  AddOutputFilterByType DEFLATE application/vnd.ms-fontobject
  AddOutputFilterByType DEFLATE application/x-font
  AddOutputFilterByType DEFLATE application/x-font-opentype
  AddOutputFilterByType DEFLATE application/x-font-otf
  AddOutputFilterByType DEFLATE application/x-font-truetype
  AddOutputFilterByType DEFLATE application/x-font-ttf
  AddOutputFilterByType DEFLATE application/x-javascript
  AddOutputFilterByType DEFLATE application/xhtml+xml
  AddOutputFilterByType DEFLATE application/xml
  AddOutputFilterByType DEFLATE font/opentype
  AddOutputFilterByType DEFLATE font/otf
  AddOutputFilterByType DEFLATE font/ttf
  AddOutputFilterByType DEFLATE image/svg+xml
  AddOutputFilterByType DEFLATE image/x-icon
  AddOutputFilterByType DEFLATE text/css
  AddOutputFilterByType DEFLATE text/html
  AddOutputFilterByType DEFLATE text/javascript
  AddOutputFilterByType DEFLATE text/plain
  AddOutputFilterByType DEFLATE text/xml

  # Remove browser bugs (only needed for really old browsers)
  BrowserMatch ^Mozilla/4 gzip-only-text/html
  BrowserMatch ^Mozilla/4\.0[678] no-gzip
  BrowserMatch \bMSIE !no-gzip !gzip-only-text/html
  Header append Vary User-Agent
</IfModule>
```

#### mod_gzip Method

Make sure **mod_gzip** module should be enabled.

```bash
<ifModule mod_gzip.c>
mod_gzip_on Yes
mod_gzip_dechunk Yes
mod_gzip_item_include file \.(html?|txt|css|js|php|pl)$
mod_gzip_item_include mime ^application/x-javascript.*
mod_gzip_item_include mime ^text/.*
mod_gzip_item_exclude rspheader ^Content-Encoding:.*gzip.*
mod_gzip_item_exclude mime ^image/.*
mod_gzip_item_include handler ^cgi-script$
</ifModule>
```

### For Nginx

Create a file at **/etc/nginx/conf.d/gzip.conf** with the following content:

```bash
# Gzip Compression

  # Enable Gzip compressed.
  gzip on;

  # Enable compression both for HTTP/1.0 and HTTP/1.1.
  gzip_http_version  1.1;

  # Compression level (1-9).
  # 5 is a perfect compromise between size and cpu usage, offering about
  # 75% reduction for most ascii files (almost identical to level 9).
  gzip_comp_level    5;

  # Don't compress anything that's already small and unlikely to shrink much
  # if at all (the default is 20 bytes, which is bad as that usually leads to
  # larger files after gzipping).
  gzip_min_length    256;

  # Compress data even for clients that are connecting to us via proxies,
  # identified by the "Via" header (required for CloudFront).
  gzip_proxied       any;

  # Tell proxies to cache both the gzipped and regular version of a resource
  # whenever the client's Accept-Encoding capabilities header varies;
  # Avoids the issue where a non-gzip capable client (which is extremely rare
  # today) would display gibberish if their proxy gave them the gzipped version.
  gzip_vary          on;

  # Compress all output labeled with one of the following MIME-types.
  gzip_types
    application/atom+xml
    application/javascript
    application/json
    application/rss+xml
    application/vnd.ms-fontobject
    application/x-font-ttf
    application/x-web-app-manifest+json
    application/xhtml+xml
    application/xml
    font/opentype
    image/svg+xml
    image/x-icon
    text/css
    text/plain
    text/x-component;
  # text/html is always compressed by HttpGzipModule
  ```

#### Restart Nginx

You can use the Forge Nginx restart dropdown, but since you’re SSH’ed in you can also just run `sudo service nginx restart`.

### To test if gzip compression is enabled, run

```bash
curl -H "Accept-Encoding: gzip" -I https://techpulsetoday.com/
```

You should see **content-encoding: gzip**
