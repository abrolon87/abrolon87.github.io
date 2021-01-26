---
layout: post
title:      "Ruby's .send method"
date:       2021-01-25 20:45:47 -0500
permalink:  rubys_send_method
---


Yesterday, I was presented with a code challenge to solve on [binarysearch.com](http://www.binarysearch.com). It was interesting to me because it required me to convert a string into a math operator. I never had to do this before so as every dev does, I asked Google, "how to convert string into a math operator ruby" and I came across the .send method. What this method actually does is it sends a message to the object you are calling it on (psst...remember everything in Ruby is an object!) and the object then decides what will be done with it. The .send method takes in a symbol or string as its first argument and it looks for any method that matches tha symbol or string. The other arguments that get passed in, get passed to the method itself. It's a bit confusing to try to explain this without an example, so let me show you....

![](https://i.imgur.com/5fiu8rW.png?1)

and for possible better understanding, here are the testcase values that were being passed in...

![](https://imgur.com/9BmWuIM.png)

and the output...

![](https://i.imgur.com/w87m169.png)

So, in my code on line 3, we have nums which is an array that we are iterating using the .map method and each element in that array is being assigned to the variable n. Then we go to line 4...

n is the object we will be calling .send on, or "sending a message to". As I mentioned, the first argument that .send takes is a symbol or string and it tries to find a method that matches it so in this case, op is a string and val is an integer that will be passed into op as an argument once the object(n) finds a method that matches the string in the op variable, which in the testcase is the addition(+) operator. So the result is, 4 will be added to each element in the nums array. 

So .send gives us a way to dynamically call methods on objects. 



I hope you enjoyed reading my post!


