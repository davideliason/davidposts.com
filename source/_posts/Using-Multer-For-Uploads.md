---
title: Using Multer For Uploads
date: 2018-09-07 17:03:27 -0700
tags: Node.js
---

My goal is to create an application where users log in, are authenticated, and once that is completed, they can Create, Read, Update, and Delete todo tasks. I'd also like for the user to be able to upload an image, as part of that todo.

In order to do that, I included the [multer module](https://www.npmjs.com/package/multer). Each file contains a variety of field keys: fieldname, originalname, encoding, mimetype, size, detination, filename, path, buffer. We can call multer, passing in a couple possible options: dest/storage, fileFilter, limits, preserverPath. In this case, I've created a storage option and a fileFilter option. Within each of those options, different configuration was needed. 

For storage, diskStorage gives you full control on storing files to disk. You have the two options of **destination** and **filename** , the first of which I set to the folder called photo-sotrage. The second was a filename cosisting of the field input text with the current timestamp and the file extension; this ensures that it will be a unique file name.

For fileFilter, we can control which files should be uploaded. We do this by calling the third argument to the method call; fileFilter(req,file,cb){} in this case would be cb(true) if it's a file we allow to upload. So, in the code, we look at the file type and if the first part of that type is 'image' then we call the method with the cb and a boolean (true) argument.
