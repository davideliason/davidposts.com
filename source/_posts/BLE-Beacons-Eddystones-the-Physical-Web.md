---
title: 'BLE Beacons, Eddystones, & the Physical Web'
date: 2018-06-25 17:03:27 -0700
tags: IoT
---

As part of my art sculpture I'm exploring the use of beacons, so thought I'd share some of what I've learned here. 

Part of my interest, as I work with embedded computing, has been inspiring projects like this one by [Aram Bartholl](https://hyperallergic.com/231483/fire-up-a-wifi-router-hidden-inside-a-rock/) He's one of my heroes by the way, check out his [blog](https://arambartholl.com/blog/)

- very small device (two quarters stacked), low power reqs (coin battery) lasting a long time (up to 3 years!) + chipset + antenna (230' range)
- BLE (Bluetooth Low Energy) is the way to go, cheaper, lower energy
- stores use it to *push info* to shoppers, get help
- The [Physical Web](https://google.github.io/physical-web/get-started) uses open source communication protocol called Eddystone to communicate - don't need to d/l an app, works across all devices. There are beacons avail. that support both iBeacon and Eddystone : in the previous you'd need to d/l a specific app, for the latter, just open a browser that supports TPW (The Physical Web) to see same content.

Reading this, I just installed 'Physical Web' on my Android phone.

To explore this, you would use a BLE beacon that supports the Eddystone protocol, this will allow you to broadcast an URL. That URL can be picked up by a phone or such. Hmmmmm...

----------------
[React Native Wrapper](https://github.com/Artirigo/react-native-kontaktio)

Running this example started the react-native server, but did require an Android SDK to be installed. Not to that point yet...

