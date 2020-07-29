---
id: 574
title: What is Linux File System? Explained
date: 2020-06-26T09:07:20+00:00
author: alonshrestha
excerpt: All the files on the Linux are organized into a single inverted tree directory which is also known as file system hierarchy. Ext, XFS, NTFS, etc.
layout: post
guid: https://stechalon.com/?p=574
permalink: /linux-file-system-explained/
site-sidebar-layout:
  - default
site-content-layout:
  - default
theme-transparent-header-meta:
  - default
image: /wp-content/uploads/2020/06/Linux-File-System-Explained.png
categories:
  - Linux
tags:
  - BtrFS
  - ext
  - file system
  - NTFS
  - VFAT
  - xfs
---
<p class="has-text-align-left">
  All the files on the <a aria-label="undefined (opens in a new tab)" href="http://stechalon.com/category/linux" target="_blank" rel="noreferrer noopener">Linux</a> are organized into a single inverted tree directory which is also known as file system hierarchy. The file system handles your data on the storage, which allows the system to know and use it at the beginning and end of the operation. By default, Linux has organized directories which is similar to almost all Linux file system. In this article, we will know about different types of Linux file systems and its hierarchy.
</p>

<div class="ub_table-of-contents" data-showtext="show" data-hidetext="hide" id="ub_table-of-contents-57e8b074-a26f-476b-8aa7-9b03da57f751">
  <div class="ub_table-of-contents-header">
    <div class="ub_table-of-contents-title">
      Table Of Content
    </div>
  </div>
  
  <div class="ub_table-of-contents-container ub_table-of-contents-1-column ">
    <ul>
      <li>
        <a href=https://stechalon.com/linux-file-system-explained/#0-linux-file-system-types>Linux File System Types</a>
      </li>
      <li>
        <a href=https://stechalon.com/linux-file-system-explained/#1-linux-file-system-hierarchy>Linux File System Hierarchy</a>
      </li>
    </ul>
  </div>
</div>

## Linux File System Types {#0-linux-file-system-types}

Linux provides different types of file system formats for partitioning the disk which is listed below. Each has its own merits of the use.<figure class="wp-block-table is-style-regular">

<table class="has-subtle-pale-blue-background-color has-background">
  <tr>
    <th class="has-text-align-left" data-align="left">
      <strong>File System</strong>
    </th>
    
    <th>
      <strong>Explanation</strong>
    </th>
  </tr>
  
  <tr>
    <td class="has-text-align-left" data-align="left">
      <strong>Ext:</strong>
    </td>
    
    <td>
      A basic file system having a lot of limitations and no longer in use.
    </td>
  </tr>
  
  <tr>
    <td class="has-text-align-left" data-align="left">
      <strong>Ext2:</strong>
    </td>
    
    <td>
      Upgrade version of Ext which allows 2 TB of data and not in use anymore.
    </td>
  </tr>
  
  <tr>
    <td class="has-text-align-left" data-align="left">
      <strong>Ext3:</strong>
    </td>
    
    <td>
      Upgrade of Ext2. Does not support file recovery and disk snapshots.
    </td>
  </tr>
  
  <tr>
    <td class="has-text-align-left" data-align="left">
      <strong>Ext4:</strong>
    </td>
    
    <td>
      Upgrade of Ext3. It allows a large file of data up to 16TB with significant speed.
    </td>
  </tr>
  
  <tr>
    <td class="has-text-align-left" data-align="left">
      <strong>XFS</strong>
    </td>
    
    <td>
      Default file system in RHEL 7. Allows data up to 500 TB
    </td>
  </tr>
  
  <tr>
    <td class="has-text-align-left" data-align="left">
      <strong>BtrFS</strong>
    </td>
    
    <td>
      The new file system not yet supported but will be included in later updates.
    </td>
  </tr>
  
  <tr>
    <td class="has-text-align-left" data-align="left">
      <strong>NTFS</strong>
    </td>
    
    <td>
      Not Supported on RHEL
    </td>
  </tr>
  
  <tr>
    <td class="has-text-align-left" data-align="left">
      <strong>VFAT</strong>
    </td>
    
    <td>
      Equivalent to the FAT32. Useful to use on a USB thumb drive.
    </td>
  </tr>
