---
layout: default
title: "Chrome Console Utilities Reference"
description: "Master Chrome DevTools console utilities including $ selector, monitor, copy, debug, keys and values commands for efficient web development and debugging."
date: 2026-01-20
categories: [development, chrome, debugging]
tags: [chrome-devtools, console, debugging, web-development, developer-tools]
author: theluckystrike
---

# Chrome Console Utilities Reference

The Chrome browser's Developer Tools console is far more powerful than most developers realize. Beyond simple console.log statements, the console provides a collection of utility functions that can dramatically improve your debugging workflow and productivity. These utilities are available directly in the console without requiring any additional setup or libraries. Whether you're debugging a complex JavaScript application, inspecting DOM elements, or analyzing objects, these console utilities can save you significant time and effort.

In this comprehensive reference guide, we'll explore the most useful Chrome Console utilities, including the dollar sign selectors, monitor functions, copy command, debugging utilities, and object inspection methods. By the end of this article, you'll have a solid understanding of how to leverage these tools effectively in your daily development work.

## The Dollar Sign Selectors

One of the most convenient features of the Chrome console is the dollar sign ($) family of selector functions. These provide quick ways to select and interact with DOM elements without writing verbose JavaScript.

### The $ Function (Single Element Selection)

The $ function is a shorthand for document.querySelector(). It returns the first element that matches the specified CSS selector. This is incredibly useful when you need to quickly inspect or manipulate a specific element on the page.

```javascript
// Select the first element with class "container"
$('.container')

// Select the first element with id "header"
$('#header')

// Select the first button element
$('button')
```

This function becomes particularly handy when you're working with pages where you don't have direct access to the source code or when you want to quickly test selector patterns. Instead of opening the Elements panel and manually searching through the DOM tree, you can simply type a selector in the console and immediately see the matching element.

The $ function also supports XPath selectors, which can be useful for more complex element selection scenarios. To use XPath, prefix your selector with "xpath://" as shown below:

```javascript
// Select using XPath
$('xpath://div[@class="container"]//p')
```

### The $$ Function (Multiple Element Selection)

The $$ function works like $ but returns an array of all elements matching the specified CSS selector. This is equivalent to document.querySelectorAll() and returns a NodeList that you can iterate over or manipulate.

```javascript
// Get all links on the page
$$('a')

// Get all paragraphs within a specific container
$$('.content p')

// Get all input elements
$$('input')
```

The $$ function is particularly useful when you need to perform operations on multiple elements at once. For example, you might want to extract all links from a page, modify the style of multiple elements, or collect data from a list of elements.

```javascript
// Example: Extract all external links
const externalLinks = $$('a[href^="http"]').map(link => link.href);
console.log(externalLinks);

// Example: Hide all images on the page
$$('img').forEach(img => img.style.display = 'none');
```

### The $x Function (XPath Selection)

The $x function provides a direct way to select elements using XPath expressions. This is particularly useful when CSS selectors aren't flexible enough to express the selection criteria you need.

```javascript
// Select all paragraphs in the document
$x('//p')

// Select all elements with a specific class
$x('//*[@class="highlight"]')

// Select elements containing specific text
$x('//*[contains(text(), "error")]')

// Select elements with specific attributes
$x('//input[@type="text"]')
```

XPath expressions offer more flexibility than CSS selectors in certain scenarios, such as selecting elements based on their position relative to other elements or selecting elements that contain specific text content.

## The monitor Function

The monitor function is an incredibly useful debugging utility that automatically logs calls to a specific function along with the arguments passed to it. This makes it easy to track when and how functions are being called without manually adding console.log statements throughout your code.

### Basic Usage of monitor

To use monitor, simply pass the function you want to monitor as an argument:

```javascript
function calculateTotal(price, quantity) {
  return price * quantity;
}

monitor(calculateTotal);

// Now when calculateTotal is called, you'll see:
// function calculateTotal called with arguments: 10, 5
calculateTotal(10, 5); // Logs: calculateTotal called with args: (10, 5)
```

