---
layout: post
title: "Difference Between Hard Link & Soft Link In Linux"
categories: [linux]
image: understand-create-hard-soft-symbolic-links-linux/1.png
tags:
- linux
- ubuntu
- centos
- symbolic-link
- soft-link
- hard-link
description: "Links are assigned to file on Linux which works as aliases. There are two types of links on Linux Symbolic Link (Soft link) and Hard link. How to use links in Linux"
---
**Links** are assigned to file on Linux which works as [aliases](https://www.dictionary.com/browse/alias){:target="_blank"}{:rel="nofollow"}. There are two types of links on Linux <span style="color:#bb1919">*Symbolic Link (Soft link)*</span> and <span style="color:#bb1919">*Hard link*</span>. If you understand what this links are in Linux and how to use it? This makes you easy to work on [Linux File System](https://stechalon.com/linux-file-system-explained){:target="_blank"}.

On Linux, every file has an [inode](https://en.wikipedia.org/wiki/Inode){:target="_blank"}{:rel="nofollow"}, and in the inode, administrative information is stored. Information like :

* Data block where the file content is stored
* Creation, access and modification date
* Permission 
* File owners 

From the above information, one important information is not stored in the inode **i.e** the <span style="color:#bb1919">*name*</span> of the file. 

Names are itself stored in the directory, and each filename knows which inode to address for further file information.

> **Table Of Content**

* TOC
{:toc}
 
# Hard Links

Giving a name while creating a file, this name is called **Hard Link**. On Linux, single file can have multiple hard links that enable you to access the file from multiple different locations.

Some of the restrictions applied to hard links are as follows:
* Hard links cannot be created to directories
* If the last name of the multiple aliases of the original file is removed, then the content is also removed.
* All the hard links should be on the same device. 

When you create multiple hard links of a file, there is no difference between the <span style="color:#bb1919">*first hard link*</span> and the <span style="color:#bb1919">*last hard link*</span> you have created. If the first hard link that exists is removed, then it does not impact other hard links.

# Symbolic Link (Soft Link)
**Symbolic Link** are also known as **soft link**. This is more flexible than hard links. The advantages and disadvantage of symbolic links are:

## Advantages Of Soft Link
* This link directly to the name of the file rather than inode.
* They can link to file as well as directories on other devices.

## Disadvantage Of Soft Link
* When the original file is removed, the symbolic link becomes invalid and does't work any longer.

# Creating Link
For creating links on Linux `ln` command is used. If you want to create a symbolic link, use the `-s` option and then specify your source and target file or directory.

# Example for Symbolic Link (Soft Link)

Creating a soft link in the <span style="color:#bb1919">*current directory*</span>.
{% highlight ruby %}

[alon@localhost Documents]$ ln -s /etc/
[alon@localhost Documents]$ ls -l
total 0
lrwxrwxrwx. 1 alon alon 5 Oct 22 00:20 etc -> /etc/


{% endhighlight %}

Creating soft link in <span style="color:#bb1919">*specified directory*</span>.

{% highlight ruby %}

[alon@localhost Documents]$ ln -s /home/ /tmp/
[alon@localhost tmp]$ ls -l
total 0
lrwxrwxrwx. 1 alon alon  6 Oct 22 00:45 home -> /home/

# soft link to the /home is created on /tmp
{% endhighlight %}


# Example for Hard Link

{% highlight ruby %}

[root@localhost Data]$ sudo  ln /etc/hosts .
[root@localhost Data]$ ls -l
total 4
-rw-r--r--. 3 root root 158 Jun  7  2013 hosts

{% endhighlight %}

{% include note.html content= " For creating hard links you must be the owner of that file." %}

# Removing Link
Removing links on Linux is a bit risky task to do. You might create an error working program or [loses the data](https://stechalon.com/install-systemback-restore-previous-state-ubuntu-linux){:target="_blank"}. Below shows the example of removing links.

{% highlight ruby %}
#create directory in your home directory

[alon@localhost ~]$ mkdir test

#copy /etc/hosts in test directory

[alon@localhost ~]$ cp /etc/hosts /home/alon/test/

#create soft link of test as link

[alon@localhost ~]$ ln -s test link

#remove link

[alon@localhost ~]$ rm link

{% endhighlight %}

{% include warning.html content= " Do not use -r or -f to remove link. You will lose the data from the original file." %}

{% highlight ruby %}
#creating link again

[alon@localhost ~]$ ln -s test link

#using -rf

[alon@localhost ~]$ rm -rf link/
[alon@localhost ~]$ ls -l
total 0
lrwxrwxrwx. 1 0 0 4 Oct 22 01:08 link -> test
drwxr-xr-x. 2 0 0 6 Oct 22 01:08 test

#you will still see the link exist, but your original directory test will be empty.

[alon@localhost ~]$ ls test/

{% endhighlight %}

{% include summaryCallout.html heading= "Summary" content= "In this articel, you learned how to manage and work with hard links symbolic (soft) links on Linux. Please feel free to write me if need any help." %}

> **Reference**
>  > Red Hat® RHCSA™/RHCE® 7 Cert Guide: Red Hat Enterprise Linux 7 (EX200 and EX300) Sander van Vugt.