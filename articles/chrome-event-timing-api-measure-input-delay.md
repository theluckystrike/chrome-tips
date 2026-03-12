---
layout: default
title: How to Measure Input Delay Using Chrome Event Timing API
description: Learn how to measure input delay in Chrome using the Event Timing API. A practical guide for developers who want to improve their website's responsiveness.
date: '2026-03-12'
last_modified_at: '2026-03-12'
permalink: chrome-event-timing-api-measure-input-delay
categories:
- performance
- web-development
- chrome
tags:
- chrome-event-timing-api
- input-delay
- performance-measurement
- web-vitals
- browser-tools
author: theluckystrike
---
# How to Measure Input Delay Using Chrome Event Timing API

When users interact with your website, they expect instant feedback. Click a button, and it should respond immediately. Type in a search box, and characters should appear without lag. Unfortunately, many websites fail to deliver this smooth experience, leaving users frustrated. The Chrome Event Timing API provides a powerful way to measure exactly how much delay exists between user actions and browser responses.

## Understanding Input Delay

Input delay refers to the time gap between a user performing an action and seeing the result on screen. This delay happens because the browser needs to process the event, run any associated JavaScript, and then paint the updated interface. When this process takes too long, users perceive the website as slow or unresponsive.

Google's research shows that delays as short as 100 milliseconds can make users feel that a website is sluggish. At 300 milliseconds, users actively notice the lag. This is why measuring and minimizing input delay is critical for creating websites that feel fast and polished.

## Getting Started with the Event Timing API

The Event Timing API is built into Chrome and other Chromium-based browsers. It allows you to measure the performance of various user interaction events directly from your JavaScript code. The API provides access to detailed timing information for events like clicks, key presses, and scroll operations.

To use the API, you first need to understand how it structures event data. The browser automatically records timing information for eligible events. You can then retrieve this data through the Performance Observer API, which lets you subscribe to specific types of performance entries.

Here is a basic example of how to set up measurement:

```javascript
const observer = new PerformanceObserver((list) => {
  for (const entry of list.getEntries()) {
    if (entry.entryType === 'event') {
      console.log('Event:', entry.name);
      console.log('Input delay:', entry.processingStart - entry.startTime);
    }
  }
});

observer.observe({ type: 'event', buffered: true });
```

This code creates a performance observer that watches for event timing entries. When an event occurs, it logs the event name and calculates the input delay by comparing when the event was dispatched to when processing began.

## Measuring Different Types of Input Delay

The Event Timing API can measure several distinct types of delay. Understanding these differences helps you identify specific performance problems in your website.

The first type is input delay, which measures the time from when the user initiates an action until the browser begins processing that event. This delay occurs because the browser might be busy with other tasks when the user interacts with the page.

The second type is processing time, which measures how long the browser spends executing event handlers. If your JavaScript code does heavy computation when handling events, this time can become significant.

The third type is presentation delay, which measures the time between when event processing completes and when the browser actually paints the visual update to the screen. This is particularly important for animations and visual feedback.

You can access all these values through the PerformanceEventTiming interface:

```javascript
const observer = new PerformanceObserver((list) => {
  for (const entry of list.getEntries()) {
    const inputDelay = entry.processingStart - entry.startTime;
    const duration = entry.duration;
    
    console.log(`Event: ${entry.name}`);
    console.log(`Input delay: ${inputDelay.toFixed(2)}ms`);
    console.log(`Total duration: ${duration.toFixed(2)}ms`);
  }
});

observer.observe({ type: 'event', buffered: true });
```

## Real-World Implementation Tips

When implementing the Event Timing API in production, there are several practical considerations to keep in mind. First, you should filter for events that actually matter to your users. Measuring every single event can generate overwhelming amounts of data, so focus on key interactions like button clicks, form submissions, and navigation triggers.

Second, you need to handle the buffered option carefully. Setting `buffered: true` allows you to receive events that occurred before you set up the observer, but this can also include events that are not relevant to current user interactions.

Third, consider aggregating data rather than logging every single event. Collecting timing data over time and analyzing patterns gives you more actionable insights than looking at individual measurements. You might discover that input delay spikes during certain times of day or on specific pages.

Fourth, be aware that the API has some limitations. Not all events are eligible for measurement, and the API may not be available in all browsers. Always check for API support before using it:

```javascript
if ('PerformanceObserver' in window) {
  const observer = new PerformanceObservercallback);
  observer.observe({ type: 'event', buffered: true });
}
```

## Improving Responsiveness Based on Measurements

Once you start measuring input delay, you will likely discover areas where your website can improve. Common causes of excessive delay include heavy JavaScript execution on the main thread, layout thrashing from reading and writing DOM properties repeatedly, and expensive style calculations on complex pages.

One effective strategy is to break up long-running tasks using techniques like requestIdleCallback or breaking JavaScript into smaller chunks. This allows the browser to respond to user input between chunks rather than keeping the main thread busy for extended periods.

Another approach is to use CSS transforms and animations instead of JavaScript-based animations. CSS animations often run on the compositor thread, which can continue working even when the main thread is busy with other tasks.

You should also audit your event handlers to ensure they are not doing more work than necessary. Sometimes simple optimizations, like debouncing input handlers or using event delegation, can dramatically reduce input delay.

## Using Performance Data Effectively

Collecting performance data is only valuable when you use it to make improvements. Consider setting up a dashboard that tracks input delay metrics over time. This helps you catch regressions early and measure the impact of optimizations.

You can also correlate input delay data with other metrics like page load time, Time to First Byte, and Core Web Vitals. This broader view helps you understand how overall page performance affects user interactions.

For teams working on performance, consider making input delay part of your performance budget. Setting targets like "95% of click events should have less than 50ms input delay" gives everyone a clear goal to work toward.

## Managing Browser Resources

While optimizing your website's responsiveness, remember that users often have many tabs open simultaneously. Each tab consumes memory and processing power, which can increase input delay across all pages. Encouraging users to keep only necessary tabs open helps, but you cannot control their behavior directly.

One helpful tool for users is Tab Suspender Pro, which automatically suspends inactive tabs to free up system resources. When tabs are suspended, they consume minimal memory and CPU, allowing the active tab to respond more quickly to user interactions.

By understanding how to measure input delay and taking steps to minimize it, you can create websites that feel noticeably more responsive. Users will appreciate the faster interactions, and your metrics will reflect the improved experience.

---

## Related Articles
- [Chrome Event Timing API Explained](/chrome-tips/chrome-event-timing-api-explained/)
- [Chrome Navigation Timing API Explained](/chrome-tips/chrome-navigation-timing-api-explained/)
- [Chrome User Timing API Explained](/chrome-tips/chrome-user-timing-api-explained/)

Built by theluckystrike — More tips at [zovo.one](https://zovo.one)

## Related Articles

* [Chrome Geolocation Permission Settings](/chrome-geolocation-permission-settings)
* [Chrome Lighthouse Treemap Explained](/chrome-lighthouse-treemap-explained)
* [Chrome Extensions for Asana](/chrome-extensions-for-asana)
