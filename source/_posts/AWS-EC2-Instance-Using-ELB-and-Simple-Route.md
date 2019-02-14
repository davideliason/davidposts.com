---
title: AWS EC2 Instance Using ELB and Simple Route
date: 2018-07-28 17:03:27 -0700
tags: AWS Resources
---

Lately I've been exploring moving my MERN applications up into the cloud using the AWS platform, and I thought I'd share how I configured setting up an EC2 instance using an Elastic Load Balancer. Hopefully it's useful!

First, I set up two generic EC2 instances within my local Region (Oregon, or us-west-2), using an AWS Linux AMI, a bash script to first install updates, then spin up Apache server, make sure that that server always rebooted, and then creating a simple html file within the server's /var/www/html folder. So, at this point, there are two EC2 instances running.

Next, I created an Elastic Load Balancer in front of those two EC2 instances. For that, I used the default HTTP port 80, used the same security group as what i'd used for the EC2 instances, dialed down the health check timing parameters to more manageable time slots, with the health check pinging the index.html file that had been spun up. 

Et Voila! To test this out, I first went to my EC2 instanes, grabbed the IPv4 public addresses and opened them in my broweser - good, they displayed those html pages correctly. Then, I copied the ELB public address and put that in my browser and that worked too.

The next thing that I learned was about DNS and Routes. That's always been somewhat mysterious to me! But here's a summary and overview of DNS, and then I'll build on that to how I used that info.

### DNS
So, DNS converts human-friendly URLs to an IP address - you know, those ones like http://126.10.12.10? Yes, impossible to remember! We have IPv4 IP addresses, which are 32 bit ones, but with the explosion of IoT and such, we're running out of those, so there's a new sheriff in town, the IPv6, which is 128 bits, and TONS of IP addresses!

Then we have Top Level Domains, which are the .com, the .net, sort of deals. There is a database that tracks all available top level domains.

That's where the Domain Registrars come into play- they assign domain names within each of those top-level domains. That's what GoDaddy.com and such do.

Now, when you register a domain name (and I'll use AWS's Route53 as an example), then you'll be given SOA and NS records. What the heck are those? Well, you need both of those, at a minimu. The SOA records point to the server which originated the domain name, and will tell you who owns the domain for example. The NS records, on the other hand, are used by the Top Level Domain servers to direct traffic to the DNS server. So zerr important! Lastly, you need an A record to map the name to the IP address.

### Back to the example
With that as a backdrop, I'm now going to create a simple A route. I used the naked domain name, or the apex domain, which basically means without the 'www', and pointed it to the ELB IP. What that does, basically, is that this route will route the request to the ELB, which sits in front of the two EC2 previously located, and those EC2 content will be displayed. 

AWS has a lot of resources to offer, as I learn this ecosystem I'll continue to share what I've learned in case it's helpful to someone else :)




