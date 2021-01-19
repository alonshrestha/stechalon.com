---
layout: post
title: "Difference Between Hard Link and Symbolic Link"
heading: "Difference Between Hard Link and Symbolic Link"
categories: [linux]
image: understand-create-hard-soft-symbolic-links-linux/1.png
tags:
- linux
- ubuntu
- centos
- symbolic-link
- soft-link
- hard-link
description: "Know the difference between hard link and symbolic link in linux. Understand how it works and how to create links"
---
Links are assigned to files on Linux which work as aliases.They are the pointer to the files and directories. There are two types of links on Linux *symbolic link* also known as soft link and *hard link*. If you understand what these links are and how it works, this will make it easy for you to work on [Linux File System](https://stechalon.com/linux-file-system-explained){:target="_blank"}.

Today we will understand the different types of links on linux and how we can use it. First, let us start by understanding it.   

> **Table Of Content**

* TOC
{:toc}

## What is Inode

On Linux, every file and directory has an inode. Inode is known as the index node which is a data structure that describes a file or a directory in Linux/Unix File System.

Each inode has a unique number and stores the attributes and disk block locations of the object's data (i.e file and directory).

Object data attributes include metadata which stores administrative information like: 

* Data block where the file content is stored
* Creation, access and modification date
* Permission
* File owners

In summary, inode is an index node that stores the administrative data of the file and directory. 

You can see from the above information, one important information is not stored in the inode i.e the name of the file.

Names are themselves stored in the directory, and each filename knows which inode to address for further file information.

![Difference Between Hard Link and Symbolic Link | sTechalon.com](/static/img/posts/understand-create-hard-soft-symbolic-links-linux/inode.png)
## What is Hard Links

Giving a name while creating a file, this name is called Hard Link. It is a direct reference to a file through an inode.

On Linux, a single file can have multiple hard links that enable you to access the file from multiple different locations.

Hard links act as a copy of the file. When you delete the original file, you will still find the data of the original file in its hard link file. 

Hard links cannot be created to directories and all the hard links should be on the same device (file system).

When you create multiple hard links of a file, there is no difference between the *first hard link* and the *last hard link* you have created. If the first hard link that exists is removed, then it does not impact other hard links.

### How to Create Hard Links
{% highlight ruby %}
$ln target-file.txt link-file.txt 
{% endhighlight %}
Where target-file.txt is the original file and the link-file.txt if the hard link file.

![Hard Link and Symbolic Link | sTechalon.com](/static/img/posts/understand-create-hard-soft-symbolic-links-linux/h2.PNG)
In the above picture a hard link of the target-file has been created and  the content *“Hello there!!”* is the same in both target and link files. 

## Symbolic Link (Soft Link)
Symbolic link is also known as soft link. These act as a reference or a pointer to the file name.

When you create a soft link of the targeted file, then the link is more likely to be a shortcut of that target file.

Unlike hard link, soft link has different inode and can be linked to both files and directories. Because of different inode this can be pointed to other file systems and also in other devices remotely connected through network file system(NFS).

Soft link does not access data from the original targeted file. So, when the targeted file is deleted then the link will be pointing to the file which does not exist.

### How to Create Soft Links
{% highlight ruby %}
~$ ln -s target-dir/ softlink-dir
{% endhighlight %}

![Hard Link and Symbolic Link | sTechalon.com](/static/img/posts/understand-create-hard-soft-symbolic-links-linux/h1.PNG)
From this picture you can see a soft link has been created. *“->”* shows the pointer of the target file.

## Removing Links
Removing links on Linux is a bit of a risky task to do. You might create an error working program or lose the data.  

For removing links in Linux  just use the rm command.

**Note**: *Never use `-r` option after rm command. The contents of the target directory will be deleted.*

Remove file link
{% highlight ruby %}
~$ rm link-file.txt
{% endhighlight %}

Remove directory link 
{% highlight ruby %}
~$ rm -f softlink-dir/
{% endhighlight %}

To get prompted before removing the symlink, use the -i option:
{% highlight ruby %}
~$ rm -i linkfile.txt
{% endhighlight %}

{% highlight ruby %}
Output:

rm: remove regular file 'linkfile.txt'?
{% endhighlight %}
