---
layout: post
title: "How to configure your \"rails new\" defaults"
comments: true
date: 2014-12-13 12:56:21 -0400
---

{% highlight bash %}
> rails new project
{% endhighlight %}

And just like that, you have a rails skeleton. However, if you're like me and prefer postgresql and rspec, you have a few extra steps before you can get started on your project.

Fortunately, rails has a few helpers. In your terminal, type:

{% highlight bash %}
> rails new --help
{% endhighlight %}

You should see some very useful options for rails new.

{% highlight bash %}
> rails new project -T -d postgresql --skip-bundle
{% endhighlight %}

Alright! Problem solved right? I no longer need to delete my test unit or configure my database.yml 

But I don't want to have to write this long command for each new project. You can put the defaults in your ~/railsrc file using your text editor (mine is sublime in this example):

{% highlight bash %}
> subl ~/.railsrc
{% endhighlight %}

Copy and paste the following 
{% highlight bash %}
--skip-bundle
--skip-test-unit
-d postgresql
{% endhighlight %}

Now restart your terminal. If I run rails new again, it will always append whatever is in the ~/.railsrc

{% highlight bash %}
> rails new project
{% endhighlight %}

One less thing to worry about. :-)
