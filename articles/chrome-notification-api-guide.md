---
layout: post
title: Chrome Notification API Guide
description: Learn how to use the Chrome Notification API for web and extension development. Master push notifications, permission requests, notification actions, and bad...
date: '2026-03-11'
last_modified_at: '2026-03-11'
permalink: chrome-notification-api-guide
categories:
- development
- extensions
- api
tags:
- chrome-notifications
- push-api
- web-development
- chrome-extensions
- browser-api
author: theluckystrike
last_modified_at: '2026-03-11'
permalink: chrome-notification-api-guide
---
# Chrome Notification API Guide

The Chrome Notification API is a powerful tool that enables developers to engage users even when they are not actively using your website or extension. Whether you need to deliver real-time updates, remind users about important events, or simply enhance user engagement, understanding how to properly implement notifications in Chrome is essential for modern web and extension development.

This comprehensive guide will walk you through everything you need to know about the Chrome Notification API, from requesting permissions to implementing advanced features like notification actions and badges. By the end of this article, you will have the knowledge and practical examples needed to integrate notifications into your projects effectively.

## Understanding the Chrome Notification API

The Chrome Notification API, part of the broader Web Notifications standard, provides a way for web pages and extensions to display system notifications to users. These notifications appear in the operating system's notification center, making them visible even when the browser is minimized or running in the background.

Chrome supports two distinct notification systems. The first is the Web Notifications API, which works on web pages and requires user permission for each origin. The second is the chrome.notifications API, which is specifically designed for Chrome extensions and offers additional features and capabilities.

For web developers, the Web Notifications API follows the W3C standard, making it compatible across different browsers. However, Chrome has extended this API with several useful features that give developers more control over notification behavior and appearance.

For extension developers, the chrome.notifications API provides a more robust set of features, including support for notification actions, icons, and persistent notifications that can remain visible until the user dismisses them. This API does not require the same permission workflow as web notifications since users must explicitly grant permission to install an extension.

## Requesting Notification Permissions

Before you can display any notifications to users, you must first request and obtain their permission. This is a critical step that respects user privacy and gives users control over which sites and extensions can send them notifications.

### Requesting Permission on Web Pages

For web pages using the Web Notifications API, you request permission using the Notification.requestPermission() method. This method returns a Promise that resolves with the user's choice, which can be "granted", "denied", or "default".

Here is a practical example of how to request notification permissions in your web application:

```javascript
function requestNotificationPermission() {
  if (!('Notification' in window)) {
    console.log('This browser does not support notifications');
    return;
  }

  Notification.requestPermission().then(permission => {
    if (permission === 'granted') {
      console.log('Notification permission granted');
      // You can now create notifications
    } else if (permission === 'denied') {
      console.log('Notification permission denied');
    } else {
      console.log('Notification permission default (dismissed)');
    }
  });
}

// Call this function when user interacts with your page
document.getElementById('enable-notifications').addEventListener('click', requestNotificationPermission);
```

It is important to note that browsers typically block notification permission requests that are not triggered by a user action, such as a click or tap. This prevents websites from spamming users with permission prompts when they first load a page. Always ensure your permission request is tied to a clear user action, like clicking a button to subscribe to notifications.

### Checking Current Permission Status

Before requesting permission, it is good practice to check the current permission status. This allows you to avoid showing redundant prompts to users who have already denied or granted permission:

```javascript
function checkNotificationPermission() {
  if (!('Notification' in window)) {
    return 'unsupported';
  }
  
  return Notification.permission;
}

// Usage
const currentPermission = checkNotificationPermission();
if (currentPermission === 'granted') {
  // User has already granted permission
  console.log('Notifications are already enabled');
} else if (currentPermission === 'denied') {
  // User has explicitly denied permission
  console.log('Notifications are blocked');
} else {
  // Permission not yet determined or dismissed
  console.log('Need to request permission');
}
```

### Extension Permission Requirements

For Chrome extensions, you need to declare the "notifications" permission in your manifest file. This permission is required regardless of whether you use the chrome.notifications API or the standard Web Notifications API within your extension:

```json
{
  "manifest_version": 3,
  "name": "My Notification Extension",
  "version": "1.0",
  "permissions": [
    "notifications"
  ]
}
```

Unlike web pages, extensions do not need to request runtime permission from users because installing the extension itself serves as consent. However, users can still disable notifications for specific extensions through Chrome's settings if they choose to do so.

## Creating Basic Notifications

Once you have obtained the necessary permissions, you can start creating notifications. The implementation differs slightly between web pages and extensions.

### Creating Notifications on Web Pages

For web pages, you create notifications using the Notification constructor:

