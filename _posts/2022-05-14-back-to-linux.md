---
title: Moving from Windows back to Linux
date: 2022-05-14 10:24:00 +0000
categories: [general]
tags: ['linux', 'windows', 'manjaro', 'arch', 'moving', 'OS-Swap', 'gaming-on-linux', 'linux_gaming', 'archbtw', 'Unraid']
---

# Initial Experience

Going to apologise off the bat, as there's quite a lot of context that led to this decision being made, but it's important if your a tinkerer and like to mess around quite a lot on your machine, I feel like you'd understand the process I went through!

I've been a bit of an OS Swapper for years now. Always giving Linux a go to see if I could squeeze extra performance and just... be different I guess. It never really worked, gaming always brought me back along with the eco system of Windows just making things easier. But I have to say, perhaps things have changed? Linux for the most part is now completely endorsed by Steam, one of the biggest gaming marketplaces. The fine detail is that Steam needs working machines in order to sell games and make money, they're hardly going to endorse Linux as an operating system if it doesn't play games, hence their users can't buy new games. Now that it has their backing, it felt worth it going back in.

Recently, earlier in the year, I made a massive effort to switch to Linux full time over a period of 6 months. Specifically, this was with Unraid, an excellent VM manager that would let you spin up virtual machines and actually have the hardware passed through to it with near 0 delay. Of course there's a lot of underlying technology within that, might talk about that later! You wouldn't notice that the hardware was being passed through, it ran just like a normal machine. To me, this was amazing. I could have one machine, with my Plex server and all my other dev things going on, while having a VM dedicated to Windows Gaming, and a VM dedicated to Linux for development. It was king.

But then, something happened. Tarkov started kicking users out of the game if they dared to have their game running in a VM. This was done to defeat cheaters. Of course cheaters still plague the game. This meant, me a completely legit player, couldn't play Tarkov a game I'd spent hundreds on. I was kinda pissed, so I went to get a refund. That didn't work. Same with Halo Infinite, Battlefield 2042, all the games that were coming out, were locked to Windows and I wanted to get on and play them.

So I was stuck. I could go back to Windows, but then I'd need to give up my entire Unraid setup and everything else. I started thinking about it and eventually it just made sense. Unraid was a fantastic solution but at the end of the day I was giving up performance just to be different.

## The transistion back to Windows

Ashamed of myself, I booted back up Windows and went to work reinstalling absolutely everything. The fun part about Windows and Linux using completely different file systems means you're totally screwed when it comes to data. Thankfully as I'll get into later, Windows did keep all my old files and such from OneDrive, so really I wasn't missing much. Heck, I didn't even notice I was missing anything when I was on Linux either. But I guess that's easy to do when you have two VMs and can access your data whenever you wanted. But I decided, a clean slate, start fresh, don't give a damn what's on the drives. All my development stuff is stored in git anyway, and anything else likely just me hording things.

I will say... getting my plex library back again was a chore. I do not wish that on anyone and I very much doubt I'll be switching away from the iMac anytime soon, especially with how useful Direct Play is. 0 Transcoding required!

But I was back. I could now play Halo Infinite, Battlefield 2042, Tarkov. And I did, I jumped right on those games just to be completely disappointed. 

I've spoke about [Battlefield 2042](https://switchedbit.com/posts/battlefield/) previously on this blog, switching my entire environment to play that game absolutely wasn't worth it. Halo Infinite never kept my attention enough and Tarkov left such a sour taste in my mouth with how the support treated me, I didn't want to play it again.

So here I was. Stuck on Windows now, absolutely dejected that I'd spent all this time moving back to Windows when it absolutely wasn't worth it. But hey, maybe the performance is better right?

## Performance

