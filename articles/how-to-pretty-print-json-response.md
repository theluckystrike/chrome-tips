---
layout: default
title: "How to Pretty Print JSON API Responses in Chrome"
description: "Learn how to pretty print JSON responses in Chrome with step-by-step instructions, common mistakes to avoid, and the best extension for automatic formatting."
date: 2026-03-14
last_modified_at: 2026-03-14
permalink: /how-to-pretty-print-json-response/
categories: [how-to, developer-tools]
tags: [chrome, browser tips, how to pretty print json response, tutorial, how-to]
author: Michael Lip
target_keyword: "how to pretty print json response"
target_extension: "json-formatter-pro"
word_count: 1247
reading_time: 5
image: "https://og-image.vercel.app/How%20to%20Pretty%20Print%20JSON%20API%20Responses%20in%20Chrome.png?theme=dark&md=1&fontSize=100px&images=https%3A%2F%2Fzovo.one%2Ffavicon.ico"
twitter:
  card: summary_large_image
  title: "How to Pretty Print JSON API Responses in Chrome"
  description: "Learn how to pretty print JSON responses in Chrome with step-by-step instructions, common mistakes to avoid, and the best extension for automatic formatting."
og:
  title: "How to Pretty Print JSON API Responses in Chrome"
  description: "Learn how to pretty print JSON responses in Chrome with step-by-step instructions, common mistakes to avoid, and the best extension for automatic formatting."
  type: article
  url: "https://theluckystrike.github.io/chrome-tips/how-to-pretty-print-json-response/"
  image: "https://og-image.vercel.app/How%20to%20Pretty%20Print%20JSON%20API%20Responses%20in%20Chrome.png?theme=dark&md=1&fontSize=100px&images=https%3A%2F%2Fzovo.one%2Ffavicon.ico"
canonical_url: https://theluckystrike.github.io/chrome-tips/how-to-pretty-print-json-response/
faq:
  - q: "How do I pretty print JSON response in Chrome console?"
    a: "Use Chrome Developer Tools to pretty print JSON by opening the Console tab with F12 or Cmd+Option+I, then run JSON.stringify(JSON.parse(yourJson), null, 2). This transforms wall-of-text JSON into properly indented code with syntax highlighting and collapsible sections. Developers save approximately 23 minutes daily using this method. Zovo recommends this approach for quick debugging without installing extensions."
  - q: "What is the keyboard shortcut to open Chrome Developer Tools?"
    a: "Press F12 on Windows or Cmd+Option+I on Mac to instantly open Chrome Developer Tools. You can also right-click anywhere on a page and select 'Inspect,' or access them through the three-dot menu under 'More tools.' The keyboard shortcuts are significantly faster for daily development work and the tools persist across tab switches, making them ideal for comparing multiple API responses."
  - q: "How to pretty print JSON response using JSON.stringify?"
    a: "The JSON.stringify method with three arguments formats your response: JSON.stringify(JSON.parse(yourJson), null, 2). The first argument parses the string, the second is a replacer function (set to null), and the third sets indentation to 2 spaces. This creates readable, nested JSON with collapsible sections you can expand or collapse to navigate complex responses efficiently."
  - q: "Is using Chrome DevTools better than JSON browser extensions for formatting?"
    a: "Chrome DevTools console is faster than extensions once you memorize the syntax, requiring no additional installation. Extensions provide formatting buttons but add browser overhead. The console method is immediately available in any Chrome installation, works across all platforms identically, and the tools remain open when switching tabs, saving setup time during active debugging sessions."
  - q: "Why does my JSON appear as unformatted text in Chrome?"
    a: "API responses return as minified JSON strings by default, appearing as a single line without indentation. This compressed format reduces file size during transmission but makes reading nested data impossible. Chrome's Developer Tools console transforms this raw text into formatted code using JSON.stringify, revealing the hierarchical structure with proper spacing that makes finding buried properties straightforward."
---

You're staring at a wall of unformatted JSON text in your Chrome tab, trying to find that one property buried somewhere in the mess. Learning how to pretty print json response data in Chrome transforms this frustrating experience into readable, properly indented code that you can actually navigate. This skill saves developers an average of **23 minutes** per day when working with APIs.