```javascript
function showNotification(title, options) {
  if (Notification.permission !== 'granted') {
    console.log('Cannot show notification: permission not granted');
    return;
  }

  const notification = new Notification(title, {
    body: 'This is the notification body text',
    icon: '/images/notification-icon.png',
    badge: '/images/badge-icon.png',
    tag: 'unique-notification-id',
    requireInteraction: false,
    vibrate: [200, 100, 200]
  });

  notification.onclick = function() {
    window.focus();
    this.close();
  };

  notification.onclose = function() {
    console.log('Notification closed');
  };
}

// Example usage
showNotification('New Message', {
  body: 'You have received a new message from John',
  icon: '/images/message-icon.png'
});
```

The Notification constructor accepts a title string and an options object that can include properties like body for the main text, icon for a small image displayed with the notification, badge for a small image shown when notifications accumulate, tag for grouping similar notifications, and requireInteraction to keep the notification visible until the user interacts with it.

### Creating Notifications in Extensions

For Chrome extensions using the chrome.notifications API, the creation process is slightly different:

```javascript
function showExtensionNotification() {
  chrome.notifications.create(
    'notification-id-1', // A unique identifier
    {
      type: 'basic',
      iconUrl: '/images/extension-icon.png',
      title: 'Extension Notification',
      message: 'This is a notification from your extension',
      priority: 1,
      eventTime: Date.now() + 5000 // Shows a progress indicator
    },
    function(notificationId) {
      if (chrome.runtime.lastError) {
        console.error('Error creating notification:', chrome.runtime.lastError);
      } else {
        console.log('Notification created with ID:', notificationId);
      }
    }
  );
}
```

The chrome.notifications API supports several notification types including basic for simple text and icon notifications, image for notifications with a larger image, list for notifications with multiple items, and progress for notifications showing a progress bar.

## Implementing Notification Actions

Notification actions allow users to interact with notifications without opening your website or extension. This feature significantly enhances user engagement by enabling quick responses directly from the notification itself.

### Actions in Web Notifications

The Web Notifications API supports basic actions through the actions property in the notification options:

```javascript
const notificationWithActions = new Notification('New Task Assigned', {
  body: 'You have been assigned a new task: Review the quarterly report',
  icon: '/images/task-icon.png',
  actions: [
    { action: 'view', title: 'View Task' },
    { action: 'complete', title: 'Mark Complete' },
    { action: 'dismiss', title: 'Dismiss' }
  ],
  data: {
    taskId: 12345,
    dueDate: '2026-01-25'
  }
});

notificationWithActions.addEventListener('actionclick', function(event) {
  event.notification.close();
  
  if (event.action === 'view') {
    // Open the task in your application
    window.open('/tasks/12345', '_blank');
  } else if (event.action === 'complete') {
    // Mark the task as complete
    completeTask(12345);
  }
  // 'dismiss' action closes the notification automatically
});

notificationWithActions.addEventListener('close', function() {
  console.log('Notification was closed');
});
```

Note that Chrome limits the number of actions you can display to three. If you specify more than three actions, Chrome will only show the first three. Additionally, the appearance of actions may vary across different operating systems.

### Actions in Extension Notifications

Chrome extensions have more flexibility with notification actions through the chrome.notifications API:

```javascript
chrome.notifications.create(
  'reminder-notification',
  {
    type: 'basic',
    iconUrl: '/images/reminder-icon.png',
    title: 'Daily Reminder',
    message: 'Time to check your progress for today',
    buttons: [
      { title: 'View Progress' },
      { title: 'Snooze' }
    ],
    priority: 1
  },
  function(notificationId) {
    console.log('Reminder notification created');
  }
);

// Handle button clicks
chrome.notifications.onButtonClicked.addListener(function(notificationId, buttonIndex) {
  if (notificationId === 'reminder-notification') {
    if (buttonIndex === 0) {
      // View Progress button clicked
      chrome.tabs.create({ url: '/progress.html' });
    } else if (buttonIndex === 1) {
      // Snooze button clicked - reschedule for later
      setTimeout(showSnoozeNotification, 15 * 60 * 1000); // 15 minutes
    }
  }
  chrome.notifications.clear(notificationId);
});
```

Extension notifications also support input fields, allowing users to enter text directly in the notification:

```javascript
chrome.notifications.create(
  'feedback-notification',
  {
    type: 'basic',
    iconUrl: '/images/feedback-icon.png',
    title: 'We Value Your Feedback',
    message: 'How would you rate your experience today?',
    buttons: [
      { title: 'Submit Feedback' }
    ],
    priority: 1
  },
  function(notificationId) {}
);

chrome.notifications.onButtonClicked.addListener(function(notificationId, buttonIndex) {
  if (notificationId === 'feedback-notification' && buttonIndex === 0) {
    // Open a page where users can submit detailed feedback
    chrome.tabs.create({ url: '/feedback.html' });
  }
});
```

