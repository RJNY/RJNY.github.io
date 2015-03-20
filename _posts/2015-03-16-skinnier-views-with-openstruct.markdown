---
layout: post
title: "Skinnier views with OpenStruct"
comments: true
date: 2015-03-16 11:02:21 -0400
---

Rails comes with some great helpers out of the box. With the help of instance variables, you are able to feed the view some pretty verbose, yet readable content. Here is what my views usually look like:

{% highlight erb %}
<% if current_user %>
  <%= current_user.name %>
<% else %>
  Guest
<% end %>
{% endhighlight %}

This is all well and good; However, we can make it more readable. We can make it so that current_user is always set to something so we don't need to make if/else conditionals. In our ```app/controllers/application_controller```, we can do something like

{% highlight ruby %}
require 'ostruct'

def current_user
  @current_user ||= User.find session[:user_id] if session[:user_id]
  if @current_user
    @current_user
  else
    OpenStruct.new(name: 'Guest')
  end
end
{% endhighlight %}

OpenStruct (from what I understand from the ruby docs) is a data structure, similar to a Hash that allows the definition of arbitrary attributes with their values.

now we can do something like this in our view:

{% highlight erb %}
<%= current_user.name %>
{% endhighlight %}

This is not always ideal as you may want to have login links or other conditionals. Still, this is a nice way to de-clutter your view.
