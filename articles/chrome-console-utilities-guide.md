---
layout: post
title: "Chrome Console Utilities Reference"
description: "Master Chrome DevTools console utilities including dollar sign selectors, copy, debug, monitor and more."
date: 2026-01-15
categories: [chrome, developer-tools, console]
tags: [chrome, console, developer-tools, devtools, debugging]
author: theluckystrike
---

# Chrome Console Utilities Reference

Chrome console utilities are powerful tools that can make your development workflow faster and more efficient. If you have ever found yourself manually selecting elements in the Elements panel, copying text through right-click menus, or writing repetitive code to inspect objects, these console utilities can save you significant time. Let me walk you through each utility and show you how to use them effectively.

## The Dollar Sign Utilities

The first set of utilities you should know about are the dollar sign commands. These are shortcuts that Chrome provides directly in the console to help you select and work with elements quickly.

The simplest one is `$()`. This is a shorthand for `document.querySelector()`, which means you can use it to select a single element using CSS selectors. For example, if you want to select the first paragraph on a page, you can type `$('p')` in the console and press Enter. This returns the same element you would get from `document.querySelector('p')`, but with fewer characters to type. This is especially useful when you are quickly testing something or need to grab an element without writing a full JavaScript statement.

There is also `$$()` which works like `document.querySelectorAll()`. This returns a list of all elements that match your selector. So if you want to see all the links on a page, you can type `$$('a')` and you will get an array of all anchor elements. From there, you can iterate through them, check their properties, or manipulate them as needed. This is much faster than switching to the Elements panel and manually inspecting each link.

Another useful variant is `$x()` which allows you to select elements using XPath expressions. While CSS selectors are more common, XPath can be helpful in certain situations, particularly when you need to select elements based on their text content or when navigating complex DOM structures. The syntax takes a string argument containing your XPath expression, so you might type something like `$x('//div[@class="container"]')` to select all divs with the class container.

## Copying Elements and Data

The console provides a `copy()` function that makes it easy to copy anything to your clipboard directly from the console. This is incredibly useful when you need to grab data, HTML, or text from the page without manually selecting it.

You can copy the outer HTML of any element by selecting it first and then passing it to copy. For instance, if you have selected a specific element using one of the dollar sign utilities, you can type `copy($('p'))` to copy that paragraph's HTML to your clipboard. You can then paste it anywhere you need, whether that is in a code editor, a document, or sharing it with a colleague.

The copy function also works with plain text and JavaScript values. If you have an object or array in memory, you can copy its JSON representation by typing `copy(myObject)`. This is handy when you are debugging and want to save a snapshot of some data structure for later analysis or when you need to share a piece of data with someone.

Beyond copying, you can also use the console to inspect elements in detail. The `inspect()` function takes an element and opens it in the Elements panel, which saves you the trouble of manually finding it in the DOM tree. This is particularly useful when you are working with dynamically generated content or when you have identified an element through a console command and want to see its full details including styles, event listeners, and computed properties.

## Monitoring Function Calls

When you are debugging JavaScript code, understanding when and how functions are called is essential. Chrome provides two powerful utilities for this: `monitor()` and `unmonitor()`.

The `monitor()` function lets you instrument any function so that every time it is called, a message is logged to the console. The log includes the function name and the arguments that were passed in the call. This is invaluable when you want to trace function executions without modifying your source code. For example, if you want to see every time a function named `handleClick` is called, you simply type `monitor(handleClick)` and then interact with the page. Every invocation gets logged automatically.

When you are done monitoring, you can use `unmonitor()` to remove the instrumentation. This stops the console from logging calls to that function. It is important to remember to unmonitor functions when you are finished, as leaving too many functions monitored can slow down your page and flood the console with messages.

There is also `monitorEvents()` which extends this capability to DOM events. You can tell Chrome to log all events of a certain type that occur on a specific element. For instance, typing `monitorEvents($('button'), 'click')` will log every click event on the first button element. You can also monitor multiple event types at once by passing an array, like `monitorEvents($('input'), ['focus', 'blur', 'input'])`. This makes it easy to see exactly what is happening with user interactions on any element.

## Inspecting Objects with Keys and Values

When you are working with JavaScript objects, it is often helpful to quickly see what properties they contain. The console utilities include `keys()` and `values()` functions that give you direct access to an object's property names and values.

The `keys()` function returns an array of all the enumerable property names on an object. This is equivalent to `Object.keys()`. So if you have a configuration object and want to quickly see what settings it contains, you can type `keys(myConfig)` and you will get a list of all the keys. This is faster than manually iterating through the object or writing out a for-in loop.

Similarly, `values()` returns an array of all the property values. This complements keys nicely and together they give you a complete picture of what an object contains. These functions are particularly useful when exploring unfamiliar code or when debugging and you need to understand the structure of an object you did not write.

