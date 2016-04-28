---
layout: post
title:  "The solution to all my problems"
date:   2011-08-09 11:10:37 +0000
categories: flex
---

I have been struggling much more than needed when it comes to debugging the admin panel I am creating in flex, for some reason I found the network manager
stopped my app from receiving the data from my service – or at least parsing it.

I have finally found the solution.

The error I was receiving was an end of stream error – basically flex didn't understand the data it was receiving. My mistake was very simple – line breaks.

To make my code more readable I had split my XML up onto separate lines, unfortunately these were being sent to flex and so confusing it (but only when the network monitor was on)
all I had to do was remove my line breaks in the code and it worked! Letting me see my PHP errors and debug my scripts properly.
