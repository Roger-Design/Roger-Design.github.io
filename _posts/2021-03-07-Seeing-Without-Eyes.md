---
title: Seeing Without Eyes
tags: Personal Vacuums Projects
mode: immersive
header:
  theme: dark
article_header:
  type: cover
  image:
    src: assets/header/Robot-Vision.jpeg
---
(image source: mitpress.mit.edu)

## Making the Inanimate Move

The first major decision to be made on our security robot is of course going to be how we make it capable of moving. There will be plenty of time to consider how we are going to make it actually move, motors, wheel placement, plenty of fun. For now however, it is time to discuss how we are going to make our vaccuum see. If the vaccuum is unable of telling where it is, and what is happening around it it will be a poor defender of an area. First let's discuss what is needed out of the actual vision, and then look at the different options and how they work. Finally, we'll try to make an educated decision for the eventual tests. 

![Eye Ball Monster](/assets/posts/eyeball.jpeg)
(image source: monster.wikia.com)

## Why Does It Need Eyes?

The main functions of our vaccuums eyes are twofold. First the robot is going to need to see in order to navigate the environment, and secondly it is going to need to detect and report changes in the environment if something/someone is moving around inside of the sector it is patrolling. Let's flesh these two concepts out a bit more:

### Movement

One might consider this important. Our machine is going to need to traverse an area with a similar pattern as a [commercial robotic vaccuum should](https://www.youtube.com/watch?v=OdR0JT652T4). This means a lot of linear paths, a handful of spirals, and fairly sharp turns. Even if the device is not equipped with functioning fans and brushes and is simulating the action, it will be critical to get the proper coverage. So we need to make sure we can see properly. Let's take roomba as an example, the first thing a roomba does is gauge the room size (less important for us since we aren't as keen on cleaning everything however it isn't a bad plus.) most likely this is done by pinging a few infrared beams off the walls to gauge the distance and then judge the amount of time it will need. For actual navigation it uses a combination of force sensors in it's bumper, and infrared sensors on it's bumper and undercarriage. The force sensors are used to detect when it collides with something, and the infrared sensors on the bumber are for following closely to a wall. Lastly the undercarriage sensors are used to detect drop offs, if there is any shift in the time it takes for them to get back it knows to stop in order to prevent a dangerous fall. Lastly, if there is a little home base then it searches for the infrared signal given by the base and follows it back in order to charge. These are pretty simple, and the implementation of a similar array would not be to difficult. To sum it up quickly, our bot needs to know the space it is in (infrared, ultrasonic, etc.), it needs to know when it hits or is about to hit something (force sensors, infrared, etc.), and it needs to know when it is about to reach a drop off that could damage it (infrared, ultrasonic).

### Detection

I don't think this eventual DIY security vaccuum is going to be competitive on the cleaning level, I am keen on security and while I enjoy mechanical engineering there are much better engineers out there. So our selling point is going to be here. Let's talk about what our robot needs to be able to detect, what things it needs to disregard, and some of the tricky bits of making it work. The robot is going to be mapping out the room and should store a representation of what is inside of that is constantly being updated, just like your brain stores an ever shifting picture of your environment over time. What we will need to do is make sure that this ever changing picture is also able to predict where everything **should** be when the device moves from one position to another. The use of infrared beams is an option, however this leads to the potential for a lot of false positives. If the device detects a moving object that isn't a person it is still going to go off, whether it is a falling item, a shifting curtain, or an animal. Modifications to the sensitivity can obviously help negate things like shifting fabrics but there are plenty of moving things in a persons house. One very common method is to use passive infrared detection, with the basic description (don't worry a more boring complete description will be in the next section), of it providing the ability of the device to detect changes in grid coverage and heat changes in order to detect when a living thing has entered the area and shifted the temperature in a given region. There are also microwave emitters that check the time it takes for them to return to get a sense of distances that can easily then check if the distances being detected are shifting. While many of these options are good, it is likely that a combination is going to be needed. A final, but unlikely, option would be to use advanced image analysis programs to analyze video footage that the device receives and then check for movement within it. This is a much more computationally expensive solution, and while it is an option is probably more than we would like in the computation area. In summation however, the device is going to need to be able to see when something, at some arbitrary size cutoff enters the region and is moving. The device should really try to limit false alarms, especially if it is hooked into a wider security platform.



## Types of Eyes

![Sensors Gallore](/assets/posts/Sensors.jpeg)
(image source: electricaltechnology.org)

This is definitely not going to be the most exhaustive review of different sensors and the most thorough outline of how they work and their effectiveness in different scenarios. However it seems like a good time to outline the different  types of sensors being considered for the bot, and list the pros and cons that each one has.

