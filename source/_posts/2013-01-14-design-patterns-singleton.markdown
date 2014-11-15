---
author: mariostallone
comments: true
date: 2013-01-14 08:05:04+00:00
layout: post
slug: design-patterns-singleton
title: Design Patterns - Singleton
wordpress_id: 126
categories:
- Design Patterns
- Technology
- Tips
tags:
- design patterns
- good code
- java
- objective c
- patterns
- programming
- singleton
- technology
---

Here's my second post on Design Patterns. So, this post is going to throw some light on the Singleton Patterns.

<blockquote>In software engineering, the **Singleton Pattern** is a design pattern that restricts the instantiation of a class to one object</blockquote>

So one might wonder why would you need to implement a Singleton?
There are many scenarios where we'd rather have just one instance of a particular class.
For eg.
	
  * The class which instantiates the DB connection
  * It can be used as a replacement to a Global Variable

Here are some of the advantages of using a Singleton
	
  * Only one instance of the class will exist
  * This saves up on memory
  * Allows one to share data amongst classes without actually passing around objects

Here are a few examples where you must have used a Singleton

{% codeblock lang:java linenos:false %}
Runtime.getRuntime().exec(new String[] {"echo", "Hello, world!"});
{% endcodeblock %}

{% codeblock lang:objc linenos:false %}
[UIApplication sharedApplication].delegate;
{% endcodeblock %}

Here's an implementation of the **Singleton** Pattern in Java

{% codeblock lang:java Singleton.java %}
public class Singleton
{
	private static Singleton instance;
	private Singleton()
	{
	}
	public static synchronized Singleton getInstance()
	{
		if(instance==null)
		{
			instance=new Singleton();
		}
		return instance;
	}
}
{% endcodeblock %}

And here'a an implementation in Objective C

{% codeblock lang:objc Singleton.h %}
#import <Foundation/Foundation.h>

@interface Singleton : NSObject

+(id)sharedInstance;

@end
{% endcodeblock %}

{% codeblock lang:objc Singleton.m %}
#import "Singleton.h"

static id _sharedInstance;

@implementation Singleton

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

+(id)sharedInstance
{
    return _sharedInstnace;
}

@end
{% endcodeblock %}

So thats how you make use of Singletons. This is one Design Pattern you will use on a regular basis.
Will update this article with more samples and issues related to thread safe creation of singletons.

EDIT : Added a slightly better way to manage Singletons in Objective C. A more detailed explanation and variations to this can be found in the next post.
