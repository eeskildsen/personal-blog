---
title: "Switching From Windows to Ubuntu as My Daily Driver"
date: 2019-11-03T10:34:21-05:00
draft: false
---

About a week ago, I started using Ubuntu as my daily driver instead of Windows. This post explains why and (partially) documents my setup ... mostly to jog my memory when I forget half of what I did, but hopefully someone else considering a similar setup will benefit too.

# Why Not Windows 10?

I like Windows. PowerShell is a fantastic abstraction of .NET, and now that it's cross platform, I'll be using it on Linux too. But recent events inspired me to make a change.

1. In September 2019, Microsoft removed the "use offline account" option for Windows 10 installations if the machine has an Internet connection.
1. In October 2019, Adobe blocked Creative Cloud in Venezuela due to U.S. sanctions. Professionals in Venezuela who rely on Adobe for their livelihood were left without a paddle.
1. Also in October 2019, [a software developer on Hacker News shared plans to require an annual subscription to their desktop software](https://news.ycombinator.com/item?id=21165736) despite the fact that it was entirely on premise and didn't make server calls.

I'd already been growing increasingly frustrated with "everything-as-a-service" culture, longing for the good old days of software "ownership" (yes, software is licensed, not sold ... but perpetual licensing is closer to ownership).

Also, I've wanted to get more familiar with Linux to use it as a server for my applications.

# Window Manager Experimentation

## i3wm

I'd installed Xubuntu on my laptop long ago (dual boot) but hadn't really used it. Coming back, I started looking for ways to spruce it up. I soon found so-called rices that I liked on [r/unixporn](https://www.reddit.com/r/unixporn) using [i3wm](https://i3wm.org/). I was impressed by Linux tiling window managers in general, compared to Windows's lackluster tiling support. I liked that i3 resized the existing grid automatically and how easy workspaces were. So I installed i3wm-gaps and started playing with my dotfiles.

I was impressed by i3 (and I still am), but I quickly realized it was "bring your own everything."

* Desktop background: Install `feh` and call it in `~/.config/i3/config`.
* Volume: Add `pactl` keybindings.
* Multiple monitor support: Learn `xrandr`.

I'd bitten off more than I could chew. Remembering why I switched in the first place, I decided to go back to Xfce for the time being and possibly return to i3wm when I was more comfortable.

## Xfce

Xfce felt like coming home. The UI was familiar but felt faster than Windows had been on my machine. Plus there was no telemetry or Cortana to worry about. However, I didn't care for how it looked.

Going to back to [r/unixporn](https://www.reddit.com/r/unixporn), I hunted up some Xfce rices. [I soon found one I liked](https://www.reddit.com/r/unixporn/comments/dav66r/xfce_nordic_xfce/) and set about replicating it.

1. Theme: Nordic-standard-buttons. At first I was confused because [OP calls the theme just "Nordic" in the comments](https://www.reddit.com/r/unixporn/comments/dav66r/xfce_nordic_xfce/f1uvae2?utm_source=share&utm_medium=web2x), but if you look at the screenshot, `Nordic-standard-buttons` is the actual name. (I originally assumed `Nordic-standard-buttons` was some kind of add-on, not a theme itself.)
	1. Download: https://github.com/EliverLara/Nordic/releases
	1. Extract: `sudo tar xf Nordic-standard-buttons.tar.xf /usr/share/themes`
	1. Apply
		1. Open *Appearance* (open the whiskers menu and search for *Appearance*) and click *Nordic* on the *Style* tab
		1. Open *Window Manager* (same process as the previous step) and click *Nordic* on the *Style* tab
1. Icons: Nordic
	1. Download: https://www.gnome-look.org/p/1267246/
		* I couldn't find it on the GitHub repo's releases page or I'd have downloaded it there
	1. Extract into `~/.icons/`
	1. Open *Appearance* and click *Nordic* on the *Icons* tab

# Installing Citrix Workspace

My work uses Citrix, so I needed to install Citrix Workspace to connect to a work VM. The download page for Linux is https://www.citrix.com/downloads/workspace-app/linux/workspace-app-for-linux-latest.html.

After installation, I tried to connect and got the error: 

> SSL error  
> Contact your help desk with the folling information: You have not chosen to trust "DigiCert High Assurance EV Root CA", the issuer of the server's security certificate (SSL error 61)

Copying the certificate from `/etc/ssl/certs/` into the Citrix client's `cacerts` directory resolved it:

    sudo cp -v /etc/ssl/certs/DigiCert_High_Assurance_EV_Root_CA.pem /opt/Citrix/ICAClient/keystore/cacerts/

# Miscellaneous Other Changes

* Changed the whisker menu shortcut to <kbd>Super</kbd> + <kbd>Space</kbd> (launch *Keyboard*, go to the *Application Shortcuts* tab, scroll to `xfce4-popup-whiskermenu`, and click *Edit*)
* Installed Mono (in order to use KeePass) via the instructions [here](https://www.mono-project.com/download/stable/#download-lin)
* Installed Remmina (for RDP) using the Software app


# Conclusion

It's going well so far. I plan to stick with it. I see more pros than cons at this point because there are still stars in my eyes, but there are definitely both.

Pros:

* **Free as in beer:** If I want to create a product whose infrastructure requires hundreds or thousands of VM instances, I don't have to worry about licensing costs.
* **Free as in speech:** I can hack the source code if I need to.
* **Free of bloatware:** There's no Cortana trying to search the Internet when I search the Start menu. (If I wanted to search the Internet, I'd have opened a browser!)
* **Free of forced updates:** I love that I can restart my computer without Microsoft making me update. (I'm about to give a presentation; I really need to reboot fast!)

Cons:

* **AutoHotkey:** I have lots of AutoHotkey scripts on Windows. [The word on StackExchange is that AutoHotkey doesn't run well on Linux, although it can be run through Wine.](https://unix.stackexchange.com/questions/165124/autohotkey-equivalent)
* **Unfamiliarity:** I have to stop to Google something more often than I would on Windows.