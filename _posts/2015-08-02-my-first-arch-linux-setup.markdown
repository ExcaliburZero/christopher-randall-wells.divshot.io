---
layout: post
type: article
title:  "My First Arch Linux Setup"
author: "Christopher Randall Wells"
image: ""
date:   2015-08-02 19:34:00
categories: linux archlinux
---
Since I have had a some extra time over the summer I decided to try installing a Linux distribution on an old laptop my family had to get it working nice and well. After looking around a bit I eventually decided on installing Arch Linux on it. Due to Arch Linux's more customizable style I got to put together the setup of programs that it would use. The following is a look at the system I put together and some of my notes on the process of putting it together.

The process of installing and configuring Arch Linux to suit my needs took me about two weeks. I learned how to do much of the installation process thanks to a [three part tutorial series on installing Arch Linux](https://www.youtube.com/playlist?list=PLo8tBedUXjpYZUEJXx0zrbrLuColFzFag) made by [Antoun Sawiers](http://www.antounsawires.com/). However, I did come across some issues that the video series didn't help with, but I was able to fix with the assistance of the helpful people on the [Arch Linux Newbie IRC channel](irc://irc.freenode.net/archlinux-newbie). They also noted that installation tutorials like the one I watched shouldn't be fully followed, and one should instead refer to the [Arch Linux Beginner's Guide](https://wiki.archlinux.org/index.php/Beginners'_guide) for more up to date installation instructions.

## Hardware
First I should note the hardware of the laptop, as some of the specifics of the hardware proved a bit difficult to work with during the installation.

| Laptop Model | HP Mini 1010NR |
| CPU | Intel(R) Atom(TM) CPU N270 @1.60 Hz |
| RAM | 2 GB |
| Hard Drive | 8 GB SSD |
| USB Ports | 2 |
| SD Card Ports | 1 |
| Wifi Card | |
| Ethernet Port | |

The laptop was several years old at the time, and was noticeably slow in running its installation of Windows XP. With an SSD space of only 8 GB there was not much room for many programs or files. Luckily it did however have an empty 16 GB SD card still inside it, so I could use that to supplement the small SSD.

I made certain to note the wifi card and ethernet port used by the laptop, because those two components proved to be the most difficult part of getting Arch Linux installed and working. If you are not familiar with the installation process for Arch Linux, it requires the use of an internet connection in order to install most of the packages used by the system, as the live cd does not have those packages in order to keep it at a very small file size (~700 MB for both the 32x and 64x on one disk).
