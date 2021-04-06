---
layout: post
title:      "Associations and Restricting Data in Django "
date:       2021-04-06 02:12:35 +0000
permalink:  associations_and_restricting_data_in_django
---


Today I will show you what I will do in order to connect a Language to a User. Let's get to it....

First I'll go to lingovault_app/models.py. I am going to need to use a ForeignKey that represents a user that a language will belong to. So, I have to import the User model by adding this line to the top of the file:

`from django.contrib.auth.models import User`

Then, in the Language class, I am going to add the ForeignKey that represents a user and assign it to a variable called "user" on line 9, like this:

![](https://i.imgur.com/ON6DXUe.png)

### Generate and Run Migrations

`python manage.py makemigrations`

Because I already have some data in the database, the migrations won't get created yet. I am presented with this message:

![](https://i.imgur.com/l5N5AIm.png)

Then is asks me something else:

![](https://i.imgur.com/4oho80m.png)

Again, I enter 1

and then the migrations are generated...

![](https://i.imgur.com/EgMPODm.png)

Now, I will run the migrations by running:

`python manage.py migrate`

![](https://i.imgur.com/vrZPDpY.png)

Now I can check to make sure that it worked from within the Django shell...

from lingovault_app.models import Language
for language in Language.objects.all():
print(language, language.user)

![](https://i.imgur.com/buXPpnf.png)

Now, all the languages that were already in the database have been assigned to lingovault_admin.

But I'm not done yet.....

### Only Allow a User to View Their Own Languages

This is a feature that I may change in the future but for now, I will implement it. It's also very simple. I'll go to views.py and in the languages view function, I'll add a filter query on line 16 like this: 

![](https://i.imgur.com/5xqrVa5.png)

All this does is looks at the user attribute that in the request object and tells Django to get only the languages that have a ForeignKey that matches the ID of the user in the request object.

### Protect the User's languages

I want to make sure that a user won't be able to manually to go to another user's language page, like localhost:8000/languages/4, and manipulate that other user's data. To make sure the current user is in fact, the owner of that language, I will just check if the language's user is the same as the user in the request object. I'm going to add this:

```if language.user != request.user:
         raise Http404
```

to a few different views, language, new_post, and edit_post, like so:
##### language
![](https://i.imgur.com/sl50VZh.png)
##### new_post
![](https://i.imgur.com/dqVB2yA.png)
##### edit_post
![](https://i.imgur.com/dGrDjiP.png)

Now if a user tries to access another user's languages, or manipulate their data, they will see a 404 error page.

### Associate the Current User with a New Language

The last thing I have to do today is set the current user to be the owner of the languages that they create. To do this, I'll set the new_language.user to equal request.user. Before that, on line 39, I also have to pass in the commit=FALSE there to the save function because I'm going to be modifing the new_language before I want it to be saved to the database. The end result will look like this:

![](https://i.imgur.com/iU29j2c.png)

A new language will now be saved with the current user's ID as its ForeignKey.

And there you have it! There are a few more things I will be adding to Lingovault before deploying it so I will include the live link in the next blog. Thanks for reading! 











