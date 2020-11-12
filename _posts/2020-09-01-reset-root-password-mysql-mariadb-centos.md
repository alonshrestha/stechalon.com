---
layout: post
title: "Reset MySQL/MariaDB Root Password In CentOS 8"
categories: [linux, backup-restore]
image: reset-root-password-mysql-mariadb-centos/1.png
tags:
- Linux
- Ubuntu
- CentOS
- root-password
- Mysql
- MariaDB
- reset-passsword
description: "Forgot mysql/mariadb root password?  Rest, change or recover the root password of mysql using skip grant tables command in centOS Linux."
---
[MariaDB](https://mariadb.org/){:target="_blank"}{:rel="nofollow"} root user has full privileges to access every data in the databases. Being human, users sometimes make mistakes or forget the root password. Using different [types of command](https://stechalon.com/linux-bash-shell-command-types){:target="_blank"} will rest your mysql root passowrd without any [data loss](https://stechalon.com/install-systemback-restore-previous-state-ubuntu-linux){:target="_blank"}. In this article, you will learn how to reset the root password of MariaDB on centOS 8 following the steps below.

{% include note.html content= "You must have root access on the server to reset mariadb root password." %}

> **Table Of Content**

* TOC
{:toc}

# Step 1: Stop MariaDB Server
First you need to down your mariaDB server. For that use the command  <span style="color:#bb1919">*'sudo systemctl stop mariadb'*</span>.  

{%highlight ruby%}

[alon@localhost ~]$ sudo systemctl stop mariadb

{%endhighlight%}

# Step 2: Start MariaDB Server with Safe Mode
Start mariadb server with safe mode using <span style="color:#bb1919">*'mysqld_safe'*</span>. For that use the command  <span style="color:#bb1919">*'sudo mysqld_safe --skip-grant-tables &'*</span>.

{%highlight ruby%}
[alon@localhost ~]$ sudo mysqld_safe --skip-grant-tables &
{%endhighlight%}

After entering the above command, if you got `hang` as shown below, press `enter`.  This will redirect you again to command line.

{%highlight ruby%}

[root@localhost alon]# mysqld_safe --skip-grant-tables &
[1] 1892
[root@localhost alon]# 191116 17:21:13 mysqld_safe Logging to '/var/log/mariadb/mariadb.log'.
191116 17:21:13 mysqld_safe Starting mysqld daemon with databases from /var/lib/mysql

{%endhighlight%}

{% include tip.html content= "--skip-grant-tables  runs the server without grants, which allows you to enter into the server without password and it is possible for user from other networks to connect to the server. " %}
# Step 3: Login to MariaDB Server as Root
Now, you will be able  to login in mariaDB as  <span style="color:#bb1919">*'root'*</span> user. For that use the command <span style="color:#bb1919">*'mysql -u root'*</span>.

{%highlight ruby%}

[alon@localhost ~]$ mysql -u root

{%endhighlight%}

You will be login to the mariadb server.  

{%highlight ruby%}

[alon@localhost ~]$ mysql -u root
Welcome to the MariaDB monitor.  Commands end with ; or \g.
Your MariaDB connection id is 2
Server version: 5.5.60-MariaDB MariaDB Server

Copyright (c) 2000, 2018, Oracle, MariaDB Corporation Ab and others.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

MariaDB [(none)]>

{%endhighlight%}

# Step 4: Change MariaDB Root Password
First change the database. For that use the command <span style="color:#bb1919">*'use mysql;'*</span>.

{%highlight ruby%}
MariaDB [(none)]> use mysql;
{%endhighlight%}

After using the mysql database, update the password of root user. For that use the command  <span style="color:#bb1919">*'update mysql.user SET PASSWORD=PASSWORD("StrongPassword") WHERE USER='root';'*</span>.
{%highlight ruby%}
MariaDB [mysql]> update user SET PASSWORD=PASSWORD("NewStrongPassword") WHERE USER='root';
{%endhighlight%}
Flush Privileges using command <span style="color:#bb1919">*'flush privileges;'*</span>.
{%highlight ruby%}
MariaDB [mysql]> flush privileges;
{%endhighlight%}
Exit from mariadb.
{%highlight ruby%}
MariaDB [mysql]> exit
Bye
{%endhighlight%}

# Step 5: Kill mysql and mysqld_safe processor
Find the pid value of <span style="color:#bb1919">*'mysql'*</span> and <span style="color:#bb1919">*'mysqld_safe'*</span> processor using command <span style="color:#bb1919">*'ps aux | grep -i "mysqld_safe" '*</span> and <span style="color:#bb1919">*'ps aux | grep -i "mysql" '*</span>.

{%highlight ruby%}
[alon@localhost ~]$ ps aux | grep -i "mysqld_safe"
{%endhighlight%}

{%highlight ruby%}
[alon@localhost ~]$ ps aux | grep -i "mysql"
{%endhighlight%}

Now kill the processor using command `kill -9`. In my case `2062` is the PID of mysqld_safe and `1892` is the PID of mysql.
{%highlight ruby%}
[alon@localhost ~]$ sudo kill -9 2062
[1]+  Killed                  sudo mysqld_safe --skip-grant-tables

[alon@localhost ~]$ sudo kill -9 1892
{%endhighlight%}

# Step 6: Restart MariaDB
Use the command <span style="color:#bb1919">*'sudo systemctl stop mariadb'*</span> and <span style="color:#bb1919">*'sudo systemctl stop mariadb'*</span>

{%highlight ruby%}
[alon@localhost ~]$ sudo systemctl stop mariadb
{%endhighlight%}
{%highlight ruby%}
[alon@localhost ~]$ sudo systemctl start mariadb
{%endhighlight%}

# Step 7: Login to MariaDB 
Use Command <span style="color:#bb1919">*'mysql -u root -p'*</span>.
{%highlight ruby%}
[alon@localhost ~]$ mysql -u root -p

Enter password:
Welcome to the MariaDB monitor.  Commands end with ; or \g.
Your MariaDB connection id is 8
Server version: 5.5.60-MariaDB MariaDB Server

Copyright (c) 2000, 2018, Oracle, MariaDB Corporation Ab and others.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

MariaDB [(none)]> exit
Bye

{%endhighlight%}

{% include summaryCallout.html heading= "Summary" content= " Hope this article helped you to reset your mysql/mariadb passowrd in centOS. Comment down below if you need any help." %}