## Using Badges for Visual Indicators

Badges provide a lightweight way to show users that there is something new or important without interrupting them with a full notification. Chrome supports badges in several contexts, including extension icons and tab indicators.

### Extension Icon Badges

Chrome extensions can display a badge on their toolbar icon to indicate status or attract attention:

```javascript
// Set the badge text
function updateBadge(count) {
  if (count > 0) {
    chrome.action.setBadgeText({ text: count.toString() });
    chrome.action.setBadgeBackgroundColor({ color: '#FF0000' });
  } else {
    chrome.action.setBadgeText({ text: '' });
  }
}

// Example: Show unread count
updateBadge(5); // Shows "5" on the extension icon

// Clear the badge
updateBadge(0); // Removes the badge
```

The badge text can be up to four characters long. You can also customize the badge background color to match your extension's branding or use different colors to convey different states. For example, you might use red for urgent notifications, green for success states, or blue for informational updates.

Here is a more advanced example showing different badge states:

```javascript
function setBadgeState(state, count) {
  const states = {
    'unread': { color: '#E74C3C', text: count > 99 ? '99+' : count.toString() },
    'success': { color: '#27AE60', text: '✓' },
    'warning': { color: '#F39C12', text: '!' },
    'info': { color: '#3498DB', text: 'i' },
    'clear': { color: '#000000', text: '' }
  };

  const config = states[state];
  chrome.action.setBadgeBackgroundColor({ color: config.color });
  chrome.action.setBadgeText({ text: config.text });
}

// Usage examples
setBadgeState('unread', 42);    // Red badge with "42"
setBadgeState('success', 0);    // Green checkmark
setBadgeState('warning', 0);    // Orange exclamation
setBadgeState('clear', 0);      // Clear the badge
```

### Tab Badges Indicators

You can also use badges to indicate information about specific tabs:

```javascript
// Set badge for a specific tab
function setTabBadge(tabId, hasUnread) {
  if (hasUnread) {
    chrome.action.setBadgeText({ text: '●', tabId: tabId });
    chrome.action.setBadgeBackgroundColor({ color: '#E74C3C', tabId: tabId });
  } else {
    chrome.action.setBadgeText({ text: '', tabId: tabId });
  }
}

// Get the active tab and set badge
chrome.tabs.query({ active: true, currentWindow: true }, function(tabs) {
  if (tabs.length > 0) {
    setTabBadge(tabs[0].id, true);
  }
});
```

## Push Notifications for Real-Time Updates

Push notifications enable you to send messages to users even when your website is not open. This is particularly valuable for maintaining user engagement and delivering timely information.

### How Push Notifications Work

Push notifications in Chrome rely on the Push API, which is built on top of the Service Worker API. When a user grants permission for push notifications, your website can subscribe to push events. The subscription includes an endpoint that your server can use to send push messages to the user.

Here is how to implement push notifications in your web application:

```javascript
// Register a service worker
if ('serviceWorker' in navigator) {
  navigator.serviceWorker.register('/sw.js').then(function(registration) {
    console.log('Service Worker registered:', registration);
    
    // Subscribe to push notifications
    return registration.pushManager.subscribe({
      userVisibleOnly: true,
      applicationServerKey: urlBase64ToUint8Array('YOUR_PUBLIC_VAPID_KEY')
    });
  }).then(function(subscription) {
    // Send subscription to your server
    console.log('Push subscription:', subscription);
    return fetch('/api/subscribe', {
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify(subscription)
    });
  }).catch(function(error) {
    console.error('Push subscription failed:', error);
  });
}

// Helper function to convert VAPID key
function urlBase64ToUint8Array(base64String) {
  const padding = '='.repeat((4 - base64String.length % 4) % 4);
  const base64 = (base64String + padding)
    .replace(/-/g, '+')
    .replace(/_/g, '/');
  const rawData = window.atob(base64);
  const outputArray = new Uint8Array(rawData.length);
  for (let i = 0; i < rawData.length; ++i) {
    outputArray[i] = rawData.charCodeAt(i);
  }
  return outputArray;
}
```

The service worker handles incoming push events:

```javascript
// sw.js - Service Worker
self.addEventListener('push', function(event) {
  const data = event.data ? event.data.json() : {};
  const title = data.title || 'New Notification';
  const options = {
    body: data.body || 'You have a new notification',
    icon: data.icon || '/images/icon.png',
    badge: data.badge || '/images/badge.png',
    tag: data.tag || 'default',
    data: data.data || {}
  };

  event.waitUntil(
    self.registration.showNotification(title, options)
  );
});

self.addEventListener('notificationclick', function(event) {
  event.notification.close();
  
  event.waitUntil(
    clients.openWindow(event.notification.data.url || '/')
  );
});
```

