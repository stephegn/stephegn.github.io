---
layout: post
title:  "Halo vs Spark – Styling differences"
date:   2011-11-28 11:37:09 +0000
categories: flex
---

Styling has always been something that I have found difficult in flex.
Most of the reasons for this is that there are so many different ways to style a component through skins, css, the styling variables I just found it so confusing!

I have recently made a discovery which has helped me iron out some cracks in my knowledge which have bugged me no end.

I am now using Flex 4.5.1 which uses 2 different types of components Spark (using the s: namespace) and mx (using the mx: namespace). I would always advise using spark components
if possible because they are much easier to style.

Spark components can be skinned really easily by using the ‘skinClass’ property and if you are using Flash Builder it will come up with a pretty template for you to edit.
In that you can change all your colours, shapes etc using some basic components like rect and label.

Mx components can also be skinned but I have yet to work out how that works, it seems a little more difficult and there are no templates set up in Flash builder.

The other way to style components is through css. This is always where I go first to look for quick styling solutions. It enables you to set style properties on an application wide scale. Which is great.
However it can lead to hours of frustration trying to find the properties which you need to change what you want. I spent at least an hour styling the button on an Alert box
(which is an mx component with no spark equivalent that I have used in quite a few places).

The first thing which made my css life a little easier is the discovery of the styleName property, these crop up in quite a few places for different things and connect to
more css which styles that individual section. This is what I use for my button.

{% highlight actionscript %}
    mx|Alert

    {
      backgroundColor: #333333;
      buttonStyleName: “popUpButton”;
    }

    .popUpButton
    {
      color: #333333;
      borderColor: #ed9e06;
      chromeColor: #F6C133;
      accentColor: #ED9E06;
    }
{% endhighlight %}

Using the buttonStyleName property I could style the button as if it were a normal mx:button.

The second thing which had me pondering for ages is the chromeColor property which is a sorry attempt at quickly styling your whole application to a certain colour.
Sometimes very unpredictably. It literally just plasters that colour all over in whatever way it thinks is best. Great! But its very difficult sometimes to work out that that is what’s affecting it.

Finally, my recent discovery. There exist 2 types of CSS. Halo and spark ‘themes’. These two I believe are dependant on the version of flex you are working with
but makes hunting for CSS solutions very difficult as some halo CSS wont work with spark CSS (this is different from spark components, in fact it applies to both types of component).

Useful Links

[Adobe Class Listings](http://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/index.html) <— Details on all styling properties (and for each theme)

[Style Expolorer](http://examples.adobe.com/flex2/consulting/styleexplorer/Flex2StyleExplorer.html)<— Flex 2 Halo (but still usefull)
