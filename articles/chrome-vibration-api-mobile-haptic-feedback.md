---
layout: default
title: "Chrome Vibration API: Mobile Haptic Feedback Guide"
description: "Learn how to use the Chrome Vibration API to create immersive mobile web experiences with haptic feedback. Step-by-step tutorial with code examples."
date: 2026-03-12
last_modified_at: '2026-03-12'
permalink: chrome-vibration-api-mobile-haptic-feedback
categories:
- mobile-web
- web-apis
- chrome-mobile
tags:
- chrome-mobile
- vibration-api
- haptic-feedback
- pwa
- mobile-development
author: theluckystrike
---

# Chrome Vibration API: Mobile Haptic Feedback Guide

The Chrome Vibration API represents one of the most powerful yet underutilized features available to mobile web developers today. This API enables your web applications to take advantage of the vibration hardware found in virtually every smartphone, creating tactile feedback that enhances user engagement and provides meaningful cues without requiring users to look at their screens.

## Understanding the Vibration API

The Vibration API is a web standard that allows web pages to control the vibration hardware of devices. Originally part of the HTML5 specification, it provides a simple yet effective way to incorporate haptic feedback into your mobile web applications.

The API consists of a single method: `navigator.vibrate()`. This method accepts either a single number representing vibration duration in milliseconds, or an array of numbers that alternates between vibration and pause periods.

```javascript
// Vibrate for 200 milliseconds
navigator.vibrate(200);

// Vibrate for 100ms, pause for 50ms, then vibrate for 200ms
navigator.vibrate([100, 50, 200]);
```

Most modern mobile browsers, including Chrome for Android, support this API. Safari on iOS does not currently support the Vibration API due to Apple's restrictions, so you'll need to implement feature detection before using it.

## Checking Browser Support

Before implementing vibration feedback in your application, always verify that the API is available. This best practice ensures your application gracefully degrades on unsupported devices:

```javascript
function isVibrationSupported() {
    return 'vibrate' in navigator;
}

if (isVibrationSupported()) {
    // Safe to use vibration features
} else {
    // Provide alternative feedback (visual or audio)
}
```

## Practical Use Cases

There are numerous scenarios where the Vibration API significantly improves user experience. Here are the most effective applications:

**Form Validation Feedback**

When users submit forms with errors, a short vibration pattern can immediately signal that something needs attention. This proves especially valuable on mobile devices where visual feedback might be less noticeable:

```javascript
function vibrateError() {
    // Two short bursts for error feedback
    navigator.vibrate([100, 50, 100]);
}

function vibrateSuccess() {
    // Single longer vibration for success
    navigator.vibrate(200);
}
```

**Game Feedback**

Mobile games benefit enormously from haptic feedback. Vibration can indicate collisions, power-ups, or game-over events, creating a more immersive experience:

```javascript
function playCollisionEffect() {
    navigator.vibrate(150);
}

function playPowerUpEffect() {
    navigator.vibrate([50, 100, 50, 100, 200]);
}
```

**Notification Alerts**

For progressive web apps and web applications running in the background, vibration provides an additional notification channel beyond visual and audio cues.

## Implementing Effective Vibration Patterns

The key to effective haptic feedback lies in creating intentional, meaningful patterns. Random or excessive vibration quickly becomes annoying, so follow these guidelines:

**Keep vibrations short.** Most users find vibrations between 50-200 milliseconds comfortable. Going beyond 500 milliseconds often feels excessive.

**Use patterns deliberately.** Arrays that alternate vibration and pause create distinct patterns that users can learn to recognize:

```javascript
// Light tap for button feedback
navigator.vibrate(30);

// Moderate feedback for important actions
navigator.vibrate(100);

// Urgent feedback for warnings
navigator.vibrate([200, 100, 200]);
```

**Respect user preferences.** Always provide settings for users to disable or customize vibration feedback. Some users have vestibular disorders that make certain vibration patterns uncomfortable.

## Chrome-Specific Considerations

Chrome's implementation of the Vibration API follows the W3C specification closely, but there are some nuances to keep in mind:

Chrome requires user activation before vibration can trigger. This means the API must be called from an event handler such as a click or touch event. Vibration calls from setTimeout or other asynchronous code that wasn't triggered by user interaction will be ignored.

The vibration hardware behavior varies across different Android devices. Some phones produce strong vibrations while others are more subtle. Test your vibration patterns on multiple devices to ensure consistent experience.

Background tabs cannot trigger vibration in Chrome. The tab must be visible and active for the vibration to work. This is intentional behavior to prevent abusive usage.

## Advanced Implementation

For more sophisticated applications, you can combine the Vibration API with other web APIs to create rich feedback systems:

```javascript
class HapticFeedback {
    constructor() {
        this.enabled = true;
    }
    
    lightTap() {
        if (this.enabled) navigator.vibrate(20);
    }
    
    buttonPress() {
        if (this.enabled) navigator.vibrate(40);
    }
    
    success() {
        if (this.enabled) navigator.vibrate([50, 100, 50]);
    }
    
    error() {
        if (this.enabled) navigator.vibrate([100, 50, 100, 50, 200]);
    }
    
    toggle(enabled) {
        this.enabled = enabled;
    }
}

const haptic = new HapticFeedback();
```

This class-based approach makes it easy to manage vibration settings throughout your application and provides a clean API for different feedback scenarios.

## Performance Considerations

While the Vibration API itself is lightweight, be mindful of how often you trigger vibrations. Excessive haptic feedback:

- Drains battery faster on mobile devices
- Can appear spammy and unprofessional
- Might frustrate users in quiet environments

Aim for purposeful, meaningful vibrations that enhance the user experience rather than distract from it.

## Conclusion

The Chrome Vibration API offers a straightforward way to add tactile dimension to your mobile web applications. By following the implementation best practices outlined in this guide, you can create more engaging, accessible, and professional web experiences that work seamlessly across supported devices.

For Chrome extension developers looking to enhance their productivity tools, similar attention to user feedback mechanisms can significantly improve user satisfaction. Just as haptic feedback creates more responsive mobile experiences, thoughtful UI design in browser extensions creates more enjoyable daily workflows. Extensions like Tab Suspender Pro demonstrate how attention to user experience details can make browser usage more efficient and pleasant.

Built by theluckystrike — More tips at [zovo.one](https://zovo.one)
