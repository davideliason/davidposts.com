---
title: Refactoring Local Mongodb Instance to Cloud
date: 2018-09-05 17:03:27 -0700
tags: AWS Resources
---

I came across a frustrating "learning moment" as the express app that I'd built, which worked fine on my local MongoDB instance, refused to work correctly when striving to use mLab's cloud service. 

I first started with swapping out the 'localhost' URI with the connection URI that mlab provides, yet the driver would not recognize the collection which I had instantiated within the database.

After reviewing a variety of posts and the MongoDB documentation, the connection worked correctly when I added:

````
MongoClient.connect(url, function(err,client){
   
    if (err) return console.log(err)
    db = client.db('personal_library')
    
  ````
