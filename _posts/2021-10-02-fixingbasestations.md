---
layout: post
current: post
cover:  assets/images/reverb-title.png
navigation: True
title: Base Station 2.0 Repair Guide
date: 2020-12-29 10:00:00
tags: [vr]
class: post-template
subclass: 'post'
author: ilja
---

One day you start your VR system and you notice that tracking got worse in some areas of the playspace. You check SteamVR and see that one of the base stations is not tracking. You peek at a base station and see a blinking red light. OH NO!
If you still have the base station under warranty, no need to panic, this can happen, you just contact Valve/HTC support (depending where you bought it from) and they will offer you a replacement. Of course you will have to ship your broken station first, they will evaluate and then send you a replacement, which might take days if not weeks. That is why I keep two spare base stations around.

But what if you are out of luck and the warranty has expired? Time to take matters in your own hands! First identify the issue. Unplug power from the base station, wait five seconds and plug it back. I have seen two different cases of failure:
At first light is green, you can hear motors starting to spin, but a few seconds later - red light. Slow red blinking light means the laser in the base station has failed. It will require a replacement. 
Immediately fast red blinking light and no sound of the motor - it means that either one of the circuits is dead or the motor. 

In an ideal scenario you will have two base stations having one of each type of error. That way, you can combine two broken base stations into one working one.

## Identify your revision

Identify which revision of the Base Station 2.0 you have. All 2.0 BSs have round glass in front, while 1.0 has flat glass. I have seen three different revisions of 2.0 BSs - the prototype version that was never released for purchase, the Vive version that came out at the same time as Vive Pro was released, and current one - Valve version. 

![](/assets/images/base_station_repair/EVT1.jpg)
![](/assets/images/base_station_repair/EVT2.jpg)
![](/assets/images/base_station_repair/valve.jpg)
*Here are the pictures of the prototype base station*

Vive versions are identified by having a sync 3.5 mm port in the back and glass going to the sides of the device. 


![](/assets/images/base_station_repair/vive_valve1.jpg)
![](/assets/images/base_station_repair/vive_valve2.jpg)
*Vive version of base station on the right, Valve version on the left*

Vive versions are not being released anymore, as Valve is responsible for producing all the base stations themselves and then selling them to partners. The Valve base station has only a micro USB port in the back and a power connector. 

![](/assets/images/base_station_repair/EVT3.jpg)
*Valve made base station (current as of August 2021)*

## Disassembly

Disconnect your base station from the power. 

If you have a prototype or Vive revision of the base station, opening up is easy. Just remove the bottom rubber layer (it is sticked by a double sided tape) and you will see the screws for opening it up.

![](/assets/images/base_station_repair/bolts.jpg)
*Access screws on the bottom*

For the Valve version things get more complex. Valve really, really, REALLY doesn’t want you to open the base station. Doesn’t mean it will stop us. 

Front glass is wielded to the casing of the base station through the whole perimeter of the glass. Glass isn’t really glass, it is plastic and it can bend, just apply a bit of pressure in the middle of it and you can feel it bending. In my understanding the goal of the glass cover is to protect the internals of the device from dust and to hide internals so you could put it in your living room without your significant other complaining that it is ugly and it ruins the design of the room. 

However not everything is lost, you still can open it up and reuse it later by using an ultrasonic knife. Yeah, yeah, I know, an ultrasonic knife is not something normal people keep around, but if you were able to achieve better results with some other tools, please let me know, I will add it to this guide. 

![](/assets/images/base_station_repair/open1.jpg)
*Not the cleanest job done with removing glass (tools used - knife and pliers)*

![](/assets/images/base_station_repair/open2.jpg)
*Better job done with ultrasonic knife*

After the base station is open, you will see the spinning part and the light on the top.
Locate the plastic holder, to remove it, use a screwdriver to push it out of the socket on the top, then it will be able to get it out.

![](/assets/images/base_station_repair/plastic.jpg)
*Plastic holder is just being held in place by one pin*

Now you have access to the screws holding the main internals. Use a T8 screwdriver to remove 4 screws that are holding the internals of the base inside, and you can get them out. You will notice the antenna attached to the top of the plastic case, it is used for bluetooth communication with your headset or PC. 

![](/assets/images/base_station_repair/dissasemble1.jpg)
*Only 4 screws are holding it in place*

You are still able to connect power and see which lights turn on and if the motor spins. 
Taking it further apart is straightforward.

Remove four screws on the main motherboard to take it off.

![](/assets/images/base_station_repair/dissasemble2.jpg)
*4 screws are holding main circuit board in place*

Three screws to remove the top circuit.

![](/assets/images/base_station_repair/dissasemble3.jpg)
*3 screws for a secondary PCB*

4 screws are holding the metal case to the motor case.

![](/assets/images/base_station_repair/dissasemble4.jpg)
*4 screws (note the part pointed with the arrow is  on the upper side, you will need that for assembly)*

Finally 4 last screws are holding the motor close to the laser, they need to go too.

![](/assets/images/base_station_repair/dissasemble5.jpg)
*Last 4 screws we need to remove*

Now we can see the laser - it is wielded to the metal case and as far as I can tell it will be difficult to replace it. 

![](/assets/images/base_station_repair/laser.jpg)
*There is no simple way of replacing laser*

But if you have a donor base station with a working laser, you don’t need to take it out, just take the whole case from the donor and start assembly

![](/assets/images/base_station_repair/laser_motor.jpg)
*The part with a laser separated from the motor and mirror system*

Do it in the same order - motor, metal bracket, top PCB, main PCB. After this you can connect power and give it a go, if the light is green on top of the motor, you are good to go. Just assemble it back and don’t forget the plastic holder. The “glass” can also be placed back and glued on the edges. Or just use black electric tape to tape it on the edges. 

![](/assets/images/base_station_repair/fixed.jpg)
*You can see that it was opened up if you look closely*

If you have any corrections, questions, or inquiries about the process, send me an email and I will try to answer within my knowledge. 
