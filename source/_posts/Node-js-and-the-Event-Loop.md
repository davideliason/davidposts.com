---
title: Node.js and the Event Loop
date: 2018-07-09 17:03:27 -0700
tags: Node.js
---

I've been diving into better understanding node.js, the Javascript runtime that runs on the server, and thought I'd post some of what I've discovered.

[Mozilla](https://developer.mozilla.org/en-US/docs/Web/JavaScript/EventLoop) has an excellent article on the concurrency model and event loop. I first googled that article by seeking to understand the difference between a process and a thread; node.js is a single-threaded runtime, but in actuality it's only single-threaded in terms of what the user can access. That is, node.js uses the open-source libuv library to handle the thread pool, and that libuv allows for concurrently running javascript code to be running at the same time as the main (user facing) single thread. Another thing that I learned is that a process differs from a thread in that the former uses different memory locations, while the thread using a localized memory area. At least, I think I got that right :)

So the single thread is possible because node.js is non-blocking, that is, using asynchronousity. This is possible due to the event loop, which is comprised of a stack, heap, and queue. From my understanding, which is pretty simple at this point, the heap is just Max Beyond Thunderdome memory area where arrays and variables are put in an unstructured way, the stack is where functions 'put' (no pun intended) as they are called, and the message queue (or event queue or task queue, whichever you prefer) is where messages (which are attached to functions) wait patiently for their turn. When it is their turn, i.e. some event has returned, then they are called, and that means that they are put onto the stack, because that's where functions go when they are called. The stack ebbs and flows, as functions are called and returned, and node will keep on chugging along through the event loops so long as there is code being run or there is a messsage in the queue.

Whew! It's actually pretty interesting, but I can tell this will take some time to really wrap my brain completely around!