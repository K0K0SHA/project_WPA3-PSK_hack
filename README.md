# July 7, 2022
# project_WPA3-PSK_hack [WORK IN PROGRESS]
# DISCLAIMER
All research performed in a safe and legal manner. Please do not discuss the wild use of the tools
in this repo, or any other tools to take actions against the law. At least, not on GitHub. Radio 
jamming is illegal, and so is deauthenticating and jamming WiFi. Don't get in trouble!
...With that said, welcome to the WIFI HACKING LAB!

# contents
  This project is a knowledge base of WLAN WPA3-PSK and WPA2 hacking tools and research. The goal of this project is to
create a way to break into a WPA3-PSK network. In my approach, part of hacking WPA3 is understanding
how WPA2 works, so this repo will have tools and knowledge for hacking WPA2-PSK as well. This 
document is meant to give a skiddie-tier overview of WLAN-cracking without diving into the weeds. 
  This repo should contain links to YouTube videos, other GitHubs, GitLabs, and places to
find code. I will also download and paste research papers from elite hackers into the repo. I take no
ownership of such research papers, and promise to do the honorable thing, and always disclaim them. 
  On the topic of research papers, this repo will contain research documents pertaining to WiFi and
security, as well as other topics. Programming languages involved will mostly consist of C and Python.
  
# GNU/Linux Distributions

  Every computer nerd's favorite subject to argue about is Linux distros. In this research lab, you are
  responsible for building and using your own Linux distribution. As long as your distro has GNU and
  can install things from GitHub, then you should be fine. Many Linux distros exist. I can't/won't 
  cover them all in this document because it's pointless. This guide assumes you're somewhat familiar
  with GNU/Linux terminal and commands.
  
  You may choose whatever distro you want. Some popular ones are Ubuntu, Kali, Redhat, Manjaro, Gentoo,
  Mint, Debian, Devuan, and Arch. Cracking WLAN's should be possible with any of these, so long as you
  can compile and install the dependencies. This lab should also be possible on a Mac, and on Windows
  if you're using a VM (see next section). As of this writing, I have not tested any 802.11 cracking
  techniques by using a Windows device, and I do not own a Macintosh.
  
  The research that I've done in this lab is all done on a Debian-based Linux distro. I tend to use 
  Linux Mint myself. I have my distro on a live USB stick. The stick can boot a live linux distro, and
  install a linux distro. You really should have one of these. 

# Kali Linux

  Kali Linux, formerly known as Backtrack, is a Linux distro with a bunch of tools for hacking. 
  It's based on Debian/Ubuntu, so it's actually pretty nice. Beginner friendly, too.
  Many hackers install and use Kali for its convenience. If you have all the tools you need for the
  lab working in Kali, then go ahead and use it. But if you're wondering which distro you should use
  for the WLAN-hacking lab, you may want to think twice about using Kali. There are certain problems 
  with using Kali Linux, as outlined here.

  Kali ISOs need to be updated in order to get updated Kali tools. Even then, the tools provided with
  the Kali ISO might be out of date. That's why it's considered good practice to always update your 
  tools when running a Kali Live USB or VM. 
  
  You may run into compatibility errors and dependency problems when trying to run 'pre-installed' 
  scripts on Kali. Back in my early hacking days before I largely gave up on using Kali, the scripts
  included could be run with intermittent success. As I developed, I realized Kali lacked what I needed,
  although I fell in love with the special node-based text editor CherryTree. I will upload notes to
  this repo in the form of CherryTree (.ctb) documents.
  
  Kali has problems running apt-get, as well as other problems that you just wouldn't expect on Ubuntu.
  For example, if you leave it running long enough for Kali live to enter lockscreen, there is a password
  but it's hardcoded as 'toor' which is root backwards. I happened to find that detail by reading several
  books on hacking and Kali. That's why I don't really recommend that you do this project from Kali. 
  
  At any rate, I find it much easier to git clone the required tools and install them myself on Ubuntu
  or Mint, than to just take Kali and run them. I'll research Kali's built in tools and their efficacy.
  I believe Kali has aircrack-ng suite preinstalled, as well as Fluxion, WiFite, mdk4, mdk3, and most
  of the other stuff you'll probably need for this lab. Hopefully I'll be able to develop a guide to 
  crack WLAN's using Kali. I'll make a specific document about using Kali to run the tools required. 