For a more comprehensive view, you can combine these utilities with the console's built-in formatting. Simply typing the variable name in the console often gives you an interactive expandable view that lets you dig into nested objects and arrays. But when you want a quick text representation that you can copy or examine at a glance, keys and values are the way to go.

## Using Debug Functions

Chrome provides several debugging utilities that can help you set breakpoints and control execution directly from the console. The most important ones are `debug()` and `undebug()`.

When you type `debug(functionName)`, Chrome automatically sets a breakpoint at the first line of that function. Whenever the function is called during page execution, the debugger will pause there and you can inspect the call stack, variables, and step through the code. This is incredibly useful when you want to investigate a specific function without having to find it in the source files and manually add a breakpoint through the Sources panel.

Once you have finished debugging, use `undebug()` to remove the breakpoint. This is the same as manually removing a breakpoint, and it cleans up your debugging state so the function runs normally again.

There are also conditional breakpoints you can set from the console, though these require a bit more code. You can use the `debugger` statement in your code to trigger a breakpoint conditionally, but that requires modifying source files. The console utilities give you a quick way to instrument functions temporarily without changing any code, which is perfect for investigative debugging.

## Table Display for Arrays and Objects

When you are working with arrays of objects, displaying them in the console can become messy if you just type the variable name. Each object might expand into a large block of text, making it hard to compare different entries. The `table()` function solves this problem by displaying arrays of objects in a nicely formatted table.

This is particularly useful when you have data like a list of users, products, or any other collection where each item has the same properties. Instead of seeing a long list of expanding objects, you get a compact table where each row represents an item and each column represents a property. The columns are automatically extracted from the objects, so you can immediately see what properties are available.

You can also pass a second argument to `table()` to specify which columns you want to display. This is helpful when you have objects with many properties but only care about a few. By passing an array of property names, you can customize the table output to show exactly what you need.

## Clearing the Console

While not strictly a utility function, knowing how to clear the console quickly is important for maintaining a clean debugging environment. You can type `clear()` to clear all messages from the console, which is equivalent to clicking the clear button in the console UI. This is useful when you want to start fresh after a lot of debugging output has accumulated.

You can also use the keyboard shortcut Ctrl+L on Windows or Linux, and Cmd+K on Mac, to clear the console quickly without typing. This becomes second nature once you use it regularly.

## Practical Examples

Let me give you a few practical examples of how these utilities can speed up your daily work. Imagine you need to test some CSS changes on a specific element. Instead of using the Elements panel to find it, you can simply type `$('.my-class')` in the console to grab it instantly. You can then use `copy()` to grab its HTML if you need to save it somewhere.

When debugging a button click that is not working, you can type `monitorEvents($('button'), 'click')` to see every click event in real time. If the events are firing, you will see them in the console immediately. If they are not, you know the issue is with event binding rather than the handler itself.

When exploring an API response, you can use `keys(response.data)` to quickly see what properties are available, then `table(response.data.items)` to display them in a readable format. This makes understanding complex API responses much faster than expanding objects manually.

## Combining Utilities for Powerful Workflows

The real power of these console utilities comes from combining them. You can chain commands together to perform complex operations quickly. For example, you could select all links on a page, filter them by those that open in a new tab, and copy their URLs to the clipboard, all in one line of console input.

You can also save frequently used selections to variables by simply typing a variable name and assigning it. For instance, `const mainNav = $('nav')` saves the navigation element to a variable that you can use throughout your console session. This is much faster than re-selecting elements each time you need them.

These utilities also work well with the snippets feature in Chrome DevTools. You can write a snippet that uses these utilities to perform a common task, like extracting all image URLs from a page or generating a report on form fields. Once saved as a snippet, you can run it anytime with a keyboard shortcut.

## One More Tool Worth Knowing

If you are looking for an extension that extends these console capabilities even further, Tab Suspender Pro offers additional features that integrate well with your debugging workflow. While it is primarily known for managing tab memory and helping you stay focused, it also includes console enhancements that make inspecting and working with page elements easier. You can use it to quickly toggle element visibility, capture console logs across sessions, and perform bulk operations on multiple elements at once. The combination of built-in utilities and extension features can really streamline how you work with the console.

## Making These Utilities Part of Your Routine

The key to getting the most out of these utilities is to start using them regularly in your daily development work. At first, you might need to remind yourself to try the console instead of manually clicking through the UI, but after a short while, these shortcuts will become automatic. The time you save on each operation adds up quickly, and you will find yourself debugging faster and exploring pages more efficiently.

Remember that these utilities are available in any page you open, whether you are working on your own projects or debugging someone else's code. They do not require any setup or configuration, so you can start using them immediately. Take a few minutes to try each one, and you will soon discover how much easier console-based development can be.

---

*Built by theluckystrike — More tips at [zovo.one](https://zovo.one)*
