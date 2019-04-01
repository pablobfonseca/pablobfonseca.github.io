---
layout: post
title:  "JS Reference vs Copy"
date:   2019-04-01 15:05:01 -0300
categories:
---

It's been a while since I don't write anything here, but here we go :)

I have been studying a lot of JS lately, and I bumped into some real nice tips,
it can be simple for those who already know JS but for me it was new and really
cool.

In Javascript if you assign the value of a variable to another variable like
this:
```javascript
let name = 'Pablo';
let name2 = name;
name2 = 'Peter';

console.log(name2);
```
This code above will return 'Pablo' or 'Peter'? It will return 'Peter' because
we re-assign the value of the variable `name2`.

What about arrays and objects?
### Arrays
```javascript
const languages = ['Javascript', 'Ruby', 'Python', 'PHP'];
const languages2 = languages;
languages2[3] = 'Elixir';

console.log(languages2);
```
What about now? If we check the value of `languages` and `languages2` now we
will see that the value has changed in both arrays:
```javascript
console.log(languages);
// ["Javascript", "Ruby", "Python", "Elixir"]
console.log(languages2);
// ["Javascript", "Ruby", "Python", "Elixir"]
```
This happens because `language2` is an array reference, not an array copy, they
point to the same array.

We can fix this using doing a copy intead:
```javascript
const languages = ['Javascript', 'Ruby', 'Python', 'PHP'];

// One way
const languages2 = languages.slice();


// Creating a new array and concat the old one in
const languages2 = [].concat(languages);

// Using the new ES6 Spread
const languages2 = [...languages];

// or using Array.from
const languages2 = Array.from(languages);
```
Now we have a copy instead of a reference, everytime we update the value in
`languages2` the array `languages` will remain the same.

### Objects
```javascript
const person = {
  name: 'Pablo',
  age: 24
}
const person2 = person;

person2.name = 'Peter';

console.log(person);
```
This will behave the same way as arrays, in this case, `person` will have the
propery `name` updated by "Peter" because it's a reference and not a copy.

We can fix that by doing the following:
```javascript
// Using Object.assign()
// The first argument will be empty Object, the second will be the object and  the third will be new properties or existent properties we want to change
const person2 = Object.assign({}, person, {name: 'Peter'})

// ES6 Spread
const person2 = {...person};
```

There's a little problem though, both `Object.assign` and ES6 Spread will do a
shallow copy of the object, what does that mean? it means that it will copy
only 1 level deep, check this out:
```javascript
const pablo = {
  name: 'Pablo',
  age: 24,
  social: {
    twitter: "@pablobfonseca",
    instagram: "@pablobfonseca",
    github: "@pablobfonseca"
   }
}

const peter = Object.assign({}, pablo, {name: "Peter"});

// If we change the value of `social` of the object `peter` we will also change the value on `pablo`
peter.social.twitter = "@peterparker"

console.log(pablo)
// {name: "Pablo", age: 24, social: {twitter: "@peterparker"}}

```
We can avoid this by doing a deep clone, but you should always think twice
before using it.

A workaround you can do is to convert the object to string and then convert it
back to object by using `JSON.parse`

```javascript
const peter = JSON.parse(JSON.stringify(pablo));
peter.social.twitter = "@peterparker";

// Now the object pablo will remain the same

```

That's it for today! I hope you guys could learn anything from it :)

Happy coding!