# Ubuntu
  I highly recommend a fresh Ubuntu install to begin with. From there, you can set it all up yourself
  just the way you want it. Ubuntu doesn't have hacking tools pre-installed, but that's actually a good 
  thing. There are significant benefits to downloading and installing your own hacking tools. 
  
# Mint
  My personal distro of choice. It's effectively the same thing as Ubuntu, with a different look n' feel.
  
# apt-get install
  Ubuntu, Mint, Kali, and Debian use apt (advanced package tool) which is a frontend for wget and dpkg. 
  Sample usage to install aircrack-ng: 
  
  sudo apt-get -y install aircrack-ng
  
  apt may also be used to search for packages (you don't need sudo):
  
  apt-cache search aircrack

# other package managers
  If you're using pacman, yum, flatpak, snap, brew, rpm, or whatever else may be out there... 
  As long as your package manager can install the required package, then you're good. If not, 
  Google the issue and post about it on the forums and here. Please remember that cloning
  from GitHub is the recommended installation for this lab, and not the package manager.

# Windows
  It's very hard to try using Windows to hack. You should just install a Linux distro instead.
  If you insist on keeping Windows installed on your device, then you should at least dual-boot.
  If you're dead-set on using Windows to hack WLANs for some reason, you will still have to
  virtualize Linux using VirtualBox or another VM hypervisor. One of the objectives in this lab
  is to test the relative effectiveness of a virtualized Linux distro with a hardware passthru
  for the network interface.
  
# Mac
  If you can figure out how to compile airmon-ng and the other utilities you'll need for this lab on a 
  Mac, then it is viable in this lab. I believe that you can use a Mac to hack WLANs. However, I have
  not tested this out. If you have experience cracking WLANs using a MacBook, please discuss it.

# 802.11 Protocol
  802.11 is also known as 'WiFi', and many generations have evolved over the ages. In general, WiFi is
just radio signals on the 2.4GHz and 5GHz bands. Because of how precise our digital electronic radios 
have become, these frequencies can be subdivided into smaller frequency ranges called channels, or bands.
The networks that are created through the use of 802.11 are known as WLANs, or Wireless LANs. WiFi.
It should also be noted that BlueTooth uses 2.4GHz frequency range, but BT is not the focus right now.
The bands of WiFi depend on which country you're in. Here is a frequency list:
https://en.wikipedia.org/wiki/List_of_WLAN_channels

# Attacking WiFi
  There is no single way to hack a WLAN. Offensive and defensive security have a way of always evolving. 
There are many techniques. The general trend in 2022 has been significant security improvements in the 
underlying security mechanisms of WiFi. This repo will have a legacy section which will outline the 
cryptographic weaknesses of old protocols if you're interested. 
Obviously, old attacks are ineffective. The only value from them is what they can tell you about new
protocols. Chances of finding old hardware is actually pretty low. We should focus on new stuff.
  
# WPA3-PSK and WiFi 6
https://www.intel.com/content/www/us/en/gaming/resources/wifi-6.html
  
  With the introduction of WiFi 6 (802.11ax), wireless security has improved once again. A skiddie can
no longer easily break into a WPA3-secured network. WPA3 offers significant security improvements over
WPA2, just like WiFi 6 offers speed improvements over its predecessor. Because security research into 
WPA3-PSK seems to still be in its nascent stage, it is hard to find information as of 2022. This proj.
will attempt to reverse engineer WPA3-PSK by understanding the attacks against WPA2-PSK, and then 
looking at how these attacks were mitigated.

  From a security point of view, WPA3-PSK has a new type of handshake called the Dragonfly handshake.
  It uses SAE (Simultaneous Authentication of Equals) for encryption. 

# WPA2-PSK
  Currently the most common type of WLAN in the wild as of 2022. Slowly being phased out by WPA3-PSK. 
Probably will become obsolete in the coming years. Wide variety of attacks exist against WPA2-PSK. 
WPA2-PSK is still more secure than its predecessors, but by 2022 it is considered very old. 
  This project's documentation details how to hack a WPA2-PSK network in every known possible way. 
There are multiple types of known attacks against WPA2-PSK which are detailed in this repo. You may
run the scripts cloned or forked within the repo to test them yourself.


# Scripts for Hacking WPA2-PSK
The most effective scripts I've found to break into WPA2-PSK networks are:

WiFite (or its new rewrite WiFite2)
airgeddon
aircrack-ng
fluxion
mdk4/mdk3
Pyrit

# General Notes on Installation/Compilation
  The most effective way to install something in this lab is to clone it from GitHub. 
  YOUR DISTRO'S PACKAGE MANAGER IS NOT GUARANTEED TO WORK!
  In my experience using apt-get install, I've installed broken and outdated scripts.
  Cloning directly from GitHub when in doubt is better, although certain tools like airmon-ng can be 
  acquired from apt-get install without a problem. This does depend on distro. Otherwise, just
  read the manpages and readme's of the tools you're using. 

# Legacy WLAN hacking methods
  It used to be extremely easy to hack a WiFi network. WLANs with WEP could be hacked easily through
a pixie dust attack. Modern scripts such as WiFite are able to easily exploit such vulns, but most 
obsolete vulns are very hard to find in the wild. Nevertheless, in this lab we will apply and test
certain legacy WiFi hacking methods as a means of research.

# what is PSK?
  PSK is the most common type of residential WiFi network. PSK stands for Pre Shared Key, where the
Pre-shared key is your WiFi password. PSK is opposed to Enterprise Wifi authentication, where the
authentication is done by a different server and you usually have to login with your ID number etc. 
Enterprise WiFi is beyond the scope of this WiFi hacking lab.

# What types of devices can be found in the wild today?
  As of July 2022, most devices in the wild are still secured by WPA2-PSK. WPA3 devices are slowly 
rolling out, but are still considered cutting edge. Obviously, this is an ongoing kind of thing.

# Privacy concerns and triangulation
  Before you go out and wildly start trying to hack everything in sight, beware that there exist 
sophisticated methods of tracking you down. This research lab will try to address the theory of 
defending and tracking attempts to hack WPA-PSK networks so that you can protect yourself.
Likewise, the techniques explored will attempt to counteract cutting-edge signal triangulation
and beacon-tracking attempts.

# Building WiFi Hacking Labs
  
  Building a lab for hacking is considered important so you can experiment in a legal and safe type
of environment. Normally, the training hacker would use VirtualBox or VMWare, or some other hyper-
visor. They would set up as many virtual machines on their network as needed, and then run the 
experiment they're trying to do. This type of lab setup is great, but in order to practice hacking
802.11 networks, you'll need more than a couple of VM's and a server. In other words, forget what
you know about setting up a conventional malware testing labs. A lab has to be purpose built.
  
  In order to keep things legal, hacking 802.11 networks would require building your own first. One
easy way of building your own 802.11 WiFi network is by plugging in an access point in your home.
Most people consider a 'router' and a wireless AP to be the same thing. For the purpose of a small
residential WLAN, this is likely the case. Your router is your primary AP, although you may have 
several AP's within your home including a hotspot. Step 1 of practicing hacking 802.11 is setting up
your router and WiFi network. I recommend going to the store and buying a spare router. The newer
the hardware, the more secure it's going to be. To practice hacking WPA3, you'll need a WiFi6 (WPA3)
compatible device. Obviously. 
  
  You may enter your router through the default gateway and use the default login, and then set up
the network you're trying to hack. This is your lab. You may connect whatever physical devices to 
your network that you want. If you want to make it more advanced, you can try running things like
Wireshark filters on your network. The point is, it's your defender's network so you can customize
it however you want. To simulate the average normie, it suffices to leave most settings at default.

# What about Hotspots?
  Hotspots are made by cell phones and cars with data plans. I have not done any research into hacking
a 'hotspot' AP, although you expect this research in the future. In theory, a hotspot is just 802.11 
with specialized hardware.

# Doing research
  I have personally found it hard to organize the vast amount of knowledge I've gained from running
WLAN cracking scripts. I gain knowledge from every corner on the internet. This includes YouTube, 
Reddit, /g/, lainchan, other forums, Google, and more. One of the cornerstones of this research 
projects will be a folder of saved thread (highlights) from my previous research. I will have to
check chan archives in order to get it.

# Dev teams working on WPA3
Most of these teams are manned by volunteers. I'm actively looking for people to collaborate with.
- airgeddon
- aircrack-ng
- WiFite (unconfirmed)
