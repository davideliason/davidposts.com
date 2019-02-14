---
title: Deploy React + Node/Express to AWS part 2
date: 2018-09-10 12:03:27 -0700
tags:
- React
- Express
- Node.js
- AWS Resources
---

Okay, the first post was getting too long so had to break it up! :)

So, I left off with having got nginx botted up and with everything being run off port 80. Now we are wanting to move away from the hard-coded simple Express server that I orginally build using vim on the EC2 instance, to being able to pull backend code using git to that instance.

To do that, I instantiated a repo for the backend code. 

Back-end, here, is using an EC2 instance with express sitting on node.js acting as RESTful API. The EC2 instance is part of a VPC architecture for firewall security.

Previously, on the EC2 instance, I'd created an Express server, very simple, to test out the framework, but building code via the terminal is awkward so added a private key to the EC2 instance and the backend repo so that I can work within the github environment and simpy pull code into my EC2 instance.

Ahh, much better!

The next thing that I did was create another route within express that would supply json data. I then pushed that revised repo to VCS, and pulled it into my codebase within the EC2 instance. With that in place, I could call add that route within the EC2 URI and see the returned JSON data; voila, we have an API server in effect!

At this point, we have a React app running on the s3 bucket, and we have a node/express server app running on the EC2 instance, the latter returning JSON data when the appropriate route is called. Now, to link the two together.