---
layout: post
title: "How to configure your \"rails new\" defaults"
comments: true
date: 2014-12-13 12:56:21 -0400
---

``` bash
> rails new project
```

And just like that, you have a rails skeleton. However, if you're like me and prefer postgresql and rspec, you have a few extra steps before you can get started on your project.

Fortunately, rails has a few helpers. In your terminal, type:

``` bash
> rails new --help
```

You should see some very useful options for rails new.

``` bash
> rails new project -T -d postgresql --skip-bundle
```

Alright! Problem solved right? I no longer need to delete my test unit or configure my database.yml

But I don't want to have to write this long command for each new project. You can put the defaults in your ~/railsrc file using your text editor (mine is sublime in this example):

``` bash
> subl ~/.railsrc
```

Copy and paste the following
``` bash
--skip-bundle
--skip-test-unit
-d postgresql
```

Now restart your terminal. If I run rails new again, it will always append whatever is in the ~/.railsrc

``` bash
> rails new project
```

One less thing to worry about. :-)
