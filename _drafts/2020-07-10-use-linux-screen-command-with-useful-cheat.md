---
id: 593
title: Using Linux Screen With Cheat Sheet
date: 2020-07-10T11:15:59+00:00
author: alonshrestha
excerpt: 'Screen command on Linux is a useful utility for those people who work on multiple screens using SSH sessions. Use Linux screen command with useful cheat. '
layout: post
guid: https://stechalon.com/?p=593
permalink: /use-linux-screen-command-with-useful-cheat/
site-sidebar-layout:
  - default
site-content-layout:
  - default
theme-transparent-header-meta:
  - default
image: /wp-content/uploads/2020/07/day.png
categories:
  - Linux
---
Screen command on <a aria-label="undefined (opens in a new tab)" href="https://stechalon.com/category/linux/" target="_blank" rel="noreferrer noopener">Linux</a> is a useful utility for those people who work on multiple screens using <a href="https://www.ssh.com/ssh/" target="_blank" aria-label="undefined (opens in a new tab)" rel="noreferrer noopener">SSH</a> sessions. This command allows you to open multiple sessions in a terminal even if you are not in a graphical session. This also allows you to share a session with other users or to attach and detach to a remote terminal session. Screen command on <a aria-label="undefined (opens in a new tab)" href="https://stechalon.com/linux-file-system-explained/" target="_blank" rel="noreferrer noopener">Linux</a> is used when you need to perform a long-running task on a remote machine.

## Installing Screen {#0-installing-screen}

### **Debian based system** {#1-debian-based-system-}

<pre class="wp-block-code"><code>&#91;stechalon@localhost ~]$ sudo apt-get install screen</code></pre>

### **RedHat based system** {#2-redhat-based-system-}

<pre class="wp-block-code"><code>&#91;stechalon@localhost ~]$ sudo yum install screen</code></pre>

After completing installation check its version by typing `'screen -v'`

<pre class="wp-block-code"><code>&#91;stechalon@localhost ~]$  screen -v
Screen version 4.01.00devel (GNU) 2-May-06</code></pre>

<div class="ub_table-of-contents" data-showtext="show" data-hidetext="hide" id="ub_table-of-contents-7aab8fe4-a181-4883-a6ac-efbc911112e3">
  <div class="ub_table-of-contents-container ub_table-of-contents-1-column ">
    <ul>
      <li>
        <a href=https://stechalon.com/use-linux-screen-command-with-useful-cheat/#0-installing-screen>Installing Screen</a><ul>
          <li>
            <a href=https://stechalon.com/use-linux-screen-command-with-useful-cheat/#1-debian-based-system->Debian based system</a>
          </li>
          <li>
            <a href=https://stechalon.com/use-linux-screen-command-with-useful-cheat/#2-redhat-based-system->RedHat based system</a>
          </li>
        </ul>
      </li>
      
      <li>
        <a href=https://stechalon.com/use-linux-screen-command-with-useful-cheat/#3-useful-screen-command>Useful Screen Command</a>
      </li>
      <li>
        <a href=https://stechalon.com/use-linux-screen-command-with-useful-cheat/#4-working-with-linux-screen-command>Working with Linux Screen Command</a><ul>
          <li>
            <a href=https://stechalon.com/use-linux-screen-command-with-useful-cheat/#5-starting-screen>Starting Screen</a>
          </li>
          <li>
            <a href=https://stechalon.com/use-linux-screen-command-with-useful-cheat/#6-starting-screen-with-session-name>Starting Screen with Session Name</a>
          </li>
          <li>
            <a href=https://stechalon.com/use-linux-screen-command-with-useful-cheat/#7-show-screen-parameter>Show Screen Parameter</a>
          </li>
          <li>
            <a href=https://stechalon.com/use-linux-screen-command-with-useful-cheat/#8-show-list-of-screen-running-in-background>Show List of Screen Running in Background</a>
          </li>
          <li>
            <a href=https://stechalon.com/use-linux-screen-command-with-useful-cheat/#9-detach-screen>Detach Screen</a>
          </li>
          <li>
            <a href=https://stechalon.com/use-linux-screen-command-with-useful-cheat/#10-reattach-screen>Reattach Screen</a>
          </li>
        </ul>
      </li>
    </ul>
  </div>
</div>

## Useful Screen Command {#3-useful-screen-command}<figure class="wp-block-table is-style-regular">

