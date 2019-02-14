---
title: Server-Side Rendering Vs Client-Side
date: 2018-09-29 12:03:27 -0700
tags:
- Express
- React
---

I created an application called 'Community Quotes' that allowed users to create, view, update, and delete quotes. This was using the MERN stack using CRUD functionality, and it first started with using the ejs template engine, and then later I switched to using react as the View. 

Having successfully finished up that application, which you can see [here](https://github.com/davideliason/community_quotes), I've been thinking about the benefits of that shift, so thought I'd write my thoughts here.

The advantage to using the template engine, from the developer's point of view, is that it's pretty darned easy to spin up and use within the express world. Just add a few lines of middleware, create some views documents, and then you use the render method with attached variable passing data to said view. Pretty sweet. The biggest drawback, however, as I see it, is that those views are all created on the server side, so that the created template document (using ejs) is built on the server and then sent to the user via the http response object. Well and good, but there's a price to pay in terms of latency for the user experience. 

We especially don't want to be going back and forth to the server every time that we want to make or receive changes to the data, and that's going to be especially true with a mobile app as we are looking for snappy responsiveness!

Which is why harnessing the power of the computing power on the client side makes sense. That's where react does shine, in terms of being able to handle event handlers and state without needing to check back to the server for minutae. Of course, the server will still need to be used for database connectivity, so I can see that there will need to be some back and forth to the server from the client side, but it certainly will not be to the same degree as pure server-side view rendering.