---
title: Updating Content-Type in Uploaded S3 HTML File
date: 2018-07-10 17:03:27 -0700
tags: AWS Resources
---

Using the [AWS docs](https://docs.aws.amazon.com/sdk-for-javascript/v2/developer-guide/s3-example-creating-buckets.html), I was able to successfully upload an html document to my s3 bucket, but when I attempted to open that file from the bucket, it would only download the uploaded file. Not what I wanted - I was expected to view the page in the browser.

What I learned is that the default that AWS sets for uploaded files (and I believe that's across the board) is of the MIME type 'application/octet-stream'. In order to set the correct Content-Type of 'text/html', [list of MIME types](https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/MIME_types/Complete_list_of_MIME_types), I added the ContentType property as the key within the AWS params, like so:

var params = {
  Bucket: '<bucket name>',
  Body : fs.createReadStream(file),
  Key : path.basename(file),
  ContentType:'text/html'
};

Those params are used within the s3.upload method, and with that change, the file opens correctly.