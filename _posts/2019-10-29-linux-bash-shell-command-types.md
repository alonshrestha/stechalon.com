---
layout: post
title: "Different Types Of Linux Bash Shell Command"
categories: [linux]
image: linux-bash-shell-command-types/1.png
tags:
- Linux
- Ubuntu
- CentOS
- Bash
- Shell
- Command
- Types
description: "There are three types of command in Linux bash shell Aliases, Internal Command, and External Command. Know its work and how to use it."
---

![Different Types Of Linux Bash Shell Command | sTechalon.com](/static/img/posts/linux-bash-shell-command-types/1.png)<br><br>
There are three kind of command found on [Linux Bash Shell (Bourne Again Shell)](https://en.wikipedia.org/wiki/Bash_(Unix_shell)){:target="_blank"}{:rel="nofollow"}. 

* Aliases
* Internal Command
* External Command

# Aliases
This kind of commands are set or created by user by themself as per their need. Some aliases are provided by default on [Linux](https://stechalon.com/category/linux){:target="_blank"}.  You can find the overview of command `alias` in your shell by typing alias.

{% highlight ruby %}

[alon@localhost ~]$ alias
alias egrep='egrep --color=auto'
alias fgrep='fgrep --color=auto'
alias grep='grep --color=auto'
alias l.='ls -d .* --color=auto'
alias ll='ls -l --color=auto'
alias ls='ls --color=auto'
alias which='alias | /usr/bin/which --tty-only --read-alias --show-dot --show-tilde'


{% endhighlight %}

For creating your own aliases, follow this syntax  <span style="color:#bb1919">*'alias yourCommand'*</span> = <span style="color:#bb1919">*'commandYouWantToReplace'*</span>.

**Example**
{%highlight ruby%}
[alon@localhost ~]$ alias move=mv
[alon@localhost ~]$ move testFile /tmp/
[alon@localhost ~]$ alias mv=move
{%endhighlight%}

# Internal Command
This type of command is the part of the system which is already loaded in the system. They are independent and can be executed at any time from the memory. Execution of this command is assumed to be fast because of the shell builtin. 

Some of the examples of this types of command are `cd`, `source`, `history`, `help`, `kill` etc. To see the list of  the builtin command type `help` in your shell. 

{%highlight ruby%}
[alon@localhost ~]$ help
{%endhighlight%}
# External Command
These commands are not built into the shell. For executing the external command shell, it needs to look for the <span style="color:#bb1919">*'$PATH Variable'*</span> of the command. While executing the external command new process has to be release. These commands take more time to execute compared to internal command. Example of external command are `cat` , `mv` , `cp`, `less` etc.

{% include tip.html content= "You can find out whether a command is internal or external by `type` command. Eg: type cat " %}

**Example**
{%highlight ruby%}
[alon@localhost ~]$ type cat
{%endhighlight%}

{% include summaryCallout.html heading= "Summary" content= "In this article, you learned about the different types of command on Linux bash shell and its use. Please feel free to write me if need any help." %}