---
title: Pointing to the WAN
tags: Personal Projects Servers
---

## Phase 1 Complete

This will be a shorter post, however I felt it might be nice to reflect on my experience of getting my server available to the internet to allow for accessing my files anywhere, and also for collaborative work to have a local area to be stored and worked on with the team. It had some nerve wracking components and I have learned that I would have probably died if not for the amount of work securing the access to the server.

## Opening the Gasket

The process for getting it live is painfully easy, and really isn't the main part of this post. One logs into the router, reads a million messages informing you that if you mess up your router it is on you and that if you aren't an advanced user to back off. One ignores these messages, and continues forward, and if you aren't what you yourself would call advanced you fear, "What could I mess up? Am I going to destroy my internet? This is a super simple task, however if I bungle this how will I connect to my all online classes?". These aren't invalid thoughts by any stretch of the word, but still it is just port forwarding so really not something to freak out about. You suppress the pit in your gut and click apply, your router resets, the fam upstairs starts making murmurings about the internet being down and for that brief moment you believe that something on their end is going to muck it up, destroy your internet, ruin everything, get your nice internet contract revoked, and then.... It all works as you figured it should, everything acts in the expected way and you try and finish feeling raw nerves. Little do you know, your unfounded fear of bricking your network is just the beginning!

## Peering at the Shadows, Turning over all Rocks

The sense of accomplishment hits and I feel pretty good, I just did some very rudimentary things. They may be rudimentary but I feel good because I feel I really did them right, and each step of the way has gone smoothly. It is time to do some tests, disconnect the phone from the internet and connect to data (It is a blessing to have reliable cell service, the homeland's cell service, well let's just say left much to be desired) and ssh in. Works beautifully you connect browse around and make sure it functions, which it does, as it should. The tests continue to go smoothly connecting from a machine, confirming root access is blocked by default, and now it is time to set up accounts for the rest of the team. All of these tests are crucial, because the concern has begun to develop, have I left anything exposed? The user account for the team is made, sudo privileges are not given to it, access is limited but not too limited, I take a peak at the rules for the firewall. All seems good only the random port chosen is allowing any traffic. Some more modifications are made, I make sure the ssh protocol is the right one and then just to be safe I run ss in the terminal, and see something, something so absolutely upsetting I would proceed to waste an hour trying to track, kill and destroy the bastard who was connected who had taken my hard work and made a mockery of it by connecting directly to my machine.

I don't want to go into the details of the hunt, partly due to embarassment, and partly because it was a feverish hunt. Trying to hunt down the IP address, find exactly where they are, I found the location, and honestly the location was surprising, middle of nowhere, in a middle of nowhere place. Not very helpful, time to try and find any associations that this IP address has, a deluge of information threatens to drown me but my lookups aren't associating it with anything nefarious, just random. At this point I am not really freaking out so much as preparing to disable the internet connection to the server and dig around for the security flaw. Until I decide to just run a battery of commands in my terminal to pull up as much information on the connection as possible.

Now let's talk about the importance of not panicking. Had I simply decided to pay a little more attention and not let the nagging fear in the back of my head get the better of me I would have realized right away something. The connection was just the tcp connection between the server and mozilla firefox. It is a very good lesson, if one isn't fully confident in something since this is the first time it has gone quite smoothly one should be a little more patient and not jump to immediate assumptions that the worst has befallen us. It really was unlikely that someone had not only already found my server, but gotten inside of it. And the fact that I was so quick to believe the worry deep within myself that I had messed it up allowed a cloudy vision of what I was seeing to develop and a hunt for an intruder that wasn't there to begin.

If any of you reading this are setting up something and about to expose it to the internet, and if you are a bit of a pessimist then I would recommend you get a second pair of eyes until the initial high alert phase mode in your mind can subside. This high alert mode can be a huge help, but it can also really mess you up, try and learn from the neverending cycle of my life.
1. Finish a thing
2. Assume the thing is flawed and needs to be scrubbed for errors
3. Tear it apart searching for the flaw
4. Start worrying you have gone well past your depth at some point
5. Take a minute to breath
6. Realize you overreacted
7. Start the next thing on your list
8. Go to step 1

--Roger
