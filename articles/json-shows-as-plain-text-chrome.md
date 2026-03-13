---
layout: default
title: "JSON Shows as Plain Text in Chrome: Fix It in Under 2 Minutes"
description: "JSON displaying as raw unformatted text in Chrome? Here's exactly why it happens and how to fix it for both API responses and local files, with permanent solutions."
date: 2026-03-14
last_modified_at: 2026-03-14
permalink: /json-shows-as-plain-text-chrome/
categories: [problem-solution, developer-tools]
tags: [chrome, troubleshooting, json shows as plain text chrome, json formatting, chrome json viewer]
author: Michael Lip
target_keyword: "json shows as plain text chrome"
target_extension: "json-formatter-pro"
word_count: 1260
reading_time: 5
canonical_url: "https://zovo.one/json-shows-as-plain-text-chrome/"
---

JSON appears as plain, unformatted text in Chrome when the server sends the wrong Content-Type header or when no formatting extension is installed. Chrome's built-in JSON viewer only activates when it receives content labeled `application/json` in the HTTP response. Anything labeled `text/plain`, `text/html`, or sent without a Content-Type header at all displays as a wall of raw text. The fastest fix for API responses is opening Chrome DevTools (F12), going to the Network tab, and clicking the "Preview" tab for the JSON request: Chrome formats the response there regardless of headers. For a permanent solution, a JSON formatter extension handles it automatically on every page.

Last tested: March 2026, Chrome 123 stable.

