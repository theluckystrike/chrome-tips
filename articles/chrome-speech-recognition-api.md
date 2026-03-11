---
layout: default
title: "Chrome Speech Recognition API Guide"
<<<<<<< HEAD
description: "A comprehensive guide to Chrome Speech Recognition API covering voice input, transcript accuracy, continuous recognition, and multi-language support. Learn how to implement voice features in your web applications."
date: 2025-03-12
categories: [features, web-development, accessibility]
tags: [speech-recognition, voice-input, chrome-api, web-speech-api, voice-commands, speech-to-text]
=======
description: "Master the Chrome Speech Recognition API with this comprehensive guide. Learn about voice input implementation, transcript accuracy optimization, continuous recognition, and multi-language support for web applications."
date: 2026-01-20
categories: [api, voice, web-development]
tags: [chrome, speech-recognition, voice-input, web-api, javascript]
>>>>>>> consumer/a57-chrome-speech-recognition-api
author: theluckystrike
---

# Chrome Speech Recognition API Guide

<<<<<<< HEAD
The Chrome Speech Recognition API represents one of the most powerful yet underutilized features built directly into Google's browser. This comprehensive guide explores everything you need to know about implementing voice recognition capabilities in your web applications, from basic voice input to advanced continuous recognition features. Whether you are a web developer looking to add voice controls to your application or a user wanting to understand how voice features work in Chrome, this guide provides detailed insights into making the most of this remarkable technology.

## Understanding the Web Speech API Architecture

Chrome implements the Web Speech API, which consists of two main components: the Speech Recognition API for converting spoken words into text, and the Speech Synthesis API for converting text into spoken words. The focus of this guide is the Speech Recognition API, which enables browsers to listen to audio input from a user's microphone and transcribe it into usable text in real-time.

The underlying technology leverages Google's extensive machine learning models trained on millions of hours of voice data. When a user speaks into their microphone, the audio is captured by the browser, compressed, and sent to Google's speech recognition servers via a secure connection. These servers process the audio using deep neural networks that have been trained to recognize speech patterns, accents, and various languages with remarkable accuracy. The transcribed text is then returned to the web application in near real-time, creating a seamless voice-to-text experience.

What makes this technology particularly powerful is that it runs entirely in the browser without requiring any plugins or additional software installations. As long as the user has a modern version of Chrome and grants microphone permission, web applications can immediately begin using voice recognition features. This democratization of voice technology has opened up new possibilities for accessibility, productivity, and user experience improvements across the web.

## Voice Input Implementation and Best Practices

Implementing voice input in your web application begins with checking browser support and requesting appropriate permissions. The first step involves verifying that the Speech Recognition API is available in the user's browser, as support varies across different browsers and versions. Chrome provides robust support for this API starting from version 25, making it the most reliable choice for deploying voice-enabled web applications.

The implementation process starts by creating a new SpeechRecognition object or using the webkit prefix for broader compatibility:

```javascript
const SpeechRecognition = window.SpeechRecognition || window.webkitSpeechRecognition;
const recognition = new SpeechRecognition();

recognition.continuous = true;
recognition.interimResults = true;
recognition.lang = 'en-US';

recognition.onresult = (event) => {
  for (let i = event.resultIndex; i < event.results.length; i++) {
    if (event.results[i].isFinal) {
      console.log('Recognized text:', event.results[i][0].transcript);
    }
  }
};

recognition.start();
```

When requesting microphone access, Chrome displays a permission prompt asking users to explicitly allow or deny the website access to their microphone. This security measure protects user privacy while ensuring that voice recognition only occurs when the user intentionally activates it. Best practices recommend providing clear visual feedback to users about when their microphone is active and when speech is being processed, helping to build trust and prevent unintended recordings.

Microphone quality significantly impacts voice recognition accuracy. Built-in laptop microphones often produce acceptable results for casual use, but dedicated headsets or external microphones can substantially improve accuracy, especially in noisy environments. Users should be encouraged to speak clearly at a normal pace and to position their microphone at an optimal distance from their mouth for best results.

## Achieving Optimal Transcript Accuracy
=======
The Chrome Speech Recognition API represents one of the most powerful yet underutilized features available to web developers today. This browser-based voice recognition technology enables websites to convert spoken language into written text in real-time, opening doors to innovative user interfaces, accessibility features, and hands-free browsing experiences. Whether you are building a voice-powered note-taking application, creating an accessibility tool for users with motor impairments, or developing a hands-free command system for your web app, the Speech Recognition API provides the foundation you need.

