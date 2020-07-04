---
id: 839
title: 'Progress Report: August 2017'
date: 2017-08-31T01:00:45+00:00
author: lcdr
layout: post
guid: https://140.82.34.142/?p=839
permalink: /2017/08/progress-report-august-2017/
categories:
- Progress Report
---
_This is just going to be a pretty technical short summary about what we’ve been doing this month. Don’t expect any big announcements here, think of it more as a “behind the scenes” look at what we’ve been working on. Server development is just one of multiple things we do, so there’s more than that listed here._

**Note:** Before I start, I’d like to mention something:
In the last post I mentioned that for server costs, we’re going to have to set up some sort of donation system at some point. I also mentioned that we’d like to thank donators in some way, and suggested an in-game cosmetic shirt for this. Some of you have responded that you see this as too similar to “freemium” or “pay-to-win”. We only planned this as a small thank-you, with nothing more in mind, similar to something like donator mentions on twitch. However, we understand your concern, and I want to assure you that we will never be “freemium”, everything is and will be 100% free, no catches. Therefore, to leave no questions open, we have decided not to give out in-game items at all. Rather, items will only be available through gameplay. We still want to thank everyone who considers donating to us to help us with the server, but we want to make clear that the playing experience is the most important thing to us.

Now, on to the actual progress report!

### Research

* Investigations on older lvl formats. Lvl files are used by the game to store world information like NPCs and Enemies, and are vital for a server to work.
* Investigations on the game’s audio formats.

### Research tooling

* As a side effect of the above investigations, it turned out the current structure definition language used to document formats is not completely capable of describing all formats. Currently missing are
	* Support for pointers in formats
	* Support for recursion
	* Support for definition of larger structures from smaller ones
	* Complex looping

This needs to be added at some point to be able to describe more complex formats. The struct definition language is used by the captureviewer and structparser tools to parse binary files and packets. Luckily so far it has sufficed for them, which is why these issues have only surfaced now.

* Work on a struct-visualizing hex-editor to help with internal research on formats. Screenshot: ![Parsed and highlighted stucts in the viewer, with unparsed part visible below.](assets/2017/08/structviewer.png)
It’s still experimental and too early to release, but it’s helpful for investigations on file formats.

* Work on the client’s fdb database format.

### Documentation

* Work on cataloging available clients. For research purposes we are always interested in clients from older versions, especially from beta and alpha.
* The docs are now also available in a faster-loading read-only mode.
* I’d like to do some more documentation maintenance at some point, but it’s difficult to find time.
* Work on improving contribution-friendliness to the docs, in cooperation with researchers from other projects. We always welcome contributions, especially if they are well-researched and -sourced.

### Development:

### Pyraknet

_Pyraknet is a minimal port of the network library used by LU, RakNet 3.25, to python. It’s open source and used by multiple projects._

* Work on making the library more robust, featuring refactors, tests and type annotations.
* Implemented support for split packet receiving. This was not possible before due to having no proper way of getting the client to send large amounts of data.
* Investigations on maximum packet size. It seems LU has a packet size of 1200 bytes hardcoded for some reason, even though it’s not really necessary in the network. But just to be sure pyraknet will also use this lower size from now on.

### Server

* Features seen in our video for this month. Side note: LU is bananas.
* Ongoing work to test the server against edgecases, high loads, network issues and others. This will take a lot of our time, so it’s pretty likely we won’t be able to release a video next month.

### Website

* The website has been online for a month now, and everything’s working well. Thank you for your threads in the forums, I’m glad the atmosphere is so nice there.
* And of course thanks to everyone commenting on twitter and youtube as well. I read all of your comments, and I really appreciate them 😊

## Notes on Alpha

It will still take a few months to prepare everything for an alpha release. Please be patient until then. We’ll post updates about release and admission phase dates once we have something to report, so you don’t have to worry about missing them.

See you all in-game!
– lcdr