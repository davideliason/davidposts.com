---
title: Sessions in Express
date: 2018-10-03 11:59:28
tags:
- Express
- React
---

In previous recent posts I described building out a MERN app with an emphasis on tying in the database with the server with a simple view using react. With that as a foundation, we can now start building in more advanced functionality, and one of the fundamental pieces of that, for an app that works with users and data, is sessions. This post reflects some of what I've learned in bringing in this funcitonality.

A [really great tutorial](https://nodewebapps.com/2017/06/18/how-do-nodejs-sessions-work/) describes that sessions are needed for applications because they create application state. That is, we need to have some way to have persistence of a user's experience within the app so that we can serve up continuity. The way that I like to think of it is that it's like going to see a therapist, and so you set up an appointment to have a *session* with the therapist. The session is going to involve notes so that what you covered during that session will be remembered. Who wants to go back to the therapist and start all over again each time?! That's what the notes are for, to create that persistence. The notes, actually, are what the *cookie* does; it holds session data.

As that tutorial describes, there are a couple ways of storing session data (to continue the analogy, ways to store those notes from the therapy session): application memory (after the therapy session, the therapist burns the notes), in a cookie (this is sent to and fro the server to the client and the cookie actually hold the data - not as secure), in a memory cache (such as redis) wherein the cookie holds just the sssionId and the data is stored in another server running redis, and finally in a database (very similar to memory cache in the setup).

With the module express-session, we still use a cookie but it's behind the scenes. As this modules's [docs](https://www.npmjs.com/package/express-session) note, we need to have q unique session value, which we can use via the [uuid](https://www.npmjs.com/package/uuid) module. The documentation also notes the use of uid-safe for ID generation too.The session data is not saved in the cookie itself with this module, session data is saved server-side.

The sessionId will automatically be saved and sent in each client request to the server (inside the header).

We use a *session store* to hold data because otherwise, if the server is restarted or the client-side application is closed, then the data will be lost.

In my app, I attached a numbers key to the sessions object and updated that value with every subsequent request sent to the server. For me, it's helpful to see how these things actually work, because the documentation can be pretty lofty and wordy! ;)

I used the 'session-file=store' module to create a local store instance file wherein the session data is saved. This is a baby-step for moving from cookie storage which will evaporate once the session is done. The session data is saved to that file.

What really drilled down for me was using Postman to send a GET request to the '/' route, and seeing the 'set cookie' within the header as part of the response. That same value, the sessionID, is what is the title of the session-file-store. So the session is created the first time, but subsequent GET requests to that route are within that session. So, on the client side we have the sessionId but all the data attached to that sessionId is stored on the server side, within that store. So, conceptually it makes sense how the cookie is providing continuity and an extra degree of security, and also how instead of saving the data to a file, it could instead be saved to the database or redis. 

But that's another post :)