In this comprehensive guide, we will explore every aspect of working with the Chrome Speech Recognition API. We will cover the fundamentals of voice input implementation, discuss strategies for maximizing transcript accuracy, examine continuous recognition for extended voice capture sessions, and explore the extensive language support options that make this API accessible to a global audience. By the end of this article, you will have the knowledge and practical examples needed to integrate voice recognition into your own web projects with confidence.

## Understanding the Speech Recognition API

The Chrome Speech Recognition API is part of the larger Web Speech API specification, which provides both speech recognition and speech synthesis capabilities. The recognition portion allows browsers to capture audio input from the user's microphone and convert it into text that your JavaScript code can process. This technology leverages Google's powerful speech recognition servers to provide highly accurate results, making it significantly more capable than simple on-device speech processing.

Before you can use the API, you need to understand the browser compatibility landscape. The Speech Recognition API is primarily supported in Chrome desktop and Chrome for Android. Other browsers have varying levels of support or no support at all, so you should always implement feature detection to provide appropriate fallback experiences for users on unsupported browsers. The API is accessed through the `window.SpeechRecognition` or `window.webkitSpeechRecognition` interface, with the latter being the prefixed version used in Chrome.

The basic workflow involves creating a SpeechRecognition instance, configuring its properties, attaching event listeners to handle recognition results and errors, and then starting the recognition process. The API is designed to be asynchronous, meaning your code continues to run while the recognition happens in the background, with results delivered through events. This makes it well-suited for interactive applications where you need to respond to user speech in real-time.

## Implementing Voice Input in Your Web Application

Getting started with voice input requires understanding several key components of the SpeechRecognition interface. The first step is to create the recognition object itself, accounting for browser prefix differences. You can do this with a simple feature detection pattern that checks for both the standard and WebKit-prefixed versions:

```javascript
const SpeechRecognition = window.SpeechRecognition || window.webkitSpeechRecognition;

if (SpeechRecognition) {
  const recognition = new SpeechRecognition();
  // Configure and use the recognition object
} else {
  console.log('Speech recognition not supported in this browser');
}
```

Once you have created the recognition object, you need to configure its basic properties. The `continuous` property controls whether recognition continues throughout a session or stops after the first result. The `interimResults` property determines whether you receive results as the user speaks or only after they pause. The `maxAlternatives` property lets you specify how many possible transcriptions you want to receive for each recognized phrase. Setting these properties appropriately is crucial for achieving the user experience you want.

Starting and stopping recognition is straightforward. Call `recognition.start()` to begin listening, and the browser will request microphone permission if it has not already been granted. The recognition will continue until you call `recognition.stop()` or the user stops speaking for a period of time, depending on your configuration. You can also abort recognition mid-session using `recognition.abort()`, which stops the process without generating a final result.

Handling the results of voice recognition is where your application logic comes into play. The most important event is the `result` event, which fires when the API has recognized speech. This event contains a SpeechRecognitionResultList with one or more recognition alternatives. Each alternative includes the transcribed text and a confidence score indicating how certain the API is about the transcription. You can access these results in your event handler and use them however your application requires.
>>>>>>> consumer/a57-chrome-speech-recognition-api

Transcript accuracy represents one of the most critical factors in determining the usefulness of voice recognition functionality. Several factors influence how accurately Chrome can transcribe spoken words, including audio quality, speaker clarity, background noise, and the specific language or dialect being used. Understanding these factors allows developers to optimize their implementations and users to achieve better results.

<<<<<<< HEAD
Chrome's speech recognition engine continuously improves through machine learning, but certain techniques can help maximize accuracy in practical applications. One important approach involves providing context through grammars or custom vocabulary. The Speech Recognition API supports the defineGrammar() method, which allows developers to specify words or phrases that are particularly relevant to their application. For a medical application, for example, including medical terminology in a custom grammar can dramatically improve recognition accuracy for domain-specific vocabulary.

Another factor affecting accuracy is audio signal quality. Background noise represents one of the biggest challenges for speech recognition systems, as it can obscure the speaker's voice and lead to incorrect transcriptions. Developers should consider implementing noise reduction techniques or providing users with guidance on finding quiet environments for voice input. Applications can also implement confidence scores provided by the API to identify potentially inaccurate transcriptions and request clarification from users when confidence is low.

