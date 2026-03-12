---
title: Chrome Extension Popup Page Tutorial
description: Learn how to create a Chrome extension popup page from scratch. This
  tutorial covers HTML, CSS, JavaScript, and manifest configuration. Discover how
  these to...
date: '2026-01-20'
last_modified_at: '2026-03-11'
permalink: chrome-extension-popup-page-tutorial
layout: post
categories: '[tutorials, extensions, development]'
tags: '[chrome-extensions, popup, tutorial, web-development]'
author: theluckystrike
---
# Chrome Extension Popup Page Tutorial

If you have ever used a Chrome extension, you have probably interacted with a popup page. That small window that appears when you click the extension icon is called a popup, and it is one of the most common ways users engage with Chrome extensions. In this tutorial, you will learn how to build your own popup page from scratch, starting with the basics and progressing to a functional example you can extend for your own projects.

## What Is a Chrome Extension Popup

A **popup page** in a Chrome extension is a small interface that opens when users click the extension icon in the browser toolbar. Unlike a regular web page, a popup only appears on demand and closes when users click outside of it or press Escape. This makes popups ideal for quick actions like toggling settings, viewing information, or interacting with the current page without navigating away.

Popups are defined in the extension manifest and typically consist of an HTML file, a CSS stylesheet, and JavaScript for interactivity. The popup lives in the extension sandbox, which means it has access to Chrome-specific APIs that regular web pages do not.

## Setting Up Your Extension Structure

Before you can create a popup, you need to set up the basic file structure for your Chrome extension. Every extension requires a manifest file, and your popup will be referenced there.

Create a new folder for your extension project. Inside that folder, create the following three files: manifest.json, popup.html, and popup.js. You will also want a styles.css file for styling, though it is optional if you are comfortable with inline styles.

The manifest file tells Chrome about your extension, including its name, version, permissions, and which file to open as the popup. For a basic popup tutorial, you will use Manifest V3, which is the current standard.

## Writing the Manifest File

Open manifest.json and add the following content. This configuration gives your extension a name, version, and tells Chrome to use popup.html as the popup when the icon is clicked.

```json
{
  "manifest_version": 3,
  "name": "My First Popup Extension",
  "version": "1.0",
  "description": "A simple popup page tutorial extension",
  "action": {
    "default_popup": "popup.html",
    "default_icon": "icon.png"
  }
}
```

For this tutorial, you do not need an icon file to test the popup, so you can omit the default_icon property or create a simple placeholder image. The key property here is default_popup, which specifies which HTML file to load when the user clicks your extension icon.

## Creating the Popup HTML

Now create popup.html. This file defines the structure of your popup interface. Keep it simple for now, since you will add functionality through JavaScript.

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>My Popup</title>
  <link rel="stylesheet" href="styles.css">
</head>
<body>
  <h1>Hello, World!</h1>
  <p>Welcome to my Chrome extension popup.</p>
  <button id="action-btn">Click Me</button>
  <p id="response"></p>
  <script src="popup.js"></script>
</body>
</html>
```

This HTML creates a simple layout with a heading, some text, a button, and a placeholder for displaying responses. The script tag at the bottom includes popup.js, which will handle user interactions.

## Adding Styles

Create styles.css to make your popup look more polished. Chrome popups have a default width, and you can adjust the appearance to fit your design.

```css
body {
  width: 300px;
  padding: 16px;
  font-family: Arial, sans-serif;
  background-color: #f5f5f5;
}

h1 {
  font-size: 18px;
  color: #333;
  margin-top: 0;
}

button {
  background-color: #4285f4;
  color: white;
  border: none;
  padding: 10px 20px;
  border-radius: 4px;
  cursor: pointer;
  font-size: 14px;
}

button:hover {
  background-color: #3367d6;
}

#response {
  margin-top: 16px;
  font-size: 14px;
  color: #666;
}
```

These styles give your popup a clean, modern appearance with appropriate spacing and colors. You can customize these values to match your brand or design preferences.

## Adding Interactivity with JavaScript

Create popup.js to handle button clicks and update the popup content. This is where the real functionality of your popup comes to life.

```javascript
document.addEventListener('DOMContentLoaded', function() {
  const button = document.getElementById('action-btn');
  const response = document.getElementById('response');
  
  button.addEventListener('click', function() {
    response.textContent = 'Button clicked! Thanks for testing.';
    response.style.color = '#4285f4';
  });
});
```

This script waits for the DOM to load, then attaches a click event listener to the button. When clicked, it updates the response paragraph with a message. You can expand this to communicate with the current tab, access Chrome storage, or perform other actions using the Chrome Extensions API.

## Loading Your Extension in Chrome

Now that your files are ready, it is time to test your popup in Chrome. Open Chrome and navigate to chrome://extensions/. Enable Developer mode by toggling the switch in the top right corner. Click the Load unpacked button and select the folder containing your extension files.

Once loaded, you should see your extension icon in the Chrome toolbar. Click the icon, and your popup should appear with the heading, text, and button you defined. Click the button and watch the response appear.

## Taking It Further

This basic popup tutorial gives you a foundation you can build upon. From here, you can explore adding more complex functionality, such as communicating with the active tab using chrome.tabs, storing user preferences with chrome.storage, or adding a popup options page for more extensive settings.

You might also consider integrating your popup with other Chrome APIs to interact with bookmarks, browsing history, or browser notifications. The more you experiment, the more you will discover the flexibility that Chrome extensions offer.

## A Practical Example

If you are building a productivity-focused extension, consider how a popup can streamline common tasks. For instance, **Tab Suspender Pro** uses its popup interface to show users which tabs are currently suspended and allow them to manage suspension settings on the fly. This demonstrates how popups can serve as both a status display and a control panel for your extension's features.

Building a popup is often one of the first steps in extension development because it provides immediate, visible feedback. As you become more comfortable with the structure, you can expand your extension to include background scripts, content scripts, and additional HTML pages for more advanced functionality.

## Conclusion

Creating a Chrome extension popup page is a straightforward process once you understand the file structure and manifest configuration. By combining HTML for structure, CSS for styling, and JavaScript for interactivity, you can build popups that are both functional and visually appealing. Start with this basic tutorial, experiment with your own ideas, and you will be on your way to building powerful Chrome extensions in no time.

## Related Articles
* [Chrome DevTools Command Menu Shortcuts](/articles//chrome-devtools-command-menu-shortcuts//)
* [Chrome Status Code 502 Bad Gateway Fix](/articles/chrome-status-code-502-bad-gateway-fix/)
* [chrome reduce data usage tips](/articles/chrome-reduce-data-usage-tips/)

Built by theluckystrike — More tips at [zovo.one](https://zovo.one)
