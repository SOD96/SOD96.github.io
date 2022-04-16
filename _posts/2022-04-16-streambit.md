---
title: Creating Streambit.TV
date: 2022-04-16 14:13:00 +0000
categories: [development]
tags: [aws,development,php,nginx,webserver,streaming,streambit,vod,video,wowza]
---

# StreamBit

I created Streambit as an answer to a lot of drama that happened a couple of years ago, **PLUS** I was heavily into streaming and wanted to learn how the process worked. What I learned was a tale of absolute hardship, uphill battles and looking at chinese encoders. If you want the skinny, please don't develop your own platform.

## Streaming

A bit of background. I streamed pretty much constantly on my old twitch channels (rip usernames), I now stream solely on [Twitch.tv](https://twitch.tv/switchedbittv) funny story about that, I created the channel SwitchedBit so I could use the username, realized that you can change usernames, now am waiting 6 months to get my better username.
Anyway, I'm a streamer, I wanted to make my own platform because it seemed like a decent market. Twitch Streamers kept getting banned for things that I found rather funny (I've grown up since, before you flame me, I realize that banning them was the best course).

## Learning

A lot of it was also built in my philosophy of build what you want to use. All my projects come from the angle that I think I could do something better, and that was slightly true for streaming. I feel like many of these platforms come from their old codebase and perhaps things aren't as optimized, maybe I'll think of a killer idea that would be great for streamers. Perhaps I'll combine ReStream and Twitch and create a streaming network that endorses going out to multiple platforms rather than stifling competition. Either way I was sold on the idea. Plus it would be a great opportunity to learn.

## Stack

For the stack I went with...

- Laravel (PHP)
- AWS

Simple as that. It's a full Laravel app using Blade Templating and integrates with various AWS services to perform the encoding to multiple different formats. Now during this process, Twitch was purchased by Amazon. Which meant that not only were Twitch a competitor of mine, AWS was now too, and if I built a streaming platform on their platform, they were winning either way. They either got my eyeballs from watching Twitch content, or they got my money from the insane charges. (Bandwidth costs and Video is extremely expensive just FYI)

So, once I came to terms with that, I pressed on. AWS was the only real way I could do something like this at scale. I can't exactly self host my own encoder platform and ingest thousands of gigs of video every second. AWS can. At a cost of course...

You might've noticed I've not mentioned streaming yet, well... let's get into that.

## How hard can streaming video really be?
So. Streaming video. All in all this was a process I'm glad I did as I learned quite a lot. Where do you start with streaming video. It's perhaps the most painful thing a developer can get involved in. Browser Standards for one, some browsers behave differently with different media players. Heck actually creating a media player, are you insane? If you want a challenge in your life try creating a media player with the different browsers. It's great that edge is chromium now, but back when I was doing this they weren't!


As it became obvious to me, off the shelf video streaming plugins or composer packages didn't really exist. I had to start from the ground up, and what that meant is I had to google and hope other devs had ran into the same issue. And oh boy they had.

There was this forum post, absolutely lost now about this NGINX RTMP encoder, only issue was it was written in Chinese. But by god it actually worked. I could sent a stream to this and place it on web pages (some, remember browsers are a hassle).

So we were good right! I had the backend! I'd just let my users throw their streams to a NGINX server then throw that content up on my website.

**SECURITY**

The biggest hurdle during all of this then became security. Stream Keys are a thing! Maybe some O-Auth, what about getting OTP implemented. Implemented into what? The world used X-Split at the time or OBS. Sure OBS is open source so I could run over and code up my own implementation, but if I wanted this to work, I'd need to have StreamBit in that dropdown so people could easily authenticate. Never mind the hurdles I'd then have trying to engineer this RTMP NGINX Plugin to only work for certain stream keys and all the rest of it. Basically, the challenge was far to large to overcome, please if you think you're better than me have a pop at it. But I gave up with that after weeks of banging my head against a wall and went with another solution... or well 5 other solutions, I tried ones such as Red5, Adobe Media Server but they never worked or has some extremely outdated documentation. Also keeping in mind that if I couldn't get StreamBit into the dropdown, I'd have to go for the dreaded "Custom" option, which then added a new layer of having users that didn't know what details to enter in. Less barriers of entry = more users.