There's a distinct vibe on the internet for me, everyone is getting better performance than me and for the life of me I can't figure out why. That happened with [Cyberpunk](https://switchedbit.com/posts/cyberpunk/) recently. I was getting drops down to 20FPS in certain areas, even on Low. Hearts of Iron takes an absolute eternity to load aswell. Also, if you use OneDrive and it is accessing the same files that your game is accessing, like, SAVE GAMES?? It'll make your game go super slow and lock it up while it uplodas it. Very annoying.
Also, when it came to something like Origin updating games. For some reason Windows Defender kept scanning every downloaded file. thus completely wrecking my SSDs and my performance. I have a Gigabit internet connection, so I'm downloading a 1Gig, onto a drive that's both trying to write and read it as fast as possible. That's not good for anybody. Also, **YOU CAN'T DISABLE IT, AS THEY RE-ENABLE IT AFTER 24 HOURS**.

I'd had enough. That day I got a USB stick and put Manjaro on it.

## What then?

Simply put I installed Manjaro to a partition on one of my M.2 Drives. Sure enough I haven't been back to Windows since. It's been 2 weeks now, I've got 4TB of SSD drives tied up in Windows Storage Spaces that I haven't been able to use, but I don't have any need for them. I can't think of anything that's on them that I actually care about. So I have a good mind to just go on there, and nuke them into some kind of ZFS pool. Heck maybe it'll perform better. Storage Spaces was a pain in the butt to setup in the first place. Genuinely crashed the first 3 times I tried to do it. It's a GUI! There isn't much else I can do other than press next!

### Performance

Now, what this whole article was really about, was gaming performance on Linux. I'm rather happy to report that those CyberPunk issues still affect me even on Linux, with one exception... I don't care as much.

On Windows it made no sense. I had DLSS, I had everything cranked to low, there wasn't a REASON for it to be hitting 20fps. That seemed like a failure in the game to me. Switching to Linux has in my eyes proved that. I don't have any of the fancy features that Windows has to preserve FPS. Yet it performance near identical. That's enough for me to back that horse and hope it gets better. At least Linux has a reason for the bad performance. IE: It's a game that isn't native to it, hence has to use Wine (Proton)

Also with Hearts of Iron, I challenge any of you, if you play Hearts of Iron, use the Windows version, and time how long it takes for the game to start up, then use the Native Linux Version. You'll be blown away at how quick it is.

## Data

There's also the topic of data. In my time I've been through the internet when we had dial up. To AOL, to storing passwords in the browser. All in all, I've seen it all and to be fair to myself it's left some pretty nasty habbits that aren't really needed anymore these days. Like the absolute want to preserve data.

All my pictures, are always sent through my iPhone. My mum sends any family pictures over Facebook, those automagically get saved to iCloud and I pay £2.99 for that peace at mind. I could go out, flush my phone, get a new one and all my data would download back to it. Heck, if I switched to android, all I need to do is migrate all the data across, and that takes a few minutes.

Secondly, passwords are stored now in the cloud, every AV tool has their own Password Manager. LastPass is a perfectly fine way of saving all your passwords, and even then it allows you to secure store files and notes. I don't know how many times it's saved my bacon when I've remembered I took an excerpt of a terminal print out with sensitive details and just lobbed it in there *INCASE* I needed it. Sure enough, always do! But that isn't dependant on my operating system!

I recall one thing that I always tried to keep was the NAND flash of my Uncles Xbox 360. We flashed it one day, and JTAG'd it so I needed to keep those files incase he ever wanted to go back to retail.

Back to retail, in 2022. Why the hell do I still have those files. Throw them into LastPass, and don't think about them again!

Although on that Topic my OneDrive subscription has saved me numerous amounts of times when it comes to certain things and documents on my desktop. That's something that I perhaps should look into for Linux. If anyone has any backup recommendations, let me know at contact@seanodonnell.co.uk


## Conclusion

So here we are, at the end of the day, I'm typing this to you on Manjaro (archbtw) Linux am just about to boot up Cyberpunk so I can finish off this blasted story. Yes from my previous blog post I was done with it, but I went back 6 hours and just did everything again. I will finish this game! I'm saving a lot more too, just incase!

I've regretted nothing so far, being adventerious and messing around so much with my own machine has led me down the path I am on today. There's no better career advancement than doing something like this just for the hell of it. You'll learn a bunch. I'd always ask any would be IT Technican to at least have one Linux system in their house so they aren't out of the loop on everything. This week was my first time installing a new Kernel for different features. I didn't even need to reboot my machine. How on earth is Windows still in the 90s.

Development has also been far more simple. I'm not running a VM Anymore or WSL2 to develop on, which means there's been less issues in the networking department. Whenever I was on a VPN, it would mean my WSL2 instance couldn't connect to the internet. A known bug apparently. Don't have that issue anymore on Linux.

So yes, I'm rather happy where I am, but we'll just need to wait and see. I do have an Xbox Series X these days so I dunno, might just attach a mouse and keyboard to it and go away playing games that way I guess!