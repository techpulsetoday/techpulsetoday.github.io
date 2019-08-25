---
layout: post
title:  "Adding the time stamp to the History Command"
author: vijayan
categories: [ Linux ]
tags: [ Linux Commands, Linux Tips, time stamp, Tips and Tricks]
image: assets/images/2017/05/time-stamp-history-command.png
description: "The History command does not output the time stamp with the log of the most recently executed commands. Add HISTTIMEFORMAT='%d/%m/%y %T ' to ~/.bashrc file. Adding time stamp History Command."
toc: true
---
The History command does not output the time stamp with the log of the most recently executed commands.

## To Display Date and Time

To do so, run the following command in the terminal:

Please note that there is a space before the last double-quotes.

```bash
HISTTIMEFORMAT="%d/%m/%y %T "
```

If you want to permanently append this changes, add the following line to the `~/.bashrc` file:

```bash
export HISTTIMEFORMAT="%d/%m/%y %T "
```

or

Run the command, it will be adding `~/.bashrc` file

```bash
echo 'export HISTTIMEFORMAT="%d/%m/%y %T "' >> ~/.bashrc
```

Then, from the terminal, run the following:

```bash
source ~/.bashrc
```

Now, to see history, type:

```bash
history
```

**Sample outputs:**

```bash
533 07/05/17 13:40:07 cd /var/www/html/
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
549 07/05/17 13:40:07 nano wp-config.php
```

## To Display dd-MON-YY & AM/PM & Timezone

```bash
HISTTIMEFORMAT="%d/%m/%y %r %Z "
```

**Sample Outputs:**

```bash
533 07/05/17 01:40:07 PM IST cd /var/www/html/
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
548 07/05/17 01:40:07 PM IST wp db optimize
```

Here’s an explanation of the commands and switches:

| Commands       | Explanation                                                                               |
|----------------|-------------------------------------------------------------------------------------------|
| history        | GNU History Library                                                                       |
| HISTTIMEFORMAT | Environmental Variable                                                                    |
| %d             | The day of the month as a decimal number (range 01 to 31)                                 |
| %m             | The month as a decimal number (range 01 to 12)                                            |
| %y             | The year as a decimal number without a century (range 00 to 99)                           |
| %T             | The time in 24-hour notation (%H:%M:%S)                                                   |
| %r             | The time in a.m. or p.m. notation. In the POSIX locale, this is equivalent to %I:%M:%S %p |
| %Z             | The timezone name or abbreviation                                                         |
| source         | In short, send the contents of the file to the shell                                      |
| .bashrc        | Is a shell script that BASH runs whenever it is started interactively                     |
{: .table }

## Reference

For more info type the following commands:

```bash
man bash
help history
man 3 strftime
```
