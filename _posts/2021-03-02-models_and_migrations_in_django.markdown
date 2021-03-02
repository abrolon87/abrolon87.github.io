---
layout: post
title:      "Models and migrations in Django"
date:       2021-03-02 20:11:51 +0000
permalink:  models_and_migrations_in_django
---


In today's blog, I will be walking you through the next few steps of building my Django app which involve creating the infrastructure needed to build the app and create models and migrations. Because this isn't a tutorial, I will not be going through more than one model or any other repetative steps in t

### Start an app 

I already have my project open, my virtual environment active, and I'm in my root directory, so I'm just going to get right to starting an app. I say "an app" because a Django project is technically a bunch of separate apps that work together in order for the whole project to work. To start an app, I'm going to run:

```python manage.py startapp lingovault_app```

After running this command, I now have a new directory called "lingovault_app" and it contains some files and a directory called "migrations". One of the files in the lingovault_app directory is ```models.py```, I'm going to start adding to that file now....

### Create a model

Time to define a model. In the models.py file, I'm going to create a Language class like so:

![](https://i.imgur.com/F7mB5vj.png)

I gave it two attributes, name and date_added and I am returning a string representation of Language.

### Include lingovalut_app in the project

Now I have to tell Django to include lingovault_app in the project. As I mentioned, Django projects consist of several apps that work together. There are default Django apps and then you can add custom apps. In the lingovault/settings.py file, there is a constant called ```INSTALLED_APPS```  that I'm going to add 'lingovault_app' to...

![](https://i.imgur.com/REB1vxI.png)

The other apps are the default apps that I mentioned. Sometimes we want to override default Django apps so it's best to put custom apps before the default ones. When I create other apps, I will add those to this array, too, right underneath ```lingovault_app```. 

### Create a migration

Now that I have my Language class defined, I'm going to tell Django to generate a migration for it by running:

```python manage.py makemigrations lingovault_app```

NOTE* As I mentioned before, I won't be going over repetative steps in this blog but just know that I will be running this same command everytime I modify the ```models.py``` file. 

This command created this file in the lingovault_app/migrations directory:

![](https://i.imgur.com/5vTJOLD.png)

This is a migration and in order for it to be applied to the database, I'm going to run:

```python manage.py migrate```

![](https://i.imgur.com/sdYSy1K.png)

And the green "OK" lets me know that everything has migrated successfully.

Well, that's all for today. Thank you for reading and stay tuned!