The continuous listening mode, while useful for extended voice input, can sometimes accumulate recognition errors over time. Implementing interim results display allows users to see real-time transcription as they speak, giving them the opportunity to correct errors immediately rather than waiting until they finish speaking. This approach significantly improves the overall accuracy of final transcriptions by involving users in the correction process.

## Mastering Continuous Recognition Mode

Continuous recognition mode represents a powerful feature of the Chrome Speech Recognition API that enables applications to process extended voice input without requiring repeated activations. Unlike single-shot recognition, which processes one utterance and then stops, continuous recognition keeps the microphone active and processes speech in real-time as long as the user continues speaking. This capability opens up numerous possibilities for voice-controlled applications, dictation systems, and accessibility tools.

Enabling continuous recognition is straightforward through the continuous property of the SpeechRecognition object:

```javascript
const recognition = new SpeechRecognition();
recognition.continuous = true;
recognition.interimResults = true;
```

When continuous mode is active, developers must implement proper event handling to manage the flow of recognized text. The onresult callback fires multiple times during a single recognition session, providing both interim results (incomplete transcriptions as the user speaks) and final results (complete transcriptions when the system detects a pause or sentence boundary). Properly distinguishing between these result types allows applications to provide responsive feedback while maintaining accurate final transcriptions.

Handling recognition errors becomes particularly important in continuous mode, as the system needs to recover gracefully from common issues such as no-speech detected or network interruptions. Implementing robust error handling ensures that temporary issues do not cause the entire voice recognition feature to fail:

```javascript
recognition.onerror = (event) => {
  if (event.error === 'no-speech') {
    console.log('No speech detected, continuing to listen...');
  } else if (event.error === 'network') {
    console.log('Network error, attempting to reconnect...');
  }
};

recognition.onend = () => {
  // Automatically restart recognition when it stops
  if (shouldContinueListening) {
    recognition.start();
  }
};
```

One consideration with continuous recognition is its impact on system resources and battery life, particularly on mobile devices. The microphone remains active, audio processing continues, and network connections must be maintained throughout the session. For mobile applications or scenarios where power conservation is important, developers might want to implement automatic pause functionality or provide users with controls to start and stop recognition manually.

## Comprehensive Language Support and Configuration

Chrome's Speech Recognition API supports an impressive range of languages and dialects, making it suitable for global applications. The API supports over 100 language variants, including regional dialects and variations such as US English, UK English, Australian English, and many others. This extensive language support enables developers to create truly international applications that can serve users in their native languages.

Setting the recognition language is accomplished through the lang property:

```javascript
recognition.lang = 'en-US'; // US English
recognition.lang = 'es-ES'; // Spanish (Spain)
recognition.lang = 'fr-FR'; // French
recognition.lang = 'de-DE'; // German
```

The language setting profoundly impacts recognition accuracy, as the speech recognition engine uses different models for each language. Users should always set the language to match what they intend to speak, as attempting to recognize speech in a language different from the one specified will result in poor accuracy. Applications serving multilingual audiences should consider implementing language detection or providing clear language selection options to users.

Beyond basic language settings, the API also supports automatic language detection in some configurations. This feature allows the system to automatically identify the language being spoken and switch recognition models accordingly. While convenient, automatic detection can sometimes be less accurate than explicitly specified languages, particularly for speakers with accents or in multilingual environments where speakers frequently switch languages.

For applications requiring support for multiple languages, implementing a language selector allows users to choose their preferred language explicitly. This approach provides the best user experience while ensuring optimal recognition accuracy. Some applications also implement language learning features that adapt to individual users' speech patterns over time, though this requires additional implementation beyond the basic API functionality.

## Performance Optimization and Browser Resource Management

While voice recognition significantly enhances user experience, it can also impact browser performance, particularly when running continuously or when multiple tabs are open simultaneously. Understanding how to optimize performance ensures that voice features remain responsive and do not negatively affect overall browser functionality.

Background tabs that use continuous speech recognition can consume significant system resources even when the user is not actively interacting with them. Tab management becomes crucial for maintaining optimal browser performance, especially for users who frequently keep many tabs open. Tools like Tab Suspender Pro can help manage resource usage by automatically suspending inactive tabs, freeing up memory and processing power for active tasks including voice recognition. This approach ensures that voice-enabled applications maintain smooth performance without being impacted by other open tabs.

