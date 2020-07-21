---
layout: post
title:      "Rails API with a JS frontend: A Whole New World"
date:       2020-07-20 17:51:02 -0400
permalink:  rails_api_with_a_js_frontend_a_whole_new_world
---


The Javascript section of the curriculum was very short. Before I knew it, I had to decide on a project idea. That was a struggle in itself. At first, I decided to make a flashcard app. It got to a point in my code that I felt like there was no fixing it, so I decided to restart and make a problem tracker instead. 


#### A special note about Git commands.
Before we go any further, I want to tell everyone who reads this that they should run the Git commands from the root project directory. **Do not run them from inside the /backend or /frontend directories**. By running these commands from the root project directory, you will save yourself a major headache. If you create a new directory, for example `/frontend`, you will need to put the whole file name when you want to stage it to Git. after you create a file in the frontend directory. For example, if you create an `index.html` file inside of it, you would run  `git add /frontend/index.html` from the root project directory. If I remember correctly, it will not get staged if it doesnt have a filed in it, I could be wrong though. If you keep reading, I will be mentioning this again when we get to the Javascript Frontend part and talking about my terminal setup.

## Rails API

This was the easy part of the project. First, I created the repo on Github and then cloned it. I cd'ed into the repo directory and that is where I ran `rails new backend --api`. I wanted "backend" as the name of my directory and `--api` leaves out things you don't need in an API. I did use the `active_model_serializers` gem. You can read more about that [here.](https://www.rubydoc.info/gems/active_model_serializers/0.8.2/ActiveModel/Serializer) I also used the `rack-cors` gem to make cross-origin happen. I did not use scaffold. I used rails g to generate the files I needed. 

### Models

I have 2 models in my project; Problem and LifeAspect. A LifeAspect `has_many :problems` and a Problem `belongs_to :life_aspect`. 

### Controllers
I also have a controller for each model. In the controllers, I have my CRUD actions and strong params.


### Seeds
If you aren't into seeding your database, I highly recommend doing it for this project. Here is how I set mine up:

```
LifeAspect.create(name: "home")
LifeAspect.create(name: "health")
LifeAspect.create(name: "work")



Problem.create(body: "arguing with mom", date: "2019-2-11", solved?: false, life_aspect_id: 1)
Problem.create(body: "neighbors too noisy", date: "2019-2-11", solved?: false, life_aspect_id: 1)
Problem.create(body: "i need to loose weight", date: "2019-5-11", solved?: false, life_aspect_id: 2)
Problem.create(body: "annoying coworkers", date: "2019-2-11", solved?: false, life_aspect_id: 3)
Problem.create(body: "not paid enough", date: "2019-2-11", solved?: false, life_aspect_id: 3)
```

Don't forget to run `rails db:seed`!



## Javascript Frontend

Once I had the backend all set, I started the frontend. I `cd ..` 'ed back into the root directory and ran `mkdir frontend`. This created my directory for my frontend code. 

Before going any further, this is where I would cd into /frontend and I would run `touch index.html`. Then `cd ..` back into the root project directory and run `git add /frontend/index.html`. From here on, I recommend having a split terminal inside of VSCode, (or Sublime, or whichever you use). One for frontend and one for backend. Also, keep your desktop terminal open in the root project directory to be able to run git commands easily without having to `cd` all the time.  



