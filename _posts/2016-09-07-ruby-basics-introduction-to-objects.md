---
layout: post
title:  "Ruby - Introduction to ruby objects"
date:   2016-09-07 19:10
categories:
  - ruby
  - basics
  - beginners
---

## Intro
We're going to go through the basics of Ruby objects in these series of articles and try to cover all you need to know to get started with Ruby.

Remeber that you can test the highlighted codes directly from your terminal
opening the IRB (Interactive Ruby Shell), to do so, just type this in yout
terminal:
```
irb
```

So, let's get started!

### Everything is an object
To make things happen using Ruby, one always puts oneself in the place of an object and then has conversations with other objects, telling them to do stuff.

Role-playing as an object in your program is an integral part of object-oriented programming. To know which object you are at the moment, one may use the keyword `self`.  

```ruby
self 
# => main
```
As you can see, if you don't specify which object you are, you automatically play the role of the `main` object that Ruby provides us by default.

We'll delve into how one can play the role of different objects and why this is useful a little further down the line.

### Talking to objects
One object interacts with another by using what are called `methods`. More
specifically, one object "calls or invokes the methods" of another object.

In the example below, we call the method `even?` on the object that is the number `2` by placing a period (`.`) after the object, then adding in the name of the
method we want to invoke.

```ruby
2.even?
# => true
```

### Looking up methods
Ruby objects are happy to tell you what methods they provide. You simply call the `methods` method on them.  

```ruby
1.methods
# => [:%, :&, :*, :+, :-, :/, :<, :>, :^, :|, :~, :-@, :**, :<=>, ...] and so on
```

We're going to continue talking about Ruby Objects in the next articles, so stay
tuned!


"Happy coding!"
