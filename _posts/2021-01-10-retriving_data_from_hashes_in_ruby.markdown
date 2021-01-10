---
layout: post
title:      "Retriving data from hashes in Ruby"
date:       2021-01-10 12:26:25 -0500
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




This returns "Chile". As you can see, we can simply access the value by its key. Let's make things a bit more complicated:


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

This returns "Finnish" because we are in the array of countries, grabbing the element at index 1, and then grabbing the value of the language key. Again, let's make it a bit more complex. Last time, I promise....


```countries = [ 
{
  name: "Chile",
  language: "Spanish",
  cities: {
    "Santiago" => {
      population: 4837295
    },
    "Valdivia" => {
      population: 127750
    }
  }
},

{
  name: "Finland",
  language: "Finnish",
  cities: {
    "Helsinki" => {
      population: 656229
    },
    "Espoo" => {
      population: 291439
    }
  }
},

{
  name: "Turkmenistan",
  language: "Turkmen",
  cities: {
    "Ashgabat" => {
      population: 1031992
    },
    "Turkmenabat" => {
      population: 234817
    }
  }
},

{
  name: "Bulgaria",
  language: "Bulgarian",
  cities: {
    "Sofia" => {
      population: 1242568
    },
    "Plovdiv" => {
      population: 346893
    }
  }
}
]```

If you notice, we have added some cities and populations (Note: The populations may not be accurate as they are just being used here as examples). We now have hashes nested in hashes! Wanna see some cities in Turkmenistan? No problem...just do this:

```countries[2][:cities]```

This will return:

```{"Ashgabat"=>{:population=>1031992}, "Turkmenabat"=>{:population=>234817}}```

Let's pretend we had a long list of cities here and we just wanted to see the population of Turkmenabat, then we would do this:

```countries[2][:cities]["Turkmenabat"][:population]```

and you would see the population.


You see? It's not very complicated, especially now that you know how to navigate it!








