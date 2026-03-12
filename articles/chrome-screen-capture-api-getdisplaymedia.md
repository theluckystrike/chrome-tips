---
layout: default
title: Chrome Screen Capture API getDisplayMedia - Complete Guide
description: Learn how to use Chrome's getDisplayMedia API for screen capture in your web applications. Includes code examples, browser permissions, and practical implementation tips.
date: 2026-01-15
last_modified_at: '2026-03-12'
permalink: chrome-screen-capture-api-getdisplaymedia
categories:
- chrome
- api
- screen-capture
- web-development
tags:
- getdisplaymedia
- screen-capture
- chrome-api
- browser-api
- media-capture
author: theluckystrike
---

# Chrome Screen Capture API getDisplayMedia - Complete Guide

Chrome's Screen Capture API, powered by the `getDisplayMedia()` method, has transformed how web developers build recording and sharing features directly in the browser. This powerful API enables users to capture their screen, application windows, or individual browser tabs without installing additional software. Understanding how to implement this API opens up possibilities for creating screenshots, video recordings, screen sharing in video calls, and collaborative tools.

## How getDisplayMedia Works

The `getDisplayMedia()` method is part of the Media Capture and Streams API (MediaStream API). When you call this method in Chrome, the browser displays a native picker dialog where users can choose what they want to share. Users can select their entire screen, a specific application window, or a browser tab. This user-controlled selection ensures privacy and prevents unintended screen capture.

The basic implementation requires just a few lines of JavaScript. You call `navigator.mediaDevices.getDisplayMedia()` which returns a Promise that resolves to a MediaStream object. This stream contains video and audio tracks representing the captured content, which you can then record, broadcast, or process further.

```javascript
async function startScreenCapture() {
  try {
    const stream = await navigator.mediaDevices.getDisplayMedia({
      video: {
        displaySurface: "monitor"
      },
      audio: true
    });
    
    // Use the stream for recording or sharing
    return stream;
  } catch (error) {
    console.error("Screen capture failed:", error);
  }
}
```

## Key Configuration Options

Chrome provides several configuration options to control what users can share and how the capture behaves. The `video` property lets you specify preferences for the captured video. You can set `displaySurface` to `"monitor"` for full screen, `"window"` for application windows, or `"browser"` for browser tabs specifically.

The `selfBrowserSurface` option, when set to `"include"`, allows users to capture the current tab where the capture originates. This is useful for creating tutorial or demo applications. The `surfaceSwitching` option controls whether users can switch what they are sharing during an active capture session.

For audio capture, you can include `audio: true` in your constraints to capture system audio (on Windows) or tab audio (on Chrome OS and macOS). However, not all systems support audio capture, so you should always handle cases where audio tracks might be missing from the returned stream.

## Handling Permissions and User Experience

When your code calls `getDisplayMedia()`, Chrome prompts users with a permission dialog explaining what your application wants to capture. Users must explicitly grant permission, and they can choose to share only specific content rather than their entire screen. This built-in privacy protection means your application cannot capture anything without user consent.

You should provide clear instructions to users before initiating capture. Explain what will happen when they click the capture button and what permissions they will need to grant. This transparency reduces confusion and increases the likelihood that users will complete the capture process successfully.

If a user denies permission, the Promise returned by `getDisplayMedia()` rejects with a `NotAllowedError`. Your code should handle this gracefully by showing a helpful message rather than failing silently.

## Recording Captured Content

Once you have a MediaStream from `getDisplayMedia()`, you can use the MediaRecorder API to create video recordings. The MediaRecorder takes your stream and encodes it into a video file format that you can download or upload to a server.

```javascript
function recordStream(stream) {
  const recorder = new MediaRecorder(stream, {
    mimeType: "video/webm;codecs=vp9"
  });
  
  const chunks = [];
  
  recorder.ondataavailable = (event) => {
    if (event.data.size > 0) {
      chunks.push(event.data);
    }
  };
  
  recorder.onstop = () => {
    const blob = new Blob(chunks, { type: "video/webm" });
    const url = URL.createObjectURL(blob);
    // Download or process the recording
    const a = document.createElement("a");
    a.href = url;
    a.download = "recording.webm";
    a.click();
  };
  
  recorder.start();
  
  // Stop after 60 seconds (or implement custom stop control)
  setTimeout(() => recorder.stop(), 60000);
  
  return recorder;
}
```

The MediaRecorder supports different MIME types depending on the browser. Chrome supports `video/webm` with various codecs including VP8, VP9, and AV1. For broader compatibility, you can check available MIME types using `MediaRecorder.isTypeSupported()`.

## Practical Applications

Screen capture functionality powered by getDisplayMedia serves many practical purposes. Developers can build screenshot tools that let users capture and annotate their screens. Online education platforms can enable teachers to record their demonstrations. Support teams can use screen sharing for remote assistance. Content creators can record tutorials and walkthroughs directly in the browser.

One thing to consider is that running screen capture alongside other browser activities can increase memory usage. If you work with many open tabs, a tool like **Tab Suspender Pro** can help manage resource consumption by temporarily suspending inactive tabs while you focus on your capture session.

## Browser Compatibility

While Chrome was one of the first browsers to implement `getDisplayMedia()`, the API is now supported in Firefox, Edge, Safari, and other Chromium-based browsers. However, there are differences in available options and behavior across browsers. Firefox supports the core functionality but may have different default behaviors. Safari added support more recently and continues to expand its implementation.

When building cross-browser applications, test your implementation thoroughly in each target browser and provide fallback experiences for users on unsupported platforms.

## Best Practices

Always listen for the `track` event on your stream to detect when the user stops sharing through the browser's built-in controls. When this happens, the video tracks in your stream will end, and you should clean up any recording or processing you were performing.

Remember that screen capture can be resource-intensive. Avoid capturing at unnecessarily high resolutions, and stop capture streams when you no longer need them to free up system resources.

Built by theluckystrike — More tips at [zovo.one](https://zovo.one)
