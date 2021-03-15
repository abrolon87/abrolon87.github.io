---
layout: post
title:      "Views and Templates in Django"
date:       2021-03-15 15:37:47 +0000
permalink:  views_and_templates_in_django
---

Since my last blog post, I have added a Post model and I added some languages and posts through the admin site to be able to work with when I start to build views and templates. Today I will be adding some views and templates to Lingovault and I want to walk you through the steps I take to do that. In my last blog, I mentioned that there are somethings that will be different in this Django version compared to the original Sinatra version so, another thing I am doing differently in this version is using an MVT(model, view, template) pattern instead of a MVC(model, view, controller) pattern. The reason is because Django is going to take care of the controller part for me. When I learned about MVT architecture, it was a little confusing because the wording is different than how it is in MVC architecture. For example, "views" in MVT are a little similar to what a "controller" is in MVC and an MVT "template" is what is known as a MVC "view".  

Let's get down to it.....
 
### Build the home.html template

I will start with writing a template called "home.html". A template is just an html file that is used to define what a page will look like in the browser. In my lingovault_app directory, I'm going to create a new directory called "templates/lingovault_app" and I'm going to put home.html inside there. As of right now, my project directory looks like this:

![](https://i.imgur.com/QZsJs70.png)

And for now, home.html looks like this:

![](https://i.imgur.com/kxX5Tn4.png)

It is just some simple html. Nothing too exciting right now.


### Build the view

The view is a function that takes in a request and preps the data before sending it to be used by the template to be rendered to the browser. The view I built is located in lingovault/views.py and it looks like this:

![](https://i.imgur.com/fX2TPnz.png)

### Map the URL

Now, to let Django know to render home.html when at the base URL, I am going to first, include lingovault_app.urls  in the project. I'll do this in the lingovault/urls.py file in the urlpatterns, like so:

![](https://i.imgur.com/F0GFcQt.png)

After that, I have to define the urlpatterns for lingovault_app in a new file that I'll create in the lingovault_app directory, called urls.py. This file did not come with Django so I have to import path from django.urls, import the views from the root directory, set the app_name to "lingovault_app" and then I can define urlpatterns and add the home page path to it. After all that, the file looks like this:

![](https://i.imgur.com/5zNNSze.png)

### How It All Works Together

So now that I have all the code I need for this to work properly, let me explain what is happening. A user goes to a particular URL in the browser, in our case, the base URL for lingovault. This is known as a "GET request" in the world of programming. The Django then matches that URL with one of the urlpatterns. When matched, a call is made to the path() function, which takes in 3 arguments:

1. A string for Django to properly route the request to a view. In our case, the URL that is being requested is the base URL which matches the empty string that I have provided. 
2. The function to call in the views.py file. In our case, we will be calling the home() function.
3. And then the ```name``` for the URL pattern. In our case, ```home```.

This is when the view takes in the information from the request and gets the data ready to be sent back to the browser. In today's example, it's not very interesting as there is no data being sent. I am just returning render() which just renders the home.html template... 

Now, if I start the server and go to the base URL of Lingovault, I see this page: 

![](https://i.imgur.com/HsK2fUa.png)

And that's it for today. In my next blog, it will be more fun because I will go more into detail about GET and POST requests as I will be walking you through how I create a form for this project. Thanks for reading!





