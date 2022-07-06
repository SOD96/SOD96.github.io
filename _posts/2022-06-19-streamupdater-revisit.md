---
title: Revisiting StreamUpdater.com | Revisiting old side projects
description: I revisit StreamUpdater which is a project which automatically updated your Twitch Stream information as your playing games
date: 2022-06-19 13:24:00 +0000
categories: [development]
tags: 
- PHP
- Laravel
- php8
- laravel8
- laravel9
- StreamUpdater.com
- Twitch
- Twitch API
- Twitch PHP API
- Twitch Web Sockets
- Old Side Projects
- PHP Side Project
- Web Development
---

# The Old Flame

It's been a good while since I opened up some of my old Web Development projects. Namely StreamUpdater. It was my first real go at something rather challenging. A C# app and a PHP Laravel API to handle all the data sending from that C# App. It was extremely fun. The jist of it is, if you're playing a game and live streaming, the last thing you want to do is bother with changing your title and what game you are playing. I developed an app in C# that would get your list of processes running on your machine, send that to StreamUpdater.com whereby I'd then do my magic and update your Twitch Account. It worked really well!

However, this week it ran into some issues...

## Users? Here? Localised entirely within this applications database?

The interesting thing about StreamUpdater is that I typically get a new organic signup every month, but I've never understood why they never really did much. Until one of those faithful signups joined the discord and complained about `500` errors.

It turns out, that since the switch from Laravel 5 to Laravel 9 there was a change to how logs were handled, so any error messages weren't getting saved. Also in my adventures changing web hosts every month it meant my .env files never got saved so plenty of details were missing. I just assumed this was fine with the new sign ups and because my account was still working. (I actively used the product) so it seemed fine to me! Just goes to show, I really wasn't testing and that's totally on me. Lessons learned.

But I had users! Turns out there were a few issues...
1. They weren't getting the welcome email
2. They weren't getting any of the correct starter data configured for things like user settings
3. Logs weren't saving, so I wasn't aware of any issues going on

So they weren't getting notified where to go for support, so that was strike one. Second was that due to that welcome email not going out, the app crashed and never setup various other settings that are requrired I have of course fixed this but yeah, not good! This mean that whenever they went to the app, they got a 500 error, since my logging wasn't working I wasn't ever notified.

## Fixes for the issues
Annoyingly, I never had an environment setup to easily get StreamUpdater up and running locally. I typically used a minified and obfuscated version of the live production database but it's been a while and looking at those relationships made me want to die. So yes, I developed in production. While not suitable, considering the only people live on the application was me and this dude that decided to let me know "Hey dude, your building is on fire did you know that", I decided it was a worthy risk and my new friend would help me along! Which he did! Thank you Benjas333

The fixes, annoyingly, were very easy...

Emails didn't send because my .env never had my G-Suite details saved, hence it wouldn't send emails from the info@streamupdater.com account

Things were 500 erroring all over the place because new accounts weren't getting their settings and configuration files saved, this was due to the previous error. I setup new accounts AFTER the welcome email sent, that now occurs before. This honestly happened because as I added new features I just added the setup step to the end of the new account login function.

## Old Code

One thing that this experience brought was learning from my old code. So many mistakes, so many un-optimized functions and things I could have done better. To be honest reading through it I wanted to just nuke the codebase and restart on a brand new Laravel 9 application, with Vue and Inertia JS. It absolutely would have been a night and day improvement. When I built StreamUpdater I don't even think I was working full time. I hadn't had any commercial PHP experience. However, with that new experience comes the making do with what you have. Plenty of companies are still out there running PHP 5.6 on their production boxes because hey, it's working and that's all that matters. I use an extreme example, please don't use out of date software (It's why, while I might avoid new features with my projects, I always migrate them to the new version of Laravel every year)


But I stuck with it, resolved everything in about 2 days. (I had a wedding in the middle of that, so reasonable excuse for the delay) Whereas if I just nuked it all, I'd have to restart completely from start, chances are I wouldn't be writing this blog and I'd just shut the project down. StreamUpdater took a good few weeks to initially build, scrapping all that time invested is just extremely bad planning. I'll keep it, and instead just refactor what I need to refactor. Frontend absolutely needs improved I'll bring in some new updates for that. The good thing is it does offload a good lot of the processing to many of the controllers and such, so nothing much is done in the front-end. I at least got that right, so plugging a new frontend should actually be smooth. Blog post for that no doubt! But I'm also developing a cross-platform app in Rust so it'll work on Linux, Mac and Windows! Before since it was C# it was Windows only.

Since we're chatting about old code, here's a fantastic foreach loop that I did years ago...

```
$bots = Bot::where('pid', '!=', NULL)->get();
if($bots) {
        foreach(Bot::where('pid', '!=', NULL)->get() as $bot) {

        }
}
```

I know it hurts to look at! Trust me there is plenty more in here, but it brings us onto a new topic rather nicely!


## Why isn't it open source?

I love Open Source code. Infact I've started building all my new projects Open Source. The main reason why this and plenty of my other old side projects aren't open source is an absolute fear of vulnerabilities. There's plenty of things I haven't done right. I know they haven't been done right and I'd love to accept pull requests for peoples suggestions on how they could be done better, but without a community around the app to do such a thing, it would be wildly irresponsible for me to open source a project, that I myself don't have time to fix, that I'm still publically allowing people to use.

At least if there is a vulnerability, it's made a hell of a lot harder to find. And I know security via obsecurity is bad but security via throwing your source code out there and not fixing any issues is also bad! Btw, if anyone wants to maintain or help me on this project. I'm all about that hit me up on contact@seanodonnell.co.uk

## Conclusion

So yes, StreamUpdater. I never fully killed it off, but I've got some new ideas and think I'll give it another go to see if people want to use it. I think the hardest part has been that it's always been in active development so it's always been a bit of a uphill battle retaining users. But now I have a suitable product that I've actually tested I'll work offline for a bit and get something worth releasing as a suitable v1.1. I'm rather happy with how it works at the moment for it to be considered a Version 1.

It'll update your stream title and game with whatever content you want to throw in there, and even log messages, has a chat bot and loyalty system. It integrates with Spotify and even allows you to do song requests via youtube. It's jank and I'd like to improve it. But it works that's the important thing.... if it doesn't... err let me know :)