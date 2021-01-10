---
layout: post
title:      "Retriving data from hashes in Ruby"
date:       2021-01-10 17:26:24 +0000
permalink:  retriving_data_from_hashes_in_ruby
---


Today I'm going to go over something that is actually quite simple but that I often draw a blank about. That "something" is how to retreive data from hashes. 

First, let's take a look at what a hash is...


A hash is a data type that stores data in key-value pairs. It can be identified by the curly braces in which the data is wrapped. It looks like this:

```this_is_a_hash = {key:  "value"}```

For better understanding, here is a real world example:

```country = { name:  "Chile"}```

The name of our hash is ```country```, the key is ```name```, and the value is ```Chile```. Now that you have an idea of what a hash is, let's retrive some data from it:


```country[:name]``` 


This returns Chile. As you can see, we can simply access the value by its key. Let's make things a bit more complicated:


```countries = [
  
{
  name: "Chile",
  language: "Spanish"
},
{
  name: "Finland",
  language: "Finnish"
},
{
  name: "Turkmenistan",
  language: "Turkmen"
},
{
  name: "Bulgaria",
  language: "Bulgarian"
}
] ```

Here we have an array of hashes called "countries". Each hash has a key of "name" and a key of "language". Let's say we want to access the language in Finland...

```countries[1][:language]```

This would return Finnish.

To be continued....



