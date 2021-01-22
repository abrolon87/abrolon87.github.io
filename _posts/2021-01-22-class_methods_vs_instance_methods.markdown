---
layout: post
title:      "Class Methods VS Instance Methods"
date:       2021-01-22 18:38:45 +0000
permalink:  class_methods_vs_instance_methods
---


Today I'm going to explain the differences between class methods and instance methods. 

As you may know, classes create objects, or "instances". Inside the class is where we can define what the objects that the class creates can do. Let's say a Human object can speak, walk, and eat....

![](https://i.imgur.com/nLC9cTc.png)

The methods in the example above are instance methods. This means we can only call these methods on an instance of Human, not on Human itself. Therefore, calling ```Human.speak``` would result in a NoMethodError. This is because Human is a class, not an instance. Let's make an instance of Human....

``` amanda = Human.new```

Now we have an instance of Human, ```amanda```. We can call these methods directly on ```amanda```.

```amanda.speak``` will puts "Hello"

```amanda.walk``` will puts "walking" 

and ```amanda.eat``` will puts "eating pizza"

If you noticed, we called ```.new``` on the Human class in order to create the instance of ```amanda```. That is what we call a built-in class method. We didn't make it, Ruby gave it to us. We can make our own class methods inside our class though. We can do this with the ```self``` keyword. We use the ```self``` keyword because we are inside the class scope and it knows what self is. Let's put a class method inside of our class. It should be something that makes sense to call on the class...

![](https://i.imgur.com/ykSR2Ct.png)

Now we can call ```Human.make_extinct``` and it will puts out "Humans are now extinct". We would not be able to call this method on ```amanda``` though, because again, ```amanda``` is only one instance of Human.

And there you have it! I hope my example is able to clear some things up for people. Thank you for reading!



