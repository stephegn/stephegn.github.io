---
layout: post
title:  "Figuring out services in flex"
date:   2011-08-02 12:56:20 +0000
categories: flex
---

This had to be one of the things I struggled on most when picking up flex however it is really really easy!

I’m using a PHP back end and all you need is a http service:

{% highlight %}
    <s:HTTPService id=”dataService”
    method=”POST”
    url=”{phpFile}”
    showBusyCursor=”true”
    result=”handleDataResult(event)”
    fault=”handleFault(event)”/>
{% endhighlight %}

And then just set up some data to send it:

{% highlight actionscript %}
    var params= {};
    params[‘action’]=”getData”;
    dataService.send(params);
{% endhighlight %}

On the PHP side these are just received as post variables:

{% highlight php %}
    action = $_POST[‘action’];
{% endhighlight %}

Then the result (whatever you echo in PHP) is stored in:

{% highlight actionscript %}
    dataService.lastResult
{% endhighlight %}


See, easy :D

__*NOTE: I had huge problems when retrieving xml. It seems there are some problems when using flash builder and the network monitor.
If you’re getting end of stream errors try running your application with the network monitor disabled. *
__

This makes it so easy to produce a client server architecture using technologies which you are already familiar with. Flex does not just work
with PHP it will also work with lots of other service types in a similar fashion.