Network connectivity also plays a vital role in recognition performance. The speech recognition process requires communication with Google's servers, meaning that network latency directly affects response times. Users on faster connections will experience more responsive recognition, while those on slower connections might notice slight delays between speaking and seeing results. Implementing visual loading indicators helps users understand when recognition is in progress, preventing confusion during network delays.

Memory management deserves attention in long-running voice recognition sessions. Applications should implement proper cleanup procedures when recognition is no longer needed, stopping the recognition service and releasing any associated resources. Failure to properly manage resources can lead to memory leaks and degraded browser performance over time.

## Privacy and Security Considerations

Understanding the privacy implications of voice recognition technology helps users make informed decisions about when and how to use these features. When voice recognition is active, audio from the user's microphone is transmitted to Google's servers for processing. While this data is processed to provide the transcription service, it is important to understand what happens to this data and how it might affect user privacy.

Chrome provides visual indicators to help users track microphone activity. A red recording dot appears in the browser tab or address bar whenever a website is actively using the microphone. Users should remain vigilant about this indicator and investigate any unexpected microphone activity, as it could indicate malicious websites attempting to capture audio without consent. The Permission API in Chrome allows users to check and manage microphone permissions on a per-site basis, providing granular control over which websites can access audio input.

For developers implementing voice recognition, following security best practices protects both users and applications. Always use secure HTTPS connections when deploying voice-enabled features, as browsers may restrict microphone access to secure contexts. Implement clear privacy policies explaining how voice data is handled, and consider providing options for users to control data retention or processing. These measures help build user trust while complying with privacy regulations in various jurisdictions.

Applications should also implement mechanisms to prevent accidental activation of voice recognition. Implementing push-to-talk or explicit activation controls ensures that voice recognition only occurs when users intentionally want to use it. This approach prevents unintended transcriptions and protects user privacy in shared or public computing environments.

## Building Better Voice Experiences

Creating exceptional voice-enabled applications requires attention to both technical implementation and user experience design. Beyond the core recognition functionality, thoughtful UX design helps users understand how to interact with voice features effectively. Clear instructions, visual feedback, and helpful error messages guide users through the voice interaction process.
=======
Achieving high transcript accuracy requires understanding the factors that influence recognition quality and implementing strategies to optimize performance. While the Chrome Speech Recognition API leverages Google's extensive machine learning models and achieves impressive accuracy in most scenarios, there are several things you can do to improve results further.

The first factor to consider is audio quality. The API processes audio from the user's microphone, so anything that degrades the input signal will affect accuracy. Encourage users to speak clearly and at a natural pace, avoiding mumbling or speaking too quickly. Background noise is particularly problematic, as it can cause the API to misinterpret words or fail to recognize speech entirely. In your application UI, you might consider showing users a visual indicator when audio levels are too low or too high, helping them adjust their microphone positioning or speaking volume.

The `lang` property allows you to specify the language or dialect you expect the user to speak. Setting this correctly is one of the most impactful things you can do for accuracy, as it tells the recognition engine which language model to use. If your application supports multiple languages, detect the user's preference or allow them to explicitly select their language. The API accepts language codes in the format specified by the BCP 47 standard, such as "en-US" for American English or "en-GB" for British English.

The confidence score provided with each recognition result can be valuable for quality control. When the confidence score is low, you might prompt the user to repeat themselves or display the text with a visual indicator that it may be inaccurate. You can also use confidence scores to build learning systems that adapt to individual users over time, storing corrections and using them to improve future recognition.

Another important consideration is the `maxAlternatives` property. By requesting multiple alternatives, you give yourself the ability to choose the best match or present options to the user when recognition is uncertain. This is particularly useful for applications where accuracy is critical, such as voice-powered search or transcription tools. You can implement logic that compares alternatives, checks against known vocabulary, or presents a disambiguation UI when the confidence is low.

## Continuous Recognition for Extended Sessions

Many voice recognition use cases require continuous recognition rather than single-phrase capture. Continuous recognition allows the API to continuously listen and transcribe over extended periods, making it ideal for dictation, meeting transcription, voice command systems, and other applications where users speak at length. Understanding how to implement and manage continuous recognition is essential for building these types of applications.

