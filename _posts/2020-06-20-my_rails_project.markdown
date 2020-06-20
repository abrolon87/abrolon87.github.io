---
layout: post
title:      "My Rails Project"
date:       2020-06-20 22:16:41 +0000
permalink:  my_rails_project
---

For my rails project, I decided to make VocabBank. It is meant to be for language learners and its basic function is to save words or phrases and their translations, meanings, and some example sentences.


This project was much bigger than the previous two projects. Apart from getting familiar with the file structure, I expirienced many challenges while making this app. That is a good thing though, because now I really feel like I understand how things are actually working behind the scenes in Rails. 


## Models

I have 4 models in my app; `User`, `Vocab`, `Language`, and `Example`. In each of the models, I have validations to make sure bad data doesn't get into the database, associations to show how the models relate to each other(or not), and other code according to the model. 

##User

`has_secured_password` is used to authenticate passwords with Bcrypt. Bcrypt is a gem that encrypts passwords.

In the User class, there is a class method that allows a person to sign into the app using GitHub. It creates a User based on their GitHub profile information . 

A user `has_many :vocabs`, and `has_many :languages, through: :vocabs`. This means that a user and a language aren't directly related. They need a join table....

##Vocab 

A `Vocab` `belongs_to` a user and also `belongs_to` a language. That makes this model a join table for `User` and `Language`. This is the thing that makes User and Language know about each other. 

A `Vocab` also `has_many :examples`. 

Vocab `accepts_nested_attributes_ for :language`. This is a macro that provides an attribute writer so we can create a language at the same time we are creating a Vocab. 

I also have a scope method that sorts the Vocab instances by their attribute, `word_or_phrase`

##Language

Language 'has_many :vocabs' and 'has_many :users, through: :vocabs'. This is the other end of the many to many relationship with User because they both `has_many` of each other `through:` the join table which, in this case, is Vocab.


##Example 

Example is currently my simplest model. It `belongs_to :vocab` and `validates :sentence` which means, it makes sure that the value is not empty.


## Controllers

The controllers are where the logic in the app lives. It the part of the app that communicates between the models and the views. In all of my controllers, I have strong params. Strong params are where you tell Rails what to permit into the database since the default is to let nothing through. Strong params are only used in the particular model, therefore they are private methods.


## Views

Finally, the views are the html.erb files that present the data to the user. The views corespond to the controller actions. We can write Ruby code in the views but we have to write it inside embedded Ruby(ERB) tags. 

This format is visible in the views, notice the = in it
`<%=  ruby code goes here  %>`  


This format is NOT visible in the views 
`<% ruby code goes here %>`


## What I learned
Before making my app, I thought I had a complete understanding about model relationships. However, while making it, I realized how much I didn't quite understand. The process of making my app was a great learning expirience. I spent a lot more time debugging in this app than any other of the ones I have made for Flatiron School. Thanks to `binding.pry` and `rails c`, I was able to play around until I figured things out for the most part. I still collaborated with other students and my instructor about a few things though. I definitely feel like I understand things better after running into errors over and over again and then fixing them.


