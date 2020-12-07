---
layout: post
title: "How To Install Apache Web Server In Ubuntu 20.04"
categories: [linux, webhosting]
image: install-apache-web-server-ubuntu/1.png
tags:
- Linux
- Ubuntu
- Unix
- Apache
- Web
- Server
- Install
- httpd
- Http
description: "Install the apache2 web server in Ubuntu 20.04.01 Linux within 3 steps. Configure firewall, server start-stop and enable, virtual host. Allow default port 80 from ufw."
---
Apache [web server](https://stechalon.com/start-blogging-with-jekyll-github-pages#why-did-i-migrate-from-wordpress-to-github-pages){:target="_blank"} is an open source software application that activates your machine to [HTTP](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol){:target="_blank"}{:rel="nofollow"} server. This allows the machine to serve the http request recived from the user. Installing apache web server in Ubuntu is free and easy. This article provides a simple tutorial on installing apache web server in  <span style="color:#bb1919">*Ubuntu 20.04*</span>.

> **Requirements**<br>
Before following this tutorial you should have following requirements.
 - System with Ubuntu 20.04.1 LTS<br>
 - Root Access<br>
 - Internet Connection

> **Table of Content**

* TOC
{:toc}

## Step 1: Installing  Apache Web Server In Ubuntu
Apache web server is a default software available in Ubuntu repositories. So, we can install it with a  few commands. Before installing apache first make sure your system is up to date.
{%highlight ruby%}
$ sudo apt update
{%endhighlight%}

Now, install apache  in your system
{%highlight ruby%}
$ sudo apt install apache2
{%endhighlight%}
 

## Step 2: Configure Your Firewall

Apache web server runs at default **port 80**. After apache is installed we need to allow port 80 for everyone from  <span style="color:#bb1919">*UFW firewall*</span>. For that, check the available ufw application list.
{%highlight ruby%}
$ sudo ufw app list
{%endhighlight%}


**Output:**
{%highlight ruby%}
Available applications:
  Apache
  Apache Full
  Apache Secure
  OpenSSH
{%endhighlight%}

Now use the below command to allow Apache.
{%highlight ruby%}
$ sudo ufw allow 'Apache'
{%endhighlight%}

**Output:**
{%highlight ruby%}
Rules updated
Rules updated (v6)
{%endhighlight%}

Verify the changes made.
{%highlight ruby%}
$ sudo ufw status
{%endhighlight%}


**Output:**
{%highlight ruby%}
Status: active

To                         Action      From
--                         ------      ----   
Apache                     ALLOW       Anywhere                            
Apache (v6)                ALLOW       Anywhere (v6)

{%endhighlight%}

## Step 3: Checking Status Of Apache Web Server

After configuring your firewall, now check the  status of the server with  <span style="color:#bb1919">*'systemctl'*</span> command.
{%highlight ruby%}
$ sudo systemctl status apache2
{%endhighlight%}

**Output:**
{%highlight ruby%}
● apache2.service - The Apache HTTP Server
     Loaded: loaded (/lib/systemd/system/apache2.service; enabled; vendor preset: enabled)
     Active: active (running) since Sun 2020-09-06 05:53:18 UTC; 16min ago
       Docs: https://httpd.apache.org/docs/2.4/
   Main PID: 20348 (apache2)
      Tasks: 55 (limit: 1164)
     Memory: 5.2M
     CGroup: /system.slice/apache2.service
             ├─20348 /usr/sbin/apache2 -k start
             ├─20350 /usr/sbin/apache2 -k start
             └─20351 /usr/sbin/apache2 -k start
{%endhighlight%}


Access your web server to configure that the server is running properly from your browser. Enter the url 
{%highlight ruby%}
http://your_ip-address
{%endhighlight%}

If you are in your local machine enter
{%highlight ruby%}
http://localhost or https://127.0.0.1
{%endhighlight%}


In my case, my machine address is  <span style="color:#bb1919">*http://3.89.36.46/*</span>. You will see the default Ubuntu 20.04 apache page which means your server is running properly. 

![How To Install Apache Web Server In Ubuntu 20.04](/static/img/posts/install-apache-web-server-ubuntu/2.PNG)
## Step 4: Configuring Your Apache Web Server
It is important to know how to control your server system. Controlling the server system means <span style="color:#bb1919">*stop, start*</span> and <span style="color:#bb1919">*restart*</span> your server. 

**Start** apache web server.
{%highlight ruby%}
$ sudo systemctl start apache2
{%endhighlight%}


**Stop** apache web server.
{%highlight ruby%}
$ sudo systemctl stop apache2
{%endhighlight%}


**Restart** apache web server.
{%highlight ruby%}
$ sudo systemctl restart apache2
{%endhighlight%}


**Enable** apache web server. This makes apache to run automatically when you reboot your system.
{%highlight ruby%}
$ sudo systemctl enable apache2
{%endhighlight%}


**Disable** apache web server. This stops apache to run automatically when you reboot your system.
{%highlight ruby%}
$ sudo systemctl disable apache2
{%endhighlight%}

{% include summaryCallout.html heading= "Summary" content= "Hope you have learn how to install apache web server in Ubuntu 20.04.1. If you have any issue please let me know through comment secetion below." %}
