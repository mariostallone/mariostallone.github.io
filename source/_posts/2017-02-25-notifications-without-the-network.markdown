---
layout: post
title: "Notifications without the Network"
date: 2017-02-25 18:00
comments: true
categories: [General, Technology, Android]
---
__A Push Notification is a message (read data), that’s sent from a remote server to a connected device__

Most of you who have had to deal with Push Notifications (GCM, etc.) would have come across how reliable they are. I stress on them not being reliable, primarily because of the way we (read India, other developing nations) use our data. A whopping 50%+ of our Internet Janta, do not have their data on through the day. Without data, there’s no way to reach a device, and hence notifications never reach a huge chunk of our customer base.

*Don’t we all have that friend recommending to us to turn off data, when we don’t need it, and use it only when we need to!*

__How do we effectively reach a message out to our users, when their data is turned off most of the time?__

Enter Scheduled Notifications. What if we can schedule a notification on a user’s device, provided we know of an event much in advance. By doing so, at the designated time, we can pop the notification to our user, delivering to them whatever message we intended to.
Every Android device ships with an AlarmManager, that well, schedules tasks to be run at a specified time. We took the capability of push — which is to send data to a device, and the capability of the AlarmManager to schedule a task at a specified interval. We send data over the wire, a few hours, or even days in advance, listen on this data and then set alarms to fire off notifications on the device. This way, we are able to reach out to our users at the designated time.
The only caveat is that we need to know of an event much in advance. We can only hope and pray that battery woes and data woes slowly cease to exist, to solve this problem for good.

While we were building this, we had to also take care of de-duplication, to ensure that the same message when sent as an instant push and a scheduled notification do not pop up together as separate notifications on a users’ tray. So we went ahead and built a system on the device to keep track of previous notifications, and we effectively de-duped notifications.

Now, since we have a system to effectively handle notifications on the device, we took it a step further and added rules to configure how many notifications a user could receive on the device. We could add these rules by classifying notifications by type, etc. You might wonder, why would we add all that logic on a device, when we should effectively be doing this on our servers. Well, we’ve learned the hard way, that we cannot always be too sure of these systems working flawlessly, we never know when they can go berserk due to an unforeseen error. So, we’ve built our apps to be extra careful in such situations.

GCM, (now FCM) supports Notification messages and Data messages. This flexibility to handle the notification, comes only when you send a notification as a data message. Just ensure that you do not spend too much time in the background. Get your work done and exit as soon as you can.
The advent of Jio has led telcos to heavily reduce the cost of data. We can only hope that user’s stop being over-protective of their data usage.