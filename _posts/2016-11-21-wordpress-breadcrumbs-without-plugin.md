---
layout: post
title:  "WordPress Breadcrumbs without Plugin"
author: vijayan
categories: [ WordPress ]
tags: [ Breadcrumbs ]
image: assets/images/2016/12/wordpress-breadcrumbs-code.png
description: "Breadcrumbs are the important part of our website, in WordPress. By adding this custom code in functions.php.Use this function to display it."
---
<h2>WordPress Breadcrumbs Code:</h2>
<p>Breadcrumbs are the important part of our website, in WordPress, there are several plugins are available for this. By adding this to functions.php To display the menu, just use this function to display it wherever you want.</p>

{% gist c7f8fa1a5f170f4ecbb049b63d0cd140 breadcrumbs-code-without-plugin.php %}

<p>After adding the code into functions.php add the below code to where you want to use this function.</p>

{% gist c7f8fa1a5f170f4ecbb049b63d0cd140 calling-function.php %}
