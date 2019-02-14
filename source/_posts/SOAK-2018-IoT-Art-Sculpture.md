---
title: BSG Enigma - an IoT Art Sculpture for SOAK (2018)
date: 2018-05-28 17:03:27 -0700
tags: IoT
---

Tweaking my art sculpture's neoPixels and ultrasonic sensor at a McDonald's booth, shamelessly enjoying free coffee refills, I earned a few sidelong glances (aka "what the heck?!") as I got ready to present 'BSG Enigma' at the [SOAK event](http://soakpdx.com/) this weekend. 
&nbsp;

{% asset_img last-minute-sensor-coffee.jpg Finishing Touches. %}

SOAK is the Pacific NW's mini-Burning Man event, focused on art, music and creative expression, and situated in a wide-open desert setting along a river - perfect for camping. This is a short piece about the inspiration for, and experience for building this piece, as well as  lessons learned for the next time.
&nbsp;

---------------

I'm a huge Battlestar Galactica fan since as a kid watching: 
&nbsp;

{% asset_img original_bsg.jpg Battlestar Galactica. %}

and then feeling like a kid again being riveted watching the new series:
&nbsp;

{% asset_img bsg_battlestar.jpg New Battlestar Galactica. %}


 and so of course I've watched and re-watched it many times. There are a lot of really intriguing metaphysical questions that are raised throughout the movie, but the series definitely rasies those topics much more in the final season - Starbuck dies but then re-appears again and even discovers her own corpse, a collective song is heard by select persons that draw them together, a Cylon--human couple have a living child whose blood can cure cancer, and so on. Anyways, since the theme of the event was "parallel universes", I thought this would be a perfect theme for that!

What I wanted: a raspberry pi running a linux OS and running as an Express server on node.js, interacting on a low-level with connected (by wifi, BLE or other) Arduinos for sensory data and also stimulating actions based on event handlers. At the same time, rendering visual responses on either a mini projector, LED displays, or such. 

I first started with building the enclosure for the raspberry pi - I used reclaimed wood as the materials, and used a planer, a joinder and various sanders to get the wood pieces smooth and squared. 
&nbsp;

{% asset_img front_enclosure.jpg Sculpture enclosure. %}

Then the table saw and chop saw to cut the pieces. The side panels were made of acrylic, so as to display LED lighting within the project, these were cut using a band saw and drill press. 

At first, I was tempted to try and cut out the display area using a band saw...
&nbsp;

{% asset_img making_rpi_frame.jpg Top opening for display. %}

...but wiser counsel suggested making the opening for the raspberry pi screen by using Illustrator and cut using a laser cutter.
&nbsp;

{% asset_img enclosure_BSG_Enigma_top.jpg Laser-cut display. %}

Bringing it all together, I came up with a solid case that was easy to carry around and offered room for sensor expansion down the line:
&nbsp;

{% asset_img full_enclosure.jpg Entire enclosure. %}


Coding-wise, what I actually experienced was that it's much more complicated than I'd thought! It's pretty easy to install node.js and run an Express server on the raspberry pi, and actually my inital approach was to use PubNub as a cloud-source for Arduino data. However, I then began to think that the remote location of the event might make internet access very difficult, so I switched to creating a LAN.

A few snags: the rpi did not like the CRA installation, whcih was a big problem because that meant that if I wanted to work with the React/Redux libraries, I'd need to work with Webpack, something I hadn't done for awhile. Another issue was that working with Johnny-Five, the Javascript library allowing interactions with IoT, kept giving me attitude in terms of the sensors.
&nbsp;

{% asset_img project_really_close.jpg In the wild. %}

On the other hand, I was running out of time (you can see my photo of working at McDonalds on finishing touches with my ultrasonic sensor and neoPixel strip) and my stress level was defnitely increasing, so many of these issues could probably be resolved. So, one lesson learned is to give much more time for unanticipated problems. The other lesson that I learned is to make sure to have multiple energy sources, as the LiPo battery and secondary battery pack discharged much faster than I'd anticipated.

On the plus side, it felt really amazing to go to the event and show people my project and to have conversations around the BSG metaphysical questions, as well as the technical building of the sculpture. I met a few other artists, who I had subsequent conversations with, one even sharing all the technical data for how they built their amazing art sculpture. So, that is definitely inspiring for my next piece!

On a slightly different note, it was an interesting experience since I didn't have stakes, so I had to whittle my own :)

It's always good to have a Leatherman in your pocket!
&nbsp;

{% asset_img knife-and-stake.jpg Making a stake. %}


Here's an example of my amazing Whittling Skills:
&nbsp;

{% asset_img tent-stake-i-whittled.jpg Whittled stakes. %}


Here's my tent setup and my scultpure ready to be installed:
&nbsp;

{% asset_img my-tent-and-sculpture.jpg All done. %}