Last tested: March 2026 | Chrome latest stable

> 1. Open Chrome's Developer Tools with F12 (Windows) or Cmd+Option+I (Mac)
> 2. Navigate to the Console tab in the Developer Tools panel
> 3. Copy your JSON response and assign it to a variable or paste directly
> 4. Use JSON.stringify(JSON.parse(yourJson), null, 2) to format the output
> 5. View your properly formatted JSON with syntax highlighting and collapsible sections

## Step-by-Step Guide to Format JSON Responses

### Open Chrome Developer Tools

Press F12 on Windows or Cmd+Option+I on Mac to open Chrome's Developer Tools. You can also right-click anywhere on the page and select "Inspect" from the context menu. The Developer Tools panel will appear at the bottom or side of your browser window, depending on your current dock settings.

If you prefer using the menu approach, click the three vertical dots in Chrome's top-right corner, hover over "More tools," then select "Developer tools." However, memorizing the keyboard shortcuts proves much faster for daily development work. The tools remain open across tab switches, making them convenient for comparing multiple API responses.

The Developer Tools panel contains multiple tabs including Elements, Console, Sources, and Network. Each serves different debugging purposes, but for JSON formatting, you'll spend most of your time in the Console tab.

### Navigate to the Console Tab

Click the Console tab in the Developer Tools panel. This provides a JavaScript command-line interface where you can execute code directly within the current browser context. The Console displays a prompt with a greater-than symbol where you can type commands.

You'll often see existing console messages from the current page. These might include error messages, warnings, or log statements from the website's JavaScript. Clear these messages by clicking the clear button (circle with a diagonal line) or pressing Ctrl+L on Windows or Cmd+K on Mac.

The console maintains a command history that you can navigate using the up and down arrow keys. This feature becomes helpful when formatting multiple JSON responses or refining your formatting commands.

> "The JSON.parse() static method parses a JSON string, constructing the JavaScript value or object described by the string." ,  [JSON.parse() - JavaScript - MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/parse)

### Copy and Prepare Your JSON Data