This is particularly valuable when you're working with third-party code or code where you can't easily add logging statements. Instead of modifying the source code, you can simply monitor the function from the console and immediately see when it's invoked.

### Monitoring Object Methods

You can also monitor methods on objects, which is useful for tracking API calls or method invocations on specific objects:

```javascript
const cart = {
  addItem: function(item) {
    // Add item logic
    return true;
  },
  removeItem: function(itemId) {
    // Remove item logic
    return true;
  }
};

monitor(cart.addItem);
monitor(cart.removeItem);
```

Now every time items are added to or removed from the cart, you'll see detailed logging in the console automatically.

### Using unmonitor to Stop Monitoring

When you're done monitoring a function, you can use the unmonitor function to stop the monitoring:

```javascript
unmonitor(calculateTotal);
```

This removes the monitoring hook from the specified function, stopping the automatic logging.

### A Real-World Example with Tab Suspender Pro

Consider a scenario where you're developing or debugging an extension like Tab Suspender Pro, which manages tab suspension to save memory. You might want to monitor when tabs are suspended or resumed:

```javascript
// If Tab Suspender Pro exposes these functions
monitor(tabManager.suspendTab);
monitor(tabManager.resumeTab);

// Now you'll see exactly when and how tabs are being managed
```

This kind of monitoring can help you understand the flow of data and identify issues in your extension's behavior without modifying the actual source code.

## The copy Function

The copy function allows you to copy any JavaScript value or object to your clipboard directly from the console. This is incredibly useful when you need to export data, share object contents, or save information for later use.

### Copying Simple Values

You can copy strings, numbers, and other primitive values:

```javascript
copy("Hello, World!");
copy(42);
copy(true);
```

### Copying DOM Elements

One of the most powerful uses of copy is to copy the outer HTML of DOM elements:

```javascript
// Copy the HTML of the first paragraph
copy($('p').outerHTML);

// Copy the HTML of multiple elements
copy($$('.item')[0].outerHTML);
```

This is particularly useful when you want to quickly grab HTML markup from a page for use in your own projects or to share with team members.

### Copying Objects and Arrays

You can copy complex JavaScript objects and arrays to the clipboard as JSON:

```javascript
const user = {
  name: "John Doe",
  email: "john@example.com",
  preferences: {
    theme: "dark",
    notifications: true
  }
};

copy(user);
// Copies: {"name":"John Doe","email":"john@example.com","preferences":{"theme":"dark","notifications":true}}
```

This makes it easy to export data from the browser for analysis, debugging, or sharing. You can also copy arrays:

```javascript
const items = [1, 2, 3, 4, 5];
copy(items);

// Copy all links from a page as JSON
const links = $$('a').map(a => ({
  text: a.innerText,
  href: a.href
}));
copy(links);
```

### Copying Console Output

The copy function can also be used to copy the results of previous console commands. When you run an expression in the console, you can reference the last result using $_, and then copy it:

```javascript
$$('a')[0];
// Output: <a href="...">Link Text</a>

copy($_);
// Copies the anchor element to clipboard
```

This creates a powerful workflow where you can inspect elements, modify them if needed, and then copy the results for use elsewhere.

## The debug Function

The debug function provides a powerful way to set breakpoints on functions programmatically. When the specified function is called, the debugger will pause execution and allow you to inspect the call stack, variables, and step through the code.

### Setting Up Debugging with debug

Using debug is straightforward:

```javascript
function myFunction(a, b) {
  return a + b;
}

debug(myFunction);

// Now when myFunction is called, the debugger will pause
myFunction(5, 3);
```

When the debugger pauses, you can inspect all local variables, the call stack, and use the DevTools debugging controls to step through the code line by line.

### Debugging Object Methods

Just like monitor, debug works with object methods:

```javascript
const api = {
  fetchData: function(url) {
    return fetch(url).then(r => r.json());
  }
};

debug(api.fetchData);

// The debugger will pause whenever fetchData is called
api.fetchData('https://api.example.com/data');
```

