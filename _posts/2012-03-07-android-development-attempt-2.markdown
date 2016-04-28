---
layout: post
title:  "Android Development Attempt #2"
date:   2012-03-07 23:19:00 +0000
categories: android series
---

OK, my android development kinda didn’t really get going so I’m having another go!

*New issues and new problems*

## Installing:

Great tutorial on how to install the current version of eclipse on ubuntu:

http://colinrrobinson.com/technology/install-eclipse-ubuntu/

While trying to install the eclipse plugin I got the following error:

    missing "org.eclipse.wst.sse.core 0.0.0"


This sounds horrid but is actually really easy to fix. Just follow these instructions: http://code.google.com/intl/es/eclipse/docs/faq.html#wstinstallerroInstalling:r

This time I started on the tab tutorial which you can find here:

http://developer.android.com/resources/tutorials/views/hello-tabwidget.html

This tutorial wasn’t quite so obvious when you aren’t used to the lingo.

Here are a few hints to save you a bit of time:

* The android manifest is in the src root.
* It is easier to add your activities using the wizard if you don’t really understand the XML just yet.
* In the end you will have 4 classes in you main package, the main application and a class for each of the 3 tabs.
* The tutorial only supplies images for one tab so you will need to change the code to put these images on all the tabs.
* The images live in you drawings folder.. not the assets folder as I expected.

I am going to look into this code in more detail to really find out what is going on here. It works but I don't know why yet.

Also, I’m gunna try out the ‘notepad tutorial’ I hope it will give me a better insight into the framework like it says…!
