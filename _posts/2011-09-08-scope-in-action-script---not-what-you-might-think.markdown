---
layout: post
title:  "Scope in Action Script – not what you might think"
date:   2011-09-08 13:15:06 +0000
categories: flex
---

I have previously coded in Java which has very strict scope for variables and this states that if a variable say ‘i’ is declared within a for loop eg:

{% highlight actionscript %}
    for(int i = 0; i<length; i++)
{% endhighlight %}

`i` only has scope within the for loop. This is not the case in action script where `i` has scope within the parent of the for loop.

This stumped me a little bit when I got a few warnings but it could have some really odd effects if you don't know about it.
