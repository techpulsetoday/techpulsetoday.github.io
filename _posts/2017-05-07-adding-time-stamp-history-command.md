---
layout: post
title:  "Adding the time stamp to the History Command"
author: vijayan
categories: [ Linux ]
tags: [ Linux Commands, Linux Tips, time stamp, Tips and Tricks]
image: assets/images/2017/05/time-stamp-history-command.png
description: "The History command does not output the time stamp with the log of the most recently executed commands. Add HISTTIMEFORMAT='%d/%m/%y %T ' to ~/.bashrc file. Adding time stamp History Command."
---
The History command does not output the time stamp with the log of the most recently executed commands.
<h2>To Display Date and Time:</h2>
To do so, run the following&nbsp;command in the terminal:

Please note that there is a space before the last double-quotes.
<pre class="lang:default mark:1 decode:true">HISTTIMEFORMAT="%d/%m/%y %T "</pre>
If you want to permanently append this changes, add the following line to the <em><strong>~/.bashrc</strong></em> file:
<pre class="lang:default mark:1 decode:true ">export HISTTIMEFORMAT="%d/%m/%y %T "</pre>
OR

Run the command, it will be adding <em><strong>~/.bashrc</strong></em> file
<pre class="lang:default decode:true  ">echo 'export HISTTIMEFORMAT="%d/%m/%y %T "' &gt;&gt; ~/.bashrc</pre>
Then, from the terminal, run the following:
<pre class="lang:default mark:1 decode:true ">source ~/.bashrc</pre>
Now, to see history, type:
<pre class="lang:default decode:true ">history</pre>
<strong>Sample outputs:</strong>
<pre class="lang:default decode:true">533 07/05/17 13:40:07 cd /var/www/html/
534 07/05/17 13:40:07 ls
535 07/05/17 13:40:07 cd techpulsetoday.com/
536 07/05/17 13:40:07 wp plugin list
537 07/05/17 13:40:07 wp package list
538 07/05/17 13:40:07 wp cache flush
539 07/05/17 13:40:07 wp help package
540 07/05/17 13:40:07 wp package update
541 07/05/17 13:40:07 wp package list
542 07/05/17 13:40:07 wp size database
543 07/05/17 13:40:07 wp transient delete --all
544 07/05/17 13:40:07 wp revisions clean
545 07/05/17 13:40:07 wp size database
546 07/05/17 13:40:07 wp db optimize
547 07/05/17 13:40:07 wp db repair
548 07/05/17 13:40:07 ls
549 07/05/17 13:40:07 nano wp-config.php</pre>
<h2>To Display dd-MON-YY &amp; AM/PM &amp; Timezone:</h2>
<pre class="lang:default decode:true ">HISTTIMEFORMAT="%d/%m/%y %r %Z "</pre>
<strong>Sample Outputs:</strong>
<pre class="lang:default decode:true ">533 07/05/17 01:40:07 PM IST cd /var/www/html/
534 07/05/17 01:40:07 PM IST ls
535 07/05/17 01:40:07 PM IST cd techpulsetoday.com/
536 07/05/17 01:40:07 PM IST wp plugin list
537 07/05/17 01:40:07 PM IST wp package list
538 07/05/17 01:40:07 PM IST wp help package
539 07/05/17 01:40:07 PM IST wp package update
540 07/05/17 01:40:07 PM IST wp package list
541 07/05/17 01:40:07 PM IST wp size database
542 07/05/17 01:40:07 PM IST wp cache flush
543 07/05/17 01:40:07 PM IST wp size database
544 07/05/17 01:40:07 PM IST wp transient delete
545 07/05/17 01:40:07 PM IST wp transient delete --all
546 07/05/17 01:40:07 PM IST wp revisions clean
547 07/05/17 01:40:07 PM IST wp size database
548 07/05/17 01:40:07 PM IST wp db optimize</pre>
Here's an explanation of the commands and switches:
<table>
<tbody>
<tr>
<th>Commands</th>
<th>Explanation</th>
</tr>
<tr>
<td>history</td>
<td>GNU History Library</td>
</tr>
<tr>
<td>HISTTIMEFORMAT</td>
<td>Environmental Variable</td>
</tr>
<tr>
<td>%d</td>
<td>The day of the month as a decimal number (range 01 to 31)</td>
</tr>
<tr>
<td>%m</td>
<td>The month as a decimal number (range 01 to 12)</td>
</tr>
<tr>
<td>%y</td>
<td>The year as a decimal number without a century (range 00 to 99)</td>
</tr>
<tr>
<td>%T</td>
<td>The time in 24-hour notation (%H:%M:%S)</td>
</tr>
<tr>
<td>%r</td>
<td>The time in a.m. or p.m. notation. In the POSIX locale, this is equivalent to %I:%M:%S %p</td>
</tr>
<tr>
<td>%Z</td>
<td>The timezone name or abbreviation</td>
</tr>
<tr>
<td>source</td>
<td>In short, send the contents of the file to the shell</td>
</tr>
<tr>
<td>.bashrc</td>
<td>Is a shell script that BASH runs whenever it is started interactively</td>
</tr>
</tbody>
</table>
<h2>Reference:</h2>
For more info type the following commands:
<pre class="lang:default decode:true ">man bash
help history
man 3 strftime</pre>