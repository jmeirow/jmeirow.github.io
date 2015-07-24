---
layout: post
title: Software Configuration - How, Why and WHERE.
category: software

excerpt: Software Configuration

---

### Software Configuration

This is the first of a two-part post on software configuration. This post will discuss configuration in a more general manner 
while the next will get into some platform-specific techniques.

At the highest level, configuration is divided into two broad categories and though I've scoured the Internet looking for 
"official terminology", I've not found any so I'll simply refer to them as "behavioral" and "environmental" configurations. 
 

#### Behavioral Configurations  (the "what" and the "when")

Behavioral configurations, as you might expect, direct a program on how to behave with respect to certain capabilities of the application. 
For example, an accounting system might have a configurations to indicate whether a client uses the cash or the accrual method of accounting.
In an example like this, the end user is actually setting the configuration through the application. In other scenarios it might be a 
developer or other IT professional that is controlling the configuration. Other examples of behavioral configuration might include:

* how many lines of information to display on a page (what)
* when a customer's order exceeds (some threshhold), apply a discount (when)


It is not uncommon for "batch" or "background" processes have more behavioral configurations controlled by IT staff in a "config" file
because there is no user interface through which end users can manage them.


#### Environmental (External) Configurations

It is rather rare that software does not deal with data in one form or another.  Programs can communicate with any number of sources: 

* file systems
* databases 
* web services
* message queues
* email

These the collection of these resources, external to the executing code define the environment in which it oeprates.

As any developer knows, it's imperative to know that during development the program is operating only with development resources. Once the code
is moved to a testing environment, again, the code should only operate against resources considered to be part of the test environment, and so on, 
extending to the production environment.

One of the goals of configurations is to eliminate the need to for the "move and change" approach to promoting software to a new environment.  
By "move and change", I mean where a program is moved, say from development to test, and along with the executable(s), a configuration file 
(or files)



I'm going to say something here and it may come off as inflamatory, but I assure you it's not intended as such. Rather is simply an observation
I've made over time and admitedly the "sample size" is not scientifically sound. So, here it goes. 





















