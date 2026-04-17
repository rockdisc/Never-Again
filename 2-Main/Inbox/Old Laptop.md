---
Area: []
Category: []
Topic: []
aliases: []
Status: Needs Sorting
tags:
  - Personization
---

#Personization 

# 0 Overview
This is for an old ThinkPad T420 that I may be getting, it will most likely only stay with me for a year before I return it again, but that is enough time to have some fun with it. My use case for it is to make it only do work, maybe use it for a storage option, but that is a hard if. What I will do with this is a lot of writing, maybe some coding, but only small scale for individual tasks or learning. I want to run Arch + Hyprland.
I ended up getting an old HP 2000 Notebook, which cannot run arch, so I will be trying debian. 
# 1 Setting Up 
Well first I need to get arch installed. I will be using the arch install script, I am not that good at this thing yet. After I somehow get that and hyprland working, I need to install rofi to navigate my apps, I have been using walker, but I think this can work just as well. Also get waybar and set it up, I can honestly just use the one I currently have as it is very minimal, but I can make a different one as well. 
Afterwards is my programs, I do not want a lot. Each one should be necessary for my work and not be distracting, or at least high friction to prevent distractions.

| Type                | Name                                    | Desc                                                                                                                                                                                                                                                                                                      |
| ------------------- | --------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Browser             | Qutebroswer or Firefox                  | Keyboard focused, light-weight browser that I will have to lean keybindings on to do anything, I will probably figure out enough to have it themed and that is it. I really only need it for Wikipedia and ChatGPT.                                                                                       |
| Terminal            | Kitty                                   | Generic and good, allows for pictures                                                                                                                                                                                                                                                                     |
| File Browser        | Dolphin                                 | Generic and I want to learn it, might move to Yazi later though.                                                                                                                                                                                                                                          |
| Text Editor         | Nvim                                    | Who doesn't like Nvim? I will most likely just go with Lazy vim.                                                                                                                                                                                                                                          |
| Notes               | Obsidian                                | No shit, though I may have to change the configuration a lot as I do not think my current setup will work on that laptop, time to learn how git ignore works.                                                                                                                                             |
| Music               | mpd+ncmpcpp or spicetify                | I think this is a terminal based music player, if this is too complex or I just realize that I need to have more than just what I have downloaded for music I will use spicetify. It is fine, but it breaks every now and again and I do not want that. If all else fails there is still a CLI i can use. |
| Podcasts/Audiobooks | Gpodder or Newsboat                     | Just something that uses RSS feeds to get my podcasts without adds.                                                                                                                                                                                                                                       |
| File Transfer       | Local send or SSH                       | I want to learn SSH though some things are easier to send through a GUI                                                                                                                                                                                                                                   |
| Notifications       | Mako or something else                  | Notifications                                                                                                                                                                                                                                                                                             |
| Battery             | Powerprofile or some debian alternative | Different power settings                                                                                                                                                                                                                                                                                  |
| macros              | dmenu                                   | It can do some cool stuff I want to try, though I may even replace rofi with this                                                                                                                                                                                                                         |
This is honestly all I should need for everything I want on this system, but you and I both know we are not done. 

# 2 Ricing 
I am going to call it "An Impression of Debian" and it will be based on impressionism. Here are the wallpapers I am thinking about:
![[Arthur_Streeton_-_Golden_summer,_Eaglemont_-_Google_Art_Project.jpg|500]]

![[Camille_Pissarro_-_Boulevard_Montmartre_-_Eremitage.jpg|500]]

![[Claude_Monet,_Impression,_soleil_levant.jpg|500]]

![[The_Fighting_Temeraire,_JMW_Turner,_National_Gallery.jpg|500]]

Even though these all look different, the accent color should stay the same. A brownish orange. There can be some apps that use a blueish color to contrast with is, but the system theme should be orange. Might get aether to get that to work. 

# 2 Home Server 
A lot of things have changed, I am running Debian on it and there is really no need for the laptop as I realized that writing on it is a painful experience and I would rather just SSH into it which beats the whole purpose. So instead I am going to make it into a home server. Here are my goals for it:
- Run pi-hole to block ads on devices of my choosing 
- Make it always running 
- Make it appear as a network on my laptop that I can send things to very easily 
- Have a way to store my data on it like music and play them from my other machines 
- Run docker on it for other things 
- Back up all of my notes onto it just in case 
Honestly not that hard, but it might still be a challenge knowing me. 
## 2.1 Steps 
1. I am going to need to download docker, should be easy to do and set up be who knows.
2. Figure out how to make it always on, even if it is shut and its display is off. Make it not log out as well. 
3. Download pi-hole on it and configure it so that it works 
4. On my other devices get pi-hole to work 
5. Figure out whatever I need to do to make it show as a network and do it and get it to work 
6. Back up my notes and music to get it on there 
7. Find a docker music player that I can use with the music there. 

Maybe try syncthing, it seems very easy to do. 

## 2.2 What I Actually Have 
I did some tinkering and I got to so that it will always stay on, and right now I am pretty sure that it will only cost me 10 cents a month though I am not too sure on that number. I got it using ssh to make it a server that can connect to the laptop in the file browser. The thing is: sftp://user@192.168.1.10

I also have pi hole in there as well, to access it, it is: http://192.168.1.10/admin/ and the password is scribe. 

to get to ssh it is ssh scribe@192.168.1.10 
I just made a command to make it do that, just run connect in your terminal. 

I also set up QBitTorrent, username is admin password is scribe at http://192.168.1.10:8080 
and the rest of the arr stack follow this: 
- Prowlarr at http://192.168.1.10:9696 
- Sonarr at http://192.168.1.10:8989 
- Radarr at http://192.168.1.10:7878
- Lidar at http://192.168.1.10:8686

And there is Jellyfin, which finally gave a name to the server, Pleroma, and that also shares the same username and login at http://192.168.1.10:8096

Tailscale at https://login.tailscale.com/admin/machines 
