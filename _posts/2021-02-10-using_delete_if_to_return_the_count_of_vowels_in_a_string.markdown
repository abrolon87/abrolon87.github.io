---
layout: post
title:      "Using delete_if To Return The Count Of Vowels In A String"
date:       2021-02-11 00:06:44 +0000
permalink:  using_delete_if_to_return_the_count_of_vowels_in_a_string
---


During my coding practice time this week, one of my challenges was to return the number of vowels in a string and I'm going to take you step by step, how I did it with Ruby. 

Because I was doing it on [CodeWars](http://www.codewars.com), I started with an empty method like this:

![img](https://i.imgur.com/sQDCOHB.png?1[/img])

The method is called getCount and it takes an argument which is a string that is represented by the parameter variable, inputStr.

First, I knew I would need to use the split() method to split the string into an array so I could evaluate each letter. I also use the p to print the result so I could see if it was what I wanted:

![img](https://i.imgur.com/y83hctl.png?1[/img])

This gave me exactly what I wanted, an array of characters:

![img](https://i.imgur.com/kN6cLqH.png?1[/img])

So since I know it's what I want, I'll assign it to a variable and return that variable:

![img](https://i.imgur.com/oo7Ny0x.png?1[/img])

Now,  I am going to iterate over the array ```vowels``` and using the ```delete_if``` method, I will delete any character that is not a vowel, and then return what is left:

![img](https://i.imgur.com/FOaySl3.png[/img])

Here, I am using the "not equal to", (```!=```) and the "and" ampersands (```&&```) to get rid of any character that is not equal to any of the vowels. Then, at the end, I am returning the vowels array since all non-vowels are gone. Now remember, I had to return the count of the vowels, so we just add the ```.count``` method to the vowels array and the number of vowels is returned.

This is not the most efficiant way to solve this challenge, but it does show the usage of ```delete_if```. So, I hope this was helpful if you wanted to know how to use ```delete_if```.  Thanks for reading!