## Wowza

[Wowza](https://www.wowza.com/) came into my life and very quickly fixed a few glaring issues. I now had the streaming problem done by a third party, with a fantastic media engine, API and affordable plans. They even had an unlimited free dev trial so I could keep plodding away whenever I wanted. How did I find Wowza? I read online that it was the engine that Twitch first went with. I'm not sure if they still use them, or if they have their own now. But it gave me enough confidence to jump in, and with a lack of sleep, reading 1 vague post online, I setup Wowza.

Now of course, with anything that I've described in this post, there's always a but. When I first streamed with it, it worked, great. Fantastic. Except... why was there nearly a 2 minute delay in my stream. I'd do something and wouldn't hear about it till the next day. Something was off. After digging through mountains of documentation and unanswered community posts on the issue, I settled with changing enough values and whatnot that over the course of messing around over 2 weeks, the lowest I could get the latency was around 10 seconds - 15 seconds. The community seemed to agree that 1 second was possible, but it would buffer like mental. And it did.

So here I was, weeks thrown away for a streaming engine that wouldn't perform anywhere near what my competitors had. Not to bash Wowza, it's a tricky challenge and apparently it's possible on their software. It's been years also since I last used it, maybe it's easier now! To be clear this isn't me bashing Wowza. It's me showing how hard and fiddly this problem is. Maybe I was a setting away from figuring it out. We'll never know.

So I gave up. Again.

## Back to Video

So I went back to Video, at least I had that working, comments, everything else, I had a bog standard video sharing platform, I could sell this surely. Then the Pandemic hit. And I seen a pivot worthy moment where the boom of Work from Home and especially Teach from home took off. Surely I could get some interest if I pivoted my platform and made it a platform that perhaps kids could use? And that's when we start getting off the deep end and start getting into societies issues, along with political ones.

My aims this entire time was to create a platform that those cancelled voices could use. But I then wanted to shift into providing content that had to be locked down, perhaps a platform that someone could license from me and do what they want.

It became too blurry, I lost sight of what I was trying to build and eventually ended up not seeing the point. Those people that got cancelled, got cancelled for a reason, their views were typically frowned upon by society and any company letting them speak was opening up the a majority not wanting to use them. As a business that is untenable.

Wanting to serve content to teachers and kids and bridge that gap. Sure, here's a very quick life lesson. If you're a developer don't get involved in safe guarding or any of that, it's a nightmare to navigate and something that genuinely you don't want to be responsible for. Leave it to the giants with lawyers and an army of business people.

So, what about just a normal video platform? I decided to give up on this because of a moderation angle. Twitter has issues with deleting videos, I don't know how many videos I've seen of the Ukrainian war of dead bodies across the street and decapitated children. It's horrible. I cannot solve that problem, I'm not even going to let it occur.

So here I was. I'd built a video platform that I didn't want to advertise because;
- The alt right might find it and upload videos of them burning other religious folk
- The actual right wing might find it and upload videos of them burning folk
- Bad people might use it
- Cancelled folk will bring it down
- Navigating the challenges of child care and ensuring COPPA is followed
- GDPR and everything there


I promptly relegated it as a learning experience and a portfolio piece, which it has done very well! It got me my current job as it was a very interesting project (I tend to not tell them about the latter half of this blog post). Would bring down the mood a bit...

## Result

The result was a project that actually worked... Briefly.
- I build the chat backend in Node.JS then lost the repo due to a self-hosting git issue, so now chat doesn't work
- Video uploading worked! It would save the video locally, send the video to S3, a trigger would occur that would then send that video to AWS MediaConvert, that would then send the video to a public bucket where the website would link to it.
- Streaming simply didn't work, it would take an army to conquer that and I could hardly afford the cost it took just to maintain the application doing nothing on AWS.
- I was far to concerned about dangerous parties using it for bad, and being unable to moderate that


So that is StreamBit.tv, it's still live now being self hosted, I doubt video uploading works but it serves as a time capsule for what might've been possible and hopefully a tale to warn developers against doing the same thing. Although if you are interested in streaming video, re-streaming and getting a job at Twitch, it might be a good idea to fire in and do the same as I did. Albeit, now you've been warned.
