---
layout: post
title:  "How To Install Systemback In Ubuntu 20.04 And 18.04"
heading: "Install Systemback In Ubuntu 20.04/19.10/18.04  And Restore To Previous State"
image: install-systemback-restore-previous-state-ubuntu-linux/10.webp
categories: [linux, backup-restore]
tags: 
- system-back
- linux
- backup
- restore
- system-image
description: "Install Systemback in Ubuntu 20.04 and restore your system to the previous state creating a .sblive image backup of user configuration without any data loss."
---
Upgrading the system without any data loss is one of the most risky tasks that I feel to do. Specially, working on open source operating systems like Linux. 

When I was new to Linux, I used to crash my system many times and reinstall it by cleaning the disk(losing data). I was repeating the same process till I encountered the systemback application for Ubuntu.

In short, systemback helps you to backup your ubuntu system and restore it to its previous state without data loss.

In this article I will be teaching you about Systemback, its uses and how to use it. 

> **Table Of Content**

* TOC
{:toc}

## What is Systemback?
Systemback is an open-source application released under the terms of GPLv3 license whose main function is to backup and restore the system. It is easy to create live backup images of your system with user saved configurations.

<a href="https://www.hostg.xyz/aff_c?offer_id=6&aff_id=57845" target="_blank" rel="nofollow"><img src="static/img/posts/affliate/affiliate-hostinger.png" width="728" height="90" border="0" /><img src="https://www.hostg.xyz/aff_i?offer_id=6&aff_id=57845" width="0" height="0" style="position:absolute;visibility:hidden;" border="0" />

## Advantages Of Using Systemback
- Backup system with users configuration files.
- System copying, system installation and Live system creation.
- Restore the system to its previous state.
- Convert backup image into bootable ISO file.
- Upgrading system and software.
- Easy installation and fast recovery.

## Install Systemback in Ubuntu 16.04
Systemback can be installed in Ubuntu 16.04 and lower version from PPA by running the following command below.
{%highlight ruby%}
sudo add-apt-repository ppa:nemh/systemback
{%endhighlight%}
{%highlight ruby%}
sudo apt-get update
{%endhighlight%}
{%highlight ruby%}
sudo apt-get install systemback
{%endhighlight%}
**Note**: *There have been no updates in systemback by its author from 2016. So, the above command works only for Ubuntu 16.04 and lower version.* 

Systemback is not in the supported list but its binary files are compatible with Ubuntu 18.04, 19.10 and 20.04. 

We can install systemback in Ubuntu 20.04, 19.10, 18.04 using Ubuntu 16.04 PPA.   


## Install Systemback in Ubuntu 20.04/19.10/18.04
First remove the PPA.

{%highlight ruby%}
sudo add-apt-repository --remove ppa:nemh/systemback
{%endhighlight%}

Now, run the following command to import the PGP signing key of this PPA. This verifies the signature from the package manager. You can get the signing key from [here](https://launchpad.net/~nemh/+archive/ubuntu/systemback){:target="_blank"}{:rel="nofollow"}.

{%highlight ruby%}
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 382003C2C8B7B4AB813E915B14E4942973C62A1B
{%endhighlight%}

You might get some error regarding *“gpg: keyserver”*

You can fix such errors using different keyservers instead of using **keyserver.ubuntu.com** use **pgp.mit.edu**.
{%highlight ruby%}
sudo apt-key adv --keyserver pgp.mit.edu --recv-keys 382003C2C8B7B4AB813E915B14E4942973C62A1B
{%endhighlight%}

Add the PPA running below command.
{%highlight ruby%}
sudo add-apt-repository "deb http://ppa.launchpad.net/nemh/systemback/ubuntu xenial main"
{%endhighlight%}

Finally, updated the list and install systemback in Ubuntu 20.04, 19.10, 18.04
{%highlight ruby%}
sudo apt update
{%endhighlight%}

{%highlight ruby%}
sudo apt install systemback
{%endhighlight%}

## How To Use Systemback?

After installation, open the application. 

Enter your user password and press OK. 

![SystemBack In Ubuntu | sTechalon.com](/static/img/posts/install-systemback-restore-previous-state-ubuntu-linux/3.PNG)<br>
Here, you can see many options in the function menu. Click on *"Live system create"*.

![ Restore Linux To Previous State With System Back| sTechalon.com](/static/img/posts/install-systemback-restore-previous-state-ubuntu-linux/4.PNG)
## Create Backup Image Of Your Current System

You can replace the working directory path *“/home”* to another. This is the directory path where your backup image and iso will be stored. 

Give name to your new live system replacing the name *“auto”*.

If you are creating the image for your personal use or image including your profile configuration then click on *“Include the user data files”*.

After these, click on *“Create new”* to continue.

![Create Image with System Back | sTechalon.com](/static/img/posts/install-systemback-restore-previous-state-ubuntu-linux/5.PNG)
**Note**: *The time depends upon your system size.*

If everything is done in process your image will be created as .sblive as shown below.

![Backup Image And Convert .sblive to ISO File System Back | sTechalon.com](/static/img/posts/install-systemback-restore-previous-state-ubuntu-linux/7.PNG)<br>
After a .sblive file is created systemback allows you to write the system in your usb flash drive directly.

## Convert .sblive File To Bootable ISO File 
Now it's time to write an image in your usb flash drive.

For that, insert your usb drive and click on the *“Green Refresh”* button. 

The *“Write target”* box should display your pendrive. In my case it’s *“SanDisk Cruzer Blade”*. 
 
![Backup Image And Convert .sblive to ISO File System Back | sTechalon.com](/static/img/posts/install-systemback-restore-previous-state-ubuntu-linux/8.PNG)
Select  the created image displayed on the  *“Created Live Images”* box. There will be different *“Live operations”* available that you can apply to this image.

Click on *“Write to target”*. You will see the configuration dialog box, click on Start. This operation writes the new image to your flash drive and a  progress bar is displayed.

Click on *“Convert to ISO”* if you want to create a bootable iso file from the created .sblive image.

You can also *“Delete”* the .sblive image and re-create the new image clicking on *“Create New”*.

**Note**: *Your image cannot be converted into iso if the .sblive file is greater than 4 GB.*

## Conclusion

I hope you have enjoyed this tutorial. In case of problems with your system you can easily restore the previous state of the system. Systemback also has other features like system copying, system installation and Live system creation.

Unfortunately, systemback does not provide any update and does not exist in the support list of the latest version of Ubuntu. If you have more queries on this you can [check here](https://answers.launchpad.net/systemback){:target="_blank"}{:rel="nofollow"}.

We have installed the systemback application in Ubuntu 20.04, 19.10, and 18.04 using PPA of Ubuntu 16.04 and [Open PGP key](https://launchpad.net/~sonicwalker){:target="_blank"}{:rel="nofollow"}. At the end, we created .sblive and wrote the system in a usb flash drive. We were also able to convert the .sblive file to bootable iso file.

**Disclaimer**:
- *Some links used in this article are affiliated. This means if you do certain actions through that link I might earn some commission.*