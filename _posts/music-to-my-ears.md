---
layout: post
title:  "Music to my ears"
date:   2016-04-28 12:37:00 +0100
categories: php
---
#Music to my ears
Having started at Magma Digital I have been given the opportunity to play with some awesome tools and frameworks for PHP which have really made me fall in love with the language again.
I started programming in PHP around 3 years ago when I started working at Just computers part time while at university. My use of the language was very imperative but PHP has moved on so
far from that and has turned into a really interesting and exciting language. In this series I want to discuss some of the tools I have discovered and any features of PHP I have found really useful.

##Composer

The first tool I want to introduce is called [Composer](http://getcomposer.org/) and is something I got really excited about when I discovered it. I think it is a must for any PHP
project and the first thing I set up. Composer at it’s simplest will pull in the dependencies of a project. Any 3rd party libraries which you want to use can all be defined in the
configuration file and then installed in one simple command. You can specify the version of these libraries in this file and update them using a similar command. This is a great way to
get everything you need installed and ready to use.

###Auto Loading
However, composer really comes into its own when you discover it’s auto load functionality. Every library is stored in the vendor folder and auto loaded using PHP namespaces so you
have access to it wherever you need by adding this single line to your project. (I might write a post on namespaces soon, they are awesome!)

{% highlight php %}
    require 'vendor/autoload.php';
{% endhighlight %}
You can easily add your own namespaces to the auto load script by just adding it into the configuration file.
{% highlight yaml %}
    {
        "autoload": {
            "psr-0": {"Mynamespace\\": "src/"}
        }
    }
{% endhighlight %}

The benefit of this configuration file is also that all your team know the dependencies for the project and can simply run composer to install them and be up and running with the project.

You can get all the details about composer from their [website](http://getcomposer.org/).And you can see all packages available from the composer repo [here](https://packagist.org/).
