---
layout: post
title: Chrome chrome.alarms API for Scheduled Tasks
description: Learn how to use the chrome.alarms API to schedule recurring tasks and timed events in your Chrome extensions.
date: 2026-01-15
categories:
- extensions
- development
tags:
- chrome-alarms
- scheduled-tasks
- chrome-extensions
- development
author: theluckystrike
last_modified_at: '2026-03-12'
permalink: /articles/chrome-chrome.alarms-scheduled-tasks/
---

# Chrome chrome.alarms API for Scheduled Tasks

If you are building a Chrome extension that needs to perform actions at specific times or intervals, the **chrome.alarms API** is exactly what you need. This powerful API allows you to schedule tasks to run in the future, either once or repeatedly. Whether you want to refresh data periodically, show notifications at certain times, or automate background tasks, the chrome.alarms API provides a reliable way to handle scheduled operations in your extension.

## What is the chrome.alarms API

The **chrome.alarms API** is a Chrome extension API that lets you schedule code to run at specific times or at regular intervals. It is similar to using setTimeout or setInterval in regular JavaScript, but with some important advantages. Unlike regular JavaScript timers that can be throttled when tabs are in the background, chrome.alarms is designed to work reliably in the context of browser extensions, even when the browser is not actively being used.

This API is particularly useful for extensions that need to perform background tasks. For example, you might want to check for new emails every 15 minutes, display a reminder at a specific time, or sync data with a server at regular intervals. The chrome.alarms API handles all of this in a way that is efficient and respects system resources.

## Getting Started with chrome.alarms

Before you can use the chrome.alarms API, you need to declare it in your extension's manifest file. If you are using Manifest V3, which is the current standard, you will need to add the "alarms" permission to your manifest. Here is how it looks in your manifest.json file.

You would add "alarms" to the permissions array. Once you have done that, you can start using the API in your extension's background script or service worker.

The basic workflow involves creating an alarm, then listening for it to fire. When an alarm fires, your extension receives an event that you can handle to perform whatever action you need.

## Creating Alarms

There are two main ways to create an alarm using the chrome.alarms API. The first is to create an alarm that fires once at a specific time in the future. The second is to create a repeating alarm that fires at regular intervals.

To create an alarm, you use the chrome.alarms.create method. This method takes two arguments: a name for the alarm and an object that specifies when it should fire. For a one-time alarm, you can set the delayInMinutes property to specify how many minutes from now the alarm should fire.

For a repeating alarm, you use the periodInMinutes property instead. This tells Chrome to fire the alarm repeatedly at the specified interval. For example, if you set periodInMinutes to 60, the alarm will fire every hour.

You can also give each alarm a unique name. This is useful if you need to manage multiple alarms in your extension. By giving each alarm a distinct name, you can update or cancel specific alarms without affecting others.

## Handling Alarm Events

Creating an alarm is only half of the equation. You also need to handle the event when the alarm fires. You do this by adding a listener for the onAlarm event in your background script.

When the alarm fires, the listener receives an Alarm object that contains information about the alarm that triggered. This includes the name of alarm, when it was scheduled to fire, and the period if it is a repeating alarm. You can use this information to determine what action to take.

Inside your event listener, you can perform any action that your extension needs. This might include sending a notification to the user, making a network request to fetch new data, updating local storage, or communicating with other parts of your extension using message passing.

## Managing Alarms

The chrome.alarms API provides several methods for managing alarms beyond just creating them. You can query existing alarms to find out what alarms are currently scheduled, get details about a specific alarm, update an alarm's schedule, or cancel an alarm when it is no longer needed.

To query all active alarms, you use the chrome.alarms.getAll method. This returns an array of all alarms that are currently scheduled in your extension. You can use this information to display the status of scheduled tasks to users or to make decisions about creating new alarms.

To cancel a specific alarm, you use the chrome.alarms.cancel method, passing in the name of the alarm you want to cancel. This is useful when users disable a feature in your extension or when a certain condition is met that makes the alarm unnecessary.

You can also update an existing alarm by creating a new alarm with the same name. This effectively replaces the old alarm with a new one, allowing you to change the timing or interval without having to cancel and recreate the alarm manually.

## Practical Use Cases

There are many practical applications for the chrome.alarms API in Chrome extensions. Here are some common use cases that demonstrate its versatility.

One of the most common uses is for **periodic data synchronization**. If your extension syncs with a server or external service, you can use chrome.alarms to trigger synchronization at regular intervals. This keeps the user's data fresh without requiring them to manually refresh.

Another common use is for **reminders and notifications**. You can schedule alarms to fire at specific times to remind users about tasks, upcoming events, or important deadlines. The alarm handler can then display a notification using the chrome.notifications API.

You can also use chrome.alarms for **tab management automation**. Extensions that help users manage their tabs can use alarms to automatically close or suspend tabs after a period of inactivity. This is similar to how **Tab Suspender Pro** works, which uses scheduled checks to identify and suspend idle tabs to save memory and improve browser performance.

Extensions that monitor websites for changes can also benefit from chrome.alarms. You can set up periodic checks to fetch web pages and compare their content against previously stored versions, alerting users when changes are detected.

## Best Practices

When using the chrome.alarms API, there are some best practices you should follow to ensure your extension works reliably and efficiently.

First, be mindful of the minimum interval you use. Chrome imposes a minimum period of approximately one minute for repeating alarms. If you need to check more frequently than that, you might need to reconsider your approach or accept that some checks might be delayed.

Second, always handle the case where your alarm fires but the required data or resources are not available. For example, if your alarm is supposed to sync data but the user is offline, your code should gracefully handle that situation and try again later.

Third, clean up alarms when they are no longer needed. If a user disables a feature in your extension, cancel the associated alarms to prevent unnecessary processing and improve resource efficiency.

Finally, test your alarm code thoroughly. Alarms can behave differently depending on whether the browser is running, whether the extension is enabled, and whether the computer is asleep. Make sure your extension handles all these scenarios correctly.

## Conclusion

The **chrome.alarms API** is an essential tool for Chrome extension developers who need to schedule tasks or perform actions at specific times. It provides a reliable way to handle timed events in your extension, whether you need one-time notifications or recurring background tasks. By understanding how to create, handle, and manage alarms, you can build more powerful and useful extensions that work seamlessly in the background.

Combined with other Chrome APIs, chrome.alarms opens up a wide range of possibilities for extension functionality. Whether you are building a productivity tool, a notification system, or an automated tab manager like **Tab Suspender Pro**, the ability to schedule tasks reliably is a valuable feature that enhances the user experience.

## Related Articles
* [chrome extensions for screenshot full page](/articles/chrome-extensions-for-screenshot-full-page/)
* [Chrome Multiple Users Same Computer Setup](/articles/chrome-multiple-users-same-computer-setup/)
* [chrome for google translate extension tips](/articles/chrome-for-google-translate-extension-tips/)

Built by theluckystrike — More tips at [zovo.one](https://zovo.one)
