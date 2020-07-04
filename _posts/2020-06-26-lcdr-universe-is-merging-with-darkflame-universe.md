---
id: 2471
title: lcdr Universe is merging with Darkflame Universe
date: 2020-06-26T17:33:39+00:00
author: lcdr
layout: post
guid: https://lcdruniverse.org/?p=2471
permalink: /2020/06/lcdr-universe-is-merging-with-darkflame-universe/
categories:
  - Uncategorized
---
Hello everyone!

I&#8217;ve been talking with the folks at DLU in the last few days.  
I&#8217;ve agreed to join them, starting immediately.

This is probably coming as a surprise, and just a while ago I wouldn&#8217;t have expected this to happen either. This goes especially as both DLU and I have said in the past that a collaboration is problematic and wouldn&#8217;t help server development much.

So, I&#8217;ll try to explain what led to this.

The current split of dev projects into DLU and lcdrU is mostly due to historical reasons. LU server emulator development got its start back in 2013/2014, with what would become the LUNI project. Back then, we didn&#8217;t know much about LU&#8217;s networking at all and were just starting to get past the login step. But just as we managed to get the first worlds loading, the project was beset by drama regarding hosting, future direction, and management. Both Darwin and a few others, as well as I and humanoid, wanted to avoid the drama, and left the LUNI forum to work on our own projects, which would eventually become DLU and lcdrU.

Having decided to withdraw from the public to avoid drama, the projects worked in relative isolation from each other, and consequently made different decisions regarding management and coding. Notably, lcdrU chose Python as a server language, while DLU chose C++.

The projects worked quietly for a few years, until 2017, when both started a public presence, and began closed alpha testing. Some people in the community have since been wondering why there are two projects, and if server emulator delevopment couldn&#8217;t be made faster by combining them into one. However, at this point, the projects had diverged far enough that a collaboration wasn&#8217;t easily done: There were differences in direction, and most importantly, merging would have meant that one project would have to give up on its promising codebase that they had spent years on developing and were planning to turn into a fully functional server. These large obstacles prohibited a fusion of server projects.

However, since then, DLU and lcdrU have been in close contact, and together we&#8217;ve been able to achieve some shared goals, such as restoring an old version of LU&#8217;s level editor, and we&#8217;ve also been able to resolve some of the differences in direction.

Unrelated to this, over the years I&#8217;ve come to the conclusion that lcdrU&#8217;s current server has some significant issues in its core architecture, and that Python has started to be unable to provide as a programming language as the codebase&#8217;s grown in size. Because of this, I&#8217;ve decided to instead rewrite the server in Rust, and this is what I&#8217;ve been working on for the past months.

Incidentally, this means that the technical barrier to collaboration has been eliminated, as there&#8217;s no longer a concern of having to abandon an existing codebase, and as Rust and C++ are much closer related. Some of the devs on DLU&#8217;s team have also expressed an interest in Rust, and I&#8217;m interested to see if we can join forces on this.

With DLU recently having committed to making their server open source after release, the barriers obstructing a collaboration have been lifted, and the timing happens to be quite ideal as well. While I really enjoyed being able to lead lcdr Universe both in code and as a project, my fundamental goal is to make LEGO Universe fully playable again, and this takes a lot of time to accomplish. Real life has taken up more of my time than anticipated, and I believe that by joining DLU I will be able to help bring about a faster game restoration by being able to focus on coding and collaborating with other devs.

I want to thank all of you for following this project over the years, and especially the alpha testers, who have helped find and fix a lot of bugs over the testing period.





## The future

With all that said, you&#8217;re probably wondering what this means for my development efforts and the project as a whole.

I&#8217;ve joined DLU in an &#8220;R&D&#8221; capacity, which means that I won&#8217;t be working on their server directly for now, but rather continuing my experiments with Rust and tools related to server development. Over time I hope to be able to integrate my libraries with DLU&#8217;s server and work on the codebase more closely. In the long term future I may even be able to contribute to future content development and add new server mechanics. I&#8217;m very much looking forward to this, as it allows me to continue my Rust work without being constrained by the size of the project.

### What will happen with lcdr Universe?

Most of all, I want to make sure that people who have already gotten involved with the project won&#8217;t be abandoned. This means that I&#8217;ll be keeping the testing server running indefinitely, so that testers will still be able to play. As for later on, DLU has offered to adopt them into their testing once they start closed beta, and I think that&#8217;s a great idea.

Similarly, the lcdrU discord will stay open for the foreseeable future, so that people may still be able to chat with others in the community. In the future, I expect the LU Community Hub discord to fill much of its role, but I&#8217;d like the shift to happen gradually, and not by closing the doors on anyone. 

As for the website, much of it is no longer necessary, and DLU&#8217;s website will be taking over its roles. I&#8217;ll be simplifying the current website to be just this blog, so you&#8217;ll still be able to find older posts as well as any future updates on my work here. I&#8217;ll also keep posting monthly updates about my work on Twitter.  




As a final word, think of this less as an end and rather as a new chapter. Thanks to the perfect timing, I will be able to continue my current work, and contribute to DLU with what I&#8217;ve learned in lcdrU. Together I believe we will be able to create a server that is better than ever.



See you all in-game!  
– lcdr