</table></figure> 

## Linux File System Hierarchy {#1-linux-file-system-hierarchy}

In the Linux file system hierarchy, the root of the tree is said to be on the top of the hierarchy, and the branches of directories and subdirectories as shown in the below image.<figure class="wp-block-image size-large">

![Linux File System Explained | stechalon.com](https://raw.githubusercontent.com/alonshrestha/stechalonPostPic/master/File%20System%20In%20Linux%20Explained/img1.png) </figure> 

You can try as well in your machine to view the hierarchy. First go to root directory using command `<span style="color:#289dcc" class="tadv-color">cd /</span>` and type `<span style="color:#289dcc" class="tadv-color">ls -l /</span>` to see this directories as shown below.

<pre class="wp-block-code"><code>&#91;stechalon@localhost ~]$ ls -l /
total 36
lrwxrwxrwx.   1 root root    7 Jul 11 09:02 bin -> usr/bin
dr-xr-xr-x.   5 root root 4096 Sep 12 15:22 boot
drwxr-xr-x.   3 root root 4096 Jul 11 08:51 data
drwxr-xr-x.  19 root root 3120 Sep 25 17:14 dev
drwxr-xr-x.  82 root root 8192 Sep 25 17:14 etc
drwxr-xr-x.   3 root root   17 Apr 11  2018 home
lrwxrwxrwx.   1 root root    7 Jul 11 09:02 lib -> usr/lib
lrwxrwxrwx.   1 root root    9 Jul 11 09:02 lib64 -> usr/lib64
drwxr-xr-x.   2 root root    6 Apr 11  2018 media
drwxr-xr-x.   2 root root    6 Apr 11  2018 mnt
drwxr-xr-x.   5 root root   76 Sep 23 14:36 opt
dr-xr-xr-x. 115 root root    0 Sep 25 17:14 proc
dr-xr-x---.   7 root root 4096 Sep 23 15:24 root
drwxr-xr-x.  26 root root  740 Oct 29 18:06 run
lrwxrwxrwx.   1 root root    8 Jul 11 09:02 sbin -> usr/sbin
drwxr-xr-x.   2 root root    6 Apr 11  2018 srv
dr-xr-xr-x.  13 root root    0 Sep 25 17:14 sys
drwxrwxrwt.   9 root root 4096 Oct 29 04:50 tmp
drwxr-xr-x.  13 root root 4096 Jul 11 09:03 usr
drwxr-xr-x.  21 root root 4096 Jul 22 14:05 var</code></pre>

Form the above sketch you can see `->` symbol pointing multiple directories in `/usr/` directory. This indicates that the directories `bin` , `lib` , `lib64` and `sbin` are the <a href="https://blog.alonshrestha.com.np/Understanding-Hard-and-Soft-Links-In-Linux/" target="_blank" rel="noreferrer noopener">symbolic links</a> from `/usr/`.

Table below describes the directories.<figure class="wp-block-table">

<table class="has-subtle-pale-blue-background-color has-background">
  <tr>
    <th>
      Directory
    </th>
    
    <th>
      Explanation
    </th>
  </tr>
  
  <tr>
    <td>
      <strong>/</strong>
    </td>
    
    <td>
      Know as <code>root</code> directory where file system tree starts.
    </td>
  </tr>
  
  <tr>
    <td>
      <strong>/bin</strong>
    </td>
    
    <td>
      Contains <code>binaries files</code> of the application or program that can be run. Essential during boot.
    </td>
  </tr>
  
  <tr>
    <td>
      <strong>/boot</strong>
    </td>
    
    <td>
      Contains all the files and directories that are needed to <code>boot</code> the Linux kernel.
    </td>
  </tr>
  
  <tr>
    <td>
      <strong>/dev</strong>
    </td>
    
    <td>
      Contains device files that allow accessing <code>physical devices</code>. Many of these files are generated at boot time. Essential during boot.
    </td>
  </tr>
  
  <tr>
    <td>
      <strong>/etc</strong>
    </td>
    
    <td>
      Know as <code>every thing to configure</code>. It contains the configuration files that are used by the application and services.
    </td>
  </tr>
  
  <tr>
    <td>
      <strong>/home</strong>
    </td>
    
    <td>
      This directory is used for local user <code>home directory</code>.
    </td>
  </tr>
  
  <tr>
    <td>
      <strong>/lib, /lib64</strong>
    </td>
    
    <td>
      Contains the shared libraries that are used by the application in <code>/boot</code> <code>/sbin</code> and <code>bin</code>.
    </td>
  </tr>
  
  <tr>
    <td>
      <strong>/media</strong>
    </td>
    
    <td>
      Contains the files of the <code>external storage</code>.
    </td>
  </tr>
  
  <tr>
    <td>
      <strong>/mnt</strong>
    </td>
    
    <td>
      Contains files that allow for <code>mounting</code> the devices.
    </td>
  </tr>
  
  <tr>
    <td>
      <strong>/opt</strong>
    </td>
    
    <td>
      This is used to install <code>optional package</code> not from the Linux distribution repositories.
    </td>
  </tr>
  
  <tr>
    <td>
      <strong>/sbin</strong>
    </td>
    
    <td>
      Similar to <code>/bin</code>. It contains all the binaries that superuser needs.
    </td>
  </tr>
  
  <tr>
    <td>
      <strong>/srv</strong>
    </td>
    
    <td>
      Directory that may be used for data by services like <code>HTTP</code>, <code>NFS</code> and <code>TCP</code>.
    </td>
  </tr>
  
  <tr>
    <td>
      <strong>/run</strong>
    </td>
    
    <td>
      System applications use this directory for storing the temporary files for their own need.
    </td>
  </tr>
  
  <tr>
    <td>
      <strong>/tmp</strong>
    </td>
    
    <td>
      This directory contains <code>temporary files</code> which gets <code>deleted</code> while system boot without warning.
    </td>
  </tr>
  
  <tr>
    <td>
      <strong>/usr</strong>
    </td>
    
    <td>
      Contains sub-directories including programs, libraries, documentation, etc. for all user-related programs. This is not needed for boot.
    </td>
  </tr>
  
  <tr>
    <td>
      <strong>/var</strong>
    </td>
    
    <td>
      Contains <code>system log</code> files which size changes dynamically.
    </td>
  </tr>
  
  <tr>
    <td>
      <strong>/root</strong>
    </td>
    
    <td>
      Home directory of <code>root user</code>.
    </td>
  </tr>
  
  <tr>
    <td>
      <strong>/proc</strong>
    </td>
    
    <td>
      Contains files that give information about <code>kernel and CPU</code>.
    </td>
  </tr>
  
  <tr>
    <td>
      <strong>/sys</strong>
    </td>
    
    <td>
      Similar to <code>/proc</code> that contains information about the connected devices from your computer.
    </td>
  </tr>
  
  <tr>
    <td>
      <strong>/lost+found</strong>
    </td>
    
    <td>
      Files that are saved during <code>system failures</code>.
    </td>
  </tr>
</table></figure> 

<div class="ub-styled-box ub-notification-box" id="ub-styled-box-02df4442-c625-4604-bc3b-23f91c999aad">
  <div class="ub-notification-text">
    <strong>Summary</strong>: In this article, you learned the concept of Linux file system types and their hierarchy. Please comment down below if you need any help.
  </div>
</div>