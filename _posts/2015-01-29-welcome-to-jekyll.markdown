---
layout: post
title:  "Xamarin, Dropbox Datastore and Me"
date:   2015-01-29 19:33:59
categories: ios C#
---


I had an idea for an app but then again, who hasn't?  As a Mac and iPhone owner of several years my target platform was already decided. My app needs the ability to sync structured information between devices and desktop computers, including eventually Windwows, Android, etc. 
 
In the past, I have "experimented" with XCode and Objective C. Frankly, it's a match made in heaven: a hideous language married to a terrible IDE. (Have I offended you yet).  When Apple launched Swift in the summer of 2014, I "heard about it" fairly quickly, but did not look into it at all. A month or two ago I dove into it more deeply and I was *really* impressed with the language, the lack of any sort if IO support into the language was a little disappointing. 

I'll probably revisit Swift sometime down the road, but I need to get moving on my app and so I made a decision, but my decision has lead me to an obstacle that I've not yet been able to overcome. 

I decided to use the Xamarin development tools because:

- I already know C# from my job
- Xamarin allows me to target iOS, Mac OS X and Android
- I can take the same C# and with little modification create a Windows version of my application.

The next big decision was synchronizing the data between devices and for this I chose Dropbox because:

- they're a leader in this space
- the price was right

Things got off fairly well with Xamarin. Although most developers probably run it as a Visual Studio plugin, I actually use the Xamarin Studio IDE on my Mac and found it quite nice, in some ways even better than Microsoft Visual Studio. Then again, depending on your perspective, that's not necessarily a tough target to hit.

It took me a while to get the hang of the iOS event model and it's notion of MVC, which is more like ASP.NET webforms than MVC, if you ask me, but 








