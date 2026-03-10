---
layout: post
title: "Chrome About Pages List Explained"
description: "The complete list of Chrome internal pages (chrome:// URLs) with explanations of what each one does and when to use it."
date: 2026-03-10
categories: [features, documentation]
tags: [chrome-about-pages, browser-internals, chrome-tips, productivity]
author: theluckystrike
---

# Chrome About Pages List Explained

Chrome is much more than a simple window to the web; it is a complex operating system for web applications. To manage this complexity, Google built in dozens of internal pages—accessible via `chrome://` URLs—that provide deep insights into how the browser is performing, what data it is storing, and how you can tweak its hidden engine.

Most users only ever see the standard Settings menu, but typing `chrome://about` in your address bar reveals the full list of over 60 internal pages available in your specific version of Chrome. Understanding these pages can help you troubleshoot performance issues, enhance your privacy, and access experimental features before they reach the general public.

## Settings and Configuration Pages

These pages represent the core of Chrome's user interface for customization. While many are reachable through the triple-dot menu, using the direct URLs is often faster for power users.

| Page | What It Does |
|------|-------------|
| `chrome://settings` | The main hub for appearance, search engine, startup behavior, and basic privacy. |
| `chrome://settings/passwords` | A dedicated view to search, edit, and export saved passwords and passkeys. |
| `chrome://settings/searchEngines` | Where you can add custom search shortcuts (e.g., using `gh` to search GitHub directly). |
| `chrome://settings/performance` | Controls for Memory Saver and Energy Saver—essential for laptop users. |
| `chrome://settings/adPrivacy` | Manage Privacy Sandbox features like the Topics API and site-suggested ads. |
| `chrome://settings/content` | Granular per-site permissions for camera, microphone, location, and JavaScript. |
| `chrome://settings/help` | Triggers a manual check for updates and displays your exact version number. |

## Extension and App Management

Extensions are the lifeblood of a customized browsing experience, but they can also be the primary cause of memory bloat.

**`chrome://extensions`** is the command center for your add-ons. Here, you can enable or disable tools, view detailed permissions, and toggle "Developer mode" to load unpacked extensions from your hard drive. If you find your browser lagging, this is the first place to look to see which extensions are running. 

For users who rely on many extensions for productivity, managing them effectively is key. Tools like **Tab Suspender Pro** complement these built-in management pages by automatically handling the memory load of inactive tabs, ensuring that even if you have dozens of extensions and hundreds of tabs, your browser remains responsive.

**`chrome://apps`** lists installed Chrome Apps. While Google deprecated Chrome Apps for most platforms in 2022, this page may still show legacy apps or shortcuts to Progressive Web Apps (PWAs).

## Diagnostics and Debugging

This is where Chrome gets truly interesting for power users and developers. These pages provide a window into the "black box" of browser operations.

**`chrome://flags`** is perhaps the most famous internal page. It contains hundreds of experimental features that are currently being tested by Google engineers. You can find everything from AI-powered tab organization to new CSS rendering engines. However, be cautious: these features are experimental for a reason and can occasionally cause instability. If a flag breaks your browser, the "Reset all" button at the top is your safety net.

**`chrome://net-internals`** is a sophisticated network diagnostics toolkit.
- **DNS tab:** Allows you to view and clear Chrome's internal DNS cache. This is a common fix when a specific website won't load even though your internet connection is otherwise fine.
- **Sockets tab:** Shows active network connections and allows you to "flush" or close stuck sockets that might be hanging a page load.
- **HSTS tab:** Useful for developers to query and delete HSTS (HTTP Strict Transport Security) entries for specific domains.

**`chrome://gpu`** provides an exhaustive report on how Chrome is interacting with your graphics hardware. It shows whether hardware acceleration is active and lists any known driver bugs that might be causing visual glitches or slow video playback.

**`chrome://discards`** is an incredibly useful page for understanding how Chrome manages memory. It displays a list of every open tab and its current "lifecycle state." You can see which tabs are active, which have been "frozen" (their JavaScript execution paused), and which have been "discarded" (completely unloaded from memory while keeping the tab visible). It even provides a "Discard" button next to each tab, allowing you to manually free up RAM without closing the tab itself.

## Advanced System Information

For those who need to know exactly what is happening under the hood, these pages provide the data.

**`chrome://version`** is the most important page to visit when filing a bug report. it lists your Chrome version, operating system, the version of the V8 JavaScript engine, and—most importantly—your "Profile Path," which tells you exactly where on your hard drive your bookmarks and settings are stored.

**`chrome://tracing`** is a deep-dive performance tool. It allows you to record "traces" of everything Chrome does for a few seconds—every process, every thread, and every millisecond of CPU time. This is primarily for developers trying to find the root cause of a specific performance "jank" or lag.

**`chrome://media-internals`** tracks every video and audio stream currently or recently active in the browser. It shows the codecs being used, any playback errors, and the buffering status. If Netflix or YouTube is stuttering, this page will tell you why.

**`chrome://webrtc-internals`** is the equivalent for real-time communication. If you are having trouble with a Google Meet or Zoom call in the browser, this page provides real-time graphs of your bitrates, packet loss, and jitter.

## Troubleshooting with Internal Pages

When Chrome starts acting up, you can use these pages as a logical diagnostic flow:
1. **Is it a network issue?** Check `chrome://net-internals/#dns` and clear the cache.
2. **Is it a rendering issue?** Check `chrome://gpu` for hardware acceleration errors.
3. **Is it a memory issue?** Use `chrome://discards` to see which tabs are eating your RAM.
4. **Is it an extension issue?** Use `chrome://extensions` to disable plugins one by one.
5. **Is it a corrupted profile?** Check `chrome://version` to find your profile path and consider creating a new one.

By mastering these `chrome://` URLs, you transition from a passive user to an active administrator of your browsing environment. Whether you're just curious about the underlying technology or you're a developer needing precise data, these pages are the key to unlocking Chrome's full potential.

Built by theluckystrike — More tips at [zovo.one](https://zovo.one)

