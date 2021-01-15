---
layout: post
title:      "Parameters and Arguements"
date:       2021-01-15 03:20:10 +0000
permalink:  parameters_and_arguements
---


A few days ago, I saw that someone posted a question about an error they were getting. It brought back memories as I remember being as frustrated and confused as the poster seemed when encountering this error. The error was was an ArgumentError and it ususally says something like this:

```wrong number of arguments (given 1, expected 0)```


The thing is many people in their early days of coding, including myself, don't understand what the "given" and "expected" means and how it has to do with parameters and arguments. I will try to explain using Ruby in the easiest way possible and give an example as well.

First, let's talk about parameters. A parameter is a variable that is defined when defining a method. Let's take a look at the following example:

![](https://i.imgur.com/kykHE2y.png) 

Here we have defined a method called sayHelloToUser. When called, this method should ```puts``` the string. If we were to run this right now, we would get a NameError because we have the undefined variables "name" and "day" in our string. We need to add parameters into those parentheses after our method name on line 1 like so:

![](https://i.imgur.com/lv2Fg49.png)

Let's call this method now...

![](https://i.imgur.com/D0N8wog.png)

Uh oh, here is that error with "given" and "expected". First we will talk about the "expected". "Expected" goes with the parameters. Remember, when we defined our method, we also defined two variables, or parameters, "name" and "day". Because we gave our method two parameter variables, this method is *expecting* us to send two arguments whenever we call this method. 

Now, let's talk about arguments. Arguments are values that are passed into a method ***when it is called***. 
Arguments are *given* to a method. We didn't give any arguments to our method. You see the empty parentheses on line 5? Let's put two arguments in there:

![](https://i.imgur.com/uxKiC2A.png)

Now there is no error and we can see the puts message.


Sometimes people get confused when they are passing arguments to a method they see an error like the one I mentioned in the beginning of this post. For learning purposes, let's remove "day" from line 1 and run the code again:

![](https://i.imgur.com/YHnISSb.png)


As you can see, the error says ```wrong number of arguments(given 2, expected 1)```. This is because there is only 1 parameter variable defined, which in this case is "name".  If we were to remove "name" from line 1 as well, then our method would not be expecting any arguments because it wouldn't have parameters.

So, the things to remember are:

Parameters are defined when defining a method and dictate how many arguments are *expected* when calling that method. They are not actual values.
Arguments are values that are *given* when calling a method. They are the data that you want your method to work with.

I hope this helps some people understand the difference between parameters and arguments a little better. Thank you for reading :)



