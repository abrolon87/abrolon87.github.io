---
layout: post
title:      "Protecting Views From Unauthenticated Users in Django"
date:       2021-03-30 01:11:27 +0000
permalink:  protecting_views_from_unauthenticated_users_in_django
---


Since my last blog, I have added some things to Lingovault. A user can now be registered and login/logout. Today I want to share with you how I will restrict access so that a user must be logged in in order to visit certain parts of Lingovault. As usual, I'm ready, let's get started....

### Django decorators

Django has these things called "decorators" that are put before a view function to change what that function does. I am going to use the login_required decorator so first, I have to import it by adding this line to the top on my lingovault_app/views.py file:

```from django.contrib.auth.decorators import login_required```

Then, I will add ```@login_required```  in several places but just to give an example, I will show you here:

![](https://i.imgur.com/cU0pqXg.png)

In my example above, this prevents someone from accessing languages unless they are logged in. If someone tries, they will be redirected to the login page. There is one more step to complete to make it work, though. In ```settings.py```, I'm going to let Django know where to redirect unauthenticated users by defining ```LOGIN_URL``` and setting it to ```users:login```. I will put it all the way at the bottom of ```settings.py```, like this:

![](https://i.imgur.com/OcaxCc4.png)

Now, if a user tries to go to '/languages' by clicking on the languages link or otherwise, they will be redirected to the login page. 

I went ahead and added ```@login_required``` before every view function in lingovault_app/views.py except the home view function. So the only thing an unauthenticated user can see is the home page. 

That's all for this blog post. While simple, it's always important to know how to control user access to certain parts of your applications. Thanks for reading! 








