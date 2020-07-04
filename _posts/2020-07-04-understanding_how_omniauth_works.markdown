---
layout: post
title:      "Understanding how OmniAuth works"
date:       2020-07-04 19:58:35 +0000
permalink:  understanding_how_omniauth_works
---


Before I get into how OmniAuth works, let me explain what it is. OmniAuth is a gem that we can use in our applications that uses an Open Authorization protocol to authenticate and login users through a third-party site(or "provider") without using a password.

<br>


The way it works is we would register our application with a provider. Facebook, Google, GitHub are all very common ones. I used GitHub in my Rails project. Then we obtain a client_id and a client_secret. It is encrypted in a way to be more secure so in may look like nonsense. We save this in a .env file and **immedietly add the .env file to .gitignore. Do forget to do this before pushing to Github! Treat this info as you would a password** The code in your .env file should look something like this:

<br>

```
GITHUB_KEY=(a long combo of random letters and numbers without parentheses)
GITHUB_SECRET=(another long combo of random letters and numbers without parentheses)
```


<br>

In config/initializers/omniauth.rb, we need to let OmniAuth know which provider to make requests from. We do so by putting in a do/end block that looks something like the code below, notice we have our saved GITHUB_KEY and GITHUB_SECRET passed in to there: 

<br>


```
Rails.application.config.middleware.use OmniAuth::Builder do
  provider :github, ENV['GITHUB_KEY'], ENV['GITHUB_SECRET']
end
```


<br>


***Note: You may need more code in this block depending on which provider you use***


<br>


Once we have that set up, we need to also add the routes to config/routes.rb like so:

```
match '/auth/github/callback', to: 'sessions#github_create', via: [:get, :post]
```

<br> 

This way the we get routed to the sessions controller github_create action during the callback process of logging in. 

<br> 

We also need to give users a link to be able to click on in order to iniciate this entire process. Shown below: 
 
 <br>
 
 `<%= link_to 'Sign in with Github', '/auth/github' %>`
 
 <br>

Where exactly you put it in your views is up to you but just be logical about it. I put my link in a conditioinal statement in my layouts/application.html.erb that shows log in and signup links if a user is not logged in. Here is what it looks like:


<br>

```
<div>
      <% if logged_in? %>
       <%= link_to "Home", user_path(current_user) %> |
       <%= link_to "Add a Vocab or Phrase", new_vocab_path %> |
       <%= link_to "My Vocabs and Phrases", vocabs_path %> |
       <%= link_to "Logout", logout_path, method:"delete" %> |
      <% else %> 
       <%= link_to "Sign Up", signup_path %> |
       <%= link_to "Log In", login_path %> |
       <%= link_to 'Sign in with Github', '/auth/github' %>
      <% end %>
    </div>
```

<br> 

So in a real situation, when a user clicks on the link that says "Sign in with GitHub", they get redireted to the GitHub sign in page. If they are not currently signed in there, they would sign in and Github would ask permission to let the app access their log-in credentials from GitHub in order to sign into the app. If the user allows, then they are redirected to the callback url which points to our sessions#github_create action. That is where a new session is created using the user's credentials obtained from the provider, in our case, GitHub. Then, they are successfully logged into the app without having to use a password directly in the app.


And that is how OmniAuth works.

Thank you for reading







