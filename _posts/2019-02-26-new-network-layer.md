---
id: 2284
title: New network layer
date: 2019-02-26T23:58:52+00:00
author: lcdr
layout: post
guid: https://lcdruniverse.org/?p=2284
permalink: /2019/02/new-network-layer/
categories:
  - LU
  - Progress Report
---
When I was working on the MLN server, one thing that made development much easier is that the lowest levels were automatically taken care of, as much of the work had already been done by the TCP and HTTP protocols. In contrast, my work on the LU server has led to me having to start at the bottom and implement the RakNet protocol, which takes the role of TCP in LU&#8217;s networking. My experience with the MLN server got me thinking that perhaps it was possible to redesign LU&#8217;s networking so that the benefits of MLN&#8217;s networking could also be applied to LU. This is what led me to develop a new network layer that I&#8217;ve now finished work on.

The protocols involved here are situated at the transport layer of networking. At this layer, there are two protocols that are widely in use: UDP and TCP. These protocols are involved in basically every traffic on the internet. UDP is an extremely simple protocol, and essentially all it does is providing ports to associate network packets with a specific process on a computer. At this layer, network traffic is still very unreliable; packets sent from one computer may get lost in the network and never arrive at the destination. They may also arrive in the wrong order, which is also important for many applications. UDP does not attempt to solve these problems, and therefore packets sent using the UDP protocol are unreliable. TCP however implements special mechanisms under the hood to ensure that packets will reliably arrive, and will arrive in the proper order. A lot of applications (websites, email, etc) need packets to be reliable, but there are some for which unreliable packets are actually useful, like DNS. However, for these applications, this is usually a clear choice, they&#8217;ll either go full unreliable or full reliable.

Games however pose a special case in that they sometimes need reliable packets, and sometimes need unreliable ones. Here are some examples from LU:

  * Logging in to the game needs to be a reliable packet, because it&#8217;s important that the server receives the login request &#8211; if not, you&#8217;d be stuck at the login screen forever.
  * The position updates sent by the client when the player walks around don&#8217;t actually need to reach the server 100% of the time &#8211; they are sent so frequently that it doesn&#8217;t matter if one is lost. Therefore position updates are more suited to unreliable packets.

Therefore LU can&#8217;t just decide on one of UDP or TCP and stick with it, it needs features from both. This is what the RakNet protocol tries to solve: it allows LU to choose between unreliable and reliable transmission for every packet. RakNet works by using UDP as a base, and then builds mechanisms on top that ensure reliability. But unlike TCP, these mechanisms are optional, and can be enabled per packet.

This seems like a solid solution for this problem. However, RakNet has a few quirks in its implementation that make using it less than optimal:

  * In addition to the distinction between &#8220;reliable&#8221; and &#8220;unreliable&#8221;, RakNet also supports some more fine grained options that are somewhere between raw UDP and a full TCP implementation. However, at least in LU&#8217;s case, these special modes are almost never used &#8211; it&#8217;s usually all or nothing.
  * RakNet has some flaws in its protocol design that make it unnecessarily complicated, the same could be achieved more elegantly.
  * RakNet is a niche protocol, with far less support than UDP or TCP. This makes it more likely to have bugs and inefficient implementations.
  * LU&#8217;s copy of the RakNet implementation is statically compiled into the client .exe, which means it can&#8217;t be updated, especially since LU itself is no longer updated.
  * RakNet implements its own combination of cryptography to encrypt its connection, and the encryption isn&#8217;t enforced. Together with the fact that RakNet is niche and more than 10 years old at this point, the protocol cannot be said to be secure.

Thus, there&#8217;s room for improvement for LU&#8217;s networking situation. While working on the MLN server, I had an idea for a possible solution: The same kind of per-packet distinction could be achieved by using both UDP and TCP simultaneously, sending on UDP when unreliable packets were needed, and on TCP when reliable packets were needed. The solution seemed both simple and obvious enough that it was more a surprise that LU wasn&#8217;t using it already.

