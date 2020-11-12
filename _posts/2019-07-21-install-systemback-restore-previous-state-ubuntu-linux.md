---
layout: post
title:  "Install SystemBack In Ubuntu 18.04, 20.04 & Restore To Previous State"
image: install-systemback-restore-previous-state-ubuntu-linux/10.jpg
categories: [linux, backup-restore]
tags: 
- system-back
- linux
- backup
- restore
- system-image
description: "Steps to install SystemBack in Ubuntu and restore your system to the previous state creating a live image backup of user configuration without any data loss."
---
## What is SystemBack?

<span style="color:#bb1919" >*SystemBack*</span> is an open-source application for [Linux](https://stechalon.com/category/linux){:target="_blank"} which makes it easy to create live backup images of your system and user saved configurations. People who are new to Linux make mistakes with the configuration of system [root files](https://stechalon.com/linux-file-system-explained){:target="_blank"} and as a result, crash the system. In this case, [SystemBack](https://launchpad.net/systemback){:target="_blank"}{:rel="nofollow"} is a helpful application for backing up and [restoring your system](https://stechalon.com/reset-root-password-mysql-mariadb-centos){:target="_blank"} in the previous state.

> **Table of Content**

* TOC
{:toc}

## Advantages Of System Back

-  Live boot image.
-  Easy installation and fast recovery.

## Disadvantages Of System Back

- If your .sblive file is more than 4 GB then, cannot be converted to ISO file.

## Install SystemBack in Ubuntu

Use the below command in your system to install system back.
 - <span style="color:#bb1919" >*sudo add-apt-repository ppa:nemh/systemback*</span>
- <span style="color:#bb1919" >*sudo apt-get update*</span>
- <span style="color:#bb1919" >*sudo apt-get install systemback*</span>

##  How To Use System Back?

- After installation, search application by clicking on windows or simply typing SystemBack in the terminal.
![Install SystemBack In Ubuntu | sTechalon.com](/static/img/posts/install-systemback-restore-previous-state-ubuntu-linux/2.PNG)

- Enter your password and press OK.
![SystemBack In Ubuntu | sTechalon.com](/static/img/posts/install-systemback-restore-previous-state-ubuntu-linux/3.PNG)

- Now go to Live system create.
![ Restore Linux To Previous State With System Back| sTechalon.com](/static/img/posts/install-systemback-restore-previous-state-ubuntu-linux/4.PNG)

- Click Create new for creating a system image.
![Create Image with System Back | sTechalon.com](/static/img/posts/install-systemback-restore-previous-state-ubuntu-linux/5.PNG)
![Create Image with System Back | sTechalon.com](/static/img/posts/install-systemback-restore-previous-state-ubuntu-linux/6.PNG)

- Your system gets back up with a live image.
![Backup Image In Linux with System Back | sTechalon.com](/static/img/posts/install-systemback-restore-previous-state-ubuntu-linux/7.PNG)

{% include note.html content= "Time depends on your system size" %}

- After that, a .sblive file is being created i.e your system image.
![ Create ISO Image With System Back and Restore | sTechalon.com](/static/img/posts/install-systemback-restore-previous-state-ubuntu-linux/8.PNG)

- Select the image file and click to convert to ISO.
- You can convert a .sblive file to ISO or can burn to CD/DVD or boot in Pendrive directly.

{% include note.html content= ".sblive cannot be converted to ISO if its size is more than 4GB." %}

- Now you can boot your system for installation and restore to the previous state.

{% include summaryCallout.html heading= "Summary" content= "In this article, you learned what is systemback? How to install and use it for recovery system data. Please feel free to write me if you have any feedback." %}