> "Does Chrome have a built-in JSON viewer? Yes, but it only activates when the server sends the correct application/json Content-Type header. Legacy and development servers frequently send text/plain instead."
> [Top 5 JSON Viewer Chrome Extensions You Need To Check Out, ful.io](https://ful.io/blog/top-5-json-viewer-chrome-extensions-you-need-to-check-out)

## Why JSON Shows as Plain Text in Chrome

### The Server Is Sending the Wrong Content-Type Header

This is the most common cause. Chrome inspects the `Content-Type` header of every HTTP response to decide how to render it. A response carrying `Content-Type: text/plain` gets rendered as plain text, even if the content is perfectly valid JSON. Many legacy APIs, development servers (Flask in debug mode, Python's SimpleHTTPServer), and misconfigured Nginx or Apache setups send `text/plain` for `.json` endpoints. Chrome does not do content sniffing for JSON by default, so it trusts the header entirely.

> "Valid JSON must use double-quoted strings and forbids trailing commas per RFC 8259. Chrome's built-in formatter validates against this standard before rendering structured output."
> [JSON - JavaScript Reference - MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON)

### Content Security Policy Blocks the Formatting Script

Websites that set strict Content-Security-Policy headers can block Chrome from injecting the JavaScript that drives formatted JSON display. When a CSP rule includes `script-src 'self'` without `'unsafe-inline'`, Chrome's JSON formatter, which relies on inline script injection, cannot run. The response displays as plain text without any error message, leaving developers confused about why formatting stopped working on a specific host.

### The File Exceeds Chrome's Formatting Size Limit

Chrome disables its JSON formatter for responses larger than 5 MB. This limit exists to prevent the browser from consuming excessive memory rendering large tree structures. Database exports, bulk API responses, and log files frequently exceed this size, resulting in raw text output regardless of the Content-Type header. The DevTools Preview tab has a higher threshold and handles files up to around 10 MB before switching to a simplified view.

### No JSON Extension Is Installed, or the Extension Lacks Permissions

Chrome's built-in JSON formatter is minimal. Without a dedicated extension, all formatting is contingent on correct server headers and file size limits. If you have a JSON extension installed but it only works on `http://` and `https://` URLs, JSON files opened from the local filesystem via `file://` protocol will still display as plain text.

## Step-by-Step Fixes

### Fix 1: Use DevTools Preview Tab for Immediate Formatted Viewing

1. Open the page or API URL in Chrome.
2. Press `F12` or `Ctrl+Shift+I` (Windows) / `Cmd+Option+I` (Mac) to open DevTools.
3. Click the Network tab.
4. Reload the page or trigger the API request.
5. Click the request entry in the network list.
6. Select the "Preview" tab instead of "Response."

Chrome formats JSON in the Preview tab regardless of Content-Type headers or CSP rules. The tree view is fully interactive: click any node to collapse or expand it. This works for files up to approximately 10 MB and requires no installation or configuration.

### Fix 2: Install a JSON Formatter Extension

For a permanent automatic fix on every JSON URL you visit:

1. Open the Chrome Web Store and search "JSON Formatter Pro."
2. Click "Add to Chrome."
3. After installation, navigate to `chrome://extensions/`, find the extension, click "Details."
4. Enable "Allow access to file URLs" if you need formatting on local files.
5. Visit any JSON URL.

JSON Formatter Pro intercepts responses before Chrome renders them, inspects the content body, and applies formatting regardless of the Content-Type header. It catches the server misconfiguration scenario and the CSP scenario by formatting at the extension layer rather than the page layer.

### Fix 3: Use a Bookmarklet to Force JSON Formatting

For situations where extensions are unavailable (locked-down corporate Chrome, Chromebook managed environments):

1. Create a new bookmark in Chrome.
2. Set the URL field to this JavaScript code (copy exactly):
`javascript:(function(){try{var j=JSON.parse(document.body.innerText);document.body.innerHTML='<pre style="white-space:pre-wrap;word-break:break-all">'+JSON.stringify(j,null,2)+'</pre>';}catch(e){alert('Not valid JSON: '+e);}})();`
3. When viewing a plain-text JSON page, click the bookmark.

The bookmarklet parses the raw text as JSON and re-renders it as formatted output in the same tab. It works on valid JSON only: malformed JSON triggers the alert message with the specific parse error, which is useful for debugging.

### Fix 4: Fix the Server's Content-Type Header

If you control the API server producing incorrect headers, this is the correct long-term fix:

For Nginx, add inside the location block:
`add_header Content-Type application/json;`

For Apache, add to `.htaccess` or the virtual host config:
`AddType application/json .json`

For Python Flask:
`return Response(json_data, mimetype='application/json')`

For Node.js/Express:
`res.setHeader('Content-Type', 'application/json');`

Correcting the header means Chrome's built-in viewer activates automatically without requiring any extension or workaround on the client side.

### Fix 5: Override Headers Using a Header Modification Extension

If you cannot change the server but need consistent formatting on a specific API:

1. Install "ModHeader" or "Header Editor" from the Chrome Web Store.
2. Create a response header rule.
3. Set the URL pattern to match your API endpoint.
4. Set the header name to `Content-Type` and value to `application/json`.
5. Enable the rule.

Chrome now receives the response with the correct header and activates its built-in JSON formatter automatically. This approach is useful for development workflows where you need to frequently inspect a third-party API that returns incorrect headers.

## Quick Fix Summary

| Root Cause | Fix | Works Without Extensions |
|---|---|---|
| Wrong Content-Type header | DevTools Preview tab | Yes |
| Large file over 5 MB | DevTools Preview tab (up to 10 MB) | Yes |
| CSP blocking formatter | Install JSON Formatter Pro | No |
| Local file via file:// | Enable file access in extension settings | No |
| Need permanent auto-formatting | JSON Formatter Pro | No |

## When to Try Alternative Solutions

The DevTools approach works for development sessions but requires manual steps every time. For teams where multiple developers work with the same APIs, distributing a consistent JSON formatter extension is more reliable than documenting a DevTools workaround. JSON Formatter Pro specifically handles the CSP-blocked scenario that the DevTools Preview tab resolves, plus adds features like JSON validation, schema checking, and one-click path copying for navigating nested objects.

> "The best JSON formatter tools in 2025 balance three features: large file handling, CSP compatibility, and response interception that catches incorrect Content-Type headers automatically."
> [Best JSON Formatter Tools 2025, superjson.ai](https://superjson.ai/blog/2025-08-10-best-json-formatter-tools-comparison/)

JSON Formatter Pro weighs 738 KiB, carries a 4.8/5 rating, and was last updated March 2, 2026. Its interception layer processes formatting before Chrome renders the response, making it effective regardless of server configuration. The extension handles files up to 10 MB with collapsible tree navigation, error highlighting for malformed JSON, and a raw/formatted toggle that lets you switch between the original and formatted views without reloading.

**[Try JSON Formatter Pro Free at zovo.one](https://zovo.one)**

## FAQ

### Why does Chrome show raw JSON instead of formatted output?

Chrome only formats JSON automatically when the server sends the `application/json` Content-Type header. If the server sends `text/plain` or no header, Chrome renders it as plain text. Installing a JSON formatter extension removes the dependency on correct server headers by intercepting and formatting the content directly.

### How do I get Chrome to display JSON in a readable format permanently?

Install a JSON formatter extension and enable it for both web URLs and (if needed) local files by granting file access permission in `chrome://extensions/`. The extension then automatically formats every JSON response without any manual action on your part.

### Does Chrome have a built-in JSON viewer?

Yes. Chrome activates a built-in JSON tree viewer for responses with `Content-Type: application/json`. It supports collapsible nodes and basic syntax coloring. It does not handle `text/plain` responses, files over 5 MB, or local `file://` URLs. Extensions extend this capability significantly.

### Why does some JSON display correctly but not others in Chrome?

The difference is almost always the Content-Type header. APIs and JSON files served by correctly configured servers activate Chrome's built-in viewer. Poorly configured servers, development servers, and local files do not send the header Chrome expects. The DevTools Preview tab or a formatter extension bridges this inconsistency.

---

Built by Michael Lip — More tips at [zovo.one](https://zovo.one)