<table class="has-subtle-pale-blue-background-color has-background">
  <tr>
    <th>
      Wildcards
    </th>
    
    <th>
      Explanation
    </th>
  </tr>
  
  <tr>
    <td>
      Ctrl+a &#8211; c
    </td>
    
    <td>
      Create a new window
    </td>
  </tr>
  
  <tr>
    <td>
      Ctrl+a &#8211; n
    </td>
    
    <td>
      Goes to the next window
    </td>
  </tr>
  
  <tr>
    <td>
      Ctrl+a &#8211; “
    </td>
    
    <td>
      List all windows
    </td>
  </tr>
  
  <tr>
    <td>
      Ctrl+a &#8211; Ctrl+a
    </td>
    
    <td>
      Goes back to last used window
    </td>
  </tr>
  
  <tr>
    <td>
      Ctrl+a &#8211; k
    </td>
    
    <td>
      Kills the current windows
    </td>
  </tr>
  
  <tr>
    <td>
      Ctrl+a &#8211; 0,1
    </td>
    
    <td>
      Switch to window 0,1
    </td>
  </tr>
  
  <tr>
    <td>
      Ctrl+a &#8211; (Shift+\ )
    </td>
    
    <td>
      Divides region into two vertical regions
    </td>
  </tr>
  
  <tr>
    <td>
      Ctrl+a &#8211; S
    </td>
    
    <td>
      Divides region into two horizontal regions
    </td>
  </tr>
  
  <tr>
    <td>
      Ctrl+a &#8211; tab
    </td>
    
    <td>
      Change input to next region
    </td>
  </tr>
  
  <tr>
    <td>
      Ctrl+a &#8211; A
    </td>
    
    <td>
      Rename current window
    </td>
  </tr>
  
  <tr>
    <td>
      Ctrl+a &#8211; Q
    </td>
    
    <td>
      Close all region except current one
    </td>
  </tr>
  
  <tr>
    <td>
      Ctrl+a &#8211; X
    </td>
    
    <td>
      Close current region
    </td>
  </tr>
  
  <tr>
    <td>
      Ctrl+a &#8211; d
    </td>
    
    <td>
      Detach the session without sopping event
    </td>
  </tr>
  
  <tr>
    <td>
      Ctrl+a &#8211; r
    </td>
    
    <td>
      Reattach the detach session
    </td>
  </tr>
  
  <tr>
    <td>
      Ctrl+a &#8211; ]
    </td>
    
    <td>
      Reattach the detach session
    </td>
  </tr>
  
  <tr>
    <td>
      Ctrl+a &#8211; [
    </td>
    
    <td>
      Reattach the detach session
    </td>
  </tr>
</table></figure> 

## Working with Linux Screen Command {#4-working-with-linux-screen-command}

### Starting Screen {#5-starting-screen}

To star a screen type `'screen'` command.

<pre class="wp-block-code"><code>&#91;stechalon@localhost ~]$ screen</code></pre>

### Starting Screen with Session Name {#6-starting-screen-with-session-name}

To star a screen with session name type `'screen -S session_Name'` command.

<pre class="wp-block-code"><code>&#91;stechalon@localhost ~]$ screen -S top</code></pre>

### Show Screen Parameter {#7-show-screen-parameter}

Type `'Ctrl+a - ?'` to show screen parameter.

<pre class="wp-block-code"><code>                       Screen key bindings, page 1 of 2.

                       Command key:  ^A   Literal ^A:  a

  break       ^B b         license     ,            removebuf   =
  clear       C            lockscreen  ^X x         reset       Z
  colon       :            log         H            screen      ^C c
  copy        ^&#91; &#91;         login       L            select      '
  detach      ^D d         meta        a            silence     _
  digraph     ^V           monitor     M            split       S
  displays    *            next        ^@ ^N sp n   suspend     ^Z z
  dumptermcap .            number      N            time        ^T t
  fit         F            only        Q            title       A
  flow        ^F f         other       ^A           vbell       ^G
  focus       ^I           pow_break   B            version     v
  hardcopy    h            pow_detach  D            width       W
  help        ?            prev        ^H ^P p ^?   windows     ^W w
  history     { }          quit        \            wrap        ^R r
  info        i            readbuf     &lt;            writebuf    >
  kill        K k          redisplay   ^L l         xoff        ^S s
  lastmsg     ^M m         remove      X            xon         ^Q q

                  &#91;Press Space for next page; Return to end.]</code></pre>

### Show List of Screen Running in Background {#8-show-list-of-screen-running-in-background}

<pre class="wp-block-code"><code>&#91;stechalon@localhost ~]$ screen -ls
There are screens on:
        3784.top        (Attached)
        2077.pts-0.localhost    (Detached)
2 Sockets in /var/run/screen/S-alon.</code></pre>

### Detach Screen {#9-detach-screen}

Type `'screen -d ID`&#8216; so that this can be reattach in future.

<pre class="wp-block-code"><code>&#91;stechalon@localhost ~]$ screen -d 3784</code></pre>

### Reattach Screen {#10-reattach-screen}

Type `'screen -r ID`&#8216; for the screen which was previously detached.

<pre class="wp-block-code"><code>&#91;stechalon@localhost ~]$ screen -r 2077</code></pre>

<div class="ub-styled-box ub-notification-box" id="ub-styled-box-f028b728-51c0-439f-abb1-f0a8c107f367">
  <div class="ub-notification-text">
    <strong>Summary</strong> <br />In this article, you learned about screen command on Linux. Please feel free to write me if you need any help.
  </div>
</div>