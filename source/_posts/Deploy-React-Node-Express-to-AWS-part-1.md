---
title: Deploy React + Node/Express to AWS part 1
date: 2018-09-10 12:03:27 -0700
tags: 
- Node.js
- React
- Express
- AWS Resources
---

My goal is to deploy a react app using CRA on the client-side using s3, and using an EC2 instance for instantiating an express server running on node.js for an API server. 

Instead of building a montolithic MERN app served by a server, which does server-side rendering for example, I've decided to separate the business logic of the API from the front-end design. There are a lot of advantages to such a microservices approach, including separation of deployment allows for speedier file access and lower latency, faster iteration, and simpler product logic. 

S3 holds files, and so is great for file storage or for hosting a static website; For this project, I'll be using s3 for the view provided by React. The advantage to using S3 is scalability, reliability, and speed. Having the CDN in front of the S3 will offer faster delivery for the users and cheaper costs.

The EC2 instance will be serving API server via node.js and express. This will be the Node API. This could have been handled by Elastic Beanstalk, but as I'm wanting to get my hands dirty with each of the MERN components, I'll be building out the EC2 instance and then connecting the db manually. Then of course there is the option of going serverless using Lambda functions and the API Gateway, which is definitely a great option, but I really want to build that solid foundation using the MERN stack before taking advantage of more speciality tools available. If that makes sense :)

As noted in [this blog](https://stackoverflow.com/questions/41250087/how-to-deploy-a-react-nodejs-express-application-to-aws), it's advantageous to put a CDN via Cloudfront in front of the s3 for a variety of reasons. 

Anywho, using CRA to create /client sub-folder within main app. Now, how to upload to s3 bucket? Simple, just use:
```
aws s3 cp build/ s3://<bucket name/> --recursive
```
That command will use the AWS CLI to upload the production build files from your local computer to the bucket. Just remember to set the bucket permissions to public accessible :) See [this post](https://stackoverflow.com/questions/5123208/upload-folder-with-subfolders-using-s3-and-the-aws-console) for more info, as well as setting up CDN.

Now on to the back-end with EC2 setup. And before doing that, we need to set up the VPC! So, back to AWS and set up the VPC, creating one with the help of [AWS docs](https://docs.aws.amazon.com/vpc/latest/userguide/working-with-vpcs.html). I used the biggest IPv4 CIDR block range of 10.0.0.0/16, with a public subnet of 10.0.1.0/24 within AZ us-west-2a. Created a second (private) subnet of 10.0.2.0/24 within AZ us-west-2b, which is where the EC2 instance will be instantiated. Attached an Internet Gateway to the VPC.

Actually, I decided to put the EC2 instance in the public subnet, so as to concentrate on the application itself. 


So, now I SSHd into the instance, updated, and installed node.js. See [AWS article](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AccessingInstancesLinux.html). Current version = 8.11.4


Now, it's time to follow [another AWS doc](https://docs.aws.amazon.com/sdk-for-javascript/v2/developer-guide/setting-up-node-on-ec2-instance.html), this time for installing node.js

Activated nvm and installed latest version 8.11.4, then created a simple express server with a single route rendering the inflamous 'hello world' :) In order to do that, I had to add an incoming route at port 3000, for test purposes. (it normally uses port 80, but that's a restricted web port). In order to run the app on port 80, we'll need to do something like use nginx, and maybe use PM2 to keep the app running on restart too. Good article on spinning up that express server [here](https://hackernoon.com/tutorial-creating-and-managing-a-node-js-server-on-aws-part-1-d67367ac5171).

Now, to change http traffic to port 80, via this [post](https://hackernoon.com/tutorial-creating-and-managing-a-node-js-server-on-aws-part-2-5fbdea95f8a1).

Just discovered that the Linux dist AMI I used doesn't support nginx, at least not easily, so time to delete and add Ubuntu. Sigh.


Okay, it's all good practice! So, right now there's an Ubuntu server running express on latest node version, running on port 3000. We'd like to switch this to port 80 so that we can use this public port and routing. That is, port 80 is the default port for HTTP traffic.

So, first things first! Nginx is great for being used as a router, so after system OS update, install nginx. This gets nginx to run automatically, so going to port 80 now shows that homepage. We are making progress!

Add config file in sites-enabled that forwards HTTP traffic from port 80 to port 3000. Now, after I shut down the server and restart it, I can use port 80 to render my express app. Woot! 

Now, onwards to process manager, using PM2, to restart server.




