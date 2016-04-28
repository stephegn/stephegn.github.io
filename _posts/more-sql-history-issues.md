---
layout: post
title:  "More SQL history issues"
date:   2011-08-30 16:33:00 +0000
categories: mysql php
---

Following my previous post about recording history in a database I have come across a wonderful lifesaving query!

{% highlight sql %}
    unix_timestamp
{% endhighlight %}

I have always been a unix timestamp sort of person, really easy to compare, offset and format in PHP however the database I have taken over from uses the SQL timestamp thing – I’m not even sure what it is.
Which is an American formatted horror when you want to do anything with it. Like so:

    2011-04-14 22:44:22

I even created my own little PHP function just to format it how I wanted using this silly query (for every date!):

{% highlight sql %}
    “SELECT YEAR( ’” . $date . “’ ) AS ’Year’,
    DAY( ’” . $date . “’ ) AS ’Day’,
    MONTH(’” . $date . “’ ) AS ’Month’,
    HOUR( ’” . $date . “’ ) AS ’Hour’,
    MINUTE( ’” . $date . “’ ) AS ’Minute’”
{% endhighlight %}

But as I started to want to use offsets for different timezones it could get really messy!

However, with the use of the unix_timestamp SQL function all my issues have been solved!

Usage:
{% highlight sql %}
    SELECT unix_timestamp(’time’) FROM ’history’
{% endhighlight %}

Useful links:

http://www.epochconverter.com/
