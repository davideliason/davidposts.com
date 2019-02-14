---
title: Using Passport for Node.js Authentication
date: 2018-09-06 17:03:27 -0700
tags: Node.js
---

Yesterday I build an application that used express to serve up JSON objects as a route as well as full-populated template html files, connected to mlab as mongodb instance. Functionality was limited to create and reads, and hosted on heroku.

This application will build upon that knowledge for full CRUD functionality as well as building in user logins and authentication using passport module. This is the traditional model of user authentication for an application, and a good place to start, but there are lots of other strategies including using an OAuth partner like Facebook to login. That might be something I explore a little later down the road :) 

Passport is middleware software for Node.js which offers a wide spectrum of authentication possibilities, more than 500 actually!- you can read about them [here](http://www.passportjs.org/). 
But, at its core, Passport is just about authentication.

Passport uses authenticate method to select the strategy, (which needs to be configured before being invoked), and can have *redirects* and *flash messages*. 

&nbsp;

{% asset_img WedsVPC.png VPC Diagram %}

