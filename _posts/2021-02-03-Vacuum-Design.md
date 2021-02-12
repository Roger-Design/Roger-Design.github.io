---
layout: post
title: Beauty, Function, Form... A.K.A Autonomous Vacuums
---

## Vacuums?

This post is going to be a post as it relates to the needs and requirements of the eventual incognito motion detector attached to or built into a robotic vacuum. There is not much in the way of planned actions on this for now, but here is a general layout of the plan.

### Planning

First I need to plan this out, this post is going to be post one in the planning phase. This will be doing research, reading up on different resources studying academic papers that relate to this and getting prepared to start running tests.

### Tests

Tests are going to be crucial. We are going to have several body designs more than likely, different choices for sensing motion (sonar, lasers, etc.) and more for each step. I already have a RaspberryPi who will act as the test platform for a lot of the sensors, the body, well I haven't figured that out besides from building 2 or 3 different robots, I might be able to theoreticalise myself out of doing this once I know more about what the body needs to support. After all the body is nothing more than an inconspicuous vessel for some sensors and possible a small board controlling itself and other devices.

### Blueprint Design

Sadly I can't start or finish on my favorite phase. At this point I will write a lot of posts about the various design ideas I am thinking of and what they look like (Unless I find an easy to use software to make my horrific artistic abilities irrelevant I may not post images, you don't want the schematics I draw by hand). This phase is going to be heavily influenced by the testing phase and with any luck will make the blueprint phase incredibly short and efficient.

### Prototyping

Here is the part where things that might be more intriguing will happen. Once I land on a blueprint I will start building the chosen design and see what works, what doesn't work and what modifications will need to be made.

### Finalization

Lastly after prototyping and finding what works we will begin work on the "production" version. It will be an attempt to make something that follows the functional requirements I'll lay out later and do what I want it to do. Lastly we will want to make sure that it is a subtle machine. It really doesn't need to be the best vacuum, although that will help! I am a CompSci student not MechEng.

## [What Do I Want](https://www.youtube.com/watch?v=gJLIiF15wjQ)

Now let's talk about what this device needs to do, I'll go step by step going over all the things the device is required to do and flesh them out as I go. Note I will refer to it as device from here on out. Vacuum __may__ be accurate however there is the chance that we opt out of having a functioning vacuum for the sake of other more important requirements. I will title each requirement with either R(equired) or I(deal) to demarcate what can and can't be cut or reduced.

### Sense Motion (R)

This is pretty important, the device is going to have to, by using sensors make a map of points within the room. Tables, chairs, walls, etc., not just to navigate but to also detect unexpected points appearing. This is going to be the most crucial function of the device as it is going to be trying to detect intruders. There are a handful of ways I am considering doing this. Either with a high or low frequency sound, or with light. This, in the event of creating an add-on to an existing robotic vaccuum model will then overwhelming majority of the device. This one kind of goes without saying, however it is still relevant noting.

### "Act" Like a Vacuum (R)

No matter what, even if this just has a small rotor and a fan that doesn't lead to a final repository for the dirt it needs to act like a vacuum cleaner. The device will need to do a predictable and full sweep of a room in order to not draw attention. This has some run on effects, the final product should be able to return to a hub area for charging, and (if I am very clever) automated bin transfer. Subtlety is key and as such it needs to look and act like every other robotic vacuum.

### Navigate Smoothly (R)

This seems like a part of the previous one but deserves it's own space. The device needs to be programming to navigate the room, and based on the objects in the room plot a course and be able to adapt if all of a sudden something is different.

### Clean (I)

This one can be fudged a bit. In an ideal world this functions nicely and cleans the room while looking for possible intruders but it might be worthwhile in the end to cut down on those capabilities in order to maximize things like battery life.

### Simple to Reprogram (I)

Obviously in order to sell a product it needs to be simple to interact with. However, I don't really plan on selling this thing so it doesn't need to be the easiest to modify if I know everything about it's design. However the device ideally will be simple to modify and have ways to be accessed by the average user.

### Command and Control (I)

We have here an opportunity. Imagine you are designing a security suite. Motion detectors, cameras, alarms, and whatver else your heart desires. There will likely be some heart to this network communicating back and forth between the various machines and facilitating the user interactions. One might try and keep everything independent but it introduces a workload to actually process all data taken in to be sent to, well some heart. In an ideal world this might act as a very hard to detect Command and Control platform for the entire network.

### Camouflauge (I)

This is something that might get some flak in a production setting, but it might be a good idea to take a generic design approach (A la Roomba), and design the robot around this. This is the intended goal, and whilst my prettification abilities may make it hard to get an exact match. Hitting identical dimensions will be a pretty big success at the very least. Obviously this can be nixed if we need more space.

### And?

And that is about it I suppose. I really just wanted to flesh out the requirements for this project as I begin to research the different aspects and start to post about them. Expect next a breakdown of the different designs of robotic vacuums, Abso-fricken-lutely thrilling read you have in store! What dimensions are common, how many fans, motor specs, motorized or non-motorized front wheel, dust bin specs, power supplies, and much much more!

--Roger