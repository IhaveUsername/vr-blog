---
layout: post
current: post
cover:  assets/images/base-station.jpg
navigation: True
title: SteamVR HMD's - technology teardown
date: 2020-09-15 10:00:00
tags: [vr]
class: post-template
subclass: 'post'
author: ilja
---

This article will dive deep into explaining how the SteamVR tracking technology works and will show how tracking point placement affects HMD's behaviour. I've also analyzed all consumer devices that rely on SteamVR tracking.

## SteamVR tracking

SteamVR tracking system (don’t mix it with the SteamVR software) is based on one or more base stations that emit lasers at fixed time intervals. This system is used in devices from many manufacturers, and Valve is kindly allowing it to be used for free with only one condition. Your device has to support SteamVR software. 

Main limitation of SteamVR tracking is that the lasers are easily reflected by glass, mirrored surfaces, glossy furniture, and when bounced back they can create tracking issues. 

If you want to create a SteamVR tracked device you will start with a mesh of Light-to-Digital Sensors located on the surface of your controller/HMD. Sensors should be distributed evenly, so at any point base stations with emitters will see two of the sensors. It is enough to see two sensors at any given moment for accurate tracking. 

## How SteamVR tracking works

Every version of the base station of the SteamVR tracking system has been following similar techniques to track devices. Each base station contains two lasers - first is lighting through the room moving horizontally, second one is moving vertically. In the SteamVR base stations 1.0 there is also a grid of flashing LEDs. This grid would light-up, sending “sync flash”, telling all the visible sensors to start counting, then one laser would pass, and every tracking point would record time difference between flash and when it was beamed by a laser. Then the process will repeat for the second laser. Based on the delay between flashes and laser signals, the system can calculate where in the two dimensional plane each tracking point is located. Knowing at least two points positions the system can introduce a third coordinate (and also calculate angle and rotation of the headset). It is possible because locations of the tracking points are already predefined in SteamVR software - it contains a very simplified model of the HMD or/and controllers with information about actual distance between two tracking points. This calculation is happening at 1000 Hz which makes SteamVR tracking the most accurate tracking in the consumer VR device today. 

In the base stations 2.0 the main concept remained untouched, but hardware was optimised. Instead of anonymous laser signal, 2.0 stations shoot a laser already containing “sync flash” timecode and base station ID - this way the amount of LEDs and other active components in the base station was reduced. It is also now relying on a single rotating motor instead of two, lowering chances of the mechanical failure. 

## HMD comparison

Now when we know how SteamVR tracking works, let’s have a look at some of the devices that use SteamVR tracking. I have not included Varjo headset in this list for two reasons - first, it is not a consumer device, second, I used to work there and my analysis of Varjo headset could be seen as biased. We will go from the best tracking to the worst tracking in this list. 

## Valve Index
Let’s start with a device that has the best positioning of sensors today. Valve has developed this tracking technology, so it is not really surprising that they have best tracking in class. It’s not like Vive or Pimax has bad tracking, but in the tests with robotic arm, Index was showing better results. I cannot disclose who and when tested it for confidentiality reasons, so you will have to believe me. 

![](/assets/images/index-front.jpg)
*Tracking points on the front of the Valve Index*

There are 9 tracking points on the front on the headset. Note that all of them are located outside of the glass panel area (removed on the picture). It is done this way because typically the laser passing through the transparent panel would slightly bend resulting in tracking issues. However on Valve Index the glass panel is reflective for the visible light (that’s why you can see your reflection in it) but it would not reflect the laser light, letting it pass through. This is a reason why there are no tracking issues with controllers, the front panel simply wouldn’t reflect lasers.

![](/assets/images/index-side.jpg)
*Tracking points on the side of the Valve Index (other side is mirrored)*

On each side of the headset there are five tracking points, most of them are located on the curved parts, so they will be visible from wider angles.

![](/assets/images/index-top.jpg)
*Tracking points on the top of the Valve Index*

There are seven tracking points on the top. Note how three points in the center are slightly lifted. That way they can be tracked also from front or side, depending on the user’s head angle. 

![](/assets/images/index-bottom.jpg)
*Tracking points on the bottom of the Valve Index*

Finally there are six tracking points on the bottom. I am a bit disappointed with placement here - tracking points can be easily covered especially if you are holding a headset with two hands. However, as we know from the teardown, middle space was taken by the IPD adjustment mechanism, so I guess Valve had to compromise.

In total there are 32 tracking points - the number is not random. It is a limit of trackers that could be attached to a single tracking processing microcontroller. If you would want to have more tracking sensors - you would have to install a second microchip inside, which would have greatly complicated things. 

## Vive Pro

Let’s compare how tracking is different on the arguably best Vive headset up to date. HTC made a decision to use tracking points as part of the design, giving their headsets this futuristic look, that is easily recognisable. 

![](/assets/images/pro-front.jpg)
*Tracking points on the front of the HTC Vive Pro*

Front panel of the Vive Pro has fourteen tracking points - the location of the sensors almost didn’t change since the original Vive, but it has become symmetrical horizontally and vertically. I have a feeling that the sensor location on the Vive Pro was guided more by the design team rather than the engineering team. 

![](/assets/images/pro-side.jpg)
*Tracking points on the side of the HTC Vive Pro (other side is mirrored)*

Each side has five sensors. 

![](/assets/images/pro-top.jpg)
*Tracking points on the top of the HTC Vive Pro*