To enable continuous recognition, set the `continuous` property to `true` when configuring your recognition object. This tells the API to keep listening and generating results rather than stopping after the first recognized phrase. When combined with `interimResults`, you can provide real-time feedback as users speak, creating a responsive experience similar to professional dictation software.

Managing continuous recognition sessions requires careful attention to state management and error handling. The recognition process can fail for various reasons, including microphone access issues, network problems, or recognition timeouts. Your application should handle the `error` event to detect and respond to these failures gracefully. Common error types include "no-speech" when no speech is detected for a period, "audio-capture" when there are microphone problems, and "network" when the connection to Google's servers fails.

Implementing restart logic is crucial for robust continuous recognition. When an error occurs or recognition stops unexpectedly, you should automatically attempt to restart recognition to maintain the user's session. However, be careful to implement reasonable limits on restart attempts to avoid creating infinite loops or excessive resource usage. A common pattern is to attempt a limited number of automatic restarts and then present the user with options to manually restart if needed.

The `onend` event provides another opportunity to manage continuous recognition sessions. This event fires whenever recognition stops, whether due to an error, user action, or natural completion. You can use this event to determine whether to restart recognition or take other actions based on your application state. For example, you might check if the session should continue based on user activity or application state before calling `start()` again.

One advanced technique for continuous recognition is implementing custom handling for partial results. By setting `interimResults` to `true`, you receive results as the user speaks rather than waiting for complete phrases. These interim results can be displayed immediately to give users feedback that their speech is being captured, then replaced or updated with final results as the API becomes more confident. This creates a smooth, responsive experience that feels much more natural than waiting for complete phrases.

## Language Support and Internationalization

The Chrome Speech Recognition API supports an impressive range of languages and dialects, making it suitable for building applications that serve global audiences. Understanding the language support capabilities and implementing proper internationalization is crucial for reaching users in their native languages.

To use a specific language, set the `lang` property on your recognition object to the appropriate BCP 47 language code. Chrome supports dozens of language variants, from widely spoken languages like English, Spanish, Mandarin, and Hindi to less common languages and regional dialects. The exact list of supported languages may vary slightly depending on the Chrome version and operating system, but the API provides a way to query available options at runtime.

The `lang` property not only affects which language model is used but can also influence accent recognition and dialect handling. For example, setting "en-US" tells the API to expect American English pronunciation patterns, while "en-GB" adjusts for British English conventions. If your application serves users from multiple English-speaking regions, you might consider allowing users to select their preferred variant for better accuracy.

For applications that need to support multiple languages, you need to consider how to handle language switching. There are several approaches you can take. One option is to detect the user's browser language setting and default to that, then allow manual overrides. Another approach is to implement a voice command that switches languages, such as "switch to Spanish" or "hablar español." You can also create a settings interface where users explicitly select their preferred language.

Building truly international voice applications requires more than just language selection. You should also consider how your application handles multilingual users, code switching between languages, and locale-specific formatting of recognized text. The API returns raw text that may need processing for your specific use case, such as adding punctuation, handling capitalization, or converting numbers to text representations based on the detected language.

When working with languages that use non-Latin scripts, such as Chinese, Japanese, Korean, Arabic, or Cyrillic languages, you may encounter additional considerations. The API handles these scripts well, but you need to ensure your application can properly display and process the returned Unicode text. This includes using appropriate character encodings, selecting fonts that support the required scripts, and testing with native speakers to ensure the user experience meets expectations.

## Performance Optimization and Best Practices

Building efficient voice-enabled applications requires attention to performance optimization beyond just recognition accuracy. The Speech Recognition API places demands on both the microphone and network resources, so understanding how to optimize these interactions is important for creating responsive, battery-friendly applications.

One key consideration is battery impact, particularly on mobile devices. Continuous microphone access and network communication for speech processing can consume significant power. For mobile applications, consider providing a battery-saving mode that reduces continuous recognition usage or prompts users to connect to power for extended sessions. You might also implement idle detection to pause recognition when users are not actively speaking.

Memory management becomes important during extended recognition sessions. Each recognition result creates objects that consume memory until properly released. In long-running applications, monitor memory usage and ensure you are not accumulating references to old results that are no longer needed. JavaScript's garbage collection should handle most cases, but being mindful of object lifecycle helps prevent memory leaks.

