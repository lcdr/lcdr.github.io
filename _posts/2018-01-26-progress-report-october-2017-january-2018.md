---
id: 1923
title: 'Progress report: October 2017 – January 2018'
date: 2018-01-26T19:00:35+00:00
author: lcdr
layout: post
permalink: /2018/01/progress-report-october-2017-january-2018/
categories:
- Progress Report
---
So, by now it’s been three months since the alpha started. Time for some updates on what’s happened in the last three months.

You’ve probably noticed that there haven’t been too many updates on progress lately. That’s partially because I’ve been pretty busy and haven’t had as much time in the last months, but also simply because alpha progress isn’t as easy to demonstrate as feature implementation progress. There’s been a bunch of improvements since the alpha started, but most of them have been minor or internal, and not the typical stuff we can show in our videos. However, by now there are enough that I can talk about them in more detail.

So here we go, a comprehensive list of bugs that were resolved and features that were implemented since the start of the alpha:

(Issue titles usually appear as the tester submitted them)

#### October

* ###### Pyraknet: Issue: Duplicate detection not working properly.

	[Pyraknet](https://bitbucket.org/lcdr/pyraknet/) is the network library implementing the RakNet 3.25 protocol that provides the low-level network layer that LU uses for network communication.
	It needs to resend packets when the client doesn’t receive them for some reason, and it needs to be able to detect and throw away resends it doesn’t need when it did receive the packet.
	In a rare case (only 1 message used by LU was using this packet type) the duplicate detection didn’t work. This patch fixed this problem.

* ###### Issue: Block Yard doesn’t work.

	Most objects on Block Yard didn’t appear for some reason. It turned out this was due to a change in the server’s spawning logic, which, ironically, actually was implementing a new feature, but invalidated an assumption made by Block Yard’s world script. The issue was quickly fixed with some changes to the script.

* ###### Implemented: Achievements for collecting powerups.

	A rare achievement type, used only by 3 achievements in the whole game, was implemented after a tester noticed the achievements not working properly.

* ###### Issue: Rocket Take-off uses another rocket than the one placed.

	Selecting a rocket using the mouse rather than pressing shift wasn’t working correctly, and got fixed.

* ###### Issue: Imaginite isn’t taken by mission.

	The mission in Nimbus station where you can trade imaginite for backpack space wasn’t removing the imaginite properly. Fixed.

#### November

* ###### Issue: Turret quickbuilds don’t despawn.

	Avant Gardens’ robots drop turret quickbuilds, which only despawned when built by a player. Most of the time the players didn’t build the turrets and only smashed the robots, leading to quickbuilds piling up on the AG battlefields. Fixed by introducing a self-destruct timer.

* ###### Issue: Imaginite isn’t taken by interactables.

	Similarly, survival and wishing wells also didn’t remove imaginite on interaction. This also got fixed.

* ###### Issue: Survival enemies don’t spawn.

	Similar to the Block Yard issue, spawning logic was also affecting AG Survival. Similarly fixed with alterations to the script.

* ###### Issue: Unimplemented achievement rewards.

	A few achievements didn’t give out rewards when completed. It turned out this was due to some entries in the game’s original database not being set correctly.

* ###### Implemented: Achievements for survival times.

	Most achievements regarding survival times were already implemented, but it turned out the game actually uses two separate mechanics for these achievements, and only one of them was implemented before.

* ###### Issue: Monument finish line won’t end quickbuilds.

	A quickbuild wasn’t completing correctly. It turned out this was because the object overrode the game’s database on quickbuild complete times. Fixed by implementing the override.

* ###### Issue: Imagination fountain doesn’t drop imagination.

	Some items that were supposed to drop powerups, didn’t. Fixed by implementing the associated script.

* ###### Pyraknet: Issue: Absolute time used when relative time needed.

	In some packets pyraknet has to send timing information in packets. It turned out the time it was sending was absolute on Linux (but not on Windows), when it should have been sending time relative to program start. This change enforced using relative time everywhere.

* ###### Implemented: Random missions.

	The game features some daily missions that are drawn from a random pool and not offered sequentially. Support for this was implemented.

* ###### Issue: “Stagecraft” achievement not working.

	Another bug caused by a script not working correctly. While some more work on the script remains to be done, it now correctly updates the achievement.

* ###### Issue: Mission to play a guitar not working.

	Similarly caused by a script, and similarly had some complications appearing that caused full implementation to be postponed. The mission is correctly updated now, however.

* ###### Issue: Paradox’s Plasma Ball 1 does not kill enemies.

	Caused by a bug in skill parsing. Skill structures remain relatively unknown, mostly due to complex conditions that are hard to reverse engineer. A few similar bugs for other items still exist, and in some cases investigations are pretty much stuck because the condition can’t be analyzed even when the matching code is found. In this case however it was possible to resolve the bug.

* ###### Issue: Plasma Ball 1 jump attack does nothing but consume imagination.

	In some instances, skills can cancel their execution, as happened with the item here, which doesn’t cast its effect if the player is jumping. The server was however still removing the skill’s imagination cost, even if the skill cast had failed. This was fixed to only take the cost if the skill actually succeeded.

* ###### Issue: Spider Cutscene being played for everyone

	Some network packets are supposed to be sent to all players, while some should be sent to just one player. In this case, it seems a message that would normally be sent to all had its behavior overridden to only be sent to one player. The server didn’t know about the override, and sent it to everyone, causing the cutscene to appear for everyone in the world. Fixed via override.

* ###### Issue: Rocco Sirocco doesn’t spin

	A script wasn’t working properly, and wasn’t displaying a cinematic when the mission completed. Fixed through script modifications.

#### December

* ###### Issue: Daily Mission “Six Shooter” doesn’t give Plunger Gun.

	A script wasn’t implemented, and didn’t give out a mission item.

	December featured several large refactors, which reorganized the server internals and cleaned up the code. They didn’t change the external behavior of the server by much, but nonetheless represent significant improvements, as they affected about half of the server and made it easier to implement new features in the future.

* ###### Refactor: Server command system.

	The server command system was rewritten to be completely separate from the core server. As a result of this change it’s now possible to delete the entire folder related to commands, and the server will continue to function as normal (just without commands, which aren’t part of normal gameplay).

* ###### Implemented: Mail attachments.

	Mailing attachments had been supported for a while, and the server was already using it to distribute achievement rewards when inventory space was full. However the interface allowing players to send items per mail was disabled, until this patch changed this.

* ###### Implemented: Mail cost.

	Sending mail costs coins, and mailing achievements increases this cost by the cost of the items mailed. With this change, the server now subtracts the correct cost from the player when sending mail.

* ###### Pyraknet & LU server: Refactor: Separate BitStream into read-only and write-only versions.

	Pyraknet also provides a way of reading and writing binary data sequentially, and which allows reading/writing single bits. It turned this was almost never used for reading and writing from/to the same stream, and therefore could be separated to make the intent of the stream more clear.

* ###### Pyraknet & LU server: Refactor: Change to use composition instead of inheritance.

	Pyraknet had previously been using an inheritance model, where the LU server overrode certain things to implement its own functionality. This worked well and allowed for a lot of freedom for overrides, but didn’t separate the low-level pyraknet stuff from the high-level LU server stuff well. This was changed to use composition instead, where the LU server interacts with the low-level layer mainly via callbacks and delegations, which provided proper separation.

* ###### Pyraknet & LU server: Refactor: Add type annotations.

	Python is dynamically typed, and as such doesn’t enforce a variable to remain the same data type. However information about the intended data type is useful for documentation and static validation, and so Python has added support for this information in recent versions. With type annotation support improving, it was time to add type information to the pyraknet & LU server projects where it hadn’t already been present.

#### January

* ###### Pyraknet & LU server: Refactor: Various refactors.

	A bunch of minor things were changed and improved, some variables were made more restricted, and some internal systems were reorganized. The changes are relatively specific to the internal implementation, so I’ll keep this paragraph short. However, that doesn’t mean these changes were insignificant – grouped together, they were one of the larger refactors.

* ###### Issue: Buttons at the AG Monument trigger even when not built.

	Buttons could be pushed even though they hadn’t been built yet, also known as “invisible buttons”. This was caused by an unimplemented check in the component, and was fixed by implementing the check.

* ###### Pyraknet & LU server: Refactor: Restrict bitstream interface further.

	Previously it was possible to access packet data both by array index notation and via the sequential interface. In practice the random access was rarely used, so this patch removed this functionality and restricted the interface in some other points as well, which makes passing the bitstream to other handlers safer.

## Next up

I hope this list could give you some insight to the kind of bugs that pop up in alpha testing, and to what I’ve been working on in the past months.

There have been a bunch of bugs fixed since the start of the alpha, but there’s plenty left to fix. 50 bugs remain open, and while most of them should be possible to fix, it will take some time. I want to make sure the server doesn’t just have a lot of worlds, but also runs smoothly, and for that to work, it’s necessary to fix the open bugs before opening the next alpha stage. Based on the time it took to fix the above bugs, it’s likely it will take some months until the server is ready for the next alpha. But by then, the server should be pretty robust. 🙂 I’ll publish something when the server’s ready, and I’ll continue the progress updates in the meantime.

See you all in-game!

-lcdr
