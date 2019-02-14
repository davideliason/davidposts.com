---
title: Express Sessions
date: 2018-08-28 17:03:27 -0700
tags: Express
---

I'm enrolled in the MongoDB University M101JS class, already entering week 4!, and it's been a deep dive in CRUD. I've been taking lots of notes, but for me the best thing to make sure it sticks is to put what I'm learning into practice. So, I'm working on tying in a MongoDB instance to node.js + express. I'm going to share what I learn as I go along.

Assuming that the goal is to build an app so that a user can log in via authentication, and then query data saved in the database, building in sessions will be important so that there is state in terms of that user's experience.

Installing the express-session module, we then use it as middleware and setting a configuration object to it. There are four fields, with the keys of 'secret', 'resave', 'saveUninitiated', and 'cookie'. With sessions initiated, and these parameters set, we then have access to the session object attached to the request body as a parameter. We can access that session object with subsequent requests.

For example, if I set the session using those four key values, I can then access request.sesesion with subsequent routes (which have the request and response parameters as part of the callback function).

In the example that I'm working right now, I successfully created a simple value attached to that session object, which was sent to the client as part of the response, and was still available with subsequent user/client requests. So, I've gotten a glimpse of what this can mean.

It's important to note that there are four different ways of working with sessions: in memory (which isn't used for production), in a cookie (which is what we have used here), in a memory cache (like Redis or Memcached), or a database. In one of the blog posts I read, it was recommended to approach sessions using caches first, then cookies, and finally databases.

However, the disadvantages of using cookies is that it adds to the overhead of a http request or response, with that added data being carried each way. The amount of data is relatively small, but it still adds overhead. Also, it's essential to keep the cookie secret just that - a secret, because if exposed, then the client's data is as well.

