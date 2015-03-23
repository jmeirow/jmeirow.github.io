---
layout: post
title:  "Working with the Dropbox Datastore API in iOS using Xamarin"
date:   2015-01-29 19:33:59
categories: ios C#
---


The Background...
==============

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



Getting Started
===============

For an app to use the Dropbox APIs, several things have to happen.  I'll list them in a second, but be warned that this is *my understanding*, which is not necessarily 100% correct, because if it were, I'd probably be writing my app and not this blog post.

1. Obtain a Dropbox developer account at <https://www.dropbox.com/developers>.
2. Register your app with Dropbox on the "App Console" page.
3. Write the code in your app so that at runtime, it prompts the user to supply their Dropbox credentials order for your app to access their data. Included in this code you write is the passing of the "App key" and "App secret" assigned by Dropbox to your application.

Let's take a closer look at items 2 and 3 above. Note: For demonstration purposes, I have created a sample app with the same name as my Twitter handle: *motownjoe*.
 

<div style='text-align:center; border-style:solid; border-color:gray;margin-top:25px; margin-bottom:25px'>
<img src='/images/appconsole.png'  />
</div>
 

Clicking on the "Create app" button leads to this page.  If you're doing moble app development with Dropbox, you'll almost certainly want to choose "Dropbox API app" Once you click on "Dropbox API app" you're presented with another choice:  "Files and Datastores" or "Datastores only".  If you're not quite sure what to choose at this point, choose "Files and datastores".



 
<div style='text-align:center; border-style:solid; border-color:gray;margin-top:25px; margin-bottom:25px'>
<img src='/images/create2.png' />
</div>

 
Finally you'll arrive at the "details" page which of course contains details about your app:<br/>
 


<div style='text-align:center; border-style:solid; border-color:gray;margin-top:25px; margin-bottom:25px'>
	<img src='/images/details.png'  />
</div>

On this last page, notice the two items "App key" and "App secret"? These will come into play very soon.  Now that we have our Dropbox environment (mostly) setup, it's time to fire up Xamarin. Let's choose a "New Solution" and then under "iOS" >> "Unified" >> "iPhone", choose "Single View Application". 
 

<div style='text-align:center; border-style:solid; border-color:gray;margin-top:25px; margin-bottom:25px'>
	<img src='/images/newsolution.png'  />
</div>


This is where things start getting a little sketchy for me, but let's forge ahead, shall we? So Xamarin has generated for us a nice, blank project (below):




<div style='text-align:center; border-style:solid; border-color:gray;margin-top:25px; margin-bottom:25px'>
	<img src='/images/blankproj.png'  />
</div>

Not knowing where to go or what to do next, I did what any developer in a pinch does, turn to the web. The problem I ran into is that the documentation from both Dropbox and Xamarin leave me feeling underwhelmed. The Dropbox examples are in Objective-C using XCode but that's not the biggest problem.  The biggest problem, at least for me, is that the documentation feels like it's targeted toward developers that don't actually need the documentation.  I would much rather read documentation that is too basic, than too cryptic. I can skim ahead of stuff I know, but if it's over my head to start with and then gets more difficult to follow, that doesn't help me at all. I was really hoping to find a step by step tutorial that assumes nothing and shows everything. Alas, I may have to make it myself as I could not find one. 

Still, let's take a look and maybe going slow enough to write this blog post at the same time, perhaps it will now make sense. I first began by Googling "Xamarin dropbox datastore"



<div style='text-align:center; border-style:solid; border-color:gray;margin-top:25px; margin-bottom:25px'>
	<img src='/images/comp-store.png'  />
</div>

I learned that Xamarin has a component for Dropbox in their Component Store. By right-clicking on the "Component" entry in the solution explorer, I could choose "Get More Components", which launched the Component Store.




<div style='text-align:center; border-style:solid; border-color:gray;margin-top:25px; margin-bottom:25px'>
	<img src='/images/dropboxcomponent.png'  />
</div>



The webpage at <https://components.xamarin.com/view/dropboxsync> brings us to this example code and explanation:



<div style='text-align:center; border-style:solid; border-color:gray;margin-top:25px; margin-bottom:25px'>
	<img src='/images/code1.png'  />
</div>

...which I dutifully copy into my AppDelegate.cs file.

Next, the Dropbox website tells me that I need to add an entry to the info.plist file. Admittedly, I don't know much about iOS programming, but it seems to me that info.plist is a file that holds configuration infomation, similar to the App.config or a web.config file in a Microsoft.NET proect.

<div style='text-align:center; border-style:solid; border-color:gray;margin-top:25px; margin-bottom:25px'>
	<img src='/images/plist.png'  />
</div>



<div style='text-align:center; border-style:solid; border-color:gray;margin-top:25px; margin-bottom:25px'>
	<img src='/images/KeyAndSecretInCode.png'  />
</div>



