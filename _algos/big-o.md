---
layout: algo
title: Big O Notation
date: 2014-11-07
---

## What is The Big-O?

The Big-O was a pretty stellar Anime that premiered in the US on Cartoon Networks "Adult Swim".

![the big o](/assets/img/the-big-o.jpg)

### J/K, LOL!!1one

![the big o](/assets/img/lolface.png)

## Ok really, What is Big O Notation?

Big O notation is basically how computer scientists talk to each other about the complexity of an algorithm.

Say we have an array of fingers on one hand.

`fingers = ['thumb', 'index', 'middle', 'ring', 'pinky']`

If we traversed through this array looking for the thumb, we'd find it instantly since it's the very first value to
come back in our iteration.

If we traversed through the same array looking for the pinky, it'd be the last value in our iteration, meaning it'd be
the slowest return value by comparison.

To be honest, on an array with 5 values, it doesn't matter much. It's pretty convenient that we know exactly how
many values we have in this array, but what about when we're accessing a database that is constantly growing, and we
can never be sure how many records we'll be accessing? What is the best algorithm to use for X amount of records. The
answer? ["It depends"](https://betterexplained.com/articles/sorting-algorithms)

## So how do I figure out what's the best for each given scenario?

The [Big O Cheat Sheet](http://bigocheatsheet.com/) helped me a lot when I was learning Big-O. I still think it's on of
the best resources for learning Big-O

