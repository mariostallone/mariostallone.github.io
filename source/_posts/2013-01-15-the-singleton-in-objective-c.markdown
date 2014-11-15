---
author: mariostallone
comments: true
date: 2013-01-15 06:19:13+00:00
layout: post
slug: the-singleton-in-objective-c
title: The Singleton in Objective C
wordpress_id: 157
categories:
- iOS Programming
- Technology
- Tips
tags:
- design partterns
- objective c
- objectivec
- programming
- singleton
---

In my previous [post](http://mariostallone.com/blog/2013/01/14/design-patterns-singleton/) I had mentioned a code example on how to write a Singleton in Objective C. I had a friend ask me, what would happen when I call an alloc init over my Singleton?

This got me thniking, so I did my fair share of research on the topic, and came up with a few conclusions.
There is no way to restrict the calling of the init method(like in Java). But, we still want to maintain only one instance. Of course, the easiest solution would be, just to remember that we are using a Singleton :-) But, often enough this is not the case, and when working in large teams, theres always a chance of making a mistake. So here are two methods by which we can ensure the creation of one and only one instance of the class
        
  * Restrict creation of another object of the same class	
  * Raise an exception when an unnecessary retain or release call is encountered

**Restricting the creation of another object**
My code would have to be modified by adding another method...
{% codeblock lang:objc Singleton.m %}
#import "Singleton.h"

@implementation Singleton

static id _sharedInstnace;

+(void)initialize
{
    static dispatch_once_t onceToken;
    dispatch_once(&onceToken, ^{
        if(_sharedInstnace==nil)
        {
            _sharedInstnace = [[self alloc]init];
        }
    });
}

+(id)allocWithZone:(NSZone *)zone
{
    if(_sharedInstnace==nil)
    {
        _sharedInstnace = [super allocWithZone:zone];
    }
    return _sharedInstnace;
}

+(id)sharedInstance
{
    return _sharedInstnace;
}

@end
{% endcodeblock %}

The _allocWithZone:_ method is what allocates memory to the object. Hence overriding this to point it back to the same object will prevent other instances of the object from being created.
This of course, ensures that, when a developer calls _alloc init_ on the class, the same instance is returned. This makes the developer oblivious to the fact that he/she is using a Singleton. 
If we want to be mindful of our actions, Id suggest the next option.

**Raising an exception when an unnecessary retain is called**
{% codeblock lang:objc Singleton.m %}
#import "Singleton.h"

@implementation Singleton

static id _sharedInstnace;

+(void)initialize
{
    static dispatch_once_t onceToken;
    dispatch_once(&onceToken, ^{
        if(_sharedInstnace==nil)
        {
            _sharedInstnace = [[self alloc]init];
        }
    });
}

+(id)allocWithZone:(NSZone *)zone
{
    if(_sharedInstnace!=nil)
    {
        [NSException raise:@"Explicit Object Creation not allowed" format:@"%@ is a Singleton",[self class]];
    }
    _sharedInstnace = [super allocWithZone:zone];
    return _sharedInstnace;
}

+(id)sharedInstance
{
    return _sharedInstnace;
}

@end
{% endcodeblock %}

This way you would have an exception raised every time you try to instantiate a Singleton

Notice, that in both these snippets, I have left the Object creation to a new method 
{% codeblock lang:objc %}
+(void)initialize.
{% endcodeblock %}
From the Developer Library...


{% blockquote %}
The runtime sends initialize to each class in a program exactly one time just before the class, or any class that inherits from it, is sent its first message from within the program. (Thus the method may never be invoked if the class is not used.) The runtime sends the initialize message to classes in a thread-safe manner. Superclasses receive this message before their subclasses.
{% endblockquote %}



So by calling this method to create our Singleton's instance, we make sure we call it only when the Class is first called.

And _dispatch_once_ ensures that any code within this block is executed only once
