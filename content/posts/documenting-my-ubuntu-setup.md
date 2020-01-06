---
title: "My Ubuntu Setup"
date: 2019-12-24T10:19:14-05:00
draft: false
---

> This post is a work in progress.

I switched from Windows to Ubuntu as my daily driver a couple months ago. It's been great fun and a great learning experience. At this point, I've customized it so much that I figured I should create a knowledge dump for reference when starting from scratch.

## Desktop Environment and Window Manager

I use i3 on top of Xfce. There's overlap, but they serve different purposes for me:

* Xfce provides the basics out of the box: plug-and-play monitor configuration, changing your speaker volume, etc. Without a desktop environment like Xfce, you'd have to find and integrate packages into i3 to do those things.
* i3 provides a tiling window manager. A tiling WM, I feel, helps you manage windows more efficiently and creatively.
    * Example: i3 lets you create a group of tiled windows and easily move them together. Let's say you need to do some work in a document that's supported by work you're doing in a spreadsheet. You also have a couple of PowerShell Core windows open to run related commands. In i3, you can create a container in which those windows are tiled next to each other. Then you can move that container around&mdash;beside other windows, as a tab, etc. It's great.

1. Install an Ubuntu distro. I chose Xubuntu since I like Xfce.
1. Install `feh`. (More documentation needed here.)
1. Install `i3-gaps-wm`.
        
       sudo add-apt-repository ppa:kgilmer/speed-ricer
       sudo apt-get update
       sudo apt install i3-gaps-wm

1. Install `polybar`. (More documentation needed here.)
1. Install `rofi`.
1. Create an i3 config file (if `i3-gaps-wm` doesn't create one automatically; I can't recall).
    1. Grab a good-looking `~/.config/i3/config` from somewhere online. (I really need to create a Git repo of my own dotfiles.)
    1. In the config:
        1. Launch polybar.
        1. Bind rofi to a keyboard shortcut. I use <kbd>Super</kbd>+<kbd>Space</kbd>.
1. Install `compton`. (I'm not sure if the version specified below is still necessary, but that's the way I got it working on Ubuntu 18.04.3. I think the PPA above has a different version that was incompatible with my Ubuntu version.)

       sudo apt install compton=0.1~beta2+20150922-1

1. Install a nice GTK theme like Layan Dark: https://www.gnome-look.org/p/1309214/
1. Disable Xfce's desktop, window manager, and panel. The substeps are based on this guide: https://feeblenerd.blogspot.com/2015/11/pretty-i3-with-xfce.html
    1. Stop the Xfce window manager and desktop processes from auto-starting.
        1. Run *Session and Startup*.
        1. Go to the *Session* tab.
        1. For `xfwm4`, `xfce4-panel`, and `xfdesktop`, change *Restart Style* to `Never`.
        1. Press *Save Session*.
    1. Auto-start i3.
        1. Go to the *Application Autostart* tab.
        1. Press *Add*.
        1. Set the *Name*, *Description*, and *Command* to `i3`.
        1. Press *OK*.
        1. Press *Close*.
    1. Remove Xfce's default keyboard shortcuts (whichever ones get in your way).
        1. Run *Keyboard*.
        1. Select the *Application Shortcuts* tab.
        1. Remove whatever you don't want. (You can define keyboard shortcuts in i3's config file, so it may be better just to put whatever shortcuts you want there.)

## Applications

1. Install LibreOffice.  (More documentation needed here.)
1. Install `taskwarrior`:

       sudo apt install taskwarrior
1. Install `pass`:

       sudo apt install pass