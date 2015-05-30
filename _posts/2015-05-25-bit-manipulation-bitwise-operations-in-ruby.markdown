---
layout: post
title: "[Bit Manipulation] Bitwise Operations in Ruby"
comments: true
date: 2015-05-30 23:35:21 -0400
---

So today I decided to learn about bit manipulation. I only learned about them today so i'll be keeping it super simple [K.I.S.S.](http://en.wikipedia.org/wiki/KISS_principle). Lets start with setting up our playground for learning.


{% highlight ruby %}
1.to_s(2)  #=> "1"
2.to_s(2)  #=> "01"
20.to_s(2) #=> "10100"
{% endhighlight%}

As shown above, you can convert an integer to a string of binary using the [Fixnum#to_s](http://ruby-doc.org/core-2.1.0/Fixnum.html#method-i-to_s) method.  

For the sake of convenience, we're gonna make a new method for he Integer class

{% highlight ruby %}
class Integer
    def bits
        self.to_s(2)
    end
end

a = 20
a.to_s(2) #=> "10100"
a.bits    #=> "10100"
{% endhighlight%}

In case this confused you, we're just adding a method to the Integer class in Ruby. Cool? Cool, moving on!

##AND & OR operators

Lets quickly go over AND & OR operators. In binary, ```1``` represents ```true``` and ```0``` represents ```false```

{% highlight ruby %}
true && true    #=> true
true && false   #=> false
false && true   #=> false
false && false  #=> false

true || true    #=> true
true || false   #=> true
false || true   #=> true
false || false  #=> false
{% endhighlight%}

This will be important as we move forward. You do not need to be a Ruby guru to learn bit manipulation, but if these didn't make sense, I recommend going on [Code Academy](www.codecademy.com) and taking the ruby course or simply opening ```irb``` and coming back since this will be pretty important moving forward.

##AND operator &

The AND operater enumerates through the binary and returns values where both integers are equal to  ```1``` at both indexes. If they don't match, they will be set to ```0```

{% highlight ruby %}
(a = 20).bits   #=> "10100"
(b = 17).bits   #=> "10001"
(a & b).bits    #=> "10000"

# index 0 was the only index where the value was 1 for both arguments 
# thus everything else was set to 0, returning 10000
{% endhighlight%}

##OR operator |

The OR operater enumerates through the binary and returns values where _either_ integers are equal to  ```1``` at that index. They will set to ```0``` only if both are 0

{% highlight ruby %}
(a = 20).bits   #=> "10100"
(b = 17).bits   #=> "10001"
(a | b).bits    #=> "10101"

# index 0, 2 and 4 all had values of 1 in either comparisons
# they returned true and resulted in "10101"
{% endhighlight%}

##The XOR operator ^

The XOR operator will specifically take the value where values do not match, return ```true``` and set that value to 1. It will also omit any leading 0's in the process

{% highlight ruby %}
(a = 20).bits   #=> "10100"
(b = 17).bits   #=> "10001"
(a ^ b).bits    #=> "101"

#index 0: matched, it's set to false
#index 1: are both false, moving on
#index 2: one of the oporators are true, other is false. The XOR operator registers this as a true value and returns 1
#index 3: are both false, moving on
#index 4: same as index(2), registers true, sets it to one
#
#we now have 00101, it will omit the leading 0's and return "101"
{% endhighlight%}

##The NOT operator ~

The NOT operator flips 

{% highlight ruby %}
(a=17).bits #=> "10001"
~a          #=> -18
(~a).bits   #=> "-10001"
{% endhighlight%}

Alright, so that's not working like we expected... It's literally just prepending a ```-``` into the string

{% highlight ruby %}
-17.bits        #=> "-10001"
"-" + 17.bits   #=> "-10001"
{% endhighlight%}

Here are some examples of positive and negative integers and their binary:  

|binary -|- decimal|
|:---------|-------:|
|```0000```| ```0```|
|```0001```| ```1```|
|```0010```| ```2```|
|```0111```| ```7```|
|```1111```|```-1```|
|```1110```|```-2```|
|```1101```|```-3```|
|```1000```|```-8```|

So it looks like our ```#to_s(2)``` method isn't going to work here. We'll have to figure something else out.  

While it's true that represent negative numbers for human readable integers, the is impossible in computer land. There is an alternative however.

Using the [two's complement](http://en.wikipedia.org/wiki/Two's_complement) method, we have a clever way of getting negative integers following these simple rules.

- for zero, use all 0's
- for positive integers, start counting up, with a max of 2(number of bits - 1 ) -1.
- for negative integers, do exactly the same but switch the role of 0's and 1's (so instead of starting with ```0000```, you'll start with ```1111```, that's the "complement" part).

With this in mind, let's sample this with a [nibble](http://en.wikipedia.org/wiki/Nibble) (1/2 byte)

- ```0000``` - ```0```
- ```0001``` - ```1```
- ```0010``` - ```2```
- ```0011``` - ```3```
- ```0111``` - ```7```

That's as far as you can go with positives 2^(3)-1 = 7
As for negatives

- ```1111``` - ```-1```
- ```1110``` - ```-2```
- ```1101``` - ```-3```
- ```1000``` - ```-8```

It's a bit confusing to look at for a moment, but if you stop to think about it, it actually makes a lot of sense. 


##That's it!

I learned this pretty quickly and decided to write a post about it same day. If you have any questions or feedback, please [email me](mailto:rjny86@gmail.com). 

##References
- [How to Count, Programming for mere mortals by Steven Frank](http://www.amazon.com/Count-Programming-Mere-Mortals-Book-ebook/dp/B005DPIKPE).  
- I learned all the oporators from [Calle Erlandsson's Ruby bitwise operators](http://www.amazon.com/Count-Programming-Mere-Mortals-Book-ebook/dp/B005DPIKPE). 
- Thanks to stack overflow for a [simplified explenation of two's complement](http://stackoverflow.com/questions/1049722/what-is-2s-complement)
