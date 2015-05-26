---
layout: post
title: "[Interviews suck] Tips for crushing it."
comments: true
date: 2015-05-11 23:35:21 -0400
---

I'm just gonna say it...Interviewing for a dev position sucks! It is the most humbling, brain racking experience I've ever been through. Alas, it is a natural process for getting hired. Lately, I've been on a LOT of interviews and got a LOT of rejections. Rejection sucks sure, but I always ask for feedback. Here is what I learned:

##KNOW THY COMPLEXITIES
Every once in a while, you go on an interview for a company that you L-O-V-E. Butterflies in your stomach, right culture, great atmosphere, refreshments. You make it to the last interview and get all the answers right. Your interviewer says "OK, this works! ...**can we do better?**" and you're thinking "wtf do you mean better? Does he mean cleaner? Is it not readable?". Interview ends, you go home, next week you get an email saying you've been rejected. What happened?

##BIG O
When I first heard about this in school, I thought about the [anime on adult swim](https://www.youtube.com/watch?v=s7_Od9CmTu0). I didn't appreciate the significance of this topic until I began interviewing. So what is Big-O?

Big-O is used to communicate the performance of an algorithm. For example. 

{% highlight ruby %}
macias_family = ["Richard", "Christina", "Mary", "Stephano", "Giovanni"] 
macias_family[0] #=> "Richard"
{% endhighlight %}

Accessing the 0th value of the family array takes O(1) time (oh-of-one). What this means is that it will always take, worst case, one operation to complete this action/algorithm. Makes sense? Moving onward!  

Say I want an algorithm that will print out all the names of any family:


{% highlight ruby %}
def meet_the_family(family)
    family.each do |member|
        puts member
    end
end

meet_the_family(macias_family) #=> O(n) operation
{% endhighlight %}

This operation will process the length of the array which is a length of 5; however,we would not say O(5), we'd say O(n). If the array is a length of 2 or 100000, We'll still call it O(n) because we are measuring by the worst case.

{% highlight ruby %}
family_tree = [["jack", "jill"], ["Angelina", "Brad"], ["foo", "bar"]]
family_tree << macias_family

def extended_family (large_family)
    large_family.each do |small_family|
        meet_the_family(small_family)
    end
end

extended_family(family_tree) #=> O(n^2) operation (oh-of-n-squared)
{% endhighlight %}

Starting to see the pattern here?

We're iterating through two arrays: the ```family_tree``` array and every array inside it. Thus, O(n^2).

#Your algorithms suck!

...Is something I was told by my mentor recently after complaining that I was submitting working code, but wasn't getting the job. Here's why.

##Get greedy

Remember that thing I was talking about? Big-O? Yeah, my complexities sucked. This is why it's good to use better data structures. A Binary tree is a good example

![image]({{site.url}}/assets/img/bst.png)

I won't go in depth with the binary tree today. I think I can make a pretty lengthy blog post about how to structure a binary search tree, so let's just talk about its complexity for a moment.

The wonderful thing about the binary search tree is the Big-O complexity. Given the above example. If I wanted to find 65, the search would begin at the root, which in this case is 60. 65 is greater than 60, so it would travel right. 65 is less than 74 so it would go left. 65 is == 65, it's a match! return true.

In a linear search, worst case wouldbe O(n), we've simplified our search to O(log n). The best way I can describe O(log n), is dividing a problem in half, over and over until you find the value you are looking for. This continuously halves your search complexity as opposed to going through each iteration.

{% highlight ruby %}
# PSEUDO CODE #
binary_tree = [{value: 60, left: {value:41 left:{Obj} right:{Obj}}, right:{value: 74, left:{Obj}, right:{Obj}}}]
def value_exists? argument
    return true if value == argument

    current_value = value
    while value != nil 
        return true if current_value == agument

        if agument < value
            current_value = right.value
        elseif agument 
            current_value = left.value
        end
    end
    return false
end
{% endhighlight %}

So in this example, we're traversing the binary tree until we find a match or bust in the process. This is great because if we had a sorted array, it'd be ```[16,25,41,42,46,53,55,60,62,63,64,65,70,74]```. if We were to run ```value_exists?(74)``` we would get it on the 2nd try, vs the linear search which would literally give us the worst result.  

##Crushing it!

That's all I got for now. I wanted to include some JavaScript examples but I think it's best I save it for another post as well since I'm gonna go pretty in depth. I'm trying my best to crush it, I hope you will too!  

<iframe width="560" height="315" src="https://www.youtube.com/embed/E3kP2A80KIw?t=36s" frameborder="0" allowfullscreen></iframe>  

##References  

You can learn more about Big-O with the [Big-O cheat sheet](http://bigocheatsheet.com/).  
I'm also a big fan of [interview cake](https://www.interviewcake.com/).
