---
title: BSG Enigma - Exploring The Mystical Elements of the Best SciFi Series Ever
date: 2018-06-22 09:10:26
tags:
- Art
- IoT
- Node.js
---

I've always been interested in the intersection of physical art materials (especially wood and glass with lighting elements), and interwining interactivity with a deeper conceptual component. 'BSG Enigma' was my first art installation in approaching all of those elements, and in this blog post I'll share my process and experience in doing so.

SOAK is a regional Burning Man festival which emphasizes interactive art, and for 2018 the theme was "Parallel Universe." To me, that immediately made me think of the (fantastic) sci-fi series Battlestar Galactica, which explicitly delved into parallel universes in terms of time and perspective. Anyone who has watched this series will have been introduced to some pretty interesting metaphysical and mystical elements, and it was this area that I wanted to focus upon.

With three months before the festival starting on May 24th, 2018, I decided to volunteer at the makerspace ADX, located in Portland, to build community and also have access to the wide variety of tools. I built much of the project there in the ADX facilities, learning the tools, and learning techniques from a number of artists who worked there.

One of the tools that I used quite a bit was the table saw, along with the drop saw, for cutting the wood pieces.
&nbsp;

{% asset_img ADX_table-saw.jpg Table Saw. %}

Another favorite tool of makers is the laser-cutting machine, which was used to precisely cut out thin sheets of wood (pine) for (in this case, the Raspberry Pi). 
&nbsp;

{% asset_img ADX-Laser-Cutter.jpg Laser Cutter. %}

Before actually using the Epilog laser cutter, I used Adobe Illustrator for creating the cutting image. This is done by creating vector-based graphics, and then assigning line widths to either tell the Epilog to cut the line, or simply "burn" the image.
&nbsp;

{% asset_img ADX-Computer-Station.jpg Creating the Image for Cutting. %}

I was interested in combining different wood types (the aesthetic is amazing!), and here's a piece that I started out with:
&nbsp;

{% asset_img Wood-Block-Start-432x491px.jpg Wood Block Start. %}

Because the different parts of wood were of different thickness, I used a planer for leveling the pieces to the same width:
&nbsp;

{% asset_img Wood-Leveling.jpg Leveling the Wood Pieces %}

Back to the Table saw for cutting the pieces to be the desired widths
&nbsp;

{% asset_img Wood-Sanding.jpg Making the Wood Pieces the Desired Width %}

With the pieces of similar widths, I then used wood glue to bring them together
&nbsp;

{% asset_img Wood-Glued.jpg Wood Glued Together %}

And another wood-gluing section:
&nbsp;

{% asset_img Mixed-Wood-Glued.jpg Mixed Wood Glued Together %}

At first I tried to use a Table Dremel to cut out the wood, but eventually used the laser cutter, which did a much nicer cut for creating a space in the wood for the Raspberry Pi 8" touchscreen interface:
&nbsp;

{% asset_img Laser-Cut-RPi-589x349px.jpg Laser Cut Opening for RPi. %}

I then created the rest of the container protecting the Raspberry Pi, by using a bandsaw to cut acrylic sheets and pieces of wood to the appropriate dimensions. Because the RPi needed access to the GPIO ports, I creaeted an opening in the back:
&nbsp;

{% asset_img BSG_Enclosure1.jpg Rest of the Enclosure. %}

And then, with the top attached, the full enclosure looked like this:

{% asset_img enclosure_front.jpg The Enclosure. %}

Concurrently while building the enclosure, I worked on the smarts. First, I tried to bring in GPS capabilities, but unfortunately fried that micocontroller:
&nbsp;

{% asset_img GPS-To-Arduino.jpg The GPS module attached to Arduino Uno. %}

