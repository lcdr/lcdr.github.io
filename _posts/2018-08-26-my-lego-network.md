---
id: 2079
title: My LEGO Network
date: 2018-08-26T11:43:21+00:00
author: lcdr
layout: post
permalink: /2018/08/my-lego-network/
categories:
	- MLN
---
**Update:** The restoration project now has a discord, which you can join to stay updated about progress and talk about MLN in general: <https://discordapp.com/invite/VGYgExX>

**Original Post:**

Hey everyone!

As I’ve mentioned on twitter, I’ve been working on a side project for a little bit, which like my main project is a server for an abandoned LEGO game. I’m now ready to announce what I’ve been working on: [A server for My LEGO Network](https://github.com/MellonNet/mln-backend-emulator/).

My LEGO Network was a mix between a social network and a game, made in Flash and accessed via web browser. It was around from 2008 to 2015, when it was shut down, like many other LEGO games before it. Some of you may remember playing it back when it was online.

I played a bit of MLN back when it was online, and although the game seemed quite grind-y, I liked the general concept of interacting with both players and networkers and expressing yourself on your public page. The networkers were interesting and varied, and they were connected to other networkers themselves, which made the concept of a LEGO social network more immersive as a game element.

A few months ago, Knightoffaith, a fellow LU server developer, mentioned he was looking into recreating a server for MLN. Having played the game years back, I was kind of curious how it worked behind the scenes, so I started investigating. Knightoffaith had already gathered (almost) all client and resource files, which made it possible to assemble the client side without too many problems. (Thanks to Knightoffaith for this, along with organizing and leading the project. Without him the restoration effort probably wouldn’t exist, or at least wouldn’t be very far along.) Using these files as a starting point I was able to research the network communication and put together a server.

I’ve managed to implement most of the core features of MLN by now. Here’s a list of what’s working so far:

#### Features

![Private view of lighthouse64, one of the MLN restoration project’s members.](/assets/2018/08/private-view.png)

The Private View, including setting your avatar, setting your profile statements (“about me” bio) and managing your friends.

![Mailbox tab](/assets/2018/08/mailbox.png)

Reading and sending mail, including support for attachments and the “easy reply” feature (suggested replies).

![Inventory tab](/assets/2018/08/inventory.png)

The inventory and blueprints are also working.

![Collections tab](/assets/2018/08/collections.png)

There’s also support for MLN’s integration with galleries, Factory (LEGO model upload), and LU’s creation lab (works similar to a gallery).

![Page Builder tab](/assets/2018/08/page-builder.png)

Modules can be placed on your page in the page builder. There are several different ways of module customization or configuration, of which all are supported.

![The public page of lighthouse64, one of the restoration project’s members.](/assets/2018/08/Screenshot_2018-08-26-Screenshot2.png)

Public pages display your badges and modules. You can also send friend requests to page owners.

![Solar Collecting Module](/assets/2018/08/vote.jpg)
![LEGO Tree Module](/assets/2018/08/tree.jpg)
![Hive Module](/assets/2018/08/hive.jpg)

You can vote on modules, set up modules with items, and harvest items that the modules have grown.

![Delivery Arcade Module](/assets/2018/08/arcade.jpg)

Arcade modules are playable as well.

Unfortunately, while a lot of resources and clientside database contents had been archived, there is one key piece that is missing: Data about networkers. Since networkers were a server-side feature, they don’t appear in the client database that was archived, and since MLN used flash, their pages weren’t archived in automated web crawlers. This means that we don’t have data about networkers’ names, their pages, their networker friends, the requirements to be their friend, and their mail responses.

Of course, the ideal solution would be that through some sort of miracle someone stumbles upon the networker database somewhere. However, even if this doesn’t happen, it should still be possible to recreate the database – but it will require some manual work. The MLN wiki has a lot of info regarding networkers archived, including page and mail trades. Mail responses can also be guessed from the mail contents (which, due to the way MLN’s message system works, are archived in the client database), as networkers usually mention what they’re sending and why they’re sending it. However, this leaves the page layout and the networker description & quote on their page missing. The only way to recover them would be if someone happened to record the pages or take a screenshot, back when they were online. Hopefully we’ll be able to piece these things together at some point.

By now you’ve probably got some questions about this project and my involvement with it. I’ll try to answer some of them below.

#### Why are you working on another game server? Shouldn’t you stick with LU and focus on development there?

It’s true that working on one server takes time that could be used for the other. I knew this when I starting getting involved with MLN, and I considered both continuing looking into a server for MLN and sticking with the LU server. In the end, I found there were a few reasons that made exploring an MLN server worthwhile:

* ###### Exploring different database options:

The LU server has had some bugs caused by the database system it uses, which unfortunately are very hard to track down and fix. I’ve been curious for a while now how other database systems resolve these kinds of issues, and whether it would make sense to switch the current system. With the MLN server I was able to use the Django framework and its database ORM, which have been widely used and tested. They also work a bit differently than the LU server’s database system, which prevents some kinds of bugs I had previously encountered.

* ###### Exploring web interfaces & Django:

I’ve got a bunch of ideas for administration and overview interfaces for the LU server that would ideally be implemented as a web interface. However, I didn’t have a lot of experience with modern data-driven web development, and working on a server for MLN seemed like a great way to get some in-depth experience that would help with the LU server later on.

* ###### Exploring open-sourcing a working game server:

I’ve always wanted to make my LU server open source at some point, to make more servers available to players and to decentralize the server landscape. However I haven’t been able to do so so far, for multiple reasons, including the LU projects situation and to avoid LEGO taking legal means against server projects while the server still requires a lot of development.
The MLN server project offered an opportunity for an open, central, community project working to recreate a game, instead of the current LU situation with multiple closed projects. The MLN server makes it possible to gauge the impact of an open source project on the community, which will hopefully come in useful when the time comes to decide whether to make the LU server open source as well.

* ###### Exploring working in a larger, community-based effort:

For similar reasons as with not being able to open source the LU server, I haven’t been able to include more people in my LU server project, the situation is quite complicated. With MLN, it’s possible to “start things off the right way”, with a single, open project that makes it easy to collaborate to bring the game back.
MLN’s restoration is also inherently more community-based than LU’s: Writing a server for LU mostly requires research and development of LU’s game mechanics, which are tasks that can be done by a relatively small team of developers. In MLN’s case, research and development takes a much smaller part of the restoration effort, and the remaining part of piecing together networker info is much more suited to a crowdsourced approach. I’m looking forward to seeing the restoration effort working with MLN fans to recover networker info.

#### Why haven’t you talked about this earlier?

Investigating the possibility of an MLN server and developing a prototype were some ventures that were quite experimental, and I first wanted to make sure that a working server for MLN was actually feasible before announcing my involvement in this project. I’m also not a big fan of releasing unfinished things, and wanted to make sure almost all core features were supported before a release.

#### Will you change your focus from developing the LU server to the MLN server from now on?

Actually, no. Part of why I chose to write a server for MLN is that MLN is far less complex than LU. By now most features are implemented, and there’s a strong foundation for other developers to pick up on my work and implement additional features. From now on, my work on MLN will consist mostly of occasional feature updates and bug fixes. Most of my time will be spent on the LU server, like before.

#### Can I actually play MLN again?

Sort of. The core system is implemented, however, without networkers, there is no story progression and no rising in the ranks, and you’re limited to the social part of MLN, customizing your page and interacting with your friends.

#### Can I try it out?

There’s no public hosted MLN server, and I don’t plan on hosting one myself, as I’d like to focus on development and less on server operation. However, the server is open source, so if you’re interested, you can host your own instance to play on. The source is available [here](https://bitbucket.org/lcdr/mlnserver/), and contains instructions on how to install and set up the server. However, to avoid any copyright problems, I can’t link content files.

#### What’s next for the MLN project?

There are a few details I haven’t gotten around to implementing yet, like statistics and modules sending out items to random friends. These should be implemented in the future. Other than that, the main challenge is to assemble comprehensive networker data and build the necessary server infrastructure to support networkers.

In the long term, the goal is to completely rewrite the client side to move from the deprecated Flash to a proper HTML-javascript-based system. It’s likely to take quite a while before the project gets to this state though, as the priority is to complete work on networkers first.

#### What’s next for you?

I will be returning to focus on developing the LU server, making use of what I’ve learned from the MLN server where possible. However, unspectacular work like bug fixing and test writing will still be a sizeable part of my work. These things are however necessary for effective development of a large project like this, and will improve the server quality and prevent regressions in the future.

I can’t yet say when I’ll be able to return to implementing features, but I’ll let you know when the time comes. Once I’ve done enough work on features I’ll also go back to recording videos for the youtube channel. Unfortunately bugfixes don’t make for very interesting videos, which is why I haven’t uploaded videos recently. Once I’m back to developing features videos will be possible again.

I also can’t yet say when the next alpha will happen. I know you can’t wait to play LU again, and I want to start the next alpha soon myself. However it’s very important to me to make sure the server is ready to handle more players before inviting more players to the server, and to fix as many bugs as possible so you can have a fun experience and play like in the original LU.

This is why I’ve put so much focus on bugfixing and testing in the last months. I don’t want to rush the next alpha and invite people while the server still has a few bugs around. Operating the server is only going to get more complicated with more players, which is why I want to fix bugs as early in development as possible. I’m sorry development is taking so long, but I hope you can understand why.

#### Can I help with restoring MLN?

Yes, this is fortunately much easier than helping restoring LU. The server is open source, so if you have experience with Python and Django, you can help with software development. MLN doesn’t really have special formats you’d need to learn, so getting started is relatively simple. However, keep in mind that this requires programming experience, so this way of contributing might not be for everyone.

However, you can still contribute, even if you can’t program. As mentioned, we don’t have a lot of data about networkers right now, and if you played MLN in the original days and remember some details that aren’t on the MLN wiki, or even better, have screenshots or videos of networkers’ pages, it’d help a lot if you could send us info or update the [MLN wiki](http://mylegonetwork.wikia.com/wiki/Welcome_to_My_LEGO_Network_Wiki!).

However the restoration has only just started, and there isn’t much organization yet regarding the collection of networker info, so please keep that in mind if you are interested in helping out.

In conclusion, I’d like to say that working on the MLN server has been a lot of fun, and I’ve learned a lot working on it. The server gives the MLN restoration project a solid base to work with, and I’m confident they will be able to restore MLN to its original state in time. The work on the server has both given me new ideas for the LU server as well as means to achieve old ones, and for example something like a web interface for the server for both admins and players doesn’t seem too far-fetched any more.

See you all in-game!

– lcdr