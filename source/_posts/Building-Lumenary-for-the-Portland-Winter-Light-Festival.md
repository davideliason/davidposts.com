---
title: Building Lumenary for the Portland Winter Light Festival
date: 2019-02-14 12:46:03
tags:
- Art
- IoT
- IoT Art
---
This past weekend, I displayed my interactive art sculpture titled "Lumenary" at the 2019 Portland Winter Light Festival. It was an amazing experience to be part of the artist community showcasing their artwork, and to experience displaying my own piece to the greater community. Here's a summary of what the meaning behing Lumenary:
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
