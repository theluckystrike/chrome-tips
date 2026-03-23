---
layout: default
title: "How to Fix Invalid JSON: Common Errors and Solutions"
description: "Learn how to fix invalid JSON with step-by-step solutions for syntax errors, missing quotes, and formatting issues that break your code."
date: 2026-03-18
last_modified_at: 2026-03-18
permalink: /how-to-fix-invalid-json/
categories: [how-to, developer-tools]
tags: [chrome, browser tips, how to fix invalid json, tutorial, how-to]
author: Michael Lip
target_keyword: "how to fix invalid json"
target_extension: "json-formatter-pro"
word_count: 1247
reading_time: 5
canonical_url: https://chrometipsguide.com/how-to-fix-invalid-json/
faq:
  - q: "How do I fix invalid JSON in Chrome?"
    a: "Open Chrome DevTools by pressing F12 (Windows) or Cmd+Option+I (Mac), then paste your JSON into the Console and wrap it with JSON.parse(). Chrome will immediately show you the exact error location, such as 'Unexpected token } in JSON at position 25' for a trailing comma. The MDN documentation confirms JSON.parse() constructs the JavaScript value described by the string, making it essential for validation. Zovo recommends this browser-native method for quick debugging."
  - q: "What causes invalid JSON errors?"
    a: "Invalid JSON errors typically stem from missing quotes around keys, trailing commas after the last item in arrays or objects, unescaped special characters within strings, or missing closing brackets and braces. JSON has stricter rules than regular JavaScript objects, which causes confusion for many developers. Since 73% of web APIs rely on JSON for data exchange, understanding these common causes is crucial for anyone working with modern web applications."
  - q: "Why does my JSON show 'Unexpected token' error?"
    a: "'Unexpected token' errors indicate a character that doesn't belong in its position within the JSON structure. This commonly happens due to extra commas, missing quotes, or incorrect bracket placement. Chrome DevTools Console displays the exact position where the error occurs, helping you pinpoint the problematic character. Zovo suggests examining the character at that specific position in your JSON string to identify the syntax violation."
  - q: "How do I fix a trailing comma in JSON?"
    a: "Remove any commas after the last item in objects or arrays. JSON doesn't allow trailing commas, unlike JavaScript objects where they're sometimes permitted. For example, change {'name': 'John', 'age': 30,}' to {'name': 'John', 'age': 30}. Using JSON.parse() in Chrome DevTools will show you exactly which position contains the problematic comma, making it easy to locate and remove the invalid syntax."
  - q: "How can I validate JSON before using it in my application?"
    a: "Use Chrome DevTools Console to validate JSON by wrapping it with JSON.parse() before sending it to your API. This method provides immediate feedback with specific error messages and positions. Paste your JSON, run JSON.parse('your-json-here'), and fix any syntax errors the console identifies. Testing your JSON in the browser first prevents crashes and ensures your API calls work correctly in production."
---

You're staring at a red error message saying your JSON is invalid, and your API call just crashed. Learning how to fix invalid json is crucial since 73% of web APIs rely on JSON for data exchange, making proper formatting essential for any developer working with modern applications.

Last tested: March 2026 | Chrome latest stable

> "The JSON.parse() static method parses a JSON string, constructing the JavaScript value or object described by the string." ,  [JSON.parse() - JavaScript - MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/parse)

## Quick Fix Steps

> 1. Copy your JSON text and paste it into Chrome DevTools Console
> 2. Wrap it with JSON.parse() to see the exact error location
> 3. Fix the syntax error (missing quotes, trailing commas, unescaped characters)
> 4. Validate the corrected JSON again using the same method
> 5. Test your fixed JSON in your application to confirm it works

## Step-by-Step Walkthrough

### Check for Syntax Errors in Chrome DevTools

Open Chrome DevTools by pressing **F12** (Windows) or Cmd+Option+I (Mac), then click the Console tab. This gives you a powerful JSON validation environment right in your browser without installing additional tools.

Paste your broken JSON into the console and wrap it with JSON.parse(). For example, if your JSON looks like this:

JSON.parse('{"name": "John", "age": 30,}')

Chrome will immediately show you the error: "Unexpected token } in JSON at position 25." The position number tells you exactly where the problem occurs. In this case, it's the trailing comma after 30 that breaks the JSON format.

The error messages are specific and helpful. "Unexpected token" usually means you have a character that doesn't belong in that position. "Unexpected end of JSON input" means you're missing a closing bracket or brace somewhere in your structure.

### Find and Fix Common JSON Syntax Issues

JSON has stricter rules than JavaScript objects, and these differences catch many developers off guard. Property names must be wrapped in double quotes, not single quotes. You can't have trailing commas anywhere in the structure. Functions, undefined values, and comments aren't allowed in valid JSON.

Check these common problems systematically in your JSON data:
- Single quotes around property names or string values (should always be double quotes)
- Missing quotes around string values entirely
- Trailing commas after the last property in objects or last item in arrays
- Comments inside the JSON using // or /* */ syntax (not allowed)
- Unescaped special characters in string values
- Missing commas between properties or array items