### Load Cells

A load cell operates on a pretty basic level in order to interpret events outside of the device doing the reading. In very general terms a load cell takes some mechanical force, and converts it into a digital measurement of what has occurred. This is useful to us, since we need to be able to understand when the device hits something. A load cell is going to be a very simple, and elegant way of translating bumping into a table into a perceivable event that can be reacted to. These are typically used for weighing things due to the sensitivity and accuracy of the devices, however for our purposes we can take advantage of this sensitivity to detect *any* spike in pressure being applied to the side moving around. I have, just to save time immediately discounted the more mechanical, and also the more exotic instances for consideration, the device will want to have minimal impact so hydraulic and pneumatic systems will likely be too large if constructed by me. In terms of the exotic ones like fiber optic cables, the level of sophistication needed isn't **that** high to warrant something that extreme.

#### Inductive Load Cells (Not just for boiling water!)
![Inductive Heating Picture](/assets/posts/induction.jpeg)

An inductive load cell is a pretty neat concept, and based purely on the concept is the one I would like to use if I don't get convinced when testing out the different options. If you don't know what induction is here is a quick primer. If you have ever used an electric cooktop in order to make food, where you could place your hand on the stove without burning yourself you have experienced the beautiful act of induction. Induction takes advantage of the connection between electricity and magnetism (probably has to do with why it is called electromagnetism), in order to create heat energy. The coil of metal in the cooktop is energised with an alternating current (the why doesn't matter so much for our purposes, but just trust me that you need an alternating current running through a coil to get the field you need), which produces a field around the cooktop. When you then take your pan and place it above the cooktop the energy contained within the field energizes the pan and heats it directly.

The inductive load cell operates by measuring the difference in induction detected by the placement of a ferromagnetic rod contained in a solanoid. Since the solanoid produces a constant directed field, (any of you electronic engineers will be able to hear my inexperience here) by inserting a core that can shift within it allows us to read the change in the induction as the core shifts within the coil. Since we will be likely using a bumper with some give, once the vaccuum hits a wall we can detect a shift in induction within the coil allowing us to detect we hit something.

This methodology should really do the trick, a solanoid with a ferromagnetic core is a pretty small order and with some additional research should be fairly simple to fabricate. There are several indcutive load cells for sale, and I would simply need to strip them down to the actual reader and the circuit that is reading it. With some modifications to convert it into a reader to waiting to trip a switch at a certain sensitivity we have a precise and most importantly nifty way of detecting the robot has walked into a wall!

#### Piezoelectric Load Cells

![Magia Negro](/assets/posts/greek.png)
(image source: gadgetbytenepal.com)

The piezoelectric effect is pretty crazy, it is what happens when an electric potential is created in a crystalline structure due to the application of mechanical pressure. Which means basically making a battery by smushing a rock. The process is produced by taking certain electrically neutral crystals (like quartz), that are not necessarily symmetrically aligned but are nonetheless neutral. In order to generate voltage within them one compresses the crystal. This forces the atoms out of alignmentllows for a positive and negative pole to develope along the sides of the crystal.

Now how do we take advantage of this you may ask? Why by making a transducer (well more likely buying one)! Our need for this sensor is to get a reading of when we have actually hit a wall. Since the mechanical pressure is going to create an electric charge, we can use this to flip a switch allowing a circuit to inform the system it has hit a wall. The sensitivity of the sensor depends on the material used, so we should be able to play around with different sensors and see what works best for the vaccuum in the event we use one of these!


#### Capacitative Sensors

![Zip zap breh](/assets/posts/capacitate.jpeg)
(image source: automation-insights.blog)

I am like 90% certain I won't be able to get one of these to work in a fool proof manner (but when the time comes I'll test it so I am including this). But roughly the use of a capacitative sensor detects when there is something that is either conductive or has a dielectric that isn't air (water for testing humidity if my memory on what a dielectric is isn't wrong). The problem with this seems pretty obvious, this is great if our device is hitting things like a person, statically chargable fabrics, but if there are non-conductive objects in a room then a capacitative sensor can not detect it. We will see, my knowledge of electronics is at best journeyman level so I may be misinterpreting this and will run some tests with capacitative sensors, if anyone reads this and I am talking out of my a^* let me know so I can correct this!

### Distance Vision

So we have talked about a few different contact sensors in order to detect when we have hit something. Now for some more intricate systems that don't just translate a whack into a signal. We need to be able to first of all tell how much space there is to traverse, and also in order to detect when something on the other side of the room is moving around the space it is patrolling. There is what feels like an endless number of options for this but I have narrowed it down to some more common methods that will be easier to source various testing sensors for the actual building process.