Network efficiency is another critical factor. The Chrome Speech Recognition API sends audio data to Google's servers for processing, which means recognition quality and latency depend on network conditions. For the best experience, users should have a stable internet connection. On slower connections, you might consider increasing timeout values and providing feedback about network status. For offline scenarios, some browsers support on-device recognition, though with reduced accuracy and language options.

For developers building extensions or browser-integrated applications, consider how voice recognition interacts with other browser features. For instance, if you're developing something like Tab Suspender Pro, which manages browser resource usage, you need to ensure that voice recognition sessions are properly handled when tabs become inactive. Voice recognition typically requires an active tab to function, so your resource management logic should account for this requirement and provide appropriate user feedback when voice features are unavailable due to tab suspension.

## Error Handling and User Experience

Robust error handling is essential for building reliable voice-enabled applications. Users will inevitably encounter situations where speech recognition fails or produces unexpected results, and how your application handles these situations greatly impacts the overall user experience.

The API can generate several types of errors, each requiring different handling strategies. The "no-speech" error occurs when the API detects audio but cannot identify recognizable speech, which commonly happens in quiet environments or when users are not actually speaking. The "audio-capture" error indicates microphone problems, which could be due to hardware issues, permission denials, or the microphone being in use by another application. The "network" error means the connection to the speech recognition servers failed, which could be due to internet connectivity issues or server problems.

For each error type, implement appropriate user feedback and recovery mechanisms. For "no-speech" errors, you might display a friendly message encouraging the user to speak or adjust their microphone. For "audio-capture" errors, provide guidance on checking microphone connections and browser permissions. For "network" errors, inform users about connectivity issues and offer alternatives or retry options.

Beyond handling recognition errors, consider how your application handles low-confidence results. When the API returns results with low confidence, you have several options. You can display the text with a visual indicator that it may be inaccurate, present alternative interpretations for the user to choose from, or simply accept the result with a note for later review. The right approach depends on your application's tolerance for errors and how the recognized text will be used.

Testing voice recognition thoroughly is crucial for identifying and addressing issues before users encounter them. Test with various accents, speaking speeds, and audio quality levels. Pay particular attention to edge cases like background noise, multiple speakers, and unusual vocabulary. Gather feedback from diverse users to identify recognition issues that might not be apparent during development.
>>>>>>> consumer/a57-chrome-speech-recognition-api

Designing for accessibility ensures that voice features benefit all users, including those with disabilities that make traditional input methods challenging. Voice recognition provides an essential alternative input method for users with motor impairments, repetitive strain injuries, or other conditions that limit keyboard and mouse use. Following Web Content Accessibility Guidelines (WCAG) helps ensure that voice-enabled applications remain accessible to everyone.

<<<<<<< HEAD
Testing voice features across different environments, devices, and user populations reveals edge cases and usability issues that might not be apparent during development. Collecting feedback from real users helps identify confusion points, recognition errors, and opportunities for improvement. Iterative refinement based on user feedback leads to increasingly polished voice experiences that users genuinely find valuable.

The Chrome Speech Recognition API continues to evolve, with new features and improvements being added regularly. Staying current with browser updates and API changes ensures that applications can take advantage of the latest capabilities. The technology has matured significantly since its initial release, making now an excellent time to explore voice-enabled features for web applications.
=======
The Chrome Speech Recognition API provides a powerful foundation for adding voice capabilities to web applications. From basic voice input implementation to advanced continuous recognition with full internationalization support, this API enables developers to create innovative voice-powered experiences that were previously impossible in web browsers.

Remember to focus on the key factors that determine success: proper implementation of voice input handling, strategies for maximizing transcript accuracy, appropriate configuration of continuous recognition for extended sessions, and comprehensive language support for global audiences. By following the best practices outlined in this guide and paying careful attention to error handling and user experience, you can build voice recognition features that delight users and provide genuine value.

As voice interfaces become increasingly prevalent in computing, mastering APIs like Chrome's Speech Recognition API positions you to build the next generation of web applications. The technology continues to improve as Google refines its recognition engines, meaning the quality and capabilities will only get better over time. Start experimenting with voice recognition today, and discover the possibilities for your own projects.
>>>>>>> consumer/a57-chrome-speech-recognition-api

Built by theluckystrike — More tips at [zovo.one](https://zovo.one)
