---
layout: post
title: The First of Many
tags: Personal Projects Servers
---

## Server Selection
One of the saddest moments of 2020, asides from well.. 2020, was probably the fact that all of my plans and setup for a CentOS server went from a nice eventuality [to a lot of wasted time](https://arstechnica.com/gadgets/2020/12/centos-shifts-from-red-hat-unbranded-to-red-hat-beta/).
I have chosen to view this in a similar way to how I viewed the accidental destruction of my Registry in Windows and the eventual decision to switch over to Debian permanently. This has led to a choice, I either go with what I know and do Debian, or I go ahead and finally do something with Ubuntu.
**I am complacent.**
Now it is not only complacency that is pushing me towards a Debian server _and_ a Debian workhorse! There is the fact that one of the main goals of this is security and maintaining a stable system. Fortunately most of the work I am going to try and get done with this should survive if the programs and applications are slightly older than if I used Ubuntu. We should see some nice stability and less long term concerns if we are using Debian.

The difference between my experiences the past several times I have been putting an OS on a new device, and the first two times I was installing a Linux OS are night and day. In mid 2020 setting up an external drive to boot a persistent copy of [Kali Linux](https://www.kali.org/) seemed like it was more likely to lead to my insanity. After triggering a security feature in my work laptop that led to the encryption of my entire hardrive, accidentally created 1 too many partitions that led to it reading the wrong drive, and after all this and deciding to start from square one for the fourth time I found myself containing a second OS I could boot on any machine, and I felt such pride!

**If you want to have a pleasant experience and not faulter just use this [null-byte](https://null-byte.wonderhowto.com/how-to/install-kali-live-usb-drive-with-persistence-optional-0162253/) article to set up your persistent drive with much less hassle**

These times however I feel a new joy, born simply out of how my head doesn't hurt after a download, I find an operating system I want to download, I boot up my windows machine, do a quick download (I thank the Lwa every day I have such nice internet, except when I don't...), and then boot up [balenaEtcher](https://www.balena.io/etcher/) and flash it to my formatted thumb drive and then plug in the drive and begin the download process.

##The Install
The machine the server is going to go on is a temporary piece of hardware, hopefully. Beforehand an ancient Toshiba laptop did the work that it was severely under qualified to do. What we have now, is something much more exciting! Obviously I won't go into too many details of the hardware, but if you manage to break in it'll be easy enough to figure out. What we have now is a refurbished VivoBook Pro. I got my hands on the machine after the hinges on it broke and the hinge placement caused it to rip the power supply jack jack apart and a lot of sparks. I was uncertain if I was going to be able to fix this but the jack cost 3 GBP and it had a shipping time of a week so I took a shot. After resetting the hinge screwholes (Epoxy, epoxy, and some more epoxy), removing the old power jack, and installing the new one we had life again!

Installing is a much simpler process nowadays, I have the knowledge that I am going to need to have the drivers for the wireless card in the install file as debian does not come with those in the base file. Now it is simply following the instructions setting it up and configuring it.

The configuration is a topic for the next post. We will go into what packages are going into it, what the first tasks we will give our server to accomplish and what groundwork will be laid for future projects.

--Roger
