---
layout: post
title:      "Setting up a Django project"
date:       2021-02-27 17:49:47 -0500
permalink:  setting_up_a_django_project
---


While attending Flatiron, I built a project using Ruby's Sinatra framework and I recently decided to build the same project again using Python's Django framework. Today I will walk you through the steps I take to do the initial set up. I already have Python installed so I will not go over that in this blog. I have also already created a repo for it.

### Plan the project

Taking the time to plan out your project before starting it is very important and can save you lots of time and keep you focused while developing any project. Because I'll basically be "translating" this from a previous project, I don't have much to plan out. The ideal user of this app would be a polyglot and the app will be a place that they can log their expiriences while learning different languages. Their entries will be organized by language. 

### Create the virtual environment

First, I will create a virtual environment. A virtual environment keeps Python packages separate from each other and you also need to do this if you plan to deploy a project. From within my project directory, I run:

```python3 -m venv lingovault_env```

This creates a new directory called lingovault_env. 

Now to activate the virtual environment, I run: 

```source lingovault_env/bin/activate```


![](https://i.imgur.com/CR4hmX7.png)


We know the virtual environment is active when we see the name of the virtual environment in parentheses as shown above. 

### Install Django

With my virtual environment active, I run: 

```pip install django```

Because I am doing this from within my virtual environment, Django will only be available while it is active so I will be building this whole project with it active. 

### Create the project in Django

Now I am ready to create my project in Django. I do this by running:

```django-admin startproject lingovault .```

This creates my project directory which I have called "lingovault". It also created a file called ```manage.py``` in the root directory which is where we put commands for Django to run. 

As of right now, my file directory looks like this:

![](https://i.imgur.com/2pDYpZD.png)

You can see the lingovault directory, lingovault_env directory, and the manage.py file that I just created. 

### Create the database

Now I am going to create the database. Again, with the virtual environment still active, I do this by running: 

```python manage.py migrate```

This creates a file in my root directory called ```db.sqlite3``` which is my database file. 

*Note: If you noticed, I just used ```"python"``` to run the command above, not ```"python3"```, that's because while the virtual environment is active, ```"python"``` refers to which ever version was used to create it. I used ```python3``` to create the virtual environment so it already knows I'm using python3.


### Start the server to view the project

Now, let's check it out to see if everything was created properly. I'm going to run:

```python manage.py runserver```

and then click on the link where it says the server is running....

![](https://i.imgur.com/YR7v9Wh.png)

Great! Everything has been set up successfully!


That's all for today. Stay tuned for future blogs where I will add models and functionality to this app. Thanks for reading!



