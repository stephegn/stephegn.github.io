---
layout: post
title:  "The XMP illusion"
date:   2012-02-28 20:30:05 +0000
categories: flex php
---

How could something so simple take 3 times as long?
Our software allows users to download files from our server. Recently we added the ability to add data about the files into our system.
It would be really great if users could then get the data back out. “Easy!” My boss says, xmp.

So I ran off to the Flex forums and found an actionscript library for XMP. “Great!” I said, “Got my library here, should take me a week tops”.

Wrong

Unfortunately, Adobe decided developers using Flex would never need to write or edit XMP data, only read it and put it in a pretty object.
Anyway, undeterred I scoured the internet hunting for anyone with some answers. I found one! A library for writing XMP data in flex.
So I tried it with a JPG and it worked perfectly, I should still be able to do this in a week.

Wrong

The library was incomplete, I needed to write to AI files (PDFs) and this part of the library was empty. Back to the drawing board.

Then I had a brain wave – we can do it server side in PHP. This idea was much more fruitful. The original XMP library is written in
C++ and it turns out this is pretty easy to convert to PHP using extensions and shared objects. I found one that looked simple enough, but could I install it? No
Our server was out of date and a pain to find the PHP dev tools I needed to install it.

To cut a very long story short here I am 2 months later, with a library that works but the task of transferring to a new server.
The library I am using is this one. The guy who wrote it was very helpful in getting it to work for me and I am very thankful for that.
The library is very simple but exactly what I need to add XMP data into my files.

*Check out my blog on how to add XMP data to files with PHP here*

Useful Links

* [The XMP PHP Extension
](http://en.alexander-block.net/Business/eZ-Systems/XMP-extension-for-PHP)
* [The actionscript library
](http://wwwimages.adobe.com/www.adobe.com/content/dam/Adobe/en/devnet/xmp/pdfs/ActionScriptAccessToXMP.pdf)
* [Installing PHP extensions
](http://mattiasgeniar.be/2008/09/14/how-to-compile-and-install-php-extensions-from-source/)
* [Flex XMP Library (Incomplete)](http://code.google.com/p/as3-xmp-file/)