On the top side there are only four tracking points. Points are facing more to the side, rather than upwards. HTC doesn’t expect players to be directly under the base station. 

![](/assets/images/pro-bottom.jpg)
*Tracking points on the bottom of the HTC Vive Pro*

Bottom side is symmetrical to the top side with only four tracking points. It is enough for most situations when you look up in VR.

In total there are again 32 tracking points. I will argue that the top and bottom side of the headset wouldn't track as well as the ones on Valve Index due to the small amount of tracking points. But scenarios when the base station could only see top or bottom sensors seems to be unlikely. 

## Vive Cosmos Elite

This headset is a weird one. Don’t get me wrong, I like the idea of modular faceplates. If you want to play casual games, you can get OG Cosmos with their horrendous (in my personal opinion) controller tracking. But having tracking sensors only on a thin faceplate creates some limitations. 

![](/assets/images/cosmos-front.jpg)
*Tracking points on the front of the HTC Vive Cosmos Elite*

In the front there are still 14 tracking points. Design has changed, there is no more recognizable Vive spirit on the face of the HMD. Four points that are closer to the center are faced inwards, so the tracking point on the bottom is best visible from the top, left tracker best visible from the right and the other way around. However notice how close sensors are to each other on the top and on the bottom. It is much easier to cover multiple trackers at once if you bring a hand or a controller close to the face. And if you take off the face plate, you can see that there is nothing that would obstruct from putting sensors closer to the cameras.

![](/assets/images/cosmos-side.jpg)
*Tracking points on the side of the HTC Vive Cosmos Elite (other side is mirrored)*

Side of the front plate has only three tracking points. And here you can clearly see how HTC have shot themselves in the foot by choosing a faceplate approach from Cosmos. Look at how much space there is around the side camera. You could easily fit there another pair of trackers which will make tracking better when not facing base stations. 

![](/assets/images/cosmos-top.jpg)
*Tracking points on the top of the HTC Vive Cosmos Elite)*

There are six tracking points on the top. But again, look how close they are to each other and how much space there is closer to the head. And what if you would shove some of the trackers in the halo strap? (Latter one wouldn't actually work as the headset can flip up, so the distance between track points on the headset and on the strap will not be constant).

![](/assets/images/cosmos-bottom.jpg)
*Tracking points on the bottom of the HTC Vive Cosmos Elite*

Bottom side is symmetrical to the top side. So much space to use, it hurts!

As you might have guessed, Cosmos Elite has the weakest tracking out of three headsets discussed here so far. But it doesn't mean it is bad. It just means in situations when there is a single base station in a room, it will fail earlier than Valve Index or Vive Pro would. 

And now about that faceplate. If you would like to buy it separately, it will cost you about $200 or €220. And what you get are 32 sensors, a small microcontroller, a proprietary connector, and a bunch of plastic that makes it look fancy. If you would want to buy your own HDK with 32 sensors and microchip, you could get it from [Tundra Labs](https://tundra-labs.com/shop/tl448k6d-gp-hdk) for $129.99. And what you will be getting is the consumer version, I am sure HTC is getting it a bit cheaper. My point here? No point, companies have to earn money, I just enjoy knowing how much they are earning from every purchase.

## Pimax 5k+

This was a tough one to dissect. On the Pimax headsets you cannot see tracking points with your bare eyes. Even though I have both 5k+ and 8k+ HMDs, I was terrified of the idea of taking them apart just for the purpose of showing tracking points. Mainly because of how fragile the casing plastic is, but also because my main expertise is in teardowns not the assembly. However, since the laser can penetrate the plastic case, so can I. I have found an old surveillance camera with an IR mode, connected to the pc and viola, I can see inside the Pimax. 

![](/assets/images/ir-pimax.png)
*This is how IR camera sees Pimax HMD*

That allowed me to find all 32 tracking sensors and map them on the photos.

![](/assets/images/pimax-front.jpg)
*Tracking points on the front of the Pimax 5k+*

The amount of tracking points on the front of the headset is underwhelming, especially considering the size of the HMD. It makes sense that Pimax was the worst SteamVR tracked headset in the tests - covering a bunch of sensors would be so easy. 

![](/assets/images/pimax-side.jpg)
*Tracking points on the side of the Pimax 5k+ (other side is mirrored)*

However, while they fail to put enough sensors on the front, they might have put a bit too much on the sides. Each side has nine tracking points. They are packed tightly, but they are facing in different directions on different planes. 

![](/assets/images/pimax-top.jpg)
*Tracking points on the top of the Pimax 5k+*

On the top there are also only six points. It is disappointing that they didn’t use elevated areas in the middle for additional trackers - it would have been useful for situations when the user is close to the base station. 

![](/assets/images/pimax-bottom.jpg)
*Tracking points on the bottom of the Pimax 5k+*

If you were counting up to now, we’ve already found 30 tracking points. Which leaves us with only two tracking sensors for the bottom side of the headset. I guess Pimax really doesn't want you to look up much. Also I think it is related to a mount at the bottom for the hand tracking module - Pimax didn't want to block the sensors for people who will get that module. 


## Conclusion

When you are designing the headset, you will have many opportunities to screw things up. Hopefully after reading this article you will know the limitations of SteamVR tracking and design HMD better. Make sure to leave space for strategically placed tracking sensors, balance their placement and test prototypes thoroughly from all the angles. I really hope to see more devices relying on this tracking system in the future, not only business oriented, but also consumer oriented. 
