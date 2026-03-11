---
layout: default
title: "Chrome MediaRecorder API Guide"
description: "Learn how to use the Chrome MediaRecorder API for audio recording, video recording, screen recording, and encoding in web applications. Complete guide with code examples and best practices."
date: 2026-03-11
categories: [chrome, development, api, media]
tags: [mediarecorder, chrome-api, audio-recording, video-recording, screen-recording, encoding]
author: theluckystrike
---

# Chrome MediaRecorder API Guide

The Chrome MediaRecorder API is one of the most powerful browser APIs available for capturing media directly in the web browser. Whether you need to record audio from a microphone, capture video from a webcam, record your screen for tutorials or demonstrations, or encode media for processing, the MediaRecorder API provides a standardized way to accomplish all of these tasks without requiring plugins or external software. This comprehensive guide will walk you through everything you need to know to start using the MediaRecorder API effectively in your Chrome extensions and web applications.

## Understanding the MediaRecorder API

The MediaRecorder API is part of the broader Media Stream API ecosystem in Chrome and provides a high-level interface for recording media streams. It was designed to be simple yet powerful, allowing developers to capture media from various sources and save them as files or transmit them over networks. The API works with MediaStream objects, which can come from getUserMedia (for camera and microphone), getDisplayMedia (for screen capture), or even from other media elements using the captureStream method.

One of the key advantages of the MediaRecorder API is that it operates entirely on the client side, meaning you don't need a backend server to handle recording. This makes it ideal for applications where privacy is important or where you want to reduce server costs. The recorded media can be stored locally, uploaded to a server, or processed further in the browser before being shared.

The API supports various MIME types for recording, including webm, mp4, and audio-only formats like webm with vorbis or opus codecs. Chrome's implementation is particularly robust, supporting multiple codecs and container formats that give you flexibility in choosing the right format for your use case. Understanding these options and how they affect file size and quality is essential for building efficient recording features.

## Audio Recording with MediaRecorder

Recording audio in Chrome using the MediaRecorder API is straightforward once you understand the basic workflow. The first step is to request permission to access the user's microphone using the getUserMedia API. This will prompt the user to allow or deny microphone access, and once granted, you can create a MediaStream that contains only the audio track you want to record.

To start recording audio, you create a MediaRecorder object with the audio stream as its parameter. You can also specify the MIME type and bits per second for encoding, which gives you control over the quality and file size of the recording. The MediaRecorder provides several events that you can listen to, including dataavailable (which provides chunks of recorded data), stop (which fires when recording ends), and error (which handles any issues that occur during recording).

When recording audio, it's important to consider the user's experience. You should always display a clear indicator when recording is active, and you should handle the case where the user revokes microphone permission during recording. Additionally, if you're building an extension like Tab Suspender Pro that runs in the background, you need to ensure that your recording logic properly handles tab visibility changes and doesn't consume excessive resources when the user isn't actively using the recording feature.

Here's a basic example of how to record audio in Chrome:

```javascript
async function startAudioRecording() {
  const stream = await navigator.mediaDevices.getUserMedia({ audio: true });
  const mediaRecorder = new MediaRecorder(stream, {
    mimeType: 'audio/webm;codecs=opus'
  });
  
  const audioChunks = [];
  
  mediaRecorder.addEventListener('dataavailable', (event) => {
    audioChunks.push(event.data);
  });
  
  mediaRecorder.addEventListener('stop', () => {
    const audioBlob = new Blob(audioChunks, { type: 'audio/webm' });
    // Process the recorded audio
  });
  
  mediaRecorder.start();
  return mediaRecorder;
}
```

The recorded audio can be saved in various formats, but webm with opus encoding is generally recommended for Chrome because it provides excellent quality at relatively small file sizes. If you need to support other browsers or want more flexibility in format conversion, you can use the MediaRecorder.isTypeSupported() method to check which MIME types are available on the user's browser.

## Video Recording Techniques

Video recording builds upon the same principles as audio recording but adds the complexity of handling video tracks alongside audio. When you request video and audio together using getUserMedia, you get a MediaStream that contains both tracks, which you can then pass to the MediaRecorder to capture synchronized audio and video.

The quality settings for video recording are particularly important because video files can become very large very quickly. You can control the video quality by specifying the bitsPerSecond parameter when creating the MediaRecorder, or by constraining the resolution and frame rate of the source media stream. For most web applications, recording at 720p (1280x720) with 30 frames per second provides a good balance between quality and file size.

When implementing video recording, you should also consider how to preview the video while recording. The simplest approach is to display the MediaStream directly in a video element, which allows the user to see what is being recorded in real-time. This is especially important for webcam recording, where users expect to see themselves on screen while recording.

For extensions that need to record video in the background, such as tools that create automated tutorials or documentation, you need to be careful about resource management. Recording video consumes significant CPU and memory, so you should pause or stop recording when the extension isn't actively being used. Tab Suspender Pro, for example, uses intelligent resource management to ensure that background operations don't impact browser performance, a principle that applies equally to recording features.

