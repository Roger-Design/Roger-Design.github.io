---
title: The Scud of the Clouds
tags: Privacy Projects
mode: immersive
header:
  theme: dark
article_header:
  type: cover
  image:
    src: assets/header/skim.jpg
---

## Magnets, Burglaries, Bluetooth, Faraday,

Credit and debit cards always held a magical allure to them for the longest time for me. There seemed like a great deal of power, and responsibility in these little pieces of plastic that could in a moments notice let you buy a snack, a tool, or as much as a vehicle. In my adolescence cards with chips came out and the capability for someone to take this magical device, tap it against a reader and make a payment was possible. It is, without a doubt, a much less mystical world understanding how these little pieces of plastic function and how they aren't really magical at all but incredibly basic. And what is worse, the understanding of how these work really show the vulnerabilities in this format that we use to pay for our things. Let's first discuss what a credit card is, then let's discuss the problems with them, then on to the meat of the topic, credit card skimmers. This is going to be fairly in depth, but not incredibly in depth, I'll link in a lot of articles going over the specific mechanisms and how they work at the end if you are interested in the tools.

## Dispelling the Illusion of the Magnets

All credit cards contain a little black strip on the back, similar to a hotel key card, or employee ID card. That similarity is because they all function in an identical fashion. The little strip on the back is a plastic film that contains little iron based particles. These can then be magnetized north or south creating a little sequence of [bar magnets](https://www.bbc.co.uk/bitesize/guides/z3g8d2p/revision/1). One can actually see the magentized pattern by getting a solution of very fine metal particulates that will stick to the magnet. Mix it with a little high proof alcohol, and then coat the strip. As the solution evaporates the particulates that have stuck to the magnetized portions will be left behind revealing the sequence (you could decode this but that is a bit low tech and inefficient for our purposes). In order to store more information and to make sure things are formatted right, there are three tracks with varying bit density and as such different information is to be written on each track. All of that information is a bit beyond the scope of this post, along with information about the actual authorization process and acquirers. [Here is a link, that should be a good starting point, if you find the idea of learning about that stuff as interesting as me](https://money.howstuffworks.com/personal-finance/debt-management/credit-card2.htm). But in summation what you need to know about the magnetic strip and the payment process it follows is:
1. The strip on the back of the card is a series of magnetized bars.
2. This sequence is all of the information on the card/card holder needed to authenticate the card holder.
3. A POS (Point of Sale), terminal takes this information and authenticates this data with an exteral authority.
4. If the card is valid the payment is processed.

## A Better Way?

The previous method has some flaws has some ugly flaws, which we will go over later. These flaws have been extensively and aggressively exploited and as such a better solution was wanted. An extraordinary number of cards issued currently contain contactless payment capabilities. As such this warrants some discussion, the later sections won't touch too much on the methods for exploiting this payment method, but be aware if you are making a contactless payment and a shifty looking person is perched across the street with a directional antenna pointed at the card reader there is a good chance they are picking up on the communication between your card and the reader.

### What is a Contactless SmartPay Solution?

This section is going to assume a very little knowledge of RFID, so if you already feel confident about your knowledge of basic RFID technology just skip this section entirely. At it's core an RFID chip is a fancy omni-directional bar code which isn't limited by the line of sight of the reader. This is done by embedding in the tag (tag is a loose term, but basically refers to the whole device), an antenna and a chip which is able to leech power off the reader device and then produce a (relatively) high frequency radio transmission containing the data sent out by the chip. This process was first employed by shipping industries and other industries that needed to track inventory. However as the devices have gotten smaller and more versatile they have found uses in many more situations, such as credit cards. There are other versions of RFID trips which utilize batteries in order to broadcast a more powerful signal but this puts a lifespan on the devices operability and limits conditions that it can be used in. Back to the ones we are discussing LF Passive RFID's. The basic process of an interaction is as follows:

1. A reader is triggered to produce a magnetic/electrical field to allow for charging of a passive tag
2. RFID tag's capacitor is charged by the field emitted by the reader (think of a smart phone with wireless charging).
3. The chip on the RFID tag computes what it needs to compute, and transfers this data to the data via the antenna.
4. The reader receives this data and is able to process it however it needs to.

So a pretty nifty technology, but it has some limitations. A tag is only able to produce a reliable communication with the reader based on the field produced by the reader and the size of the antennas in question. As such someone can limit the reading and spoofing capabilities of an attacker by making the antennae intentionally small and weak. Or by boosting the amount of energy needed to be accrued by the capacitor for functionality. I believe, but have had difficulty confirming since it is a bit beyond my skill level and degree path, that a resonance frequency is needed to be attained in order to let optimal current flow(Not an electric engineer or computer engineer, I can only strip down machines and change them modestly at this point). There are undoubtedly more limitations but again, it is a bit beyond the scope of this and the knowledge I need.

## Improvements from RFID Chips

Now there may be limitations in RFID chips but that doesn't mean there aren't perks to this new technology. For starters it effectively eliminates the nefarious merchant risk, the need to hand over the card to a clerk is gone as the contactless payment is so minimal effort. It is also more effort for someone to actual get the data from an RFID chip in the instance of a nefarious merchant, the lack of a clear record of information is very beneficial many regards. Another type of improvement is that some cards provide an ever changing cryptographic sequence. This means that in order to verify a card with an external authority the attacker would need to intercept the card, spoof the card, and then make a payment before the cardholders next purchase. Otherwise the adversary would need to break the cryptographic method used to generate the unique code, which if they did that then this blog post isn't gonna prepare you for someone of that caliber. These improvements should not be discounted and make for significantly more secure payments than previous methods. And whilst there are ways to make it more secure, such as sensors to detect intent (light or motion sensors) or a little button to enable the capacitor or antenna it is still better than having cleartext credit card information that is easily harvested with a skimmer.

### Disclaimer

First just a disclaimer to the reader. I really wouldn't recommend going around making skimmers and sticking them on stuff. It is definitely very illegal and people are getting wiser to them. Particularly the devices we are going to be discussing in more depth the ability to scan and find them is getting more and more advanced. This is not a tutorial on how to get started making a skimmer and shouldn't be read as such. It is a jumping off point on a theory for a future device that will be discussed on this blog. So please, don't go breaking the law and trying to steal peoples credit card data, it is definitely rude.

## Skimming

So what is skimming? Skimming is very much based on it's name sake of just pulling some off of, usually, the top of some liquid. A skimming device operates to intercept the data that is being given to a system and then passing the rest on to the system to allow for regular transactions. There are various types of credit card skimmers, the most primitve is an external cover for a reader that reads in the information of a card in tandem with the credit card reader. The header image for this post is an image of one such device. They are traditionally not as clever and neat as they have gotten. But nowadays skimmers are able to put a cover onto a device and then skim it with shocking subtlety. One can attack an RFID chip by exploiting the passive nature of the device. If a user were to get an RFID reader up to a card and power the capacitor they would receive all the information that a regular reader would receive. A very clever and savvy attacker could also intercept the communications between a reader and a card by placing an antenna in range to pick up the conversation of a reader and card. But what we are interested in is a more subtle method, that we can later spin off to new methods of attack for differet readers and scanners. A small PCB, connected to the internal mechanism of a reader that intercepts the data feed from the reader itself, stores the data, and then forwards the data on to the rest of the machine to process and request authentication.

## Bluetooth Fraud

These devices can be broken down to a handful of components. First a PCB, this can be a small and cheap board as it really only needs to hold a handful of components. The skimmer requires fairly paltry amounts of memory and storage, and the main expense is having a bluetooth component to allow for remote exfiltration of data. Power is not a particular concern for most of these devices, especially ones designed for fuel pump card readers as they are able to be supplied power by the reader itself, and are able to operate indefinitely (or until the device runs out of storage). The attacker will need direct access to the reader and this presents a few issues. One if they are discovered they are going to be in a bit of a pickle. But by taking advantage of time and social engineering a capable adversary can access these things with varying levels of ease.

## What We Need

For our skimmer design of choice we need to consider a few things when designing our implementation. First our connection, we'll want to scope out the target device and get as much information about it as possible. Fortunately for us branding is not something a company will refrain from and you can learn a shocking amount of information from a distance about a device. With a little bit of OSINT investigation you should be able to gather information on it's construction, either from posts about it online, manuals online, patents, etc. Armed with this information you'll be able to figure out how you will need to interface your Input and your Output for the skimmer. Secondly, storage is a vital consideration. How many transactions do we expect to take place on the given device and how much data is going to be moving back and forth. For credit cards this is simple to deduce as we know how many bits of data *could* be stored on the given tracks of a card and you can simply multiply that by expected number of transactions to figure outa good amount of padding in terms of memory. Lastly is data exfiltration, this is very important as you won't get a lot of use out of your skimmer if you can't see what data you gathered. Bluetooth is a strong contender as it is cheap, readily available, and can be connected to via a smartphone, computer, or really any device with ease. Bluetooth should be used cautiously however, and paired in advance. As bluetooth skimmers have become more common Police Agencies have begun scanning for these bluetooth devices in order to detect them. Pairing in advance will allow you to prevent people from pinging them, but requires you to not lose the given device and will leave a direct trail to that device in the future. These are some considerations to take into account when designing any skimmer not just a credit card skimmer.

## Conclusion

There aren't a lot of things to take away from this but one should be cognizant of the risks that are prevalent when walking around with a piece of plastic with access to large amounts of their money. Obviously it is risky to go around only carrying cash but once should have robust measures in place to detect fraudulent purchase. While you may have to occasionally respond to a text from your bank it is possible for copious amounts of devices on interacts with to be compromised. A second more interesting line of thought can also be pursued from this point, what other things require very clear and easy to read transfer of **secure** data that we just presume to be safe. A skimmer isn't necessarily a device just for targetting credit card data and have many more applications. One should consider these things with all of their security solutions. Simply because you can't see an intricate operation doesn't mean that someone with the right, inexpensive device, can't see precisely what it is you are doing and spoof your interaction. While the mystique of these things is no longer there for me and that little bit of magic is gone, it is better to lost that and better understand these flaws and ways to secure them than to not.

--Roger

## Post Script.

Here are some further reading on skimmers that go a little more into detail and are actual scientific papers.

[An Aperture Labs presentation of PIN harvesting and skimming](https://files.laggy.org/infoconatdc27/contents/cons/Hack%20In%20The%20Box/HITB%202011%20-%20Malaysia/D2T1%20-%20Daniele%20Bianco%20and%20Adam%20Laurie%20-%20Credit%20Card%20Skimming%20and%20PIN%20Harvesting%20in%20an%20EMV%20World.pdf)

[An analysis of different skimming devices, pretty neat.](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=5609418)

[A good, and intentionally dated, paper on the skimmers that are of interest to me. Definitely a great place to start reading.](https://dl.acm.org/doi/pdf/10.1145/3404663.3406874)

[RFID card vulnerabilities, there is a lot in this whole thing, but it is good.](https://d1wqtxts1xzle7.cloudfront.net/30838821/Sven_Dietrich_Financial_Cryptography_and_Data_S.pdf?1362514335=&response-content-disposition=inline%3B+filename%3DVulnerabilities_in_first_generation_RFID.pdf&Expires=1612566807&Signature=bs-eGUkYShhEW8AqgYDO11melwVmIluWUzGQu1kO895aWMyOrmcp-h1k0TOBdsiiJmzNWmykC10AIAgnoc2vUg1gsJdzr1pibBNJo-hrfHLcaQ~M8N2X9e6tFtxtop5uV1cgcslQ8iKBvSyK-nrlGnI-Z7RQNkiFltyt-tEs96lxJsCSUk6~u3ZRNFOyZ1cjy3vYbmubYxn3xs8dQVh2U6b4bUwpSQwIbgVT1eZONQbuYDHMorgobNGwCGtEDSPl0YbvXDFOPZr6S9XWrv7R~uk78UJg-2WPTVM70-awWXP9nvkXu9Imy8FU2eJFQovymX1pKUNlRHHQk6gHteP9tg__&Key-Pair-Id=APKAJLOHF5GGSLRBV4ZA#page=13)

