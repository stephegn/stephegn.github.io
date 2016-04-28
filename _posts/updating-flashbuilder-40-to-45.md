---
layout: post
title:  "Updating FlashBuilder 4.0 to 4.5"
date:   2012-01-04 10:38:01 +0000
categories: flex
---
After importing my project to the new Flash Builder I thought I was safe, how wrong I was.

It turns out updating the clients to the new Flex SDK is not quite so simple.

However, I took to it in good spirit. Adobe will have though about this I told myself. There will be tutorials, it will be fine.

There is… [one](http://www.adobe.com/devnet/air/articles/air_update_framework.html#articlecontentAdobe_numberedheader_4).

I read it. I read it again. I read it one more time and when I’d finally thought I’d got my head around it.

Basically, one must first update the updater, send this update out and then update the SDK, send this update out and this must then point to a new updater for the next update which may not be updating just yet.

OK, so I’m making it sound a little bit worse than it is.

Follow the instructions closely – by the letter and you will be OK.
Unless you are like me that is, who decided to call their version Beta 1.0.

The problem with this is that 4.5 doesn’t support strings, only numbers in the form x.x.x

Therefore the update files should be as follows:

Original update file

    <update xmlns=”http://ns.adobe.com/air/framework/update/description/1.0”>
    <version>Beta 1.0.1</version>

Intermediate update file

    <update xmlns=”http://ns.adobe.com/air/framework/update/description/2.5”>
    <version>1.0.2</version>

Final update file

    <update xmlns=”http://ns.adobe.com/air/framework/update/description/2.5”>
    <versionNumber>1.0.3</versionNumber>
    <versionLabel>Beta 1.0.3</versionLabel>

Useful Links

[Update Tutorial](http://www.adobe.com/devnet/air/articles/air_update_framework.html#articlecontentAdobe_numberedheader_4)
