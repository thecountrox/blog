+++
authors = ["Prajol David"]
title = "The Internet is so cool"
description = "I yap about how cool the internet is made and how great it is architecture wise"
date = 2025-07-04
edited = 2025-07-04
[taxonomies]
tags = ["internet", "architecture" , "lore"]
categories = ["information", "lore"]

[extra]
toc = true
toc_inline = true
toc_ordered = true
+++

We take internet for granted these days like so hard.
No one actually takes the time to stop and think how fucking magical the internet today actually is.
We are running on pretty much the same infrastructure a few gigachads made YEARS ago.
You could say that the internet architecture was way ahead of its time.
This was a culimination of years of communication between multiple gigachad coders to properly put down an architecture that is currently
undergoing the test of time.

You can actually "practically see the internet evolve" to the architecture that it is currently seen today **[HERE](https://www.rfc-editor.org/)**

There are a lot of such archival mailing lists (most notably the Linux Kernel one) [lore](lore.kernel.org)
Where you can find age old mailings and the complete lore of the linux kernel.

### Architecturally sound, still standing:
In short the following technologies have withstood the test of time and are still being actively used without any obvious hatred for how its architected:

- TCP/ IP (although IPv6 adoption is currently underway)
- DNS (Domain Name System)
- HTTP (Hyper Text Transfer Protocol)
- Packet Switching (Still the least overhead, most efficient way to route packets that can be decentralized)


### Current Trends / Adoption:
Although currently, the following technologies are in the verge of being adopted with industry leaders trying to get them adopted (and trying to make money in the process):

- QUIC (UDP but with transport handshake that is marginally more secure and faster than TCP)
- AI/ML on transit network (still insane that this exists, AIOps)
- Edge computing 
- Decentralization (web3, blockchain)
- DNS over *protocol* (HTTPS, TLS)
- DNSSEC (seperate protocol that implements DNS clients with authenticity and integrity)


### QUIC (why its a game changer):

Have you ever clicked on a link and felt that *every so slightly* delay between click to website render on your page?
Are you a web developer and have tried to optimize this but its always that slow, even on local ip?

Its just TCP showing its age. Yeah TCP is cool, I **just** talked about it.
BUT: **QUIC is UDP with handshake**

QUIC is *QUIC*ly reshaping the networking landscape with almost all new *BIG* networking projects often times opt for QUIC protocols (ex: [Syncthing](https://syncthing.net/)

TCP is old, has security issues that has been discovered by *very smart people*, The 3-way handshake is "extremely slow" for today's standards (it is LITERALLY the only thing holding you back from **instant** page loads)

### What Does This Mean for You (and the Future)?
QUIC, especially as the foundation for HTTP/3 (the latest version of the web's core protocol), is already delivering tangible benefits:

- Faster Page Loads: Especially noticeable on mobile or unreliable networks.
- Smoother Streaming & Real-Time Apps: Less buffering, more fluid interactions.
- Improved Security: More of your online activity is encrypted by default.
- Better Mobile Experience: Seamless transitions between Wi-Fi and cellular.