This is particularly useful when debugging event handlers or methods that are called by third-party code.

### Debugging Built-in Functions

You can even debug built-in browser functions or library functions:

```javascript
// Debug the fetch function to see all network requests
debug(fetch);

// Debug localStorage methods
debug(localStorage.setItem);
debug(localStorage.getItem);
```

This level of visibility can be incredibly valuable when trying to understand how code is interacting with browser APIs.

### Using undebug to Remove Breakpoints

To remove a debug breakpoint, use the undebug function:

```javascript
undebug(myFunction);
```

This removes the debugger hook from the specified function.

## The keys and values Functions

The keys and values functions provide quick ways to extract the keys and values from JavaScript objects. These are particularly useful for inspecting objects without having to write iteration code.

### Using keys to Get Object Keys

The keys function returns an array of an object's own property keys:

```javascript
const person = {
  name: "Alice",
  age: 30,
  city: "New York"
};

keys(person);
// Returns: ["name", "age", "city"]
```

This is equivalent to Object.keys() but more concise to type in the console.

### Using values to Get Object Values

The values function returns an array of an object's own property values:

```javascript
const person = {
  name: "Alice",
  age: 30,
  city: "New York"
};

values(person);
// Returns: ["Alice", 30, "New York"]
```

This is equivalent to Object.values().

### Practical Examples

These functions become particularly useful when working with complex objects:

```javascript
// Inspecting response headers
keys(response.headers);
values(response.headers);

// Inspecting DOM element attributes
keys($('input').dataset);
values($('input').dataset);

// Working with configuration objects
const config = {
  apiUrl: 'https://api.example.com',
  timeout: 5000,
  retries: 3,
  debug: true
};

console.table([keys(config), values(config)]);
```

### Combining keys and values

You can combine keys and values with other console methods for more detailed inspection:

```javascript
const product = {
  id: 123,
  name: "Wireless Headphones",
  price: 99.99,
  inStock: true
};

// Create an array of key-value pairs
keys(product).map(key => ({ key, value: values(product)[keys(product).indexOf(key)] }));
```

However, a more practical approach is to use console.table() which automatically formats objects beautifully:

```javascript
console.table(product);
```

## Additional Console Utilities Worth Knowing

While we've covered the main utilities requested, Chrome's console offers several more helpful functions that can improve your debugging workflow.

### table

The table function displays arrays of objects in a formatted table, making it much easier to compare data:

```javascript
const users = [
  { name: "Alice", age: 30, city: "New York" },
  { name: "Bob", age: 25, city: "Los Angeles" },
  { name: "Charlie", age: 35, city: "Chicago" }
];

table(users);
```

This is particularly useful when working with larger datasets or API responses.

### dir and dirxml

The dir function displays an object in a hierarchical tree view, while dirxml displays the XML representation of an object:

```javascript
dir(document.body);
dirxml(document.body);
```

### clear

Clears the console:

```javascript
clear();
```

### timestamp

The console.timeStamp() method adds a marker to the Performance and Waterfall toolbars in DevTools, helping you correlate console events with other performance data.

## Conclusion

The Chrome console utilities provide a powerful toolkit for web developers and debugging professionals. From the convenience of dollar sign selectors for DOM manipulation to the advanced debugging capabilities of monitor and debug, these utilities can significantly enhance your productivity.

The keys and values functions make object inspection straightforward, while the copy function enables easy data export. Combined with other console methods like table, dir, and clear, you have a comprehensive debugging environment at your fingertips.

Whether you're developing extensions like Tab Suspender Pro, debugging complex web applications, or simply exploring web pages for development purposes, these console utilities will serve as invaluable tools in your workflow. Take time to familiarize yourself with them, and you'll find yourself reaching for them more often in your daily development tasks.

Remember, the console is not just for logging errors—it's a powerful interactive development environment that can help you understand, debug, and optimize your code more effectively than ever before.

---

Built by theluckystrike — More tips at [zovo.one](https://zovo.one)
