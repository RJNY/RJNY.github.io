---
layout: algo
title: Linked List
date: 2014-12-07
code-url: https://github.com/RJNY/Computer-Science-Is-Fun/blob/master/linked-list.js
---

## What is a linked list?
A linked list is a linear data structure. Each node has it's own value and where the next node is.

![linkedlist_example](/assets/img/linked-list2.png)

Take the above image for example:

- Node 1 (the head node) has it's own value `1` and knows only where the next node is.
- Node 2 doesn't know anything about it's parent node. It has the value of 2 and knows where the next node is (node 3)
- Node 3 has the value of 3, but it doesn't have another node, this is also known as the tail node.

If you were to drop the 2nd node, you'd also lose the 3rd. This has advantages and disadvantages.

## Doubly Linked Lists
A doubly linked list has a previous node and a next node. Similar to the Linked List, except that a child node
knows where its parent is.

![doubly linked list](/assets/img/doubly-linked-list.png)
