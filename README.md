# July 7, 2022
# project_WPA3-PSK_hack [WORK IN PROGRESS]
# DISCLAIMER
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
All research performed in a safe and legal manner. Please do not discuss the wild use of the tools
in this repo, or any other tools to take actions against the law. At least, not on GitHub. Radio 
jamming is illegal, and so is deauthenticating and jamming WiFi. Don't get in trouble!
Try to say "it is possible to X" or "a hacker could Y" instead of "You should X" or "I will Y". 
...With that said, welcome to the WIFI HACKING LAB!

# contents
  Knowledge base of WLAN WPA3-PSK and WPA2 hacking tools and research. The goal of this project is to
create a way to break into a WPA3-PSK network. In my approach, part of hacking WPA3 is understanding
how WPA2 works, so this repo will have tools and knowledge for hacking WPA2-PSK as well. This 
document is meant to give a skiddie-tier overview of WLAN-cracking without diving into the weeds of
all the technical specifics in this specific document. 
  In general, this repo should contain links to YouTube videos, other GitHubs, GitLabs, and places to
find code. I will also download and paste research papers from elite hackers into the repo. I take no
ownership of such research papers, and promise to do the honorable thing, and always disclaim them. 
  On the topic of research papers, this repo will contain research documents pertaining to WiFi and
security, as well as other topics. Programming languages involved will mostly consist of C and Python.
  Cryptography is also a very important topic of discussion in this research project. 

# 802.11 Protocol
  802.11 is also known as 'WiFi', and many generations have evolved over the ages. In general, WiFi is
just radio signals on the 2.4GHz and 5GHz bands. Because of how precise our digital electronic radios 
have become, these frequencies can be subdivided into smaller frequency ranges called channels, or bands.
The networks that are created through the use of 802.11 are known as WLANs, or Wireless LANs. WiFi.
It should also be noted that BlueTooth uses 2.4GHz frequency range, but BT is not the focus right now.
The bands of WiFi depend on which country you're in. Here is a frequency list for USA:
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

# WPA2-PSK
  Currently the most common type of WLAN in the wild as of 2022. Slowly being phased out by WPA3-PSK. 
Probably will become obsolete in the coming years. Wide variety of attacks exist against WPA2-PSK. 
WPA2-PSK is still more secure than its predecessors, but by 2022 it is considered very old. 
  This project's documentation details how to hack a WPA2-PSK network in every known possible way. 
There are multiple types of known attacks against WPA2-PSK which are detailed in this repo. You may
run the scripts cloned or forked within the repo to test them yourself.

# Scripts for Hacking WPA2-PSK
The most effective scripts I've found to break into WPA2-PSK networks are:

>WiFite (or its new rewrite WiFite2)
>airgeddon
>aircrack-ng
>fluxion
>mdk4/mdk3
>Pyrit

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
  Actually, hardware is a very important question in 802.11 hacking. 802.11 hacking is unlike most
other types of hacking that you can just practice online. Many types of hacking such as web hacking,
privilege escalation via buffer overflows, etc. can be done completely remotely online on someone 
else's machine. For a legal example of such labs, you can visit overthewire.org/wargames
  Overthewire.org is a great place to hack, but does not have 802.11 wargames. The reason for this
is because building a WiFi hacking lab is actually pretty hard. As previously mentioned, you need
various hardware. In this research project, I'll summarize the hardware I've used, why I've used it,
and what other hardware can be used in the lab.
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
a 'hotspot' AP, although you expect this research in the future.

# Doing research
  I have personally found it hard to organize the vast amount of knowledge I've gained from running
WLAN cracking scripts. I gain knowledge from every corner on the internet. This includes YouTube, 
Reddit, /g/, lainchan, other forums, Google, and more. One of the cornerstones of this research 
projects will be a folder of saved thread (highlights) from my previous research. I will have to
check chan archives in order to get it.

# Dev teams working on WPA3
(I'm actively looking for people to collaborate with)
airgeddon
aircrack-ng
WiFite
