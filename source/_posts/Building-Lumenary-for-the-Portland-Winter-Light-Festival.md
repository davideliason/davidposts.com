---
title: Building Lumenary for the Portland Winter Light Festival
date: 2019-02-14 12:46:03
tags:
- Art
- IoT
- IoT Art
---
This past weekend, I displayed my interactive art sculpture titled "Lumenary" at the 2019 Portland Winter Light Festival. It was an amazing experience to be part of the artist community showcasing their artwork, and to experience displaying my own piece to the greater community.

Here's Lumenary: a modern-day interpreation (spoiler alert!)
&nbsp;

{% asset_img Lumenary_At_Night.jpg Lumenary at night %}

Here's a summary of what the meaning behing Lumenary:
&nbsp;

{% asset_img FoL-LumenaryDescription-cropped.jpg Lumenary Meaning. %}

In this post I'll share some of the highlights on building Lumenary.

Initially, I was intrigued by the story of <a href="https://arthistoryproject.com/artists/hildegard-von-bingen/">Hildegard von Bingen</a>, as described by the theologian Matthew Fox. In particular, I was drawn to an illuminated manuscript containing an image by Hildegard, which depicted the essential unity of the cosmos:
&nbsp;

{% asset_img Hildegard_cosmos.png Hildegard's Cosmological Vision. %}



I was intrigued by this image for a variety of reasons, but especially for how the image reminded me of Jung's mandalas, the beautiful interplay of colors, and especially how the message of connectedness and unity was reflected in the imagery. In today's society, oftentimes were are exposed to only messages concerning the divisions amongst ourselves, and so this message seemed especially relevant and timely.

A big part of Lumenary was the interactive aspect, which was generally provided by a raspberry pi and several Arduino microcontrollers which, attached to sensors, allowed for responsive light interactivity via programmable LED strips. With the Raspberry Pi's built-in wifi capabilities, I built a serverless application using AWS resources, including a MongoDB table, AWS Lambda, API Gateway, Cognito, and more.
&nbsp;

{% asset_img RaspberryPiEnclosure.jpg Working on the Raspberry Pi. %}

This was my basic workplace: my laptop, a welding machine, a third-hand helper for holding the small electronic pieces for soldering, the various microcontrollers, and of course, a copious amount of coffee :)
&nbsp;

{% asset_img CodingSetupForLumenary.jpg My Workspace. %}

I found that the most useful sensor was the HC-SR04 sensor, which I used to provide much of the interactivity. As a person drew closer to the art installation, the sensor would sense the proximity and vary the LED strip colors via the programming through the Arduino IDE.
&nbsp;

{% asset_img ultrasonic_sensor.jpg Ultrasonic Sensor. %}

Here's a glimpse of hooking up the sensor to the Arduino:
&nbsp;

{% asset_img Arduino_HCSR04.jpg Ultrasonic Sensor & Arduino. %}

One of the microcontrollers that was used was Adafruit's Trinket, which was nice because it was lightweight, and it's circular shape mirrored that of the NeoPixel LED ring. Together, they provided a light source and interactivity towards the upper part of Lumenary; also, the NeoPixel light ring provided the light for a crystal hanging from it, providing moving "stars" on the canvas.
&nbsp;

{% asset_img Trinket_NeoPixel_Ring.jpg  Trinket & NeoPixel Ring. %}

Here's a snapshot of doing the coding needed for the LED movement:
&nbsp;

{% asset_img CodingLEDInteractivity.jpg Coding the Arduino for LED Strip. %}

Now, onto the physical layer of Lumenary!

First, created the frame for holding the canvas (a cotton sheet) using 1/2" pine:
&nbsp;

{% asset_img CanvasFrame.jpg Canvas Frame %}

Then filling out the canvas:
&nbsp;

{% asset_img TheWhiteCanvas.jpg Canvas %}

And then adding the Raspberry Pi, a fish tank with a beta fish (to represent the Ocean element) and lighting:
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

Transporting Lumenary to the Festival site was facilitated with copious amounts of coffee, I mean, Syran Wrap, and duct tape:
&nbsp;

{% asset_img ReadyForTransport.jpg Transport challenges %}

Here was the setup, having been moved under a shelter as there was a major storm in Portland - yes, snow and rain.
&nbsp;

{% asset_img DaytimeSetup.jpg Setup challenges %}

At night, Lumenary lived up to it's name :)
&nbsp;

{% asset_img PeopleInteracting.jpg People interacting with Lumenary %}


Here's Lumenary Lit Up At Night
&nbsp;

{% asset_img Lumenary_At_Night.jpg Lumenary at night %}

A special thanks to my sister, Karen, who came to help me on the project! :)
&nbsp;

{% asset_img Karen_And_David_Lumenary.jpg Lumenary with me and Karen %}

In conclusion, it was a wonderful experience, and I had some great conversations with people who were intrigued by Hildegard. It was enrichening to feel like I was part of an important conversation, and hopefully provided a glimpse into an amazing historical figure.