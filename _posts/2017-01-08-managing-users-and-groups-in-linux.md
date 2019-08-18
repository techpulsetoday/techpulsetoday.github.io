---
layout: post
title:  "Managing Users and Groups in Linux"
author: vijayan
categories: [ Linux ]
tags: [ Linux Groups, Linux Tips, Linux Users, Password, Server ]
image: assets/images/2017/01/Managing-Users-and-Groups-in-Linux.png
description: "Managing Users and Groups in Linux, like adding or removing them, giving them a password etc -all from a system administrator's point of view."
---
This is an article that takes the reader back to the basics of Linux. Managing Users and Groups in Linux, like adding or removing them, giving them a password, etc -all from a system administrator's point of view.

Linux is a multi-user operating system, which means that more than one user use Linux at the same time. Linux provides a beautiful mechanism to manage users in a system. On of the most important roles of a system administrator is to manage the users and groups in a system. All the commands used in this article are explained using the CentOS Linux distro.
<h2>Linux user</h2>
A user or account of a system is uniquely identified by a numerical number called the <em><strong>UID</strong></em> (unique identification number). There are two types of users - the root or super user can access all the files, while the normal user has limited access to files. A superuser can add, delete and modify a user account. The full account information is stored in the <strong><em>/etc/passwd</em></strong> file and a hash password is stored in the file <strong><em>/etc/shadow</em></strong>. Some operations on a user account are discussed below.
<h3>Creating a user with a default setting:</h3>
A user can be added by running the <strong>useradd</strong> command at the command prompt. After creating the user, set a password using the <strong>passwd</strong> utility, as follows:
<pre class="lang:default decode:true">root@vijayan-VPCCA35FA:/home/vijayan# useradd techpulsetoday
root@vijayan-VPCCA35FA:/home/vijayan# passwd techpulsetoday
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully
root@vijayan-VPCCA35FA:/home/vijayan#</pre>
The system automatically assigns a UID, creates the home directory (<strong><em>/home/&lt;username&gt;</em></strong>) and sets the default shell to <strong><em>/bin/bash</em></strong>. The useradd command creates a user private group whenever a new user is added to the system and names the group after the user.
<h3>Specifying a user's full name when creating a user:</h3>
A systems administrator can use the <strong><em>-c</em></strong> options with useradd to specify the user's full name, as shown below:
<pre class="lang:default decode:true">root@vijayan-VPCCA35FA:/home/vijayan# userdel techpulsetoday
root@vijayan-VPCCA35FA:/home/vijayan# useradd -c "TechPulseToday" techpulsetoday</pre>
<h3>Creating a user with the UID:</h3>
You can create a user with a custom UID with the <em><strong>-u</strong></em> option, as follows:
<pre class="lang:default decode:true">root@vijayan-VPCCA35FA:/home/vijayan# useradd -u 1036 techpulsetoday</pre>
<h3>Creating a user with the non-default home directory:</h3>
A non-default home directory can be set by executing the following command:
<pre class="lang:default decode:true ">root@vijayan-VPCCA35FA:/home/vijayan# useradd -d /home/test techpulsetoday</pre>
<h3>Adding a user to a primary group and supplementary group:</h3>
A system administrator can specify a primary group and a supplementary one by specifying the <strong><em>-g</em></strong> and <strong><em>-G</em></strong> option, respectively.
<pre class="lang:default decode:true">root@vijayan-VPCCA35FA:/home/vijayan# useradd -g "head" -G "faculty" techpulsetoday</pre>
<h3>Locking and unlocking a user:</h3>
A superuser can lock and unlock a user account. To Lock an account, one needs to invoke <strong><em>passwd</em></strong> with the <strong><em>-l</em></strong> option.
<pre class="lang:default decode:true">root@vijayan-VPCCA35FA:/home/vijayan# passwd -l techpulsetoday
Locking password for user techpulsetoday.
passwd: Success</pre>
The <strong><em>-u</em></strong> option with <em><strong>passwd</strong></em> unlock an account, as shown below:
<pre class="lang:default decode:true">root@vijayan-VPCCA35FA:/home/vijayan# passwd -u techpulsetoday
Unlocking password for user techpulsetoday.
passwd: Success</pre>
<h3>Changing a user name:</h3>
The <strong><em>-l</em></strong> option with the <strong><em>-r</em></strong> option drops a user and the home directory associated with that user, as shown below:
<pre class="lang:default decode:true ">root@vijayan-VPCCA35FA:/home/vijayan# usermod -l "Vijayan J" techpulsetoday</pre>
<h3>Removing a user:</h3>
Combining <strong>userdel</strong> with the <strong><em>-r</em></strong> option drop a user and the home directory associated with that user, as shown below:
<pre class="lang:default decode:true">root@vijayan-VPCCA35FA:/home/vijayan# userdel -r techpulsetoday</pre>
<h2>Linux Group</h2>
Linux group is a mechanism to organize a collection of users. Like the user ID, each group is an also associated with a unique ID called the <strong>GID</strong> (group ID). There are two types of groups <em>- a</em> primary group and a supplementary group. Each user is a member of a  member of a primary group and of zero or '<strong><em>more than zero</em></strong>' supplementary group. The group information is stored in <strong><em>/etc/group</em></strong> and the respective passwords are stored in the <strong><em>/etc/gshadow</em></strong> file. Some operations such as creating, deleting and modifying on a group are discussed below.
<h3>Creating a group with default settings:</h3>
To add a new group with default settings, run the <strong><em>groupadd</em></strong> command as a root user, as shown below:
<pre class="lang:default decode:true">root@vijayan-VPCCA35FA:/home/vijayan# groupadd employee</pre>
If you wish to add a password, then type <em><strong>gpasswd</strong></em> with the group name, as follow:
<pre class="lang:default decode:true">root@vijayan-VPCCA35FA:/home/vijayan# gpasswd employee
Changing the password for group employee
New Password:
Re-enter new password:</pre>
<h3>Creating a group with a specified GID:</h3>
To explicitly specify the GID of a group, execute the <em><strong>groupadd</strong></em> command with the <em><strong>-g</strong> </em>option, as follow:
<pre class="lang:default decode:true">root@vijayan-VPCCA35FA:/home/vijayan# groupadd -g 1200 manager</pre>
<h3>Removing group password:</h3>
To remove a group password, run <strong><em>gpasswd</em> <em>-r</em></strong> with the relevant group name, as follow:
<pre class="lang:default decode:true">root@vijayan-VPCCA35FA:/home/vijayan# gpasswd -r employee</pre>
<h3>Changing the group's name:</h3>
To change the group's name, run the <em><strong>groupmod</strong></em> command with the <strong><em>-n</em></strong> option as a super user, as shown below:
<pre class="lang:default decode:true ">root@vijayan-VPCCA35FA:/home/vijayan# groupmod -n techmanager employee</pre>
<h3>Changing the group's GID:</h3>
To change the GID of a group, run the <em><strong>groupmod</strong></em> command with <em><strong>-g</strong></em>, as follow:
<pre class="lang:default decode:true">root@vijayan-VPCCA35FA:/home/vijayan# groupmod -g 1050 manager</pre>
<h3>Deleting a group:</h3>
Before deleting a primary group, delete the users of that primary group. To delete a group, run the <em><strong>groupdel</strong></em> command with the group name, as shown below:
<pre class="lang:default decode:true ">root@vijayan-VPCCA35FA:/home/vijayan# groupdel manager
root@vijayan-VPCCA35FA:/home/vijayan# groupdel employee</pre>
If you wish to know much more about the user and group management, you can refer to the <a href="https://www.redhat.com/en">Red Hat System Administration</a> and manual page of each command.