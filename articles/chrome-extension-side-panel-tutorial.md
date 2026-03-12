---
title: "Chrome Extension Side Panel Tutorial"
description: "Learn how to build a Chrome extension with side panel support. This comprehensive tutorial covers manifest configuration, HTML/CSS/JS implementation, and bes..."
date: "2026-03-11"
last_modified_at: "2026-03-11"
permalink: "chrome-extension-side-panel-tutorial"
layout: "default"
categories: "[chrome, extensions, development, tutorials]"
tags: "[chrome-extension, side-panel, chrome-dev, extension-development, manifest-v3]"
author: "theluckystrike"
---

# Chrome Extension Side Panel Tutorial

Chrome's side panel API has opened up exciting possibilities for extension developers. Unlike traditional popup windows that appear and disappear, side panel extensions provide a persistent, always-accessible interface that stays alongside the user's browsing content. This tutorial walks you through building a Chrome extension with side panel functionality, from manifest configuration to final implementation.

## Understanding the Side Panel API

The side panel API was introduced in Chrome 114 and represents a significant improvement over older approaches. Previously, developers had to use browser action popups or content scripts to create persistent interfaces, each with significant limitations. Side panels solve these problems by providing a dedicated space that users can toggle on and off while maintaining full access to the page content.

Side panel extensions are particularly useful for productivity tools, note-taking applications, reference managers, and any extension where users need to interact with your interface while browsing. The persistent nature of side panels means users don't have to keep reopening your extension—they can leave it open and reference it throughout their browsing session.

To use the side panel API, your extension must target Manifest V3, which is now the standard for Chrome extensions. This tutorial assumes you have basic familiarity with HTML, CSS, and JavaScript, as well as access to Chrome or a Chromium-based browser for testing.

## Setting Up Your Manifest

The foundation of any Chrome extension is its manifest.json file. For side panel support, you'll need to specify the appropriate permissions and declare your side panel HTML file. Here's a minimal manifest configuration to get started:

```json
{
  "manifest_version": 3,
  "name": "My Side Panel Extension",
  "version": "1.0",
  "description": "A tutorial extension with side panel support",
  "permissions": ["sidePanel"],
  "side_panel": {
    "default_path": "sidepanel.html"
  },
  "action": {
    "default_title": "Open Side Panel"
  },
  "permissions": ["sidePanel", "storage"]
}
```

The key addition here is the "side_panel" object, which tells Chrome which HTML file to load in your side panel. The "sidePanel" permission is required to use the API. I've also included the "storage" permission, which you'll likely need for saving user preferences or data.

You also need to grant the sidePanel permission in the permissions array. Note that you cannot request host permissions for the side panel—it operates in its own isolated context, separate from web pages.

## Creating the Side Panel HTML

Your side panel needs its own HTML file that will be loaded when users open the panel. This file operates independently from web pages, so it won't have access to page content directly. Here's a basic structure:

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>My Extension</title>
  <style>
    body {
      width: 300px;
      padding: 16px;
      font-family: system-ui, sans-serif;
    }
    .container {
      display: flex;
      flex-direction: column;
      gap: 12px;
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>My Side Panel</h1>
    <p>Welcome to my extension!</p>
  </div>
  <script src="sidepanel.js"></script>
</body>
</html>
```

The styling here uses a fixed width, which is important because side panels have limited space. The container uses flexbox for clean layout, and the system font stack ensures consistent appearance across different operating systems.

## Implementing Extension Logic

Now you'll create the JavaScript file that handles user interactions and extension functionality. This script runs in the context of your side panel:

```javascript
// sidepanel.js
document.addEventListener('DOMContentLoaded', () => {
  // Your extension logic here
  console.log('Side panel loaded');
  
  // Example: Handle button clicks
  const actionButton = document.getElementById('actionBtn');
  if (actionButton) {
    actionButton.addEventListener('click', handleAction);
  }
});

function handleAction() {
  // Perform your extension's main function
  chrome.storage.local.get(['userData'], (result) => {
    console.log('Stored data:', result.userData);
  });
}
```

The side panel has access to most Chrome extension APIs, including storage, runtime, and tabs. However, it cannot directly access the DOM of the current web page—that requires a content script running on the page itself.

## Enabling the Side Panel

Users need a way to open your side panel. The most common approach is to add a browser action that opens the panel when clicked. Create a background script to handle this:

```javascript
// background.js
chrome.action.onClicked.addListener((tab) => {
  // Open the side panel
  chrome.sidePanel.open({ tabId: tab.id });
});

// Optionally, set the panel to open automatically on certain pages
chrome.runtime.onInstalled.addListener(() => {
  chrome.sidePanel.setOptions({
    default: { enabled: true }
  });
});
```

This background script listens for clicks on your extension's toolbar icon and opens the side panel for the current tab. Users can also right-click the icon to access additional options.

## Advanced: Communicating Between Contexts

Many extensions need to share data between the side panel and content scripts running on web pages. This requires the message passing API. From your side panel, you can send messages to content scripts:

```javascript
// From sidepanel.js
chrome.tabs.query({ active: true, currentWindow: true }, (tabs) => {
  chrome.tabs.sendMessage(tabs[0].id, { action: 'getData' }, (response) => {
    console.log('Response from page:', response);
  });
});
```

Your content script would listen for these messages:

```javascript
// content script
chrome.runtime.onMessage.addListener((message, sender, sendResponse) => {
  if (message.action === 'getData') {
    sendResponse({ data: 'Page data here' });
  }
});
```

This bidirectional communication allows your side panel to display information from the current page, process data, and return results—all without requiring users to navigate away from their content.

## Best Practices for Side Panel Extensions

When developing side panel extensions, keep these recommendations in mind for the best user experience. First, optimize for the constrained space—side panels typically display at 300-400 pixels width, so design your UI to work within these limitations. Use collapsible sections, tabs, or accordions to organize content efficiently.

Performance matters in side panels because they remain open during browsing. Avoid heavy computations or excessive API calls that could slow down the browser. Use lazy loading for optional features and cache data appropriately.

Consider accessibility by ensuring your side panel works with keyboard navigation and screen readers. Use semantic HTML, proper ARIA labels, and maintain focus management when opening or closing panels.

Finally, test your extension across different screen sizes and with Chrome's side panel resizing. Users may have smaller screens or prefer narrower panels, so your design should remain functional at various widths.

## Conclusion

Building a Chrome extension with side panel support opens up powerful possibilities for creating persistent, user-friendly tools. The side panel API provides a clean way to offer always-available functionality without interrupting the browsing experience. By following this tutorial, you've learned the foundational concepts needed to create your own side panel extensions.

Extensions like Tab Suspender Pro demonstrate how side panels can deliver significant value by providing convenient access to extension controls while users browse. With these basics in place, you can expand your extension with additional features like bookmarks management, note-taking capabilities, or any other functionality that benefits from persistent side-panel access.

Start experimenting with your own side panel extension today, and remember to test thoroughly before publishing to the Chrome Web Store.

Built by theluckystrike — More tips at [zovo.one](https://zovo.one)