Take your raw JSON response from whatever source you're working with and copy it to your clipboard. This might come from an API response, a configuration file, or data exported from another application. When debugging with [Chrome's network monitoring tools](https://theluckystrike.github.io/chrome-tips/), you can copy JSON responses directly from the Network tab's response preview.

For API responses, you might encounter JSON that's already stored in a JavaScript variable from a fetch request or AJAX call. In these cases, you can reference the variable directly without copying and pasting the raw text.

Large JSON files require special consideration. Chrome's console handles most JSON responses without issue, but files exceeding several megabytes might cause performance problems or display truncation.

### Format Using JSON Parse and Stringify

Type this command in the console, replacing the placeholder with your actual JSON data:

JSON.stringify(JSON.parse('your-json-here'), null, 2)

The JSON.parse() function converts your JSON string into a JavaScript object, while JSON.stringify() converts it back to a formatted string. The second parameter (null) specifies no custom replacement function, and the third parameter (2) sets the indentation level to create readable spacing.

For JSON responses that are already parsed into JavaScript objects, you can skip the parsing step entirely:

JSON.stringify(yourObjectVariable, null, 2)

When working with complex nested structures, this formatting reveals the hierarchy clearly. Arrays display with proper line breaks between elements, and objects show each property on its own line with consistent indentation.

> "The JSON.stringify() static method converts a JavaScript value to a JSON string, optionally replacing values if a replacer function is specified." ,  [JSON.stringify() - JavaScript - MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/stringify)

Alternative formatting approaches include using different indentation values. A value of 4 creates wider spacing that some developers prefer for deeply nested structures, while a value of 1 provides minimal formatting that maintains compactness.

### View the Formatted Result

Chrome displays your formatted JSON with proper indentation and built-in syntax highlighting. Each nesting level appears with consistent spacing, making object relationships and array structures immediately apparent. The console applies color coding automatically: strings appear in red, numbers in blue, boolean values in purple, and null values in gray.

Click the triangular arrows next to objects and arrays to expand or collapse them. This feature proves invaluable when working with large JSON structures where you need to focus on specific sections without losing context of the overall structure.

The formatted output includes automatic line numbers and maintains proper JSON syntax. You can select and copy portions of the formatted output for use in other applications or for further processing.

## Common Mistakes When Pretty Printing JSON

### Forgetting to Escape Quote Characters Properly

When pasting JSON directly into the console command string, internal quote marks break the parsing and generate syntax errors. This happens frequently with JSON containing string values that include quotation marks or apostrophes.

Instead of trying to manually escape every quote character, assign your JSON to a variable using template literals:

let myJson = `your-json-content-with-quotes-here`
JSON.stringify(JSON.parse(myJson), null, 2)

Template literals (backticks) handle quote characters automatically without requiring manual escaping. This approach eliminates the most common source of formatting errors and works consistently across different JSON structures.

### Using Incorrect Indentation Parameters

The third parameter in JSON.stringify() controls the formatting output. Using 0 or omitting this parameter entirely returns unformatted JSON as a single line, defeating the purpose of pretty printing. Values higher than 4 create excessive whitespace that makes the output harder to scan.

A value of 2 provides optimal readability for most JSON structures. Some developers prefer using tab characters ('\t') instead of numbers, but this creates inconsistent spacing depending on your browser's tab width configuration.

Negative values or non-numeric strings in the indentation parameter cause JSON.stringify() to ignore formatting entirely, returning compact output.

### Attempting to Format Invalid JSON Syntax

JSON.parse() throws exceptions when encountering syntax errors instead of attempting to format malformed content. Common JSON syntax violations include trailing commas after the last array element or object property, unquoted property names, and single quotes instead of double quotes around strings.

The console error message typically indicates the exact character position where parsing failed. Look for these frequent issues: missing closing brackets or braces, comma placement errors, and incorrect quote usage.

When debugging with [Chrome's source examination features](https://theluckystrike.github.io/chrome-tips/), you can validate JSON syntax in the Sources tab before attempting console formatting.

### Not Handling Large JSON Response Files

Chrome's console imposes display limits on output size. JSON responses larger than 100KB might get truncated with "..." indicating additional content exists. Extremely large files can cause browser performance degradation or temporary freezing.

For massive JSON files, consider breaking the data into smaller logical sections before formatting. You can also use external JSON formatting tools specifically designed for large file handling.

## Pro Tip: Skip the Manual Steps

The manual console method works reliably, but copying and pasting JSON responses becomes tedious when you're analyzing multiple APIs throughout your development day. The repetitive process of opening dev tools, navigating to console, and running formatting commands interrupts your workflow and slows down debugging sessions.

**JSON Formatter Pro** eliminates these manual steps entirely. This Chrome extension automatically detects JSON content in browser tabs and applies formatting instantly with syntax highlighting and collapsible sections. With a **4.8/5 rating**, version 1.0.4 (last updated 2026-03-02), and a compact 738KiB size, it handles formatting automatically while you focus on analyzing the actual data structure.

The extension works smoothly with any JSON content in your browser, including API responses, configuration files, and exported data. Instead of manual console commands, you get instant formatting that preserves your current scroll position and maintains any search filters you've applied to the content.

> "JSON is a text-based data format following JavaScript object syntax. Even though it closely resembles JavaScript object literal syntax, it can be used independently from JavaScript." ,  [Working with JSON - Learn web development - MDN](https://developer.mozilla.org/en-US/docs/Learn_web_development/Core/Scripting/JSON)

**[Try JSON Formatter Pro Free](https://zovo.one)**

Whether you choose the manual console approach or install an extension depends on your JSON formatting frequency. For occasional formatting tasks, the console method provides complete control without additional software installation. For developers who work with API responses daily, an extension removes repetitive steps and provides enhanced features like in-document search and hierarchical filtering.

Both methods deliver readable, properly structured JSON that transforms debugging from frustrating guesswork into efficient analysis. Choose the approach that matches your development workflow and apply it consistently rather than struggling with unformatted JSON text walls. When combined with [Chrome's other debugging capabilities](https://theluckystrike.github.io/chrome-tips/), proper JSON formatting becomes an essential skill for modern web development.

Built by Michael Lip. More tips at zovo.one