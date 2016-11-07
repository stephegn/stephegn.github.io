---
layout: post
title:  "Hack Manchester 2016"
date:   2016-11-07 22:23:00 +0000
categories: thoughts
---

## Year #4

This is the 4th year I have competed in HackManchester and as always I had a blast. We decided not to take on a challenge this year and just challenge ourselves to build a game (something we have never really done before). We built M60 Mayhem and were short listed for best in show, something we have never really come close to before and were really pleased with.
Since this year was a bit of a change of tact and it was so successful, I thought I'd go through some of the differences over the last 4 years and some interesting things we noticed.

<blockquote class="twitter-tweet" data-partner="tweetdeck"><p lang="und" dir="ltr"><a href="https://twitter.com/hashtag/4years?src=hash">#4years</a> <a href="https://twitter.com/stephegn">@stephegn</a> <a href="https://twitter.com/hashtag/hackmcr?src=hash">#hackmcr</a> <a href="https://twitter.com/HackManchester">@HackManchester</a> <a href="https://t.co/5L7nVX6BDe">pic.twitter.com/5L7nVX6BDe</a></p>&mdash; Si Levy (@silevy) <a href="https://twitter.com/silevy/status/792382056479227904">October 29, 2016</a></blockquote>
<script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

## Organisation and planning

How we organised ourselves has changed a lot over the years, this year was infact the least planned, we only had a vauge idea of what we wanted to create - a racing game, with multiplayer, probably over websockets. Organisation on the day however was probably the best yet, we had regular catch ups to add postits and switched what we were working on frequently. I think the all Javascript codebase (server and clients) really helped with this, allowing us to all work on everything easily and not have to context switch too much. A real kanban board really helped too, even if we did have to run back after forgetting the postits, it really was worth it.

One important goal we have learn over the years is to get something working ASAP. This is so important, and really helped us gain momentum. Coupled with continuous deployment (which we set up at the same time) we could charge ahead with everything else.

![Kanban](http://www.playbyplay.io/wp-content/uploads/2016/10/IMG_6536-1024x682.jpg)

## The codebase

I've already mentioned the all Javascript codebase, in past projects have usually used a mix of 2, even 3 languages. Usually only one or two people would work on a single codebase. The codebases have also been huge, we are talking thousands of lines of code across multiple repos. Some of that code is generated but you still have to get you head into it (while half asleep). The M60 Mayhem codebase including the server, the main client and the mobile controller client hits about 1000 lines. This is a huge difference and I think part of the reason this worked so well. Features were quick and easy to add and this keeps you motivated, it also fits in your head, while sleep deprived.

## Choosing what is fun

Another big discision we made early on was to keep it simple. We ignored the features (which were calling to us) that didnt really add much value. One the big ones for us was lobbies. It's a multiplayer game, of course it needs lobbies to be a reality but really all this would have done is added a huge amount of complexity for no real benefit. Working on a proof of concept which works in your set of conditions is what it's all about, you only have 24(5) hours! Maybe one day we will go back and add lobbies so multiple sessions can happen at once, maybe.

![Planning lobbies](http://www.playbyplay.io/wp-content/uploads/2016/10/DSC_1828-1024x683.jpg)

By not having a fully fleshed out idea we were able to come up with great ideas on the fly and just add them in. We managed to get a working game up in very little time so from then on it was all just adding in the fun bits, power ups, sound effects, even vibrations! The only problem we did have with this was that when the judges came round initially we couldnt really give them an idea of what everything was going to turn into.

## M60 Mayhem
[https://github.com/QasAshraf/fluffy-umbrella](https://github.com/QasAshraf/fluffy-umbrella)
<iframe width="560" height="315" src="https://www.youtube.com/embed/A5aAISyJCtI" frameborder="0" allowfullscreen></iframe>
