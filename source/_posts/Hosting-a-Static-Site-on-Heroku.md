---
title: Hosting a Static Site on Heroku
date:  2018-06-25 17:03:27 -0700
tags: Cloud Deployment
---

I recently decided that it was Time To Spruce Up The Repos in my Github portfolio, so... out went the repos that, well, just needed to go. What to do about that odd repo that was front-end only code only? How should that be posted without having to build up a framework around it?

Following some online advice, I found that there's a pretty easy solution, which is to host it on Heroku. Here's the steps that I took to do so with a browser-based Babel and React application:

1. In the root directory, where your index.html resides, create a composer.json file:
````
$ touch composer.json
````
2. Add an empty object within that file 
````
{}
````
3. Add a index.php file
````
$ touch index.php
````
4. Add a single line within that file:
````
<?php include_once("index.html"); ?>
````
5. create a heroku repo for your code to go into:
````
$ heroku create <your app name>
````
6. Push your code into that repo
````
$ git push heroku master
````
7. open it up
````
$ heroku open
````

And that was it - my vanilla html file successfully rendered the React application. This would have worked with a project that had more to it, such as CSS or Javascript files.

 You can take a look at it [here](https://browser-react-todolist.herokuapp.com/)

 [Github Repo](https://github.com/davideliason/react-todo-list)

&nbsp;

 {% asset_img heroku-hosted-react.png Browser React. %}

