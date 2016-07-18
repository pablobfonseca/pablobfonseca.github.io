---
layout: post
title:  "Underscore - Ruby Secret Weapon"
date:   2016-07-18 18:40:00 -0300
categories: ruby
---

Once in IRB, the underscore holds the return value from the last command.

```ruby
{name: "John Doe", job: "Developer"}
data = _ # it assigns the last command to the variable data
data.inspect
# => {name: "John Doe", job: "Developer"}
```

Guess what? It works in the Rails console too :)

