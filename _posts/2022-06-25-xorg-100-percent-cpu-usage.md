---
title: XOrg stuck at 100% CPU Usage | Laggy Experience in Games | Laggy Manjaro (SOLUTION)
description: Issues with XOrg on Linux going to 100% CPU Usage and causing your games to lag? I found the solution!
date: 2022-06-25 13:24:00 +0000
categories: [development]
tags: 
- Manjaro Lag
- Manjaro
- Battlefield 4 Lag
- Battlefield 4 choppy mouse movements
- xorg
- x11
- xorg 100% CPU
- xorg lagging
- Linux Lagging
---

# The initial Problem

It'll be good to set the scene because this one was a head scratcher, but it makes sense so I'm actually fine to have ran into this after months on Manjaro. I've been slowly migrating over game after game to Linux, and one big one I was into just before I switched was Battlefield 4. I've been enjoying replaying it, but I always ran into a few issues with the Linux version
- Origin was hell, Lutris never worked either with it
- Colour Grading was way off, it was like I was playing it on a 4 bit display
- FPS performance tanked
- Mouse Movements lagged behind, it would be around a 2 second delay
- My entire desktop would freeze for a good 3 minutes while it shut down

In other words, it was completely unplayable, however the good people on the Manjaro forums, Steam and everywhere else seem to be having no issues at all. Surely it must be me! But I've played nearly 60 hours of SWTOR the past 2 weeks, and countless hours of nearly every Call of Duty / Cyber punk game, never ran into any issues like this on those... was it me?

It did dawn on me however, that my experience with Call of Duty, wasn't the best. It did chop around and the mouse movements were so bad it would put you in hospital with stress. Perhaps it was an issue with me, so I set out to find out!

## An entirely new Desktop Environment???

Yes, the first thread I came across recommended a new desktop environment or playing around in that sector. Straight up, do not do this. I've now got a situation where I have two, split across different users and my original doesn't work like it used to. It's fine, but whatever commands I ran, just don't do it. Don't go down this hole because your problem is unlikely to be with the DE, at least consider your own hardware. I'm running a Ryzen 9 3900x and a RTX 2080ti. I should be able to handle any DE that comes my way. I'm now left trying to restore my life back to how it used to be!

## Perhaps it was Lutris!
A Worthy suggestion, I'm not too clever with how Lutris works, but I imagine the brainboxes at valve with their far simplier UI must have figured it out a tad better, after all, whenever I launched Battlefield 4, all it did was launch Origin! Surely Steam would have a better solution... It does and it doesn't. It doesn't launch Origin (At least not fat origin), but it came with all the same problems that Lutris had. I spent £3.99 on EA Access just to test this, problem existed on both platforms. Game would be choppy, mouse lagging, etc...

## WHY XORG!

Throughout all of this one common enemy was XORG being at 100% CPU usage whenever Battlefield launched. This same thing occured whenever I moved the Spotify window, which also was powered off this, however firefox was fine, I presume because that goes via Wayland? I'm still getting used to all the terminology, but this is when things started to click and the research got deeper. I came across an archived article https://archived.forum.manjaro.org/t/high-cpu-usage-caused-by-xorg/139238 which is exactly why I am making this post, to forever preserve this information, at least in a git repo somewhere (This blog is hosted on Github Pages), doubt it'll be closing anytime soon.

My issue, was with xorg, and more importantly an application that was using Xorg to render the view. As Fabby said

>Yup. That's an application bug that crashes the compositor and has Xorg CPU usage rung through the roof!

>Which application? That's the hard one to figure out: I've had it with VLC and qBittorrent in the past, but they're OK now, so see which applications you're running and if you find the offending one, file a bug report.

Straight away I started closing things off in the task bar one by one, then I seen Xorg go from 100% CPU to not even on the list. Fired up Battlefield 4, and the issue was completely gone.

## Normal Users

Now, throughout all of this I've had to do some pretty damn technical stuff. Everytime I come into one of these challenges I always leave happier because now I know in the future if XOrg is kicking up a stink, it'll be because some application is having a good old time somewhere ruining my day. But one thing I can't escape from, is how on gods earth would a user know how to troubleshoot any of this. There's a good chance I wouldn't have found that article, and still not have fixed it. I was inches away from reinstalling Manjaro. Which would have fixed it, until I reinstalled Jetbrains Toolbox. But that's exactly what happens. We get an issue like this, rather than fixing it, we just reinstall and call it a day without knowing exactly what happened and what might help someone else in the future.

So, lucky internet user, if this sorts you out, let me know!

## Conclusion

Something like this, I feel should warn the user. It doesn't seem normal that a key system process like this should be able to exhaust resources to the point where the system becomes unresponsive. A simple check on how resources are being used to warn the user perhaps of the offending process would be suitable. Let them terminate the app, or keep it running. 

Either way, it's a really complex issue it seems for it all just to be related to "Aw you've got a dodgy application open that's not got that great support"

Great, guess we're all just waiting on Wayland right :)