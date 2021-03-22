---
layout: post
title:      "Forms in Django "
date:       2021-03-22 17:49:01 +0000
permalink:  forms_in_django
---


I will continue to build onto my Lingovault app and bring you guys along with me. Today I'll be building a form that we can use to add a language. When I add user accounts, a user will be able to add languages to their lingovault. The form for adding a post for each language will not be covered in this blog as the process is very similar. In fact, a lot of what I will do today will be similar to what I wrote in my last blog. I will mostly be going into detail when I get to the GET and POST requests in the new_language view function. 

As usual, I'm in my project directory, virtual environment is active, server is running, and I'm ready to go.....

### Add URL path to urlpatterns

Because it is something I have been forgetting, I will first define the URL by adding the path() for new_language to the urlpatterns in lingovault_app/urls.py on line 15: 

![](https://i.imgur.com/xQeO8bK.png)

### The Magical ModelForm

I say "magical" because Django automates a lot of stuff here. ModelForm comes from the forms module which I will import along with Language because Language is the model I will be creating a form for. I'll build a class called LanguageForm and it will inheret from forms.ModelForm. Then I will nest a Meta class to tell Django which model to build the form from and which fields and labels to include in it. I have put all of this in a file called forms.py in the lingovault_app directory. The file currently looks like this:

![](https://i.imgur.com/wo9Fg6P.png)

### The new_language view

Ok, this is where I will be going into detail about what is going on in this view function. I'm going to show you what the view function looks like for new_language and then I will walk you through it. It is in the same views.py as my other views and here it is: 

![](https://i.imgur.com/m76Yat2.png)

Before I forget, I also imported 'redirect' from django.shortcuts at the top of this file. I totally forgot to do that while building this and then realized it was missing. Anyways...

Whenever we go to a page on the internet, we are basically telling the browser to make a GET request. The browser then sends that request to the server and then in short, the server renders the page. Whenever we fill out a form with  data, like a blog or a simple name and address form, and click a button to submit it, we are telling the browser to send a POST request. The POST request is sent to the corresponding view and it processes the data from the form. If it's valid, it is saved to the database and then we are often redirected to another page. So in the case of the new_language view, the function takes in a request, the method of that request is checked, if it is NOT a POST request, then the variable "form" is just an empty form. If it is a POST request, then the data that is stored in the POST request is passed into LanguageForm and stored in the "form" variable. The data in "form" is checked to see if it's valid, if it is, it get's saved and then it redirects back to "/languages" which is the page that shows all the languages. If it's not valid, there are default error messages that will appear to explain what is wrong. Then because the new_language.html template will be using data, I am setting "context" to equal the key-value pair that just holds "form". Now things get easy again....

### Build the new_language template

The new_language template is pretty simple. It just has some simple HTML defining a form. The action says where the form will be sent to, in this case, to the new_language view. The method is set to 'post' because there will be data sent will this form. The csrf_token(cross-site request forgery) tag is just to prevent unauthorized access to the server. Some more magic is happening on line 9. Django creates all the fields for the form automatically when use the template variable "form" that is from the view. ```as_p``` is just a way to tell Django to put everything into paragraph format so that it looks nice. new_language.html is with my other templates in templates/lingovault and it looks like this: 

![](https://i.imgur.com/dUjj9Dy.png)

### Link It Up

Then, I just add an a tag to languages.html so that I can go to the new_language form from the languages page. I put it on line 14:

![](https://i.imgur.com/gVDBtHz.png)


I can now add languages without using the admin site. 

That's all for today. Thanks for reading and I hope you enjoyed it. I'm not sure what I will blog about next but it will be something to do with this app. Stay tuned!