Our goals with these are to accurately read the distance of things, and to be able to accurately tell where something should be when the robot moves. The trickiness of course comes from the fact that the robot is moving and as such the sensitivity needs to be fairly precise in order to see when something is moving around, we also need a fairly wide angle of view (ideally 360 degrees) in order for the constantly moving device to detect these changes.

#### PIR (Passive Infrared)

![Passive Infrared Sensors](/assets/posts/PIR.png)
(image source: getsafeandsound.com)

Passive infrared is, if I can get it to work, a very good option to have alongside a radar-esque detector. Everything that isn't at absolute zero and floating in voids in space emits infrared energy. What a passive infrared system does is passively take in, and by passively it means that it doesn't emit anything itself but simply reads what is directed at it, the infrared energy that is within a grid in front of it. They utilize Fresnel (like the ones found in a lighthouse to amplify the xenon lamps contained within) in order to focus in the infrared energy coming from a region onto a chip that reads the energy. After the device has had sufficient time to get a baseline reading on the chip it can start constantly monitoring for shifts in heat changes. The process is pretty simple, if someone moves around the room then they will shift the latent temperature detected by the chip from the focused beams of the fresnel lens. When the intruder moves from one position to another this causes a shift in which spot of the sensor is experiencing an elevated temperature. Thus when detecting this type of shift the device can tell something is moving around and send an alert to the system.

One incredibly useful aspect of these systems is the fact that you can modify the point at which it triggers. By having an understanding of roughly what temperature a person is, verus say a dog or cat, you can have certain thresholds of shifting temperatures to alert the system of movement in temperature ranges expected of people only. Now there are concerns in getting a PIR system to function properly. First of all there is the fact that the device needs these focusing lens' to channel the energy properly, if the profile is too large and unweildly then the intruder may detect something is on the machine and be curious about what is on the monitoring device. Second is the fact that the device is moving, I need to do more research, but I do not think that it will work quite as well if it is unable to get a baseline temperature that is static. Most PIR's have a 'warm up' period where is get's up to temperature and is what it uses as a reference. Unless I can get this warm up period to occur in fractions of a second (which will probably mean big mirrors), then the device is likely to get an extreme number of false positives as the defensive grid changes with each movement forward and turn.

#### Active Infrared Sensors

![Infrared Sensors](/assets/posts/IR.png)
(image source: electricalfundablog.com)

This method will use more energy than the PIR but will likely serve a different purpose and be predominately used for navigation instead of detection. The basic principle with an active IR sensor is to introduce a transmitter along with the receiver. Instead of simply reading in the latent infrared temperature of a room the active sensor sends out a infrared signal, and there is a receiver (like a photodiode) right next to the transmitter. The object will then reflect back a portion of the unabsorbed radiation which the receiver will then be bombarded by. As the device get's close to the object the incidence rate (hence the name Reflective Indirect Incidence) of these collisions will go up. By being smarter than me, people have figured out the difference one should see between two differences for a given wave length. As such one can approximate the distance of an object from the sensor.

An alternative use for these types of sensors is for tripwires and burglary detection systems. The sensor is either two components, receiver and transmitter separated and placed on opposite sides, or they could be embedded in the same device and use the reflection to make a line. The system will then have a constant stream of IR radiation being either beamed directly to it, or being reflected to it at a constant rate. If an intruder moves through the line it will disrupt the connection, causing the system to know something has moved through it and causing a problem. We can use a similar methodology in our system to detect if something passes straight through the line being made but this creates some problems in being used for detection. The device is going to be quite low profile, meaning the intruder may full well step over the line and not be detected. To minimize this the device could be outfitted with a ring of detectors creating a 360 degree ring of beams, but that seems a bit overkill, not to mention needing to be careful of sudden shifts in range that could be seen by the beams on the side as it navigates past tables and such.

The best scenario is to have the logic programmed to detect if something all of a sudden breaks the connection between the range finder in order to have a redundancy in already present technology.

#### Ultrasonic Sensors

![Ultrasonic Sensors](/assets/posts/ultrasonic.png)
(image source: theengineeringprojects.com)

Ultrasonic sensors work by either comparing a receiver and a transmitter (like the image), or a transeiver in order to detect the distance it takes for sound waves to travel to and from an object. This is in principle very similar to the infrared sensors but it has a few additional benefits. For starters sound is slower than light which means the sensitivity needed is going to be lesser than and the need for signal amplification should be reduced. Secondly is the fact that glass will be detected whereas a LED will emit light that will pass through a pane of glass. There is also the effects that dust have on anything optical. Since this is a vaccuum there is likely to be dust accumulation on components, and a ultrasonic detector is looking for soundwaves and not light that could get dispersed or reflected by floating and caked dust.

