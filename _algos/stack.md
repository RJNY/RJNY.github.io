---
layout: algo
title: Stack
date: 2014-12-07
code-url: https://github.com/RJNY/Computer-Science-Is-Fun/blob/master/stack.js
---

## What is a Stack?

A stack is a container of objects that are inserted and removed according to the last-in, first-out (LIFO) principle.

Imagine you had a stack of big plates at the bottom, smaller plates on the bigger plates, and bowls on top.

![stack of plates](/assets/img/stack-of-plates.jpg)

If you wanted a bowl, it'd be pretty simple. You can just gram from the top of the stack. If you wanted a large plate
however, it'd be a little more complicated. You'd have to remove the bowls, the small plates, and finally you
could grab a large plate.

## The Tower of Hanoi

![Tower of Hanoi](/assets/img/tower.jpg)

A perfect example of a stack would be the [Tower of Hanoi](https://en.wikipedia.org/wiki/Tower_of_Hanoi). You're
unable to grab the larger disks at the bottom without removing the smaller disks on top. This abides by the principles
of LIFO.

## Stacks in JavaScript

I've made a stack in JavaScript:

``` javascript
var App = (function () {

  function Stack () {
    this.top = null
  }

  Stack.prototype.pop = function() {
    this.top = this.top.next
  };

  Stack.prototype.push = function(el) {
    var next_node = this.top
    this.top = new Node(el, next_node)
  };

  Stack.prototype.peek = function() {
    if (this.top !== null) {
      console.log(this.top.value);
      return this.top.value
    };
    console.log("stack is empty");
    return null
  };

  function Node (value, next) {
    this.value = value
    this.next = next
  }

  return new Stack
})()
```

A stack is initialized by calling `App` and saving it to a variable. From there, you can `#peek` to see what's on the
stack. you can `#push` and `#pop` things from the stack.
