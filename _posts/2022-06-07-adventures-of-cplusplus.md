---
title: Adventuring into C++
date: 2022-06-07 13:24:00 +0000
categories: [development]
tags: 
- C++
- CPlusPlus
- beginners c++
- starting C++
- Adventures of C++
---

# Intro

Today I'm going to be summing up at the moment how my C++ adventures are going. One thing that you can always bet on, is that as soon as I have annual leave or some kind of holiday, about 6 hours in I'll get bored and want to do something programming related. In a bid to try avoid anything involving work this week, I bought a course on Udemy regarding C++. It's something I've never hidden in that I do want to get into game development within some capcity. I feel like whenever I play games I have some great ideas, or run into bugs I'm sure I'd love to fix. Unfortunetly, being the self taught variety of programmer, it means I've never really understood the appropriate name for things. I was using OOP before I even knew what it was. I didn't even know what OOP stood for before I was comercially deploying features and bug fixes.

I've understood code, and read code, it's how I've gotten to where I am, by hitting breakpoints and debugging what something does. I suppose it's the reverse order of what most people do, but it's why I think I'm pretty decent at bug fixing and working things out! It's also why I think, once I understand the syntax any language is possible given enough determination, I suppose that's the same for nearly everybody! You can master anything, given enough time. (Except any egg eating competitions, sadly I'm allergic)


## So where now?

Now that I've been developing in PHP for some time. To be honest I love the language, and I can find so many uses for it. It's rather easy to create projects and such when all you need to do is tell folk to go to an address. C++ on the other hand, hmm not so much. Say I wanted to create StreamUpdater but within C++. Really what would the purpose of that be? The Website is fantastic place where you can edit things all rather easily, in C++ I'd likely have to make a desktop app. Then you need to think about syncing settings aswell, sure I could have a Web API for that, but then if I'm creating Web Services I might aswell just keep it all on the web? Perhaps there's a benefit to creating a Desktop App. I know there's plenty that would prefer it, even just for the performance uplift, I've not been too bothered about things like that though, especially when you know your market. The people most likely to use something like a Stream Updater aren't going to be on low power machines, if they are, then chances are they won't be streaming for much longer if their quality isn't the best. Who knows, plenty of people have broken through with their scufffed-ness.

## Offtrack

Anyway, we're getting offtrack. The main purpose of me wanting to learn C++ was one of just wanting to be able to read it in a more understanding way. Also, plenty of the concepts involved in C++ actually infiltrate many other languages. As I said before with OOP or Inheritance, variables, constants they all are present in something like a PHP. So I've no doubt really that picking up C++, would actually also broaden my understanding of how things work in PHP. Oddly enough I can't actually think of any projects I'd like to do in C++ that doesn't involve some part of Game Development. The issue with Game Development is my mind is always shooting for the stars. 

## Stars shot and missed

You can always count on me to start a very ambitious project. For a start I was trying to create an MMORPG. (I know, everyone does this), very quickly I ran into some massive uphil battles.

- How on earth do I create a dedicated server
- How on earth can I trust what the client sends me
- Inventory management, what Database do I use for that??
- Hacks, Cheats, bad people are at the forefront of decisions

Just on the subject of hackers and cheaters. It has to be at the forefront of your decision making, which plenty of AAA studios tend to neglect. I'm sure your all aware of when New World launched plenty of exploits were quickly found due to development decisions taken when the game was first being built. Something like that, you don't want to get 1 year into a project and it turns out you need to do everything differently or account for it through hacks and sloppy-ness in the code. Ouch!

I actually created a pretty decent loading screen, but it was based on my prior knowledge that I did it on...

I had a loading screen, whereby you would pick a name, class, some customization options then create the character. What that would then do is send a POST request to a API that would then do all the validation and everything else. The data would then be stored in a database. Of course this was a laravel backend.

But my question was. Is this correct? Surely not. Surely Blizzard isn't doing a POST request to an accounts.blizzard.eu are they? Perhaps they are, but that's why I want to get involved in learning, perhaps the concepts I know in PHP don't apply to things like C++ or an architecture where you have a dedicated server. Surely there's another protocol or call I can do server side to create these things. Things like UDP traffic for tracking what players are doing in the world, would a UDP packet create the account some how? I have no idea! 

If anyone has any suggestions for books that might answer these questions or talks let me know! I Always attend the Eurovision talks on Game Development, they're always very insightful and interesting. However they do tend to lead a bit heavy on the marketing. 

## Conclusion

Anyway, as I was saying. Bored on my holidays so now I've ventured 6 chapters into a C++ course and I'm enjoying it very much! So far the start has been a lot of what I already know via PHP, but I'm picking up the terms and it seems very easy. I suppose my questions are... when do I stop making console C++ applications and how hard am I going to hit my head when creating a GUI?

Still need to figure out an appropriate C++ project though. I'm doomed if I don't have some way to channel the learning into something I actually want to make. But who needs C++ apps these days? Is there anywhere people have requests or something? I don't mind making some open source software for folks that need it. I created a simple CRM (https://zodazn.com) for anyone not wanting to pay through the nose for the others out there.

Any thoughts, hit my inbox contact@seanodonnell.co.uk