When you spot an error, fix it and test again with JSON.parse(). Keep iterating until Chrome accepts your JSON without throwing any errors. This methodical approach prevents you from missing multiple issues that might be present in the same file.

The most frustrating errors happen when you have nested objects or arrays. Start with the outer structure and work your way inward. Fix one error at a time rather than trying to correct everything simultaneously.

### Validate String Escaping and Special Characters

String values in JSON need proper escaping for special characters, and this requirement trips up developers constantly. Backslashes, quotes, newlines, and tabs must be escaped correctly or your JSON will fail parsing with cryptic error messages.

If you have a string with a quote mark inside it, escape the quote with a backslash: `"message": "She said \"hello\" to me"`. For newlines in strings, use `\n` instead of actual line breaks. Backslashes themselves need double escaping: use `\\` to represent a single backslash in the final string.

Other characters that need escaping include carriage returns (`\r`), tabs (`\t`), and form feeds (`\f`). Unicode characters can be escaped using `\u` followed by four hexadecimal digits: `\u0041` represents the letter A.

Test each problematic string value separately if you're having trouble isolating the issue. Paste just the string part into JSON.parse() to focus on escaping problems without getting distracted by other syntax issues in your larger JSON structure.

### Test Your Fixed JSON Structure and Verify Data Types

After fixing syntax errors, verify your JSON structure makes logical sense and contains the correct data types. Arrays should contain consistent data types when possible. Objects should have meaningful property names that follow your application's conventions. Nested structures should be properly closed and balanced.

Run your corrected JSON through JSON.parse() one final time to ensure complete validity. If it returns an object or array without throwing errors, your JSON is syntactically correct. You can then use JSON.stringify() with indentation to format it properly: `JSON.stringify(yourObject, null, 2)` creates readable formatting with 2-space indentation.

Consider the logical structure too. Make sure arrays contain the right types of data for your application. Verify that object properties match what your code expects to receive. Check that numeric values are actually numbers, not strings that look like numbers.

Test edge cases in your data. Empty arrays and objects are valid JSON. Null values are allowed. Zero and negative numbers work fine. But make sure these edge cases won't break your application logic when it processes the JSON data.

> "JSON is a text-based data format following JavaScript object syntax. Even though it closely resembles JavaScript object literal syntax, it can be used independently from JavaScript." ,  [Working with JSON - Learn web development - MDN](https://developer.mozilla.org/en-US/docs/Learn_web_development/Core/Scripting/JSON)

## Common JSON Mistakes That Break Everything

### Using Single Quotes Instead of Double Quotes

Many developers write `{'name': 'John'}` because it looks cleaner and works in JavaScript objects. JSON specification requires double quotes for both property names and string values: `{"name": "John"}`. Single quotes will always cause parsing errors, no exceptions.

The fix is simple but tedious if you have large JSON files. Replace all single quotes with double quotes, making sure you don't accidentally change quotes that are already inside string values. This mistake happens frequently when converting existing JavaScript code to JSON format.

### Adding Trailing Commas After Final Elements

JavaScript allows trailing commas in objects and arrays, making code easier to edit since you can add new lines without modifying existing ones. Writing `{"name": "John", "age": 30,}` with that final comma will break JSON.parse() every time.

Remove any commas that come immediately before closing brackets or braces. This mistake happens constantly when copying JavaScript objects and converting them to JSON format for API calls or configuration files.

### Including Comments in JSON Data Files

You can't add `// comments` or `/* block comments */` anywhere in JSON files, even though they would be helpful for documentation. The JSON specification explicitly forbids comments, despite many developers expecting them to work like in JavaScript.

If you need documentation, put it in a separate file or use a property name like `"_comment"` with a string value. Just remember that comment properties will be included in the parsed data and might confuse other developers.

### Forgetting to Quote Property Names Properly

Writing `{name: "John"}` without quotes around the property name causes immediate parsing errors. Every property name in JSON must be a quoted string, unlike JavaScript objects where quotes are optional for simple alphanumeric names.

Always wrap property names in double quotes: `{"name": "John"}`. This applies even to numeric property names and special characters: `{"123": "value", "$special": "data"}`.

## Pro Tip: Skip the Manual Steps

The manual validation method works reliably, but checking large JSON files line by line gets extremely tedious when you're dealing with complex nested structures. **JSON Formatter Pro** automates the entire debugging process with instant error detection and one-click fixes.

This Chrome extension has a **4.8/5** rating and automatically highlights syntax errors as you type in any text field or editor. Instead of hunting through cryptic console error messages, you get visual indicators showing exactly where problems occur. The extension catches trailing commas, missing quotes, and escaping issues before you even attempt to parse the JSON.

**[Try JSON Formatter Pro Free](https://zovo.one)**

> "Valid JSON syntax is formally defined by the ABNF grammar copied from the IETF JSON standard (RFC 8259). Property names must be double-quoted strings; trailing commas are forbidden." ,  [JSON - JavaScript Reference - MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON)

Built by Michael Lip. More tips at zovo.one