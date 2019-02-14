---
title: Creating a VPC With a Single Public-Facing EC2 Instance
date: 2018-08-01 17:03:27 -0700
tags: AWS Resources
---

I wanted to share how I successfully created an EC2 instance within a VPC instance, using a custom route table and connected to an internet gateway. I find working with the cloud to be super interesting, but there's a lot of moving parts, and I thought it'd be helpful to share this successful step with other interested parties.

So the goal was multifold: to create a VPC, a NACL, a route table, an internet gateway, a subnet, and a security group. Also, to spin up an EC2 instance within one of two subnets, the one which is public facing and internet accessible.

Here's the result of this blog's efforts:
&nbsp;

{% asset_img WedsVPC.png VPC Diagram. %}


The first thing that needs to be done is to create a VPC. Now, I'm assuming that you already have a AWS free-tier account that you can access. Within the VPC Services, you can create a VPC by using a descriptive name tag, and selecting an IPv4 CIDR block. 

The IPv4 CIDR block is basically an IP range that you'll have available to you within your VPC. So what's a VPC? It's like your own virtual private cloud, your own data center. So what we're working on is configuring the network within our own little VPC world :) Just to have more options, I also selected Amazon providing a IPv6 CIDR block as well. And that's it for creating a VPC! Amazon does some behind-the-scenes work, by creating a default route table, network ACL, and security group as defaults.

Here's what we have so far: a VPC structure, and a few defaults: route table, NACL, security group. Right now the route table, by default, is open to the whole wide world, something that we don't necessarily want and will be fixing next:
&nbsp;
{% asset_img WedsVPC_step1_VPC_creation.png VPC Diagram: Defaults. %}


Next up, we need to create a *subnet*, which is a logically-distinct area of your VPC. You can have multiple subnets, and they are each their own little kingdom (is how I like to think of it). They can interact with each other using peer sharing, but it's all very controlled. Which is complicated, but super powerful!

Anyways, let's create our subnet! Still within the VPC service category, we do so by selecting a distinctive name, selecting the VPC that we just made, and then selecting a CIDR range (yes, again). Before, we selected 10.0.0.0/16 because that gave the widest range of IP addresses, but now we don't need so many, so we can just select 10.0.1.0/24. Each subnet is associated with a unique Availability Zone (AZ), so you select the AZ that you want this subnet to be in. And, that's all you need to do to create a subnet.

For this exercise, I haven't linked up my subnet with another, I'm just going to focus on getting the single EC2 instance, subnet, route table, NACL, and internet gateway working. Baby steps! :) 

Now, we need to think about the *internet gateway*, because we want to our soon-to-be-provisioned EC2 instance to be able to access the internet. So, once again within the VPC services category, we can create an internet gateway (IG), by simply creating it (give it a name if you like), and attaching it to our VPC.

So, now we have this:
&nbsp;
{% asset_img WedsVPC_IG.png VPC Diagram: Internet Gateway. %}

Next, we have to create our *route table*, and that's because the default one which AWS configured for us automatically when we created the VPC, is set, by default, to the internet. That's not a problem, but also by default, all subnets are attached to that route table, and we don't want all of our subnets to necessarily to be exposed like that. So, let's create a route table that's especially tailored for public access.

We can do that by creating a route table and creating two new routes as part of that table (From the Route Tables selection, just go ahead and select the route table that you just created. Now, at the bottom you should see a tab called Routes, and there you can add those two routes).

The first route we want the destination to be '0.0.0/0/0' for HTTP access and attach that to the internet gateway. The second raoute we weant to be '::/0' which is used by the HTTPS. Now, what we have done is create a route table that is pointing to the internet gateway and that has approved two routes for HTTP and HTTPS access. Cool!  The last thing that we need to do is actually associate that route table with our subnet; you can do that by selecting the *subnet associations* tab, select the subnet that we've been working on, and they are now associated.

Oh, wait, there's one more thing that we have to do! We have to allow AWS to provide public IP addresses, which we need for accessing the internet. We can do that by selecting VPC > Subnets and then selecting our VPC. Now, select 'Actions' > 'Modify auto-assign IP settings' to true. 

Now that we've created the framework architecture, we can go ahead and provision our EC2 instance. I selected the Linux free-tier 64 bit AMI, on a micro t2 instance, selected the VPC and subnet that we just created, and also selected a security group (firewall) that allowed SSH, HTTP, and HTTPS into that instance. And with that, we can SSH into our instance.

One fun thing to do is add a shebang bash script to our EC2 instance:
yum install httpd -y 
yum update -y
chkconfig httpd on
service httpd start
echo "<html><h3>hello world</h3></html>" > /var/www/html/index.html

That script goes in the advanced settings of the EC2 instance setup. If you do that, then the instance will spin up, update its settings, install Apache server, start it, make sure that it boots up upon server rebooting, and create an index.html file that is served by the Apache server. You can access that via the public DNS address that is given in your EC2 instance page. 

And with that, we have successfully completed what we wanted to do!
&nbsp;

{% asset_img WedsVPC_success.png Success!. %}






