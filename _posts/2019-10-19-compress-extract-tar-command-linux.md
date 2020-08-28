---
layout: post
title: "Compress & Extract Files In Linux Using Tar Command"
categories: [linux]
image: compress-extract-tar-command-linux/1.png
tags:
- linux
- ubuntu
- centos
- unzip
- command
- compression
- archive
- tar
- gz
- bz2
description: "How to compress and extract files in Linux using tar command with examples. What is tar command and how to use in Linux for unzip and zip .tar .gz archive?"
---

![Compress & Extract Files In Linux Using Tar Command | sTechalon.com](/static/img/posts/compress-extract-tar-command-linux/1.png)
Managing and working with file compression and archive is the most important file-related task in Linux. [tar](https://en.wikipedia.org/wiki/Tar_(computing)){:terget="_blank"}{:rel="nofollow"} command is known as <span style="color:#bb1919">*Tape ARchive*</span> which is used to create an archive of [files in Linux](https://stechalon.com/linux-file-system-explained){:targer="_blank"}. This command creates an archive without compression. 

For creating an archive file with compression, you need to use specific compression tools or need to specify an option that compresses the archive while it is created. In this article, we will learn how to manage and work with archives and compressed files. 

> **Table Of Content**

* TOC
{:toc}

# Create Archive
To create an archive we use <span style="color:#bb1919">*'tar -cf  Archive-file-name.tar  /file-you-want-to-archive'*</span>.  In below example an archive is created with the name <span style="color:#bb1919">*myFiles.tar*</span> for directory <span style="color:#bb1919">*/home/alon/Documents/*</span>.

**Example:** 

{% highlight ruby %}

[alon@localhost ~]$ tar -cf myFiles.tar /home/alon/Documents/

{% endhighlight %}

If you want to see what is happening while running above command, use `-v` option.

{% highlight ruby %}

[alon@localhost ~]$ tar -cvf myFiles.tar /home/alon/Documents/
/home/alon/Documents/
/home/alon/Documents/passwd
/home/alon/Documents/newfile
/home/alon/Documents/oktest.tar
/home/alon/Documents/oktest.tar.bz2
/home/alon/Documents/linkedfile

{% endhighlight %}

{% include note.html content= " In -cvf option ( - ) was not being used in old version of tar." %}

# Add File in Existing Archive
While managing archives with tar,  there might also be a case to add a new file in the existing archive. For that, we use `-r` options. Syntax <span style="color:#bb1919">*'tar -rvf  Archive-file-name.tar  /path-of/file-you-want-to-add-to-the-archive'*</span>. 

**Example:**

{% highlight ruby %}

[alon@localhost ~]$ tar -rvf myFiles.tar /etc/hosts

{% endhighlight %}

# Update Existing Archive

To update current existing archive file, we can use the `-u` options. Syntax <span style="color:#bb1919">*'tar -uvf  Archive-file-name.tar /path-to/File-you-want-to-update'*</span>.

**Example:**


{% highlight ruby %}

[alon@localhost ~]$ tar -uvf myFiles.tar updatefile

{% endhighlight %}


# Monitoring Archive

You can also view all the files for the archive before extracting. For that, use `-t` option. Sytntax <span style="color:#bb1919">*'tar -tvf  Archive-file-name.tar'*</span>

**Example**

{% highlight ruby %}

[alon@localhost ~]$ tar -tvf myFiles.tar
drwxr-xr-x alon/alon         0 2019-10-19 15:28 home/alon/Documents/
-rw-r--r-- alon/alon      2268 2019-10-19 15:27 home/alon/Documents/passwd
-rw-rw-r-- alon/alon         0 2019-10-19 15:27 home/alon/Documents/newfile
-rw-rw-r-- alon/alon    235520 2019-10-19 15:27 home/alon/Documents/oktest.tar
-rw-rw-r-- alon/alon     27291 2019-10-19 15:27 home/alon/Documents/oktest.tar.bz2
-rw-rw-r-- alon/alon         0 2019-10-19 15:27 home/alon/Documents/linkedfile
-rw-r--r-- alon/alon         0 2019-10-19 15:28 home/alon/Documents/hosts
-rw-r--r-- root/root         0 2019-10-05 21:29 etc/hosts

{% endhighlight %}

{% include tip.html content= "It's good practice to monitor your archive before extracting it." %}

# Extracting Archive
Now its time to extract the content of the archive. For that, use `-x` option. Syntax  <span style="color:#bb1919">*'tar -xvf Archive-file-name.tar'*</span>

**Example:**

{% highlight ruby %}

[alon@localhost ~]$ tar -xvf myFiles.tar
home/alon/Documents/
home/alon/Documents/passwd
home/alon/Documents/newfile
home/alon/Documents/oktest.tar
home/alon/Documents/oktest.tar.bz2
home/alon/Documents/linkedfile
home/alon/Documents/hosts
etc/hosts


{% endhighlight %}

The above command extracts the content of archive in the current directory. To specify your target directory where you want to extract the the file use `-C` option. Syntax <span style="color:#bb1919">*'tar -xvf Archive-file-name.tar -C /your-path'*</span>.

**Example:**

{% highlight ruby %}

[alon@localhost ~]$ tar -xvf myFiles.tar -C /tmp/
home/alon/Documents/
home/alon/Documents/passwd
home/alon/Documents/newfile
home/alon/Documents/oktest.tar
home/alon/Documents/oktest.tar.bz2
home/alon/Documents/linkedfile
home/alon/Documents/hosts
etc/hosts

{% endhighlight %}

# Using Compression in Archive
Using compression utility in archive allows you to make files that take less disk space by removing the redundancy. In the above example, none of the archive were compressed with a single byte. For compression archive, it had to be compressed with separate utility such as [gzip](https://www.gzip.org/){:target="_blank"}{:rel="nofollow"} or [bzip2](https://en.wikipedia.org/wiki/Bzip2){:target="_blank"}{:rel="nofollow"}. 

You can compress the <span style="color:#bb1919">*'Archive-file-name.tar'*</span> file using `gzip` command which generates <span style="color:#bb1919">*'Archive-file-name.tar.gz'*</span>. For alternative of using `gzip`, we can use `bzip2` utility which uses more efficient encryption algorithm.

For compression, simply include `-z` option for `gzip` or `-j` option for `bzip2`.

**Example for tar.gz**

{% highlight ruby %}

[alon@localhost ~]$ tar -czvf myFiles.tar.gz myFiles.tar

{% endhighlight %}

**Example for tar.b2z**

{% highlight ruby %}

[alon@localhost ~]$ tar -cjvf myFiles.tar.bz2 myFiles.tar

{% endhighlight %}

**Example for tar vs tar.gz vs tar.bz2**

{% highlight ruby %}

[alon@localhost ~]$ du -sh myFiles.tar
272K    myFiles.tar
[alon@localhost ~]$ du -sh myFiles.tar.gz
88K     myFiles.tar.gz
[alon@localhost ~]$ du -sh myFiles.tar.bz2
64K     myFiles.tar.bz2

{% endhighlight %}

The below table gives you an overview of the significant options used in tar.

|Options  |Use  |
|---|---|
| c  | Creates an archive. |
| v  | Shows verbose output while tar is working |
| f  |   Used to specify the name of the tar archive that is to be used. Without using this option, the default destination is STDIN for  -x  and STDOUT for  -c .     |
|   t  | Shows the contents of an archive |
|   z  | Compresses/decompresses the archive while creating it, by using gzip |
|   j  | Compresses/decompresses the archive by using bzip2 |
|   x  | Extracts an archive. |
|   u  | Updates an archive; only newer files will be written to the archive |
|   C  |  Changes the working directory before performing the command.  |
|   r  |  Appends files to an archive. |

{% include summaryCallout.html heading= "Summary" content= "In this articel, you learned how to manage and work with Linux file management tools. Please feel free to write me if need any help." %}

> **Reference**
>  > Red Hat® RHCSA™/RHCE® 7 Cert Guide: Red Hat Enterprise Linux 7 (EX200 and EX300) Sander van Vugt.