---
layout: post
title: "Using Vim Editor In Linux Tutorial With Command"
categories: [linux]
image: vim-editor-tutorial-linux-command-example/1.png
tags:
- linux
- ubuntu
- centos
- text-editor
- vi
- vim
- command
- tutorials
description: "Vim is an improved version of the vi editor. Vi which stands for Visual Interface. This tutorial provides you how to use vim with its command and examples."
---
Editing files is the most frequent job done by the system admin on [Linux](https://stechalon.com/category/linux){:target="_blank"}. Most of the configuration of Linux is done through files. So, managing a Linux server often means working with the [files on Linux](https://stechalon.com/linux-file-system-explained){:target="_blank"}. 

The important advantages of using files for config on Linux is that they can be moved or share between the system without any changes and also can be edit with a variety of text editors available.

> **Table Of Content**

* TOC
{:toc}

# Introduction
**vi**([visual interface](https://www.vim.org/){:target="_blank"}{:rel="nofollow"}) is one of the oldest and widely used text editors among the other text editors. Even some other text editors are easier to use, vi is only the text editor which will be in the continuous update and available. This is the main reason why every Linux user should know about vi text editor.

**Vim** is an improved version of the vi editor. Vim is highly configured and upgraded with many features such as:
* Screen Editing
* Syntax Highlighting
* Colour Formatting
* Spell Checking
* Scripting Multiple Languages

Vim uses important modes like <span style="color:#bb1919">*command mode*</span>, <span style="color:#bb1919">*visual mode*</span>, and <span style="color:#bb1919">*input mode*</span>. 

In Command Mode user can just enter the command and cannot change the content of the file. Input Mode allows the user to change the content of the file. The user first opens the Vim enters the command mode and using `i` keystroke enters the insert mode and `v` for Visual Mode.

# Basic Workflow of Vim
Working with all the commands of vim is not easy. Just use a minimal set of commands and use them often for remembrance. The below example shows you the minimum keystrokes that every vim user must know.

## Installing Vim
By default `vi` is installed in your system. For using upgrade version you need to install `vim` manually.

**Installing In Ubuntu**
{% highlight ruby %}

[alon@localhost ~]$ sudo apt install vim -y

{% endhighlight %}
**Installing In CentOS**
{% highlight ruby %}

[alon@localhost ~]$ sudo yum install vim -y

{% endhighlight %}



## Opening Files
Using vim command to open hosts file.   

{% highlight ruby %}
[alon@localhost ~]$ vim /etc/hosts
{% endhighlight %}

{% include note.html content= "When you try to open files in vim that does not exist, but the path is available, vim will inform you that you are editing a new file, and create the file when you save it." %}

Now, vim will open the hosts file and start with command mode . You will find the information about the file in the bottom  left as (filename, number of lines, number of character) and bottom right current cursor position(line, character) and what part of file is displayed (ALL for all, Top for the first lines of file, Bot for bottom of a file or % to indicate where in the file you are).

{% highlight ruby %}
127.0.0.1   localhost localhost.localdomain localhost4 localhost4.localdomain4
::1         localhost localhost.localdomain localhost6 localhost6.localdomain6
~
~
~
~
~
"/etc/hosts" [readonly] 2L, 158C                              1,1           All
{% endhighlight %}

## Editing Files
For editing the file, first switch from command mode to insert mode, You can use below command table for switching to insert mode.

|Command  | Explanation  |
|---|---|
| i |  Switches to insert mode. Start inserting before the current cursor position. |
| a |  Switches to insert mode. Start inserting after the current cursor position.  |
| I |    Move the cursor to the start of the line and switch to insert mode.  |
|  A  |  Move the cursor to the end of the line and switch to insert mode.  |
| R  |  Switch to replace mode. Here text is not inserted, but the character of the file is replaced with the character you enter. |
| o | Open a new line below the current one, and switch to insert mode. |
|   O  |  Open a new line above the current one, and switch to insert mode. |

<br>
The below example shows editing a file by inserting 127.0.0.0      mylocalhost.com.

{% highlight ruby %}

127.0.0.1   localhost localhost.localdomain localhost4 localhost4.localdomain4
::1         localhost localhost.localdomain localhost6 localhost6.localdomain6
127.0.0.1   mylocalhost.com
~
~
~
~
~
-- INSERT --                                                  3,28          All
{% endhighlight %}

`--INSERT--` or `--REPLACE--` indicates that you are in insert or replace mode. Press `Esc` to return back to command mode.

{% include note.html content= "Esc will always cancel the current command or returns to command mode. " %}

## Saving Files
In vim file is saved from <span style="color:#bb1919">*ex mode*</span>. For entering ex mode simply press `:` within command mode. After entering ex mode use the below command as your need.

|Command  | Explanation  |
|---|---|
| :wq |  Save and quit the file. |
| :w |  Write the file and remain in the editor.  |
| :w <filename> |    Save the file name under the different file name.  |
|  :x  |  Save the file if there are unsaved changes and quit.  |
| :q |  Quit the file. |
| :q! |  Quit the file ignoring any unsaved changes. |

<br>
The below example shows saving the file using `:wq` command and press enter.

{% highlight ruby %}

127.0.0.1   localhost localhost.localdomain localhost4 localhost4.localdomain4
::1         localhost localhost.localdomain localhost6 localhost6.localdomain6
127.0.0.1   mylocalhost.com

~
~
~
~
~
~
~
~
:wq
{% endhighlight %}

The below table shows some other useful command that allows you to work with vim more easily.

## Useful Command Used In Vim

|Command  | Explanation  |
|---|---|
|   v  |   Enters in visual mode. This allows you to select a block of text using the arrow keys. Use  d  to cut, or  y  to copy the selection. |
|   dd  |  Deletes the current line |
|   yy  |  Copies the current line |
|   p  |  Pastes the current selection.  |
|   u |   Undo the last command. |
| Ctrl+r |    Redoes the last undo |
|  gg  |   Goes to the first line in the document |
| G | Goes to the last line in the document. |
| /key |  Searches for the text key  from the current cursor position forward. |
| ?key |  Searches for  text key  from the current cursor position backward |
| ^ |  Goes to the first position in the current line. |
| $ |  Goes to the last position in the current line. |
| !ls |   Adds the output of  ls  (or any other command) in the current file |
| :%s/oldKey/newKey/g  |  Replaces all occurrences of  oldKey  with  newKey .  |

<br>You can also <span style="color:#bb1919">*compress*</span> the file having large size without any [data loss](https://stechalon.com/install-systemback-restore-previous-state-ubuntu-linux){:target="_blank"} using tar command. Learn how to compress and extract files in Linux using tar command from [here](https://stechalon.com/compress-extract-tar-command-linux){:target="_blank"}.

{% include summaryCallout.html heading= "Summary" content= "In this articel, you learned the basic workflow of vim editor. How to use it? with its useful command. Please feel free to write me if need any help." %}

> **Reference**
>  > Red Hat® RHCSA™/RHCE® 7 Cert Guide: Red Hat Enterprise Linux 7 (EX200 and EX300) Sander van Vugt.