However, even though this seems straightforward in theory, LU&#8217;s situation made it quite complicated to actually implement in practice. We can&#8217;t just switch LU from one protocol to another, since RakNet is baked into the program and can&#8217;t be removed. Therefore, what I&#8217;ve been working on the past few months is a &#8220;shim&#8221;: A program running on the client side, acting as a local server for the RakNet protocol, translating the traffic to the TCP/UDP based protocol, and relaying it to the actual server. Due to the way LU works, this has been a bit more complicated than initially thought, as the shim also needs to simulate multiple server instances for when the player switches worlds. However, after a lot of development and testing, I&#8217;ve been able to get it fully working.

With the TCP/UDP protocol fully working, it was straightforward to swap out the TCP protocol for the encrypted TLS protocol, which is widely used, for example to secure HTTPS connections. With the protocol now using this cryptographic industry standard, LU&#8217;s security is now rock solid.

Additionally, the UDP and TCP implementations are provided by the operating system, so they can be improved without the program having to change. This also means that they are optimized to the full extent possible, as the same implementations are used for things like high speed file transfer and video streaming.

I&#8217;ve done a few unscientific benchmarks, loading worlds in LU with the old RakNet protocol and the new TCP/UDP protocol, and there are some quite noticeable improvements:

_Values are time from when the client signals clientside load completion to the end of the loading screen, on localhost, without encryption, in seconds:_

<table>
  <tr>
    <td>
      World
    </td>

    <td>
      Old Time
    </td>

    <td>
      New Time
    </td>
  </tr>

  <tr>
    <td>
      Venture Explorer
    </td>

    <td>
      4
    </td>

    <td>
      2
    </td>
  </tr>

  <tr>
    <td>
      Crux Prime
    </td>

    <td>
      27
    </td>

    <td>
      2
    </td>
  </tr>

  <tr>
    <td>
      Avant Gardens
    </td>

    <td>
      36
    </td>

    <td>
      3
    </td>
  </tr>
</table>

_Edit: It seems my connection or my ISP&#8217;s firewall may have significantly slowed down RakNet&#8217;s loading times in this test. It appears RakNet can be significantly faster on better connections, but the new protocol still seems to outperform it there._

Previously, loading a world could be quite slow, mostly because the congestion control and retransmission timeout algorithms used in my RakNet implementation seemed to have some problems estimating the ideal values for the amount of packets per second to send, and how long to wait until the packets would be resent. With the new implementation, everything is lightning fast, and the complexity is outsourced to the TCP implementation of the operating system.

### Next steps

However, it&#8217;s possible to make these improvements even better. To keep backwards compatibility with the RakNet protocol, right now the shim needs to run in the background all the time as a visible console application. The client&#8217;s boot.cfg also needs to be changed to to configure the client to connect to the shim instead of connecting to the server directly. This isn&#8217;t as user-friendly as I&#8217;d like it to be. The complexity of running the shim and translating between the protocols also adds some overhead, though it&#8217;s usually small compared to network latency.

However, these things can be fixed. As I&#8217;ve mentioned above, the RakNet implementation is baked into the client .exe &#8211; it&#8217;s not possible to replace it, as you&#8217;d need to be able to recompile the client. This isn&#8217;t 100% true &#8211; there is a way of modifying the client to run code instead of RakNet&#8217;s network functions: .dll hooking. Dll hooking works by getting the client to load a dynamically linked library at startup. The code in this library then has access to the internals of the client process, and with some surgical precision, it can find the location of the machine instructions of the RakNet functions and hijack them to run its own code instead. This technique has been successfully done in a number of games to mod them without source code. However it&#8217;s also much more intricate and complicated than the shim solution, which is why I chose to focus on completing the shim first to show that this kind of protocol replacement is possible and valuable. Now that that&#8217;s done, I can further look into a .dll-hooking-based solution, which should in theory be able to provide record speeds at less overhead.

In the meantime, I&#8217;ll be releasing both the shim executable and source code in the next days, so that other projects are also able to make use of this new protocol.

### Alpha

The network layer has been very important to me in making a decision about opening the ongoing Alpha test to new players. Some alpha testers have previously reported getting randomly disconnected from the server sometimes, which this new protocol should fix. Along with the faster loading times and the increased security, this new protocol is vital in improving the user experience of the testers. Therefore it has been an absolute requirement to me for a new alpha opening. With the protocol completed, the outlook for an alpha opening now looks much better&#8230; but more on that in the next progress report 😉

See you all in-game!
&#8211; lcdr