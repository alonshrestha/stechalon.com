---
layout: post
title:  "Create Your Own (CS:GO) Counter-Strike Dedicated Server"
heading: "How To Create Personal Custom (CS:GO) Counter-Strike: Global Offensive Dedicated Linux Server (Ubuntu/CentOS)"
image: how-to-create-your-own-csgo-counter-strike-global-offensive-dedicated-custom-server-ubuntu-centos/main.webp
categories: [linux, gaming]
tags: 
- CS:GO
- Counter-Strkie:Global Offencive
- Persoanl Custom Server
- Dedicated Server
- Ubuntu
- CentOS
description: "How to create your own personal custom dedicated counter-strike: global offensive (cs:go) server on Linux ubuntu and centos."
--- 
Ready for gaming? Yeah! haha &#128526;. Playing games with your friends on a personal server at lower than 5 pings is an awesome feeling that only gamers can understand.

Over two months ago I had built my personal server for Counter-Strike: Global Offensive (CS:GO) to play with my friends. Trust me it was far more fun than expected as well as helped me to earn some money. How? I will let you know shortly.

However, if you are new to this and have no technical knowledge I will suggest you go deep in the article else you can directly jump to the [setup section](http://localhost:4000/how-to-create-your-own-csgo-counter-strike-global-offensive-dedicated-custom-server-ubuntu-centos#setup-counter-strike-global-offensive-csgo-in-ubuntucentos-server). 

Steam allows you to setup a custom server changing different settings like tick rate, number of players, base map, game rule, etc. Also, you can download and install free custom skins for your weapons. It's like you are the admin and you can change any function as you want.

Creating a custom CS:GO server on Linux is not as difficult as you think. You don't need to be from a technical background. Setup can be done easily by entering a few commands which I will be guiding you step by step. 

Before moving on to the command guide you should know the system requirements to setup custom CS:GO and the hosting provider where you can get the best server at an affordable price.

I had used the EC2 **t2.micro** server from AWS having 1 GB RAM with 40 GB disk space. This spec was enough for me to play a competitive match with my 9 other friends. 

Due to 1 GB of RAM sometimes we were facing lag in the system. So, I suggest you go with at least 2 GB of RAM.

Usually, CS:GO can be installed in 15 - 20 GB disk space but due to frequent game updates and space used by OS(Operating System), 40 GB is recommended.

## System Requirements For (CS:GO) Counter-Strike: Global Offensive Server
- RAM: 2 GB Minimum - 4 GB Maximum
- CPUs: 2 Minimum
- Disk Space: 40 GB (Recommended)
- Bandwidth: Unlimited (Recommended)
- Operating System: Linux (CentOS, Ubuntu)

***Note***: *You can use the **windows** operating system but this costs more than Linux OS.*

Now, we will need a VPS(Virtual Private Server) to deploy CS:GO. For that, I have mentioned VPS server at affordable price provided by the best hosting company.

***Important***: *For the lowest ping gameplay you must select the server located near your location or in your country. This is only the best way to get the lowest ping for game play.*

## Affordable VPS Hosting For Counter-Strike: Global Offensive (CS:GO) 
The below mention hosting price is in special offer. This offer is only available for certain period of time.

### [Hostinger: $8.95 / Month (55% OFF)](https://www.hostg.xyz/SH54u){:target='_blank'}{:rel='nofollow'}
- RAM: 2 GB
- Disk Space: 40 GB
- Bandwidth: 2 TB
- 30 days money back gurantee.
- [Visit site](https://www.hostg.xyz/SH54u){:target='_blank'}{:rel='nofollow'}

If you find the above server expensive then, remember this server will be up and running 24x7. When you are not using this server then someone else can.

This means you can rent this gaming server at a rate per hour to others who are searching for a personal server for tournaments. This is the best way you can cover up the hosting money and earn some extra.

Select Linux operating systems such as Ubuntu or CentOS. This article will guide how to setup CS:GO on both OS.

## Setup Counter-Strike: Global Offensive (CS:GO) In Ubuntu/CentOS Server 
Login to your instance through ssh with the **root** user account. First, we need to install a library that helps steamCMD to run in the operating system. 

### Installing Library In Ubuntu

**Step 1**: Install lib32gcc1 package in the ubuntu server.

{%highlight ruby%}
sudo apt-get install lib32gcc1
{%endhighlight%}

### Installing Library In CentOS

**Step 1**: Install the required library to run SteamCMD in centOS.

{%highlight ruby%}
yum install glibc.i686 libstdc++.i686 -y
{%endhighlight%}

**Step 2**: It is better to create a new user for installing CS:GO. We will create a new user *“steam”*. For that type:

{%highlight ruby%}
sudo useradd -m steam
{%endhighlight%}

Switch user to *"steam"*

{%highlight ruby%}
su - steam 
{%endhighlight%}

**Step 3**:Create an installation path directory where we download SteamCMD.
{%highlight ruby%}
mkdir ~ / Steam && cd ~ / Steam
{%endhighlight%}

Downloading and Installing SteamCMD.

**Step 4**: Download the latest version of SteamCMD.
{%highlight ruby%}
wget https://steamcdn-a.akamaihd.net/client/installer/steamcmd_linux.tar.gz
{%endhighlight%}

**Step 5**: Unzip the downloaded file.
{%highlight ruby%}
tar xf steamcmd_linux.tar.gz
{%endhighlight%}

**Step 6**: Run the SteamCMD file by typing:
{%highlight ruby%}
./steamcmd.sh
{%endhighlight%}

This command will download the update from steam which seems like this.

![Downloading and Installing SteamCMD In Linux | sTechalon.com](/static/img/posts/how-to-create-your-own-csgo-counter-strike-global-offensive-dedicated-custom-server-ubuntu-centos/1.PNG)
After downloading the updated steam will provide you the cmd prompt as shown below. 

{%highlight ruby%}
Steam>
{%endhighlight%}

**Step 7**: Login using a steam account here.
{%highlight ruby%}
Steam> login <userID> <password>
{%endhighlight%}

Replace your userID and password with your steam credential.

You can also use an anonymous login. I prefer you to use this.

{%highlight ruby%}
Steam> login anonymous
{%endhighlight%}

**Step 8**: Now, we are ready to install CS:GO in a dedicated folder.
{%highlight ruby%}
force_install_dir ./cs_go/
{%endhighlight%}

**Step 9**: Finally download and install CS:GO files from the server.
{%highlight ruby%}
app_update 740 validate
{%endhighlight%}

This process takes some time to complete. If everything was done correctly in the process your installation will complete successfully as shown below. 

![Downloading and Installing SteamCMD In Linux | sTechalon.com](/static/img/posts/how-to-create-your-own-csgo-counter-strike-global-offensive-dedicated-custom-server-ubuntu-centos/3.PNG)<br>
We need to open TCP and UDP firewalls from the game server so that players can join and play through these protocols. This can be done by configuring a network security group.

This is optional if your server does not have a firewall and accepts all protocols or the firewall is in stopped status. But make sure you look into this.

### Configure TCP and UDP Firewalls
Allow TCP and UDP ports from your server. It is better to allow specific ports, for example 27015/tcp and 27015/udp or you can open all the ports. Follow the below picture.

![Downloading and Installing SteamCMD In Linux | sTechalon.com](/static/img/posts/how-to-create-your-own-csgo-counter-strike-global-offensive-dedicated-custom-server-ubuntu-centos/4.PNG)
You can also do this from the command line in your server by typing:
### CentOS
{%highlight ruby%}
firewall-cmd --zone=public --add-port=27015/tcp --permanent
firewall-cmd --zone=public --add-port=27015/udp --permanent
firewall-cmd --reload
{%endhighlight%}

If you are unable to do these, I will suggest you coordinate with your hosting provider. They will make it done for you.

## Register Counter-Strike:Global Offensive (CS:GO) Game Auth Token
To start a game you need your steam token ID. Without a token ID, you won’t be able to host a game. 

Generating token ID needs some requirements to be qualified by your steam account. Check [here](https://steamcommunity.com/dev/managegameservers){:target='_blank'}{:rel='nofollow'} for the requirements and get your token ID.

Follow this picture to generate your auth token ID.

![Downloading and Installing SteamCMD In Linux | sTechalon.com](/static/img/posts/how-to-create-your-own-csgo-counter-strike-global-offensive-dedicated-custom-server-ubuntu-centos/5.PNG)
The [appID 740](https://steamdb.info/app/740/){:target='_blank'}{:rel='nofollow'} used while installing CS:GO is the registered ID for Counter-Strike: Global Offensive dedicated server. And the [appID 730](https://steamdb.info/app/730/){:target='_blank'}{:rel='nofollow'} is the official game ID. 

You will generate a token ID similar to this **X38F6E71A3B8G6FE08354AF5BE078**.

## Host Counter-Strike:Global Offensive (CS:GO) Server
There are specific commands to run different desired game modes. This means you have to hit different commands to run **Causal** Mode, **Competitive** Mode, and **Death Match** Mode. 
The command seems to be like this: 

{%highlight ruby%}
./srcds_run -game csgo -console -usercon + game_type 0 + game_mode 0 + mapgroup mg_active + map de_dust2 + sv_setsteamaccount X38F6E71E4FA3B8G6FE08354AF5BE078 THISGSLTHERE -net_port_try
{%endhighlight%}
For different game modes, we will change the game_mode value. 

**Example:**

*game_mode 0 = Casual*

*game_mode 1 = Competitive*

*game_mode 2 = Death Match*

Always remember to be in **cs_go** directory before you run the command. If you get confused then see the highlighted image below and follow the command.

![Downloading and Installing SteamCMD In Linux | sTechalon.com](/static/img/posts/how-to-create-your-own-csgo-counter-strike-global-offensive-dedicated-custom-server-ubuntu-centos/6.PNG)
Change the directory to cs_go
{%highlight ruby%}
cd cs_go
{%endhighlight%}
And, do not forget to replace ***“YOUR AUTH TOKEN”*** in the below command.

### CASUAL GAME MODE
{%highlight ruby%}
./srcds_run -game csgo -console -usercon + game_type 0 + game_mode 0 + mapgroup mg_active + map de_dust2 + sv_setsteamaccount “YOUR AUTH TOKEN” THISGSLTHERE -net_port_try
{%endhighlight%}

### COMPETITIVE GAME MODE
{%highlight ruby%}
./srcds_run -game csgo -console -usercon + game_type 0 + game_mode 1 + mapgroup mg_active + map de_dust2 + sv_setsteamaccount  “YOUR AUTH TOKEN” THISGSLTHERE -net_port_try
{%endhighlight%}

### DEATHMATCH MODE 
{%highlight ruby%}
./srcds_run -game csgo -console -usercon + game_type 1 + game_mode 2 + mapgroup mg_allclassic + map de_dust + sv_setsteamaccount “YOUR AUTH TOKEN” THISGSLTHERE -net_port_try
{%endhighlight%}

After entering the above command, the game will be hosted in the server’s public IP. The terminal will provide you with the public IP. 

![Downloading and Installing SteamCMD In Linux | sTechalon.com](/static/img/posts/how-to-create-your-own-csgo-counter-strike-global-offensive-dedicated-custom-server-ubuntu-centos/7.PNG)<br>
*Note your public IP you will need this later to join the game.*

### Join Hosted Counter-Strike:Global Offensive (CS:GO) Server
Log in to your steam application and open CS:GO game.

Now there are two ways you can connect and join the server.

**First**, connect through the game console. For that enable the developer console.

![Downloading and Installing SteamCMD In Linux | sTechalon.com](/static/img/posts/how-to-create-your-own-csgo-counter-strike-global-offensive-dedicated-custom-server-ubuntu-centos/8.webp)
Come back to the dashboard and open the console using *“ **~** ”* keyword and type *“**connect < your-ip-address >**”*.

![Downloading and Installing SteamCMD In Linux | sTechalon.com](/static/img/posts/how-to-create-your-own-csgo-counter-strike-global-offensive-dedicated-custom-server-ubuntu-centos/9.PNG)<br>
**Second**, adding your server IP address to your favorite list. For that go to *Community Server Browser*.

![Downloading and Installing SteamCMD In Linux | sTechalon.com](/static/img/posts/how-to-create-your-own-csgo-counter-strike-global-offensive-dedicated-custom-server-ubuntu-centos/10.webp)<br>
Click on favourite tab.

![Downloading and Installing SteamCMD In Linux | sTechalon.com](/static/img/posts/how-to-create-your-own-csgo-counter-strike-global-offensive-dedicated-custom-server-ubuntu-centos/11.PNG)<br>
Add your server IP and connect it. 
![Downloading and Installing SteamCMD In Linux | sTechalon.com](/static/img/posts/how-to-create-your-own-csgo-counter-strike-global-offensive-dedicated-custom-server-ubuntu-centos/12.PNG)<br>

## Run Counter-Strike:Global Offensive (CS:GO) Server In Background
Usually, when you run the command and host the game in a normal session, your game will be disconnected or stopped when you log out from the server.

And, It is not possible to host your game by staying logged in 24x7 on the server. So, we will host the game in a background session. This process will run your game ever until you kill that process by yourself. 

For that, we will install a screen utility on the server.
### Install Screen In Ubuntu
{%highlight ruby%}
sudo apt-get install screen -y
{%endhighlight%}

### Install Screen In CentOS
{%highlight ruby%}
sudo yum install screen -y
{%endhighlight%}

After finished installation, again remember to be in the cs_go directory always before you run the command.

Create a new session named csgo by typing: 
{%highlight ruby%}
screen -R csgo
{%endhighlight%}

Now run the game host command. In my case, I am running competitive game mode.

{%highlight ruby%}
./srcds_run -game csgo -console -usercon + game_type 0 + game_mode 1 + mapgroup mg_active + map de_dust2 + sv_setsteamaccount  “YOUR AUTH TOKEN” THISGSLTHERE -net_port_try
{%endhighlight%}

When the game is hosted successfully, exit from that screen(detach) by hitting the below command at the same time.

{%highlight ruby%}
crtl + a + d 
{%endhighlight%}

Now you are out of that session. To see the running background session type

{%highlight ruby%}
screen -ls
{%endhighlight%}

You will get the output like this:

{%highlight ruby%}
There is a screen on:
    7166.csgo    (Detached)
1 Socket in /run/screen/S-stechalon.
{%endhighlight%}

**7166** is the ID and **csgo** is the name of the screen. 

To rejoin the detached screen type:

{%highlight ruby%}
screen -r 7166
{%endhighlight%}

These commands tutorial is enough to host the game in a background session. To know more tricks about screen command check my post on [how to use screen command with its example](https://stechalon.com/using-screen-command-linux){:target='_blank'}. 

## Change Counter-Strike(CS:GO) Server Configuration File

In this section, you will learn to change your server hostname and password. This allows you to make your server private and professional. 

Edit **autoexec.cfg** file and add your hostname and password that you want. Type:

{%highlight ruby%} 
vim csgo-ds/csgo/cfg/autoexec.cfg
{%endhighlight%}

Follow the below picture instructions.

![Downloading and Installing SteamCMD In Linux | sTechalon.com](/static/img/posts/how-to-create-your-own-csgo-counter-strike-global-offensive-dedicated-custom-server-ubuntu-centos/13.PNG)<br>
To save this file press *“esc”* and *“ :wq!”* 

Refresh your favorite list and check the Hostname. You will see the changes as mine as shown below.

![Downloading and Installing SteamCMD In Linux | sTechalon.com](/static/img/posts/how-to-create-your-own-csgo-counter-strike-global-offensive-dedicated-custom-server-ubuntu-centos/14.PNG)<br>
You can customize your game with different variables. To know more about this visit  CS:GO advanced configuration article. I am sure this article will help you a lot to create a custom game mode.

## Change Counter-Strike:Global Offensive (CS:GO) Tick Rate
Tick rate collects the information of incoming player data and events which help to calculate the performance of the game and send data to players. This might be helpful for the player in better game mode. You can get more knowledge about the tick rates [here](https://win.gg/news/4379/explaining-tick-rates-in-fps-games-difference-between-64-and-128-tick){:targer="_blank"}{:rel="nofollow"}. 

It is easy to change the tick rate of your game. Simply, add some command in the autoexec.cfg file.

Open the file
{%highlight ruby%}
vim csgo/cfg/autoexec.cfg
{%endhighlight%}

And add the following command.
{%highlight ruby%}
sv_minupdaterate 128
sv_mincmdrate 128
{%endhighlight%}

Save and quit pressing  *“esc”* and *“ :wq!”*. 

## Conclusion
We have come at the end of this article. I hope you have setup your own personal server and will enjoy it with your friends playing CS:GO or renting it out.

There are some important things that you should know for maintaining your dedicated server.

### How To Update CS:GO On The Dedicated Server 
Usually, CS:GO provides updates every week or in a month. In this case, your game won't be hosted without updating it on the server. To update the game run the command from above **steps** 6 to 9.

### Create Backup Image Of Server
This is very important. You never know what is going to be next so to be on the safe side, always take a backup image of your VPS server. So, whenever your server gets crashed you can re-lunch the server from the backup images.

This helped me a lot while changing the configuration of the game. Even though I crash the system I was able to re-launch the system  

### Low Ping Solution
As I have already mentioned above, the only best way to get the lowest ping is to select the game hosting server located in near you or your country. Try to get a server from a well-known hosting provider.

You can also use a different VPN and select the country where the game is hosted to reduce the ping level.

Well, I have tried my best to cover the topic on how to setup your own CS:GO dedicated server in Linux in this article. If there are any queries you have please let me know in the comment section below. 

GG Guys &#129304;.

**Disclaimer**:
- *Some links used in this article are affiliated. This means if you do certain actions through that link I might earn some commission.*
- *The hosting server price mentioned upon offer might be changed.*
