---
title: Building Lumenary for the Portland Winter Light Festival
date: 2019-02-14 12:46:03
tags:
- Art
- IoT
- IoT Art
---
This past weekend, I displayed my interactive art sculpture titled "Lumenary" at the 2019 Portland Winter Light Festival. It was an amazing experience to be part of the artist community showcasing their artwork, and to experience displaying my own art piece to the greater community.

Here's Lumenary: a modern-day interpreation of an image created by a twelth-century mystic named Hildegard von Bingen:
&nbsp;

{% asset_img Lumenary_At_Night.jpg Lumenary at night %}

In essence, Hildegard had a vision of the interconnected nature of people, animals, and the entire cosmos. She spoke her truth in an environment that did not always value her message. Lumenary is an homage to her strength as a person, and for the message that seeks to find the bridges that connect people, and also values the environment.
&nbsp;

{% asset_img FoL-LumenaryDescription-cropped.jpg Lumenary Meaning. %}

In this post I'll share some of the highlights and milestones of building Lumenary.

Initially, I was intrigued by the story of <a href="https://arthistoryproject.com/artists/hildegard-von-bingen/">Hildegard von Bingen</a>, as described by the theologian Matthew Fox. In particular, I was drawn to an illuminated manuscript containing an image by Hildegard, which depicted the essential unity of the cosmos:
&nbsp;

{% asset_img Hildegard_cosmos.png Hildegard's Cosmological Vision. %}



I was intrigued by this image for a variety of reasons, but especially for how the image reminded me of Jung's mandalas, the beautiful interplay of colors, and especially how the message of connectedness and unity was reflected in the imagery. In today's society, oftentimes we are exposed to messages that stress the divisions amongst ourselves. Thus, this message of unity seemed especially relevant and timely.

A big part of Lumenary was the interactive aspect, which was generally provided by a raspberry pi microcontroller, as well as several Arduino microcontrollers. These tiny computers were attached to sensors, and through their programming allowed for responsive light interactivity via LED strips. With the Raspberry Pi's built-in wifi capabilities, I built an application using using cloud platform and services, including serverless architecture, and such resources as a MongoDB database, AWS Lambda, API Gateway, Cognito, and more.
&nbsp;

{% asset_img RaspberryPiEnclosure.jpg Working on the Raspberry Pi. %}

This was where most of the work got done: my laptop, a soldering machine,a third-hand helper for holding the small electronic pieces for soldering, the various microcontrollers, and of course, copious amount of coffee :)
&nbsp;

{% asset_img CodingSetupForLumenary.jpg My Workspace. %}

I found that the most useful sensor was the HC-SR04, which uses ultrasonic waves to determine the proximity of an object. This type of feedback provided much of the interactivity of the interaction, changing lighting patterns as a person drew near.
&nbsp;

{% asset_img ultrasonic_sensor.jpg Ultrasonic Sensor. %}

Here's a glimpse of hooking up the HC-SR04 ultrasonic sensor to the Arduino:
&nbsp;

{% asset_img Arduino_HCSR04.jpg Ultrasonic Sensor & Arduino. %}

One of the microcontrollers that was used was Adafruit's Trinket, which was useful because it was lightweight, and it's circular shape mirrored that of the NeoPixel LED ring. Together, they provided a light source and interactivity towards the upper part of Lumenary. In addition, the NeoPixel ring provided the light source for a crystal hanging from it, providing moving "stars" on the canvas as the wind gently moved it in relation to the light.
&nbsp;

{% asset_img Trinket_NeoPixel_Ring.jpg  Trinket & NeoPixel Ring. %}

Here's a snapshot of doing the coding needed for the microcontrollers to control the LED lighting patterns:
&nbsp;

{% asset_img CodingLEDInteractivity.jpg Coding the Arduino for LED Strip. %}

Now, onto the physical layer of Lumenary!

First, the frame was created for holding the canvas (a cotton sheet) using 1/2" pine:
&nbsp;

{% asset_img CanvasFrame.jpg Canvas Frame %}

Then filling out the canvas. The goal was to create an art space that mirrored a traditional painting canvas and easel:
&nbsp;

{% asset_img TheWhiteCanvas.jpg Canvas %}

With the frame completed, the Raspberry Pi, a fish tank with a beta fish (to represent the Ocean element) and lighting were added in stages:
&nbsp;

{% asset_img Canvas_RPi_FishTank.jpg Canvas with RPi %}

As the piece grew, elements were added to the canvas for representing an interpretation of Hildegard's original vision. The Trinket and NeoPixel ring was added to the top of the canvas, El-Wire was added to the side to represent an organic aspect of nature/land. Bit by bit, pieces were added to the canvas.
&nbsp;

{% asset_img CanvasRPi_ElWire.jpg Canvas with El Wire %}

Part of the imagery that was needed/wanted was to add the mystical elements, and that was provided by crystals. Light bulbs, with their embedded connotations of thought and creativity, were added, and as you can see, crystals were added to them as well. 
&nbsp;

{% asset_img LightBulb_Crystals.jpg CLightBulbs with Crystals %}

One challenge was adding all the myriad wiring and electrical/electronic components without detracting from the overall aesthetic. Here was one junction that invited some creative approaches!
&nbsp;

{% asset_img RPi_Electrical.jpg Aesthetic challenges %}


With the Festival happening in the dead of winter, I tried to protect the electronics as much as possible. I will need to do a better job on this part, as I lost some of the sensors when it started to rain hard on Friday night.
&nbsp;

{% asset_img Protecting_Electronics.jpg Protective challenges %}

Transporting Lumenary to the Festival site was facilitated with copious amounts of Syran Wrap, and duct tape:
&nbsp;

{% asset_img ReadyForTransport.jpg Transport challenges %}

Here was the setup, having been moved under a shelter as there was a major storm in Portland - yes, snow and rain.
&nbsp;

{% asset_img DaytimeSetup.jpg Setup challenges %}

At night, Lumenary lived up to it's name, and people were drawn to inspect the piece more closely.
&nbsp;

{% asset_img PeopleInteracting.jpg People interacting with Lumenary %}


Here's Lumenary Lit Up At Night
&nbsp;

{% asset_img Lumenary_At_Night.jpg Lumenary at night %}

A special thanks to my sister, Karen, who came to help me on the project! :)
&nbsp;

{% asset_img Karen_And_David_Lumenary.jpg Lumenary with me and Karen %}

In conclusion, it was a wonderful experience, and I had some great conversations with people who were intrigued by Hildegard. It was enrichening to feel like I was part of an important conversation, and hopefully provided a glimpse into an amazing historical figure.