Here's how you might implement basic video recording:

```javascript
async function startVideoRecording() {
  const stream = await navigator.mediaDevices.getUserMedia({
    video: { width: 1280, height: 720 },
    audio: true
  });
  
  // Show preview
  const videoElement = document.getElementById('preview');
  videoElement.srcObject = stream;
  videoElement.play();
  
  const mediaRecorder = new MediaRecorder(stream, {
    mimeType: 'video/webm;codecs=vp9',
    videoBitsPerSecond: 2500000
  });
  
  const videoChunks = [];
  
  mediaRecorder.addEventListener('dataavailable', (event) => {
    if (event.data.size > 0) {
      videoChunks.push(event.data);
    }
  });
  
  mediaRecorder.addEventListener('stop', () => {
    const videoBlob = new Blob(videoChunks, { type: 'video/webm' });
    const videoURL = URL.createObjectURL(videoBlob);
    // Handle the recorded video
  });
  
  mediaRecorder.start(1000); // Collect data every second
  return mediaRecorder;
}
```

One advanced technique for video recording is to use the canvas element to capture frames and then compose them into a video. This gives you complete control over what appears in the video, including the ability to add overlays, annotations, or combine multiple video sources. This approach is commonly used in screen recording software and video editing tools.

## Screen Recording with getDisplayMedia

Chrome's screen recording capabilities come primarily from the getDisplayMedia API, which was added to enable screen sharing functionality similar to what you see in video conferencing applications. While originally designed for real-time sharing, this API also serves as the foundation for building screen recording features in Chrome extensions and web applications.

To start screen recording, you call navigator.mediaDevices.getDisplayMedia(), which prompts the user to choose what they want to share. The user can choose to share their entire screen, a specific application window, or a browser tab. This is an important privacy feature because it gives users control over what gets recorded and prevents accidental recording of sensitive content.

The MediaStream returned by getDisplayMedia can be used directly with the MediaRecorder, just like streams from getUserMedia. However, there are some important differences to consider. Screen recordings typically don't include audio from the user's microphone unless you explicitly combine the screen stream with an audio stream from getUserMedia. Additionally, the resolution and frame rate of screen recordings depend on what the user chooses to share and the capabilities of their display.

One of the most powerful features of getDisplayMedia is the ability to track when the user stops sharing. The API provides a track event that fires when the user clicks the browser's built-in stop sharing button, allowing you to automatically stop recording and process the captured content. This creates a smooth user experience where the recording ends naturally when the sharing session ends.

For building comprehensive screen recording tools, you might want to combine multiple recording sources. For example, you could record the screen and the user's webcam simultaneously, then use the Web Audio API and canvas to composite them into a single video with a picture-in-picture effect. This is how many professional screen recording tools work and can significantly improve the quality of your recordings.

```javascript
async function startScreenRecording() {
  const displayStream = await navigator.mediaDevices.getDisplayMedia({
    video: {
      displaySurface: 'monitor',
      width: { ideal: 1920 },
      height: { ideal: 1080 },
      frameRate: { ideal: 30 }
    },
    audio: true
  });
  
  // Handle when user stops sharing via browser UI
  displayStream.getVideoTracks()[0].addEventListener('ended', () => {
    console.log('User stopped screen sharing');
    // Stop recording automatically
  });
  
  const mediaRecorder = new MediaRecorder(displayStream, {
    mimeType: 'video/webm;codecs=vp9',
    videoBitsPerSecond: 5000000
  });
  
  // Recording logic here
  return mediaRecorder;
}
```

## Understanding Encoding and MIME Types

The MediaRecorder API's flexibility comes largely from its support for different encoding options and MIME types. Understanding these options is essential for producing recordings that meet your quality requirements while managing file sizes appropriately. Chrome supports several container formats and codecs, each with different characteristics and browser compatibility.

The most common container format for Chrome recordings is WebM, which is based on the Matroska container and works exceptionally well with VP8 or VP9 video codecs and Vorbis or Opus audio codecs. WebM files are typically smaller than equivalent MP4 files while maintaining good quality, making them ideal for web applications where bandwidth and storage are concerns. The Opus audio codec is particularly impressive for speech, providing near-CD quality at very low bitrates.

For situations where you need broader compatibility or specific format requirements, Chrome also supports MP4 recording with H.264 video and AAC audio. However, not all Chrome versions and platforms support MP4 encoding, so you should always check using the MediaRecorder.isTypeSupported() method before attempting to record in a specific format. This method returns true if the browser can create a MediaRecorder with the specified MIME type.