We could use this for both navigation and for detection. The device would constantly emit 1 - 4 (depending on sensor position and type) ultrasonic signals and receive them back on the receivers. This would give a map of the various objects and their distances, by adding additional receivers along the body of the device we could gather a pretty clear image of objects in the area. The onboard computer would then maintain the expected positional changes as the robot moves along the environment. As such if something is moving through space then the sensors would detect a constantly shifting vector inside of the space it is in and could trigger an alert. Depending on the granularity of the mapping, we could even detect rough size of the object to eliminate incredibly small things like pets that might trigger the alarm.

#### [Microwave Sensors](https://www.youtube.com/watch?v=lUAoti2TwRk)

![Microwave Sensors](/assets/posts/microwave.jpeg)
(image source: pixelelectric.com)

You will have definitely experienced the effect taken of advantage of in order to detect motion via microwaves, called the [Doppler Effect](https://www.youtube.com/watch?v=OXUFF7ptH8k), which when an [ambulance drives towards you and away from you you can detect the difference in the pitch](https://www.youtube.com/watch?v=BgSoYt2uWBY) What is happening here is the shift that the sound waves are undergoing due to the distance they have to travel. As the ambulance comes closer and closer to you the frequency are more (not being scientific here) compressed and as a result are of a higher pitch. When the ambulance is right upong you the frequency is at it's highest as it bombards you. As it passes you and moves farther away the pitch shifts as the sirens signal needs to be pushed farther and farther to reach you. 

The same can be used for microwave detection as well. This means that if we have an intruder moving inside of the area then the radar will hit the person, and come back to us compressed or not allowing us to get directional data about the intruder. The microwave sensors sitting on the bot would emit a signal and then read what it receives back. By processing the shifted wave it can tell if it was interrupted or not. But there are some problems we may face, these signals are, well good at moving. We may have signals travelling through walls and detecting action outside, or in rooms we expect movement and aren't worried about. Presuming I can get a smart enough device configured to detect the shifts in the wavelength that would occurr beyond certain distances we can use this methodology to get some pretty precise information about an intruder. A future project may be to make a little doppler radar in order to detect positions and movement inside of my house and map out this information on a graphic.

### Other Sensors

The contact sensors and ranged sensors we have discussed are not the only options when it comes to sensors. There are other ways to see if things are happening around the bot, some of these include detecting movement through vibrations, or by using advanced image processing tools. These are unlikely to be used but I feel they might be nice to discuss (who knows maybe I'll land a nice paying job in uni and get some of the high paying internships and I can begin throwing money at sensors with reckless abandon).

#### Vibration Sensors

A vibration sensor would serve some pretty nifty diagnostic conditions to maintain the condition of the device. Placing something to detect axial or radial vibration along the drive shaft would allow us to be able to see if there is some issue being generated by the wheel, motor, etc. In terms of detection of intruders we could implement various types of load cells in the suspension of the roomba (if there is suspension). We could then calculate expected load exerted on these sensors as the device operates normally. Then in the event that something is causing an increased load on the cells we could then try and figure out why this is, either for diagnostic purposes or to see if someone is stomping around nearby.

I think the best use of these is for diagnostics, detection is doable but a bit tricky for me to think of ways to tease out the ways of just isolating foot falls..

#### Thermographic Cameras and Other Camera Based Sensors

![Infrared Pomito](/assets/posts/infrared_pom.jpg)
(image source: wikipedia.com)

Cameras are probably not an option for the roomba. These are going to be computationally and electronically expensive to implement. The basic premise of using any type of optical sensor would be to create a 2D or 3D image and to then use image processing software to see how far things are, and to tell if there is movement going on in the image. This isn't as expensive as a recording device, but if we are implementing cameras on the board we might as well store relevant information. One possible usage would be if there are not other devices connected to embed a thermographic camera in the device. Then when we detect movement via some way it snaps an infrared snapshot of the space it detected the movement for later review.

## Conclusion

The main conclusion to draw from this is that there are a lot of sensors that are going to need to be tested. In an ideal world, we would have probably inductive contact sensors. And then implement for range finding ultrasonic transceivers that will detect distance to objects. On the bottom of the device we will want to have some infrared sensors in order to prevent the device from falling off a ledge. Since the speed of light is faster than sound it will be best to use in this instance. Lastly for detection either a ultrasonic, microwave, or some combination of these more precise methods and infrared redundancies will be used. The use of ultrasonic seems ideal, since we can work in the alert system into it as well. Doppler is a strong contender if we can overcome the fact that it can see through walls, which is neat, but going to cause a lot of false alarms.
