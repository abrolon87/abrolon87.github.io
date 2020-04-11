---
layout: post
title:      "My First Sinatra App"
date:       2020-04-11 03:23:52 +0000
permalink:  my_first_sinatra_app
---



I recently finished my first Sinatra app. It was a challenge but it was a bit easier than the CLI project, only much bigger. The file structure is different and it can be confusing to navigate in the beginning. I used the Corneal Ruby gem by running `gem install corneal`,  `corneal new lingovault` and then `bundle` to get setup.

As I am part of the polyglot internet space, I thought it would be cool to make an app that users can keep track of the languages that they know or are learning and share a little about their experience with the language. Be it how they learned, what materials they used, how long they focused on it, etc.

To start, a user must first sign up and then they will be able to log in using a username and a password.
The user must be logged in to use the app because no actions can be completed otherwise. I included all of the CRUD actions in my app so: 


* A user can Create a language entry which is then saved to the ActiveRecord database.
* A user can Read all of the languages
* A user can Update their own language entry 
* A user can Delete their own langauge entry


My app also uses an MVC framework to provide seperation of concerns. This means that each group of files has specific jobs and they interact with each other in certain ways. MVC stands for Model, View, Controller. The model folder contains the logic of the app and where data is worked on and/or saved. The views folder contains the HTML, CSS, Javascript, things that the user sees also know as the "front-end". The controllers folder contains files that communicate between the views and the models, and from the app to the browser. 

### Models:

*user.rb
This file contains the User class. A user `has_many` languages. 

*language.rb
This file contains the Language class. A language `belongs_to` a user. 

`has_many` and `belongs_to` are associations that make it easier to find data in the database. A language has a foreign key that is called `user_id` to show which user it belongs to.

### Views:

The Views directory contains 2 sub-directories; users and languages. The files in each directory are responsible for collecting information from the user by displaying forms and then rendering that information.

### Controllers:

*application_controller.rb
    This is the main controller. It is responsible for the general things in the app like, enabling and setting sessions, setting the public and views folder, etc. It also inherets from Sinatra::Base which is important because the other controllers will inheret this controller and will then have access to Sinatra::Base as well.
		
*users_controller.rb
    This controller is responsible for things that users do; login, signup, logout. It also makes sure the user uses the correct password when logging in and that a user enters a unique username and email when signing up.
		
*languages_controller.rb
    This controller is responsible for things that are done to languages; creating, reading, editing, deleting. It confirms the user is in fact the owner of the language entry in order to edit or delete.


I also have a helpers directory in the top level that contains a file with two methods that I can reuse in my app. One method, `Helpers.current_user(session)`  is for identifying the current user. The other method `Helpers.is_logged_in?(session)` can be used to check if the user is logger in.  They both take the argument of `(session)`.


I have learned a lot of stuff while building this app. That is usually the way it goes. While doing the labs, it can seem confusing but, when you know what you're trying to do on your own project, it's a bit easier to understand. Every new error I see, I see it as a new learning opportunity. 

Now that I'm done with this project, I'm now realizing that we really went over a lot of stuff in this section of the curriculum. 

If you want to check out this repo, you can check it out [here](https://github.com/abrolon87/lingovault_sinatra_MVC)


Thanks for reading about my Sinatra MVC app project!







