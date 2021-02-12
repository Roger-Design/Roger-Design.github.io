---
layout: post
title: Setup and Configuration at Last
tags: Personal Projects Servers
---

## Incomparable To The Past

It is hard to put into words how nice it is for something to work, and for it to work in an almost effortless way in comparison to the past attempts. Had you sat me down 2 years ago and said, "Simple just take this laptop, install a new operating system, and configure it to act as a ftp and web server.". You might as well have asked me to build a rocket and get to moon. Nowadays, this is almost a brainless task and any research I am doing is to see if there is anything new or better than what I already plan on doing. The comparison between the time spent, and security of the server setup I have done this weekend and my _old_ Toshiba is night and day! I am very glad that it never got exposed to the great wild expanses that are the internet, at the very least it was a junker of a machine. This new one though, has a processor of equal ability to my daily driver, 3 times the storage, and the only thing it is in need of some replacements are it's RAM sticks, which can be boosted up to 32 no problem. The only other things to do is to build a [distributed computing](https://en.wikipedia.org/wiki/Distributed_computing) setup a la [grid computing](https://en.wikipedia.org/wiki/Grid_computing) to put some of these weaker machines I seem to collect to some use processing data or brute forcing passwords.

## Hurray, you have a server, now what?

If you have read the [first blog post](https://roger-design.github.io/Server-Selection/) you'll know that one of the goals of this server is to act as the command and control center for the robotic fleet of sensors I wish to build in order to cut their individual computational needs to a minimum. Later this will hopefully be translated to a RaspberryPI in a more light weight efficient instance.

This begs the question, what do I do with it now? I have no solid designs for the server, I don't plan on building anything for quite awhile even. Nonetheless there was work to be done, the server will have many jobs and some of those will require it to be open to the [wider internet](https://www.youtube.com/watch?v=cphNpqKpKc4)! As such we need to make sure that not every casual scan is going to go ahead and reveal the inner contents of the server so it was checklist time:
	* Secure access to make it as secure/forgetfulness proof as possible
	* Set up firewall to limit connections to the server.
	* Set up Apache2 to make a web server for attacking (Will be fleshed out later)
	A pretty simple list of tasks and though it requires one to open up configuration files and muck around in settings it is pretty simple and straightforward.

### Locking the Front Door.
We have locks on our front doors for a reason, we lock windows, our phones and our laptops and a server should do the same. Especially if it is going to do anything important. I am using OpenSSH on Debian 10 and once you run the server after [installing all the packages](https://phoenixnap.com/kb/how-to-enable-ssh-on-debian) you can start up your ssh server and let people connect in. Logging in is pretty simple, you specify who you are signing in @ the address of the server and the **magic** of the internet takes you there to sign in (who@Where)! This is fine but without fine tuning anyone doing a scan for openSSH ports can find you and bruteforce attack their way inside, and got forbid they can sign in as a root user. This is no good, so we have to take some precautions.

First things first is to make sure you have a very strong password, I have given up on the belief that I am capable of coming up with truly random and complex passwords and also remember them for the countless accounts I need for Uni and just life in general. I have made the switch to a [password manager](https://uk.pcmag.com/password-managers/4296/the-best-password-managers) and I suggest you do the same, I use BitWarden but if you are using anything that is secure then I commend you!

You may be wondering if there is a better way to connect to your server instead of needing to type in your very long and complex and easily forgettable password? There is, [RSA key pairs](https://www.comparitech.com/blog/information-security/rsa-encryption/) (If you think back to year 1 CompSci, remember Bob and Alice, if you weren't in that or know about public key cryptography click the link.) OpenSSH allows for pretty painless use of RSA encryption for all people communicating with your server. Tweak the configuration file, send your key to the server and voila! No more typing in a password from a trusted machine.

Alright, now we have a way to communicate without using a password, a strong password that is _hopefully_ stored in a password manager. But can we do better? Of course! I have set up 2FA authentication on my server as well, so if I need to let someone else access the server I can provide this one trusted person the password and the code they need to sign in, then they can send their public key and have the same easy access as I do (It should go without saying that next to nobody should have this type of access unless they are incredibly trusted by you.). This isn't a tutorial so [here is a link](https://www.globo.tech/learning-center/setup-ssh-server-with-two-factor-authentication-ubuntu-debian/) to a tutorial for setting it up on a Debian/Ubuntu server. 

Now that we have passwords set to something strong what about trying to weed out a lot of people just trawling for ssh-able computers. Well it is simple enough cut out a large portion of these by switching the port people can connect with. Since 22 is the standard for SSH a lot of wide scans are going to be looking for that port, whilst nmap can scan **ALL** ports open on all machines in a network it is time consuming to do this, and people trying to get into your server are either looking for quantity over quality, or they have zeroed in on you (and your problems are bigger than switching the port used).	   
	   
Lastly one should prevent unwanted connections, you can't be everywhere at once and it is unrealistic to imagine you will know all attack vectors on your machine. I have opted for a whitelisting approach to most things security related. Instead of trying to figure out all the problems I need to defend against I opt to instead narrow the entryway to only take in those who are able to go there. You need to be attentive to needed changes to allow new users in, but it is better than being open to new unknown threats! I can't go into great detail of how I have my firewall configured (obvio huevon), but if you are reading this for ideas, use ufw and be restrictive, you can always open up connections if need be!	   

Getting the apache server up was a woefully trivial task compared to what I imagined it would be! But there are some developments. I personally am not aesthetically gifted, I am better at making something functional than something attractive and as such I have opted for this web server to be done using [Gatsby](https://www.gatsbyjs.com/docs/glossary/static-site-generator/). This blog is all in Jekyll, but the attack and defense site is going to be more of a mock business/personal site so I needed something different! The next couple blog posts will probably be about getting that set up and my inevitable troubles with getting it just right!

## Conclusion

One really shouldn't skimp on security for their server. Especially if you are going to be making it front facing, I intend to have my server available to the wider internet so myself and my team can do some work inside of that and store a lot of our work inside a secure space that isn't reliant on the cloud. If you let someone inside your network and they have too much access they can wreak havoc on your network, installing malicious software or just sitting inside your network harvesting all of the data they want from everyone on your network! One should treat their network and servers like they do their property and keep it accessible to trusted individuals but not open for anyone who wants to pop in!

--Roger