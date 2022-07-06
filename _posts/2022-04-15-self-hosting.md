---
title: Self Hosting Your Own Projects
description: Is it worth self hosting your own projects? I task myself with converting my AWS account into a web server in my living room.
date: 2022-04-15 19:55:00 +0000
categories: [development]
tags: [aws,development,php,nginx,webserver]
---

# Self Hosting
Self hosting has pretty much gone out the door, relegated to being used for top 500 firms, those with in-house sysadmins or a developer testing their own local builds and projects.

I was born in 1996, so it was that weird middleground of having my entire childhood **nearly** tech free. I didn't grow up with the worry of having a camera pointed in my face or my worst nightmare posted on TikTok. Camcorders were much bigger back then, and they had tapes!

So it's safe to say that the expectation that you'd host your own website, wasn't ever one that crossed my mind. We had Dial Up, DSL, ADSL, these were never capable of sending a website anywhere. So you relied on data centers and third party to do all that hosting for you!

When AWS and Azure came on the scene, it made this a dream. I'm skipping a lot of background obviously but the point exists all the same.

## Back to Basics

Now a days, you can get an internet connection with 80 down 20 up as standard. This isn't the truest measure of performance but it's a hell of a lot better to send data to folk at 20mbit than it ever was at 0.5mbit.

I decided to go a bit outlandish for my package, and went with a local firm that supplied gigabit links to resedential properties. I was now dealing with having a connection at 1Gbit, that's 12 times faster than what I was used to and 99% of the time it was sitting around doing nothing. What could I actually do to utilize the power of this connection. Streaming Netflix is at what, 20mbit. I do all my own local Plex so actually I don't even stream.

We don't do much around the house, we're just two people in a house with a couple cats. This connection is overkill. So I figured let's put it to use!

## Equipment, Software & Setup
- iMac
  - Virtual Machine Ubuntu Server
- EdgeRouter X
- Cloudflare

It's a real simple setup. I've got a virtual machine running on an iMac. That network is bridged with the normal iMac connection. From there I've got port forwarding setup on my router to direct any 80 or 443 traffic to that Virtual Machines IP.

Now, I can't just go broadcasting my home IP to the wild, that would be crazy, and sure there's going to be someone out there that might be able to find it, but to at least protect against the curious, I've implemented CloudFlare.
Cloudflare will serve up content as a CDN, and since they're now my nameservers they can protect my IP from any lookups. Win win! And they cost nothing to run as well.

So for an old iMac, a router that I already had and a free subscription to CloudFlare. I've been able to turn off my two AWS instances and host everything myself. Now of course it doesn't come with the power of the cloud, with redundency and whatnot. But for projects that are more show pieces than actual businesses, it's more than enough!

## Conclusion

One thing might be appearing clear. I used to have a ~£45p/m AWS Bill, very quickly I've been able to cut that to nill going down this route. Sure you could argue the cost of power running that iMac. But that serves my plex server anyway, so it would have been on whether I did this or not.

I'll be saving £540 a year. That's a good saving especially for someone whos projects have always came out their own pocket. It might be a bit more hands on at first, but I've been able to leave it alone for a while now and it's been up running absolutely fine! I did have to take it down one day to fix the ram usage, but other than that, I've had non-stop uptime!

I'd absolutely put it forward to anyone else in this position. Do you have an internet connection that's massively over what you need? Do you have spare hardware lying around collecting dust? Might be worth checking into whether it's worth getting your own things self hosted.

Now of course I wouldn't advocate for this approach these days for any serious implementations or projects. But for your own stuff? Why not! Saves you money and you get a good whack of experience becoming your own mini data center.
