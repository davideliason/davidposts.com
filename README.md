# David Posts

## A blog for David Eliason

## About
I had created a blog using Jekyll and served on Github, but I always had challenges around it, and there was a lot of "black boxes" which made any tweaks feel mysterious.

Finally, after having created a number of posts, I started receiving build errors, and that black box aspect really was problematic.

Since I have already been working on utilizing AWS resources, I decided to build my own blog using a S3 bucket and my own domain. I decided to use Hexo to do so.

## Quick resources

Create a new post
```
$ hexo new "My New Post"
```
Add an image
```
{% asset_img test_image_thumb.jpg Alt text. %}
```
Multiple tags:
```
tags :
- tag_1
- tag_2
- tag_n
```
Making space:
```
&nbsp;
```
Generate the post:
```
$ hexo generate
```

Deploy to S3:
```
$ hexo deploy
```
