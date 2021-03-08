---
layout: post
title:      "Django's Admin Site and Superusers "
date:       2021-03-08 16:24:20 +0000
permalink:  djangos_admin_site_and_superusers
---

Today is when this app will start to be a bit different than the Sinatra version. I am going to set up the admin site for Lingovault and create a superuser. An admin site is meant for people who manage the site. These people have superuser accounts which gives them more privileges than a regular user. For example, a regular user can usually only edit or delete their own data and may be able to read others' data. A superuser can can delete anyone's data if they wanted. 

### Create a superuser account

As usual, I am all set to go with VS Code open, virtual environment active, and server running. So from my terminal, I am going to run:

```python manage.py createsuperuser```

and it gives me the fields to fill out. I filled out username and the password fields. It isn't mandatory to use an email.

![](https://i.imgur.com/xhMxPNi.png)

I have now successfully set up a superuser account. 

### Sign into the admin site 

To sign into the admin site, I just go to http://localhost:8000/admin and it gives me the Django administration login page:

![](https://i.imgur.com/nkNIEpA.png)

I sign in using the username and password I just used to create a superuser, and it brings me to the admin dashboard:

![](https://i.imgur.com/dBNx1TQ.png)

You can see the Users and Groups here now. These are models that Django automatically includes and I have to tell it to include the models that I create. I already created a Language model so I will register it with the admin site so that we can see it here, too....

### Register Language model with the admin site

In order for Django to include my custom models on the admin site, I have to register it by adding some code to the admin.py file:

![](https://i.imgur.com/d1JMREM.png)

First I import it, and then pass it in as an arguement to .register. 

Now, let's go back to the server and refresh.....

![](https://i.imgur.com/OoqEO1Y.png)

The lingovault_app models will now show here. This means that an admin is able to perform CRUD actions on any one of my custom models. I only have a Language model for now but I will be adding more before the next blog. In the next blog, I will talk about views and templates. 

That's all for today. Thank you for reading and I hope you enjoyed it!










