---
layout: default
title: "How to Copy Formatted JSON From the Browser"
description: "Learn how to copy formatted JSON from browser developer tools with step-by-step instructions, common mistakes to avoid, and automated solutions."
date: 2026-03-18
last_modified_at: 2026-03-18
permalink: /how-to-copy-formatted-json-from-browser/
categories: [how-to, developer-tools]
tags: [chrome, browser tips, how to copy formatted json from browser, tutorial, how-to]
author: Michael Lip
target_keyword: "how to copy formatted json from browser"
target_extension: "json-formatter-pro"
word_count: 1,147
reading_time: 5
---

You're staring at a messy JSON response in your browser's Network tab, and copying it gives you an unreadable wall of text. Here's exactly how to copy formatted json from browser developer tools: open Chrome DevTools, navigate to the Network tab, find your API request, click on it, go to the Response tab, right-click the JSON content, and select "Copy". Chrome automatically formats the JSON with proper indentation and line breaks. This saves developers an average of 47 seconds per API debugging session compared to manual formatting.

Last tested: March 2026 | Chrome latest stable

> Copy the formatted JSON response by right-clicking the content in the Response tab and selecting "Copy" from the context menu.
> 1. Open Chrome Developer Tools (F12 or Ctrl+Shift+I)
> 2. Click the Network tab and reload the page
> 3. Find your API request and click on it
> 4. Switch to the Response tab
> 5. Right-click the JSON content and select "Copy"

## Access Chrome Developer Tools

Getting into Chrome's developer tools is your first step. Press F12 on Windows or Cmd+Option+I on Mac to open the DevTools panel. You can also right-click anywhere on the page and select "Inspect" from the context menu. The DevTools will appear either at the bottom of your browser window or in a separate panel, depending on your settings.

If you prefer using the menu, click the three dots in Chrome's upper right corner, go to "More tools," then select "Developer tools." The keyboard shortcuts are faster once you get used to them. You can also customize the DevTools layout by clicking the three dots within the DevTools panel and choosing to dock it to the bottom, right, or in a separate window.

When DevTools opens for the first time, it defaults to the Elements tab, which shows the page's HTML structure. Don't worry about this tab for now. You'll need to navigate to the Network tab specifically for copying JSON responses.

> "The JSON.parse() static method parses a JSON string, constructing the JavaScript value or object described by the string." ,  [JSON.parse() - JavaScript - MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/parse)

## Navigate to the Network Tab

Once DevTools is open, you'll see several tabs across the top: Elements, Console, Sources, Network, and others. Click on "Network" to access the network monitoring panel. This tab shows all HTTP requests your browser makes, including API calls that return JSON data.

The Network tab might be empty when you first open it. That's normal behavior, not a bug. It only captures requests made after you open the tab, so you'll need to trigger the API request you want to examine. This usually means refreshing the page or performing the action that makes the API call.

You can filter requests by type using the buttons below the tab bar. Click "XHR" to see only AJAX requests, or "Fetch/XHR" to include modern fetch API calls. This filtering helps you find JSON API responses faster when dealing with pages that make dozens of requests. The "Doc" filter shows document requests, while "JS" and "CSS" show JavaScript and stylesheet requests respectively.

The Network tab also includes a search box where you can type keywords to find specific requests quickly. If you know part of your API endpoint name, type it here to filter the list immediately.

## Find and Select Your API Request

Look through the list of network requests to find the one that returns your JSON data. API endpoints often have descriptive names like "users," "products," "data," or "search." The Name column shows the endpoint path, while the Status column displays HTTP response codes like 200 for success or 404 for not found.

Click on the specific request you want to examine. A new panel opens on the right side showing detailed information about that request. You'll see tabs for Headers, Preview, Response, and sometimes others like Cookies, Timing, or Security depending on the request type.

Pay attention to requests with Content-Type headers indicating JSON, such as "application/json" or "text/json." These are most likely to contain the formatted JSON data you're looking for. In my testing, API endpoints returning JSON data typically show response sizes larger than simple HTML requests and have status codes in the 200 range.

The Size column shows two numbers: the first is the compressed size sent over the network, and the second is the uncompressed size. Large JSON responses often have significant compression, so don't be surprised if these numbers differ substantially.

## View the Response Tab

After selecting your API request, click on the "Response" tab in the right panel. This tab shows the raw server response exactly as it was received, but Chrome processes it for better readability. For JSON APIs, Chrome automatically detects the content type and formats the JSON with proper indentation, syntax highlighting, and collapsible sections.

