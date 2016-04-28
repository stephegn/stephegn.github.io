---
layout: post
title:  "The ‘simple’ things are always the hardest"
date:   2011-08-25 14:20:00 +0000
categories: mysql
---

We have recently added ‘history’ to our application which is great!
I display this as a list of items and dates and we only show the user the last 15 items. I got this working with some simple SQL:

{% highlight sql %}
    SELECT * FROM history WHERE user = username ORDER BY time DESC LIMIT 15
{% endhighlight %}

Then I looked at it, the items you use a lot were duplicated so all I wanted to do was get rid of these. Simple! I hear you say. Not so…

First I tried looking at DISTINCT which was great but it only selected the item not both item and time. Then I looked at GROUP BY this gave some seemingly random results when I tried ordering by time.

I’ve still not found a resolution to this problem and am instead selecting the last 100 items and then looping through to find the first 15 duplicates. Obviously this is not the most efficient way of doing it but its all I have for now.

Gunna keep looking for a solution, maybe it will be simple and I just haven’t found it or maybe it will be 4 queries long like some people on the internets suggest.

Useful links I found:

* http://www.webmasterworld.com/forum88/9204.htm
* http://www.w3schools.com/sql/sql_distinct.asp
* http://www.w3schools.com/sql/sql_groupby.asp

__UPDATE
__
My wonderful coding partner has done it, he is a genius!
{% highlight sql %}
    SELECT filename,MAX(time) AS lastDownloadTime FROM history
    WHERE username = 'name'
    GROUP BY filename
    ORDER BY lastDownLoadTime DESC
    LIMIT 15
{% endhighlight %}
