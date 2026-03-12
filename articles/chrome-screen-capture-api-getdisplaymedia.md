---
layout: default
title: Chrome Screen Capture API getDisplayMedia – Complete Guide
description: Learn how to use the Chrome Screen Capture API (getDisplayMedia) to capture screens, windows, and tabs in your browser. Practical examples and best practices included.
keywords: chrome screen capture api getdisplaymedia
categories:
- chrome
- screen capture
- browser api
tags:
- chrome-screen-capture
- getdisplaymedia
- browser-api
- screen-sharing
author: theluckystrike
---

# Chrome Screen Capture API getDisplayMedia – Complete Guide

The ability to capture screen content directly from a web browser has become increasingly valuable. Whether you're building a collaborative tool, creating a screencast application, or developing an online presentation platform, the Chrome Screen Capture API—known as **getDisplayMedia**—provides a powerful solution for capturing screens, windows, and individual tabs directly within Chrome.

## What is getDisplayMedia?

The **getDisplayMedia** API is a browser-based method that allows websites to request access to a user's screen or a portion of it. Part of the Media Capture and Streams API, this function triggers the familiar Chrome screen picker dialog, where users can select what they want to share: their entire screen, a specific application window, or a single browser tab.

Unlike older screen recording solutions that required browser extensions or external software, getDisplayMedia works directly in modern Chrome without any additional installations. This makes it an excellent choice for web developers building collaborative platforms, distance learning tools, or remote assistance applications.

## How to Use getDisplayMedia in Chrome

Implementing screen capture in your web application is straightforward. Here's a basic example of how to request screen capture:

```javascript
async function startScreenCapture() {
  try {
    const stream = await navigator.mediaDevices.getDisplayMedia({
      video: {
        displaySurface: "browser"
      },
      audio: true
    });
    
    // Handle the stream
    const video = document.querySelector("video");
    video.srcObject = stream;
    
    return stream;
  } catch (error) {
    console.error("Error capturing screen:", error);
  }
}
```

This code triggers Chrome's screen picker, allowing the user to choose what to share. The returned stream contains video (and optionally audio) data that you can record, broadcast, or process as needed.

## Understanding the Options

The getDisplayMedia API offers several configuration options that give you control over what users can capture:

**displaySurface** lets you suggest preferred capture types. You can set it to "browser" to encourage tab capture, "window" for specific application windows, or "monitor" for full-screen recording. Chrome respects these preferences but ultimately lets users make the final choice.

**selfBrowserSurface** determines whether users can select the current page as a capture source. Setting this to "include" allows it, while "exclude" prevents it.

**systemAudio** controls whether system audio is included in the capture. This is particularly useful for capturing audio from videos or presentations.

## Recording the Captured Stream

Once you've obtained a screen capture stream, you can record it using the MediaRecorder API:

```javascript
function recordStream(stream) {
  const mediaRecorder = new MediaRecorder(stream, {
    mimeType: "video/webm;codecs=vp9"
  });
  
  const chunks = [];
  
  mediaRecorder.ondataavailable = (event) => {
    if (event.data.size > 0) {
      chunks.push(event.data);
    }
  };
  
  mediaRecorder.onstop = () => {
    const blob = new Blob(chunks, { type: "video/webm" });
    const url = URL.createObjectURL(blob);
    // Download or display the recording
    const a = document.createElement("a");
    a.href = url;
    a.download = "screen-recording.webm";
    a.click();
  };
  
  mediaRecorder.start();
  
  // Stop recording after 60 seconds (example)
  setTimeout(() => {
    mediaRecorder.stop();
    stream.getTracks().forEach(track => track.stop());
  }, 60000);
}
```

This example records the screen capture for 60 seconds and automatically downloads the result as a WebM file.

## Practical Applications

The getDisplayMedia API opens up numerous possibilities for web-based applications. Online educators can create automated course recording systems without requiring students to install additional software. Remote support tools can let technicians view a user's screen instantly through the browser. Team collaboration platforms can incorporate instant screen sharing for meetings and presentations.

For developers building productivity tools, combining screen capture with other browser APIs enables features like automatic meeting notes, annotated screenshots, and collaborative whiteboards. The integration possibilities are extensive.

## Performance Considerations

When implementing screen capture, keep in mind that recording and processing video consumes significant system resources. On computers with limited RAM, screen capture can strain performance, especially when capturing high-resolution displays or multiple monitors.

If you're building applications for users with slower computers, consider implementing controls that allow users to pause capture when not needed, or offer lower resolution options. Additionally, properly cleaning up media streams when they're no longer needed prevents memory leaks and keeps browsers running smoothly.

For users who frequently work with many browser tabs while running screen capture or other resource-intensive applications, managing tab memory becomes essential. Extensions like **Tab Suspender Pro** can help by automatically suspending inactive tabs, freeing up memory for more demanding tasks like screen recording.

## Browser Compatibility

While getDisplayMedia is widely supported in Chrome and other Chromium-based browsers, compatibility varies across browsers. Firefox and Safari have implemented similar functionality, though with some differences in available options. Always check the specific browser documentation and implement fallback handling when necessary.

## Security and User Privacy

The getDisplayMedia API includes important security protections. Users must explicitly grant permission for each capture session, and Chrome clearly displays a visual indicator whenever screen capture is active. The API cannot capture without user consent, making it a safe choice for privacy-conscious applications.

However, always inform your users when recording is occurring and obtain appropriate consent. Building transparency into your application helps maintain user trust and complies with privacy regulations in many jurisdictions.

## Tips for a Better User Experience

When implementing screen capture, provide clear instructions to users about what will be captured and how to stop sharing. Include visible controls for starting and stopping capture within your interface. Test your implementation across different Chrome versions and consider providing guidance for users on slower computers about optimal settings.

Handling errors gracefully improves the experience significantly. Users might cancel the screen picker or encounter permission issues. Your application should respond to these scenarios with helpful messages rather than confusing errors.

## Conclusion

The Chrome Screen Capture API (getDisplayMedia) provides a robust, extension-free way to capture screen content directly in the browser. Whether you're building educational tools, support applications, or collaboration platforms, this API offers the functionality needed to create powerful screen capture experiences.

By understanding the available options, implementing proper error handling, and considering performance implications, you can build reliable screen capture features that work well for users across different hardware configurations.

Built by theluckystrike — More tips at [zovo.one](https://zovo.one)