### Considerations for Push Notifications

When implementing push notifications, there are several important considerations to keep in mind.

First, push notifications require a secure context, meaning your site must be served over HTTPS. This is a requirement for both the website and the service worker.

Second, you need to set up a VAPID key pair for authentication. The public key is used on your client side when subscribing, and the private key is used on your server to authenticate push messages.

Third, userVisibleOnly must be set to true in the subscription options. This ensures that every push message results in a visible notification, which is required by most browsers.

Fourth, push notifications do not work when the browser is completely closed on some platforms. They work when the browser is running in the background, which is typically sufficient for most use cases.

## Best Practices for Notification Design

Creating effective notifications requires more than just technical implementation. Following best practices ensures that your notifications are useful rather than annoying.

Always provide clear and concise content. The notification title should be informative but brief, typically no more than 50 characters. The body text should provide enough context for users to understand what the notification is about without having to open it.

Timing is crucial. Avoid sending notifications at inconvenient times, such as late at night or early in the morning, unless they are genuinely urgent. Consider implementing quiet hours or allowing users to set their own notification preferences.

Respect user preferences. If users choose to disable notifications, respect that choice and do not try to work around it. Make it easy for users to manage their notification settings within your application.

Test across platforms. Notifications may appear differently on Windows, macOS, and Linux. Test your notifications on all target platforms to ensure they look and function correctly.

## Practical Example: Building a Notification System

Let me walk you through a complete example of building a notification system for a web application:

```javascript
class NotificationManager {
  constructor() {
    this.permission = Notification.permission;
    this.notifications = new Map();
  }

  async init() {
    if (this.permission === 'default') {
      await this.requestPermission();
    }
    return this.permission === 'granted';
  }

  async requestPermission() {
    this.permission = await Notification.requestPermission();
    return this.permission === 'granted';
  }

  show(options) {
    if (this.permission !== 'granted') {
      console.warn('Cannot show notification: permission not granted');
      return null;
    }

    const id = options.id || Date.now().toString();
    const notification = new Notification(options.title, {
      body: options.body,
      icon: options.icon,
      badge: options.badge,
      tag: options.tag || id,
      requireInteraction: options.requireInteraction || false,
      data: options.data
    });

    notification.onclick = () => {
      if (options.onClick) {
        options.onClick(notification);
      }
      notification.close();
    };

    notification.onclose = () => {
      this.notifications.delete(id);
      if (options.onClose) {
        options.onClose(notification);
      }
    };

    this.notifications.set(id, notification);
    return notification;
  }

  close(id) {
    const notification = this.notifications.get(id);
    if (notification) {
      notification.close();
      this.notifications.delete(id);
    }
  }

  closeAll() {
    this.notifications.forEach(notification => notification.close());
    this.notifications.clear();
  }
}

// Usage
const notifications = new NotificationManager();

async function setupNotifications() {
  const granted = await notifications.init();
  if (granted) {
    notifications.show({
      title: 'Welcome Back',
      body: 'Thanks for using our application',
      icon: '/images/welcome.png',
      onClick: (notification) => {
        console.log('Notification clicked');
      }
    });
  }
}
```

This NotificationManager class provides a clean interface for managing notifications in your application, handling permission requests, and tracking active notifications.

## Managing Tab Resources with Notifications

If you build extensions that deal with multiple tabs or need to manage browser resources efficiently, combining notifications with other Chrome APIs can create powerful user experiences.

For example, **Tab Suspender Pro** demonstrates excellent use of Chrome's notification and badge APIs. This extension automatically suspends inactive tabs to save memory and can notify users when tabs are suspended or when there are issues that require attention. It uses badges to show resource savings and notifications to keep users informed about background activities.

When implementing notifications in your own extensions, consider how they can work alongside other Chrome APIs to provide a seamless user experience. Notifications are most effective when they provide genuine value rather than simply alerting users to events.

## Summary

The Chrome Notification API provides a versatile set of tools for engaging users through system notifications. Whether you are building a web application or a Chrome extension, understanding how to request permissions, create notifications, implement actions, and use badges effectively is essential for creating engaging user experiences.

Remember to always respect user privacy by only requesting permissions when needed and providing clear controls for users to manage their notification preferences. Test your implementation across different platforms and consider the user experience at every step.

With this knowledge, you are now equipped to implement powerful notification systems that keep users informed and engaged without being intrusive. Start small, iterate based on user feedback, and continuously improve your notification strategy.



## Related Articles
- [Chrome Fetch API Complete Guide](/chrome-fetch-api-complete-guide)
- [Chrome Web NFC API Guide](/chrome-web-nfc-api-guide)
- [Chrome Web Serial API Guide](/chrome-web-serial-api-guide)

Built by theluckystrike — More tips at [zovo.one](https://zovo.one)
