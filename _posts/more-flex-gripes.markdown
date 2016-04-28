---
layout: post
title:  "More Flex Gripes"
date:   2011-07-25 14:07:00 +0000
categories: flex
---

Flex looks really nice but it does cause some problems.
One biggy I had to deal with last week was just simple styling. We are working with flex 4 which seems to me a sort of middle man between flex 3 and flex 4.5.
In flex 4 the beginnings of spark components came to be these seem to have been completed in flex 4.5 however in flex 4 there just aren’t all the components there
to make your life easy so we are still using some mx components. These mx components are horrid to style in any way.

We have settled with a UI that is reasonable but it is far from correct and I’m just not happy with it. Somehow something else is controlling the style of our tab
navigator component and I really don’t know what. We ended up using chrome color – a property which generically styles all the old components. This will have to do
but I’m still looking for a better way to fix it so I have more control.

Currently I am working on a back end to the system which is giving me a great opportunity to work out how to connect flex to an SQL database using PHP. Again not as
easy as it sounds, I have discovered that the network manager is stopping connections going through. I’m still getting errors but it’s a step forward.

On a happier note we release the new version of the software on Friday, very exciting and hopefully getting some interest from some large companies this week.

__UPDATE__: I have fixed the tab navigator for the time being by just trial and error really with the chromeColor property