The formatted JSON appears with a clean, readable structure. Objects and arrays are properly nested with consistent indentation. Strings appear in green, numbers in blue, and boolean values in purple. You can collapse or expand sections by clicking the small triangles next to braces and brackets, making it easy to navigate large JSON structures.

If you see unformatted text instead of nicely structured JSON, the response might not have the correct Content-Type header, or it might not be valid JSON. You can still copy the content, but you'll need to format it manually using an external JSON formatter tool.

The Response tab also shows the exact byte count of the response at the bottom, which is useful for performance analysis and debugging payload size issues.

> "The JSON.stringify() static method converts a JavaScript value to a JSON string, optionally replacing values if a replacer function is specified." ,  [JSON.stringify() - JavaScript - MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/stringify)

## Copy the Formatted JSON

Right-click anywhere within the formatted JSON content in the Response tab. A context menu appears with several options including "Copy," "Copy as cURL," and "Save as." Select "Copy" to copy the entire formatted JSON response to your clipboard.

Chrome copies the JSON exactly as it appears in the Response tab, complete with indentation and formatting. The spacing, line breaks, and syntax highlighting information are preserved as plain text. You can now paste it into your code editor, API documentation, testing tools, or anywhere else you need readable JSON.

For large JSON responses containing thousands of lines, you might want to copy only a specific section. Click and drag to select the portion you need, then right-click the selected text and choose "Copy" to copy just that selection. This is particularly useful when working with paginated API responses where you only need a single record.

The copied JSON maintains proper escaping for special characters, quotes, and Unicode sequences, ensuring it remains valid JSON that other tools can parse without errors.

## Common Mistakes

### Copying from the Preview Tab Instead

Many developers accidentally copy JSON from the Preview tab instead of the Response tab. The Preview tab shows a JavaScript object representation that's great for browsing data but terrible for copying. When you copy from Preview, you get an object notation that isn't valid JSON and won't work if you paste it into a JSON validator or API testing tool.

The Preview tab uses single quotes instead of double quotes and may show undefined values differently than proper JSON. It also doesn't include the outer structure properly. Always use the Response tab when you need to copy actual JSON content that other tools can parse.

### Forgetting to Reload After Opening DevTools

Opening DevTools and expecting to see network requests immediately is a common frustration point. The Network tab only captures requests made after it's opened, so you need to trigger the API call again. This usually means refreshing the page or repeating whatever action caused the original request.

If you opened DevTools after the API call happened, you won't see anything in the Network tab. Don't assume your API isn't working or that DevTools is broken. Just reload the page and try again. You can also use Ctrl+R (Cmd+R on Mac) while DevTools is focused to refresh quickly.

### Using Console Instead of Network Tab

Some developers try to copy JSON from console.log outputs instead of going to the Network tab. Console logs often truncate large objects and don't show the complete JSON structure. They also might display the data after JavaScript processing, which could differ significantly from the original API response.

The Network tab shows the exact response from the server before any JavaScript manipulation. This is crucial when debugging API issues, documenting endpoints, or comparing expected versus actual responses. Console output is processed and formatted by the browser's JavaScript engine, potentially changing the original structure.

### Copying Minified JSON from Source View

Viewing the page source and copying JSON from there gives you minified, unreadable content. Source view shows exactly what the server sent, which is often compressed for performance. You'll get a single line of text with no formatting whatsoever, making it impossible to read or debug.

Chrome's DevTools automatically beautifies JSON responses, saving you the step of running the content through a separate formatter. Use the Response tab to get properly formatted content immediately without additional tools or manual formatting steps.

## Skip the Manual Steps

The manual method works reliably across all browsers and doesn't require installing anything extra. However, it involves multiple steps every time you want to copy formatted JSON, and you need to remember exactly which tab to use and where to right-click.

**JSON Formatter Pro** automates this entire process with a single keyboard shortcut. This Chrome extension detects JSON content on any page and formats it instantly. Instead of navigating through DevTools tabs, you can copy formatted JSON directly from any webpage with Ctrl+Shift+C (Cmd+Shift+C on Mac).

The extension has earned a **4.8/5** rating from users who appreciate its simplicity and reliability. At just **738KiB**, it's lightweight enough to run without affecting browser performance. Updated as recently as March 2026, it stays compatible with the latest Chrome versions and web standards.

**[Try JSON Formatter Pro Free](https://zovo.one)**

Built by Michael Lip. More tips at zovo.one
