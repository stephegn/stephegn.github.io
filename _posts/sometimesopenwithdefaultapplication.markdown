---
layout: post
title:  "SOMETIMESopenWithDefaultApplication()"
date:   2011-09-01 16:01:00 +0000
categories: flex
---

openWithDefaultApplication() is a wonderful function available in flex for AIR.

It is pretty much the basis of our application which allows you to download files from our server.

Also, flex is great for being multi-platform so we can write one application for Linux, Mac, Windows and maybe mobile in the future.

However, the openWithDefaultApplication() function is far from perfect here are some of its flaws I have found:

1. A try catch around the function is advised but will not catch errors in windows
2. I found Linux would always error when opening the file, the fix is:

    sudo apt-get install gvfs-bin

3. I had massive issues when trying to use Adobe Reader as my default program for.ai files in Windows. I do not know the fix/reason for this.

*Edit: Some wonderful person suggested changing the file extension to .pdf. This works and opens nicely in Adobe Reader!
*

I have spent a whole day trying to sort the application out on Linux and am still not sure what will happen with no default application for the file, I will test this on Windows and Linux and report back.
