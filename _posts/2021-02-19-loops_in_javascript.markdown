---
layout: post
title:      "Loops in JavaScript"
date:       2021-02-19 22:26:47 +0000
permalink:  loops_in_javascript
---


Today we will talk about loops in Javascript. More specifically, ```for``` loops because they are the most commonly used. We will go over both old and new syntax.

### What is a loop?

In programming, a loop is a structure that is used to repeat a block of code until the specified condition is met. 

### When to use a loop?

We usually use loops when we want to iterate over every element in an array or an object and check if it meets the condition specified or if we want to do something like add/subject something to/from an array or object. Counters are another common thing loops are used for. There are many other uses but these are quite common ones.

### Let's get into syntax...

The old syntax was like this:

```
let arr = [1, 2, 3];

for (let i = 0; i < arr.length; i++) {
    console.log(arr[i]);
}
```

It's a bit ugly but it gets the job done. Now we have more attrative ways to do this:

### ```for...of```

This is an example of the ```for...of``` loop that ES6 introduced to us. This loop works on arrays as well as strings.

```
let arr = ["x", "y", "z"];
for (let val of arr) {
    console.log(val);
}
```

And on a string:

```
let str = "string"
for (let char of str) {
  console.log(char)
}
```

### ```for...in```

The ``` for...in``` loop is for iterating over the enumerable keys of an object and should not be used to interate over arrays.

```
let obj = {a: 1, b: 2, c: 3};
for (let val in obj) {
    console.log(val);
}
```

And for fun, if we wanted to ```console.log``` the values instead...

```
let obj = {a: 1, b: 2, c: 3};
for (let val in obj) {
    console.log(obj[val]);
}
```

I hope this is blog helped anyone who needed it. Thanks for reading!