When choosing encoding settings, consider the intended use of the recording. For video tutorials or demonstrations where clarity is important, use higher bitrates (2-5 Mbps for 720p, 5-10 Mbps for 1080p). For quick recordings that will be shared immediately or stored temporarily, lower bitrates can significantly reduce file sizes without making the content unwatchable. The key is to find the right balance for your specific use case.

The videoBitsPerSecond and audioBitsPerSecond parameters in the MediaRecorder options allow you to fine-tune the encoding quality. These values represent the target bitrate in bits per second, so a value of 2500000 equals 2.5 megabits per second. Higher values generally mean better quality but larger files, while lower values mean smaller files but potentially noticeable quality loss, especially for complex video content with lots of movement.

```javascript
function getSupportedMimeType() {
  const types = [
    'video/webm;codecs=vp9,opus',
    'video/webm;codecs=vp8,opus',
    'video/webm',
    'video/mp4'
  ];
  
  for (const type of types) {
    if (MediaRecorder.isTypeSupported(type)) {
      return type;
    }
  }
  throw new Error('No supported MIME type found');
}
```

## Advanced Recording Patterns

Beyond basic recording, the MediaRecorder API supports several advanced patterns that enable more sophisticated applications. One such pattern is pausable and resumable recording, which allows you to temporarily stop recording and then continue from where you left off. This is particularly useful for creating long-form content where you want to take breaks without creating multiple separate files.

The MediaRecorder provides pause() and resume() methods that control the recording state. When you call pause(), the recorder stops collecting data but maintains the stream connection, allowing you to resume recording at any time. The dataavailable event continues to fire, but with empty data chunks that you can ignore. This feature is especially valuable for applications like note-taking tools or educational platforms where users might want to record in segments.

Another advanced technique involves real-time processing of recorded data. Instead of waiting until recording stops to handle the data, you can process chunks as they become available during recording. This enables use cases like live streaming, real-time transcription, or immediate upload to a server. The dataavailable event fires at intervals you specify when calling the start() method, giving you control over how frequently you receive data chunks.

For applications that need to combine multiple media sources, you can use the MediaStream API to merge tracks from different streams. This allows you to create recordings that include video from multiple cameras, combine screen recordings with webcam overlays, or mix multiple audio sources. The combineTracks() method and the MediaStream constructor provide the tools you need to create these composite streams.

Error handling is another crucial aspect of advanced recording implementations. The MediaRecorder can fail for various reasons, including permission revocation, device disconnection, or encoding errors. You should always add an error event listener to handle these situations gracefully, and you should implement recovery logic that allows users to restart recording after an error occurs.

## Best Practices and Performance Considerations

Building reliable recording features requires attention to performance and user experience considerations. One of the most important practices is to always request only the media capabilities you need. Requesting 4K video when you only need 720p will significantly increase resource usage and battery consumption on mobile devices. Similarly, requesting stereo audio when mono is sufficient will create larger files than necessary.

Memory management is critical when recording for extended periods. The MediaRecorder doesn't automatically write data to disk; instead, it accumulates data in memory until you handle the dataavailable events. For long recordings, you should process and clear the data chunks regularly to prevent memory issues. Consider uploading chunks to a server or writing them to IndexedDB as they arrive, rather than keeping everything in memory until recording ends.

When building Chrome extensions that include recording features, be aware of the limitations imposed by the extension platform. Extensions have access to additional APIs like chrome.desktopCapture that can enhance recording capabilities, but they also have their own permission requirements and user experience guidelines. Make sure your extension clearly explains why it needs recording permissions and what it will do with the recordings.

For extensions like Tab Suspender Pro that manage background processes, integrating recording features requires careful consideration of resource allocation. Recording should be treated as a foreground activity that gets appropriate priority, and the extension should provide clear UI indicators when recording is active so users aren't surprised by the behavior. Consider providing keyboard shortcuts or quick-access menus that make starting and stopping recordings convenient.

Finally, always test your recording implementation across different Chrome versions and platforms. While the MediaRecorder API is well-standardized, there can be subtle differences in behavior, particularly around encoding support and performance characteristics. Automated tests that verify recording produces valid output files are invaluable for maintaining quality as you update your application.

## Conclusion

The Chrome MediaRecorder API provides a powerful foundation for building audio, video, and screen recording features in web applications and Chrome extensions. By understanding the fundamentals of MediaStream creation, the various recording modes, encoding options, and advanced patterns, you can create sophisticated recording experiences that work reliably across different use cases.

Whether you're building a simple audio note-taking app, a comprehensive screen recording tool, or integrating recording capabilities into an extension like Tab Suspender Pro, the principles covered in this guide will help you make informed decisions about implementation. Remember to prioritize user experience through clear feedback, thoughtful permission handling, and efficient resource management.

As web technologies continue to evolve, the MediaRecorder API will likely gain additional capabilities and improvements. Stay current with Chrome's release notes and the W3C specification to take advantage of new features as they become available. With the solid foundation this guide provides, you'll be well-positioned to build recording features that serve your users effectively.
