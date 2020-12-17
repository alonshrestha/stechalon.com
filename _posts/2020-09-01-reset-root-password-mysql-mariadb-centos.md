---
layout: post
title: "How To Reset MySQL Or MariaDB Root Password"
heading: "How To Reset MySQL Or MariaDB Root Password"
categories: [linux, backup-restore]
image: reset-root-password-mysql-mariadb-centos/1.webp
tags:
- Linux
- Ubuntu
- CentOS
- root-password
- Mysql
- MariaDB
- reset-passsword
description: "Reset MySQL or MariaDB root password in linux centos and ubuntu. Change password using mysql safe mode"
---
MariaDB root user has full privilege to access every data in the databases.

Being a human, we sometimes make a mistake or forget the root password. And that is normal, not to worry &#128513;.

You can still gain access to your database without losing your data. In this article, you will learn how to reset MariaDB or MySQL root password.

## Prerequisites
- You must have **sudo** user access on MySQL or MariaDB running Linux machine.

## Identify Your Database Server Version
Before we move on to recovering the password you should know which version of MySQL or MariaDB you are running on your machine.

Depending on the version of your server you need to run the command. To check the version run the following command.

{%highlight ruby%}
$ mysql --version
{%endhighlight%}

According to your version, you will see a similar output as shown below.

MySQL Output

{%highlight ruby%}
mysql  Ver 14.14 Distrib 5.7.22, for Linux (x86_64) using  EditLine wrapper
{%endhighlight%}

MariaDB Output
{%highlight ruby%}
mysql  Ver 15.1 Distrib 10.1.33-MariaDB, for debian-linux-gnu (x86_64) using readline 5.2
{%endhighlight%}

**Note:** *Make sure you note your running database server version. You need this later.*

## Step 1: Stop Your MySQL / MariaDB Server
First, you need to stop your running server so that you can access your database manually.

Stop MySQL Server
{%highlight ruby%}
$ sudo systemctl stop mysql
{%endhighlight%}

Stop MariaDB Server
{%highlight ruby%}
$ sudo systemctl stop mariadb
{%endhighlight%}

## Step 2: Restart Your MariaDB / MySQL Server In Safe Mode
Start your database server without loading the grant tables. This means you are going to start the server without loading information about user privileges.

This will allow you to access your database through a root user with no password.

{%highlight ruby%}
$ sudo mysqld_safe --skip-grant-tables --skip-networking &
{%endhighlight%}

After entering the above command, your terminal may look similar as shown below. Press enter and you will be redirected to the command line.

{%highlight ruby%}
91116 17:21:13 mysqld_safe Logging to '/var/log/mariadb/mariadb.log'.
191116 17:21:13 mysqld_safe Starting mysqld daemon with databases from /var/lib/mysql
{%endhighlight%}

**Note:** *'--skip-grant-tables' run the server without grants, which allows you to enter into the server without a password and it is possible for users from other networks to connect to the server. Try to skip the network while you do this operation.*

## Step 3: Login MariaDB / MySQL Server as Root
Now, you will be able to login into the server as a root user.
{%highlight ruby%}
$ mysql -u root
{%endhighlight%}

In my case, I am using MariaDB and you can see that I am able to login in to the server as shown below.
{%highlight ruby%}
Welcome to the MariaDB monitor.  Commands end with; or \g.
Your MariaDB connection id is 2
Server version: 5.5.60-MariaDB MariaDB Server

Copyright (c) 2000, 2018, Oracle, MariaDB Corporation Ab and others.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

MariaDB [(none)]>
{%endhighlight%}

## Step 4: Change MariaDB / MySQL Root Password
First, reload the database server grant tables using the *'FLUSH PRIVILEGES'* command.

{%highlight ruby%}
> FLUSH PRIVILEGES;
{%endhighlight%}

Follow the below command to change the password of the root user if you have *MySQL 5.7.6* and newer or *MariaDB 10.1.20* and newer.

{%highlight ruby%}
> ALTER USER 'root'@'localhost' IDENTIFIED BY 'NEW_PASSWORD';
> FLUSH PRIVILEGES;
{%endhighlight%}

**Note:** *Do not forget to replace your password with NEW_PASSWORD in above command.*

If the *'ALTER USER'* command does not work for you then, try modifying the user table directly as shown below.

{%highlight ruby%}
> UPDATE mysql.user SET authentication_string = PASSWORD('NEW_PASSWORD')WHERE User = 'root' AND Host = 'localhost';
{%endhighlight%}

Remember to reload the grant tables after running the above command.

{%highlight ruby%}
> FLUSH PRIVILEGES;
{%endhighlight%}

For *MySQL 5.7.5* and older or *MariaDB 10.1.20* and older:

{%highlight ruby%}
> SET PASSWORD FOR 'root'@'localhost' = PASSWORD('NEW_PASSWORD');
> FLUSH PRIVILEGES;
{%endhighlight%}

If everything was done in the process, you will see the below output.

{%highlight ruby%}
Query OK, 0 rows affected (0.00 sec)
{%endhighlight%}

You have changed the password. Now, you can stop the manual run database server and restart it again.

## Step 5: Kill mysqld and mariadb PID
Stop the database server that was run manually in step 2. To do this search the process ID or PID of MySQL and MariaDB and kill it.

You can kill the process in different ways for example: using *'ps aux'* command to find the process ID or kill directly if you know the path of the .pid file of the process. I will suggest you use

For MySQL

{%highlight ruby%}
$ sudo kill `cat /var/run/mysqld/mysqld.pid`
{%endhighlight%}

For MariaDB

{%highlight ruby%}
$ sudo kill `/var/run/mariadb/mariadb.pid`
{%endhighlight%}

## Step 6: Restart Your MariaDB / MySQL Server Normally
For MySQL

{%highlight ruby%}
$ sudo systemctl start mysql
{%endhighlight%}

For MariaDB

{%highlight ruby%}
$ sudo systemctl start mariadb
{%endhighlight%}

Verify your password

{%highlight ruby%}
$ mysql -u root -p
{%endhighlight%}

## Conclusion
I hope this article helped you to reset your MySQL or MariaDB root password. Make your database secure using a strong password and try to take a backup of your database daily using the *'mysqldump'* command.