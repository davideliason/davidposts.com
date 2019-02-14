---
title: AWS EC2 instance using SSH Blink and nginx reverse proxy server
date: 2018-08-02 17:03:27 -0700
tags: AWS Resources
---

{% asset_img 8218-VPC-EC2-Post.png Intro. %}
&nbsp;

There's my fancy splash page! I wanted to share the steps I took to get some experience doing a few things: first, creating an EC2 instance within a VPC, then spinning up a simple express app on top of node, spitting out response to port 3000 but allowing our reverse proxy nginx server to channel that to route 80.

First step was that I started with the VPC that I created in yesterday's post. Basically, I created a VPC with a 10.0.0.0/16 CIDR IP address block, and then I created four subnets within the VPC - one is for expansion uses, and the other three each were situated within a different Availability Zone. Why did I do that? For fault tolerance reasons, as we can locate a server within a different subnet, in the case an AZ goes down, another mirrored server can be spun up. Also, it made it easier to allocate the CIDR sub IP ranges.

I went ahead and deleted the EC2 instance that I'd spun up yesterday, and created a new one using a Linux AMI, without additional storage, using a security group which allowed SSH, HTTP and HTTPS. I created that EC2 instance within the us-west-2a availability zone.

Next up, I created an Internet Gateway which I associated with the VPC. I actually didn't need to do that, as I'd done that yesterday, but just wanted to get more practice :)

Next, I created a route table that was attached to that Internet Gateway, and which had two routes pointing to the IG: the first was for HTTP and the second was for HTTPS. Each subnet needs to be attached to a route table. So, for the subnet that was located within us-west-2a availability zone, I had the (soon to be provisioned) EC2 instance pointing to the route table which was publicly facing via the IG.

Okay, so that's good. Now that we had that infrastructure, we could spin up the EC2 instance. Nothing fancy, just a Linux instance using free tier AMI, and plugged it into our subnet within our VPC.

## Building the EC Instance
1. SSHd into the instance using the key-value pair
2. wihtin the trusted keys subfolder, added the public key from Blink
*Boom* Now am connected by Blink and my laptop *at the same time* oh yeah!

3. installed nvm
```
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.11/install.sh | bash
```
then installed node:
```
# nvm intall node
```

then:
1. made a directory
2. cd'd into that directory
3. $ npmm init
4. npm i --save-dev express
5. created server.js file with verrrrrry basic exepress server, listening at port 3000
6. installed nginx
```
 sudo yum install nginx
```
7. edited the nginx config file to point to server behind it with port 3000
[link](https://medium.com/@nishankjaintdk/setting-up-a-node-js-app-on-a-linux-ami-on-an-aws-ec2-instance-with-nginx-59cbc1bcc68c)
8. restarted ngnix server

&nbsp;

{% asset_img Exercise-Steps.png Steps. %}

