---
id: 2079
title: My LEGO Network
date: 2018-08-26T11:43:21+00:00
author: lcdr
layout: post
guid: https://lcdruniverse.org/?p=2079
permalink: /2018/08/my-lego-network/
categories:
  - MLN
---
**Update:** The restoration project now has a discord, which you can join to stay updated about progress and talk about MLN in general: <https://discordapp.com/invite/VGYgExX>

**Original Post:**

Hey everyone!

As I&#8217;ve mentioned on twitter, I&#8217;ve been working on a side project for a little bit, which like my main project is a server for an abandoned LEGO game. I&#8217;m now ready to announce what I&#8217;ve been working on: <a href="https://bitbucket.org/lcdr/mlnserver/" target="_blank" rel="noopener noreferrer">A server for My LEGO Network</a>.

My LEGO Network was a mix between a social network and a game, made in Flash and accessed via web browser. It was around from 2008 to 2015, when it was shut down, like many other LEGO games before it. Some of you may remember playing it back when it was online.

I played a bit of MLN back when it was online, and although the game seemed quite grind-y, I liked the general concept of interacting with both players and networkers and expressing yourself on your public page. The networkers were interesting and varied, and they were connected to other networkers themselves, which made the concept of a LEGO social network more immersive as a game element.

A few months ago, Knightoffaith, a fellow LU server developer, mentioned he was looking into recreating a server for MLN. Having played the game years back, I was kind of curious how it worked behind the scenes, so I started investigating. Knightoffaith had already gathered (almost) all client and resource files, which made it possible to assemble the client side without too many problems. (Thanks to Knightoffaith for this, along with organizing and leading the project. Without him the restoration effort probably wouldn&#8217;t exist, or at least wouldn&#8217;t be very far along.) Using these files as a starting point I was able to research the network communication and put together a server.

I&#8217;ve managed to implement most of the core features of MLN by now. Here&#8217;s a list of what&#8217;s working so far:

#### Features<figure id="attachment_2099" aria-describedby="caption-attachment-2099" style="width: 956px" class="wp-caption alignnone">

<img class="size-full wp-image-2099" src="https://lcdruniverse.org/wp-content/uploads/2018/08/private-view.png" alt="" width="956" height="966" srcset="https://lcdruniverse.org/wp-content/uploads/2018/08/private-view.png 956w, https://lcdruniverse.org/wp-content/uploads/2018/08/private-view-297x300.png 297w, https://lcdruniverse.org/wp-content/uploads/2018/08/private-view-768x776.png 768w, https://lcdruniverse.org/wp-content/uploads/2018/08/private-view-100x100.png 100w" sizes="(max-width: 767px) 89vw, (max-width: 1000px) 54vw, (max-width: 1071px) 543px, 580px" /> <figcaption id="caption-attachment-2099" class="wp-caption-text">Private view of lighthouse64, one of the MLN restoration project&#8217;s members.</figcaption></figure> 

The Private View, including setting your avatar, setting your profile statements (&#8220;about me&#8221; bio) and managing your friends.<figure id="attachment_2098" aria-describedby="caption-attachment-2098" style="width: 1852px" class="wp-caption alignnone">

<img class="size-full wp-image-2098" src="https://lcdruniverse.org/wp-content/uploads/2018/08/mailbox.png" alt="" width="1852" height="1147" srcset="https://lcdruniverse.org/wp-content/uploads/2018/08/mailbox.png 1852w, https://lcdruniverse.org/wp-content/uploads/2018/08/mailbox-300x186.png 300w, https://lcdruniverse.org/wp-content/uploads/2018/08/mailbox-768x476.png 768w, https://lcdruniverse.org/wp-content/uploads/2018/08/mailbox-1024x634.png 1024w" sizes="(max-width: 767px) 89vw, (max-width: 1000px) 54vw, (max-width: 1071px) 543px, 580px" /> <figcaption id="caption-attachment-2098" class="wp-caption-text">Mailbox tab</figcaption></figure> 

Reading and sending mail, including support for attachments and the &#8220;easy reply&#8221; feature (suggested replies).<figure id="attachment_2097" aria-describedby="caption-attachment-2097" style="width: 1858px" class="wp-caption alignnone">

<img class="size-full wp-image-2097" src="https://lcdruniverse.org/wp-content/uploads/2018/08/inventory.png" alt="" width="1858" height="1500" srcset="https://lcdruniverse.org/wp-content/uploads/2018/08/inventory.png 1858w, https://lcdruniverse.org/wp-content/uploads/2018/08/inventory-300x242.png 300w, https://lcdruniverse.org/wp-content/uploads/2018/08/inventory-768x620.png 768w, https://lcdruniverse.org/wp-content/uploads/2018/08/inventory-1024x827.png 1024w" sizes="(max-width: 767px) 89vw, (max-width: 1000px) 54vw, (max-width: 1071px) 543px, 580px" /> <figcaption id="caption-attachment-2097" class="wp-caption-text">Inventory tab</figcaption></figure> 

The inventory and blueprints are also working.<figure id="attachment_2101" aria-describedby="caption-attachment-2101" style="width: 1856px" class="wp-caption alignnone">

<img class="size-full wp-image-2101" src="https://lcdruniverse.org/wp-content/uploads/2018/08/collections.png" alt="" width="1856" height="1497" srcset="https://lcdruniverse.org/wp-content/uploads/2018/08/collections.png 1856w, https://lcdruniverse.org/wp-content/uploads/2018/08/collections-300x242.png 300w, https://lcdruniverse.org/wp-content/uploads/2018/08/collections-768x619.png 768w, https://lcdruniverse.org/wp-content/uploads/2018/08/collections-1024x826.png 1024w" sizes="(max-width: 767px) 89vw, (max-width: 1000px) 54vw, (max-width: 1071px) 543px, 580px" /> <figcaption id="caption-attachment-2101" class="wp-caption-text">Collections tab</figcaption></figure> 

There&#8217;s also support for MLN&#8217;s integration with galleries, Factory (LEGO model upload), and LU&#8217;s creation lab (works similar to a gallery).<figure id="attachment_2096" aria-describedby="caption-attachment-2096" style="width: 2055px" class="wp-caption alignnone">

<img class="wp-image-2096 size-full" src="https://lcdruniverse.org/wp-content/uploads/2018/08/page-builder.png" alt="" width="2055" height="1453" srcset="https://lcdruniverse.org/wp-content/uploads/2018/08/page-builder.png 2055w, https://lcdruniverse.org/wp-content/uploads/2018/08/page-builder-300x212.png 300w, https://lcdruniverse.org/wp-content/uploads/2018/08/page-builder-768x543.png 768w, https://lcdruniverse.org/wp-content/uploads/2018/08/page-builder-1024x724.png 1024w" sizes="(max-width: 767px) 89vw, (max-width: 1000px) 54vw, (max-width: 1071px) 543px, 580px" /> <figcaption id="caption-attachment-2096" class="wp-caption-text">Page Builder tab</figcaption></figure> 

Modules can be placed on your page in the page builder. There are several different ways of module customization or configuration, of which all are supported.<figure id="attachment_2087" aria-describedby="caption-attachment-2087" style="width: 950px" class="wp-caption alignnone">

<img class="wp-image-2087 size-full" src="https://lcdruniverse.org/wp-content/uploads/2018/08/Screenshot_2018-08-26-Screenshot2.png" alt="" width="950" height="1039" srcset="https://lcdruniverse.org/wp-content/uploads/2018/08/Screenshot_2018-08-26-Screenshot2.png 950w, https://lcdruniverse.org/wp-content/uploads/2018/08/Screenshot_2018-08-26-Screenshot2-274x300.png 274w, https://lcdruniverse.org/wp-content/uploads/2018/08/Screenshot_2018-08-26-Screenshot2-768x840.png 768w, https://lcdruniverse.org/wp-content/uploads/2018/08/Screenshot_2018-08-26-Screenshot2-936x1024.png 936w" sizes="(max-width: 767px) 89vw, (max-width: 1000px) 54vw, (max-width: 1071px) 543px, 580px" /> <figcaption id="caption-attachment-2087" class="wp-caption-text">The public page of lighthouse64, one of the restoration project&#8217;s members.</figcaption></figure> 

Public pages display your badges and modules. You can also send friend requests to page owners.

<div id='gallery-1' class='gallery galleryid-2079 gallery-columns-3 gallery-size-full'>
  <figure class='gallery-item'> 
  
  <div class='gallery-icon landscape'>
    <img width="579" height="517" src="https://lcdruniverse.org/wp-content/uploads/2018/08/vote.jpg" class="attachment-full size-full" alt="" aria-describedby="gallery-1-2091" srcset="https://lcdruniverse.org/wp-content/uploads/2018/08/vote.jpg 579w, https://lcdruniverse.org/wp-content/uploads/2018/08/vote-300x268.jpg 300w" sizes="100vw" />
  </div><figcaption class='wp-caption-text gallery-caption' id='gallery-1-2091'> Solar Collecting Module </figcaption></figure><figure class='gallery-item'> 
  
  <div class='gallery-icon landscape'>
    <img width="581" height="516" src="https://lcdruniverse.org/wp-content/uploads/2018/08/tree.jpg" class="attachment-full size-full" alt="" aria-describedby="gallery-1-2094" srcset="https://lcdruniverse.org/wp-content/uploads/2018/08/tree.jpg 581w, https://lcdruniverse.org/wp-content/uploads/2018/08/tree-300x266.jpg 300w" sizes="100vw" />
  </div><figcaption class='wp-caption-text gallery-caption' id='gallery-1-2094'> LEGO Tree Module </figcaption></figure><figure class='gallery-item'> 
  
  <div class='gallery-icon landscape'>
    <img width="581" height="516" src="https://lcdruniverse.org/wp-content/uploads/2018/08/hive.jpg" class="attachment-full size-full" alt="" aria-describedby="gallery-1-2095" srcset="https://lcdruniverse.org/wp-content/uploads/2018/08/hive.jpg 581w, https://lcdruniverse.org/wp-content/uploads/2018/08/hive-300x266.jpg 300w" sizes="100vw" />
  </div><figcaption class='wp-caption-text gallery-caption' id='gallery-1-2095'> Hive Module </figcaption></figure>
</div>

You can vote on modules, set up modules with items, and harvest items that the modules have grown.<figure id="attachment_2089" aria-describedby="caption-attachment-2089" style="width: 230px" class="wp-caption alignnone">

<img class="wp-image-2089 " src="https://lcdruniverse.org/wp-content/uploads/2018/08/arcade.jpg" alt="" width="230" height="200" srcset="https://lcdruniverse.org/wp-content/uploads/2018/08/arcade.jpg 578w, https://lcdruniverse.org/wp-content/uploads/2018/08/arcade-300x261.jpg 300w" sizes="(max-width: 230px) 100vw, 230px" /> <figcaption id="caption-attachment-2089" class="wp-caption-text">Delivery Arcade Module</figcaption></figure> 

Arcade modules are playable as well.

Unfortunately, while a lot of resources and clientside database contents had been archived, there is one key piece that is missing: Data about networkers. Since networkers were a server-side feature, they don&#8217;t appear in the client database that was archived, and since MLN used flash, their pages weren&#8217;t archived in automated web crawlers. This means that we don&#8217;t have data about networkers&#8217; names, their pages, their networker friends, the requirements to be their friend, and their mail responses.

Of course, the ideal solution would be that through some sort of miracle someone stumbles upon the networker database somewhere. However, even if this doesn&#8217;t happen, it should still be possible to recreate the database &#8211; but it will require some manual work. The MLN wiki has a lot of info regarding networkers archived, including page and mail trades. Mail responses can also be guessed from the mail contents (which, due to the way MLN&#8217;s message system works, are archived in the client database), as networkers usually mention what they&#8217;re sending and why they&#8217;re sending it. However, this leaves the page layout and the networker description & quote on their page missing. The only way to recover them would be if someone happened to record the pages or take a screenshot, back when they were online. Hopefully we&#8217;ll be able to piece these things together at some point.

By now you&#8217;ve probably got some questions about this project and my involvement with it. I&#8217;ll try to answer some of them below.

#### Why are you working on another game server? Shouldn&#8217;t you stick with LU and focus on development there?

It&#8217;s true that working on one server takes time that could be used for the other. I knew this when I starting getting involved with MLN, and I considered both continuing looking into a server for MLN and sticking with the LU server. In the end, I found there were a few reasons that made exploring an MLN server worthwhile:

  * ###### Exploring different database options:
    
    The LU server has had some bugs caused by the database system it uses, which unfortunately are very hard to track down and fix. I&#8217;ve been curious for a while now how other database systems resolve these kinds of issues, and whether it would make sense to switch the current system. With the MLN server I was able to use the Django framework and its database ORM, which have been widely used and tested. They also work a bit differently than the LU server&#8217;s database system, which prevents some kinds of bugs I had previously encountered.</li> 
    
      * ###### Exploring web interfaces & Django:
        
        I&#8217;ve got a bunch of ideas for administration and overview interfaces for the LU server that would ideally be implemented as a web interface. However, I didn&#8217;t have a lot of experience with modern data-driven web development, and working on a server for MLN seemed like a great way to get some in-depth experience that would help with the LU server later on.</li> 
        
          * ###### Exploring open-sourcing a working game server:
            
            I&#8217;ve always wanted to make my LU server open source at some point, to make more servers available to players and to decentralize the server landscape. However I haven&#8217;t been able to do so so far, for multiple reasons, including the LU projects situation and to avoid LEGO taking legal means against server projects while the server still requires a lot of development.  
            The MLN server project offered an opportunity for an open, central, community project working to recreate a game, instead of the current LU situation with multiple closed projects. The MLN server makes it possible to gauge the impact of an open source project on the community, which will hopefully come in useful when the time comes to decide whether to make the LU server open source as well.</li> 
            
              * ###### Exploring working in a larger, community-based effort:
                
                For similar reasons as with not being able to open source the LU server, I haven&#8217;t been able to include more people in my LU server project, the situation is quite complicated. With MLN, it&#8217;s possible to &#8220;start things off the right way&#8221;, with a single, open project that makes it easy to collaborate to bring the game back.  
                MLN&#8217;s restoration is also inherently more community-based than LU&#8217;s: Writing a server for LU mostly requires research and development of LU&#8217;s game mechanics, which are tasks that can be done by a relatively small team of developers. In MLN&#8217;s case, research and development takes a much smaller part of the restoration effort, and the remaining part of piecing together networker info is much more suited to a crowdsourced approach. I&#8217;m looking forward to seeing the restoration effort working with MLN fans to recover networker info.</li> </ul> 
                
                #### Why haven&#8217;t you talked about this earlier?
                
                Investigating the possibility of an MLN server and developing a prototype were some ventures that were quite experimental, and I first wanted to make sure that a working server for MLN was actually feasible before announcing my involvement in this project. I&#8217;m also not a big fan of releasing unfinished things, and wanted to make sure almost all core features were supported before a release.
                
                #### Will you change your focus from developing the LU server to the MLN server from now on?
                
                Actually, no. Part of why I chose to write a server for MLN is that MLN is far less complex than LU. By now most features are implemented, and there&#8217;s a strong foundation for other developers to pick up on my work and implement additional features. From now on, my work on MLN will consist mostly of occasional feature updates and bug fixes. Most of my time will be spent on the LU server, like before.
                
                #### Can I actually play MLN again?
                
                Sort of. The core system is implemented, however, without networkers, there is no story progression and no rising in the ranks, and you&#8217;re limited to the social part of MLN, customizing your page and interacting with your friends.
                
                #### Can I try it out?
                
                There&#8217;s no public hosted MLN server, and I don&#8217;t plan on hosting one myself, as I&#8217;d like to focus on development and less on server operation. However, the server is open source, so if you&#8217;re interested, you can host your own instance to play on. The source is available <a href="https://bitbucket.org/lcdr/mlnserver/" target="_blank" rel="noopener noreferrer">here</a>, and contains instructions on how to install and set up the server. However, to avoid any copyright problems, I can&#8217;t link content files.
                
                #### What&#8217;s next for the MLN project?
                
                There are a few details I haven&#8217;t gotten around to implementing yet, like statistics and modules sending out items to random friends. These should be implemented in the future. Other than that, the main challenge is to assemble comprehensive networker data and build the necessary server infrastructure to support networkers.
                
                In the long term, the goal is to completely rewrite the client side to move from the deprecated Flash to a proper HTML-javascript-based system. It&#8217;s likely to take quite a while before the project gets to this state though, as the priority is to complete work on networkers first.
                
                #### What&#8217;s next for you?
                
                I will be returning to focus on developing the LU server, making use of what I&#8217;ve learned from the MLN server where possible. However, unspectacular work like bug fixing and test writing will still be a sizeable part of my work. These things are however necessary for effective development of a large project like this, and will improve the server quality and prevent regressions in the future.
                
                I can&#8217;t yet say when I&#8217;ll be able to return to implementing features, but I&#8217;ll let you know when the time comes. Once I&#8217;ve done enough work on features I&#8217;ll also go back to recording videos for the youtube channel. Unfortunately bugfixes don&#8217;t make for very interesting videos, which is why I haven&#8217;t uploaded videos recently. Once I&#8217;m back to developing features videos will be possible again.
                
                I also can&#8217;t yet say when the next alpha will happen. I know you can&#8217;t wait to play LU again, and I want to start the next alpha soon myself. However it&#8217;s very important to me to make sure the server is ready to handle more players before inviting more players to the server, and to fix as many bugs as possible so you can have a fun experience and play like in the original LU.
                
                This is why I&#8217;ve put so much focus on bugfixing and testing in the last months. I don&#8217;t want to rush the next alpha and invite people while the server still has a few bugs around. Operating the server is only going to get more complicated with more players, which is why I want to fix bugs as early in development as possible. I&#8217;m sorry development is taking so long, but I hope you can understand why.
                
                #### Can I help with restoring MLN?
                
                Yes, this is fortunately much easier than helping restoring LU. The server is open source, so if you have experience with Python and Django, you can help with software development. MLN doesn&#8217;t really have special formats you&#8217;d need to learn, so getting started is relatively simple. However, keep in mind that this requires programming experience, so this way of contributing might not be for everyone.
                
                However, you can still contribute, even if you can&#8217;t program. As mentioned, we don&#8217;t have a lot of data about networkers right now, and if you played MLN in the original days and remember some details that aren&#8217;t on the MLN wiki, or even better, have screenshots or videos of networkers&#8217; pages, it&#8217;d help a lot if you could send us info or update the <a href="http://mylegonetwork.wikia.com/wiki/Welcome_to_My_LEGO_Network_Wiki!" target="_blank" rel="noopener noreferrer">MLN wiki</a>.
                
                However the restoration has only just started, and there isn&#8217;t much organization yet regarding the collection of networker info, so please keep that in mind if you are interested in helping out.
                
                In conclusion, I&#8217;d like to say that working on the MLN server has been a lot of fun, and I&#8217;ve learned a lot working on it. The server gives the MLN restoration project a solid base to work with, and I&#8217;m confident they will be able to restore MLN to its original state in time. The work on the server has both given me new ideas for the LU server as well as means to achieve old ones, and for example something like a web interface for the server for both admins and players doesn&#8217;t seem too far-fetched any more.
                
                See you all in-game!  
                – lcdr