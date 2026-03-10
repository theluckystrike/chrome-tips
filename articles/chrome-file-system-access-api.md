---
layout: post
title: "Chrome File System Access API Guide"
<<<<<<< HEAD
description: "Learn how to use the Chrome File System Access API to open files, save files, access directories, and implement drag-and-drop functionality in web applications. Complete developer guide with code examples."
date: 2026-01-15
categories: [chrome-api, web-development, file-system]
tags: [chrome-file-system-access-api, file-api, web-apps, chrome-extension, file-handling]
=======
description: "Learn how to use the Chrome File System Access API to read, write, and manage files directly from your web applications in Chrome browser."
date: 2026-01-20
categories: [development, web-apis, chrome]
tags: [chrome-file-system-access-api, file-api, browser-api, web-development]
>>>>>>> consumer/a24-chrome-file-system-access-api
author: theluckystrike
---

# Chrome File System Access API Guide

The **Chrome File System Access API** is a powerful feature that allows web applications to interact with files and directories on your local computer directly from the browser. This API transforms the way we think about web applications, enabling them to function more like native desktop applications when it comes to file handling. Whether you are building a code editor, a document management system, or a media processing tool, understanding this API will open up new possibilities for your web-based projects.

In this guide, I will walk you through everything you need to know about the Chrome File System Access API, including how to open files, save files, work with directories, and implement drag-and-drop functionality. I will also show you how this technology can be combined with browser extensions like **Tab Suspender Pro** to create powerful productivity tools.

## What Is the Chrome File System Access API?

The **File System Access API** is a web API that provides secure access to the file system on a user's device. Originally developed by Google for Chrome, it has since been adopted by other Chromium-based browsers. This API goes far beyond the traditional file input element that has been part of HTML for years. While the old approach required users to select a file through a system dialog and then read that specific file, the new API allows for much more sophisticated interactions.

With the File System Access API, you can prompt users to open a file and then get a handle to that file. This handle persists, allowing you to read from or write to the file multiple times without requiring the user to select it again. You can also create new files, modify existing ones, and even work with entire directories. The API is designed with security in mind, requiring explicit user permission before any file access occurs.

The permissions system works similarly to how other browser permissions function. When your web application attempts to access a file, Chrome displays a prompt asking the user to grant permission. The user must explicitly choose to allow access, and they can revoke this permission at any time through Chrome's settings. This ensures that malicious websites cannot access files without the user's knowledge and consent.

## Opening Files with the File System Access API

<<<<<<< HEAD
Opening files is the most common use case for the File System Access API. The process begins with calling the `showOpenFilePicker()` method, which displays a native file picker dialog to the user. This method returns a promise that resolves to an array of file system file handles, allowing users to select one or more files depending on your application needs.
=======
The most common use case for the File System Access API is opening files. This functionality replaces the traditional `<input type="file">` element with a more powerful and flexible approach. To open a file, you use the `showOpenFilePicker()` method, which displays the native file dialog and returns a file system file handle.

Here is a basic example of how to open a text file:
>>>>>>> consumer/a24-chrome-file-system-access-api

```javascript
async function openFile() {
  const [fileHandle] = await window.showOpenFilePicker({
    types: [{
      description: 'Text Files',
      accept: {
        'text/plain': ['.txt', '.text']
      }
    }],
    multiple: false
  });
  
  const file = await fileHandle.getFile();
  const contents = await file.text();
  console.log('File contents:', contents);
  return contents;
}
```

This code does several important things. First, it calls `showOpenFilePicker()` which opens the system's file dialog. The `types` option allows you to filter what kinds of files the user can select, which provides a better user experience than showing all files. In this example, we are telling the browser to only show text files with .txt or .text extensions.

Once the user selects a file and confirms their choice, the method returns an array of file handles. Since we set `multiple` to false, we know there will be only one file. We then use the file handle to get a `File` object by calling `getFile()`, and we can read its contents using standard file reading methods like `text()`.

One of the key advantages of this approach is that the file handle persists. You can store this handle and use it later to read the file again without requiring the user to select it once more. This is particularly useful for applications that work with the same file over an extended period, such as a code editor or a document editor.

The API also supports opening multiple files at once. Simply set `multiple: true` in the options, and the method will return an array of file handles. You can then iterate through each handle and read its contents:

```javascript
async function openMultipleFiles() {
  const fileHandles = await window.showOpenFilePicker({
    types: [{
      description: 'Images',
      accept: {
        'image/*': ['.png', '.jpg', '.jpeg', '.gif']
      }
    }],
    multiple: true
  });
  
  for (const handle of fileHandles) {
    const file = await handle.getFile();
    console.log('Opened file:', file.name);
  }
}
```

## Saving Files with the File System Access API

Saving files is equally straightforward with the File System Access API. You use the `showSaveFilePicker()` method, which is similar to the open method but works in reverse. Instead of reading from an existing file, this method allows users to choose where to save new content or how to save modifications to an existing file.

<<<<<<< HEAD
Saving files is just as important as opening them, and the File System Access API provides the `showSaveFilePicker()` method for this purpose. This method displays a native save dialog, allowing users to choose where to save their file and what to name it. The method returns a file system file handle that you can use to write content to the selected location.

```javascript
async function saveFile(defaultName = 'document.txt') {
  const fileHandle = await window.showSaveFilePicker({
    suggestedName: defaultName,
=======
Here is how you can save content to a new file:

```javascript
async function saveFile(content) {
  const fileHandle = await window.showSaveFilePicker({
    suggestedName: 'document.txt',
>>>>>>> consumer/a24-chrome-file-system-access-api
    types: [{
      description: 'Text Files',
      accept: {
        'text/plain': ['.txt']
      }
    }]
  });
<<<<<<< HEAD
  return fileHandle;
}
```

The `suggestedName` parameter provides a default filename that users can accept or change. This is particularly useful when your application works with named documents, such as saving a document with its title as the filename.

Once you have a save handle, writing content is accomplished through the `createWritable()` method, which returns a writable stream:

```javascript
async function writeFileContents(fileHandle, content) {
=======
  
>>>>>>> consumer/a24-chrome-file-system-access-api
  const writable = await fileHandle.createWritable();
  await writable.write(content);
  await writable.close();
  console.log('File saved successfully');
}
```

<<<<<<< HEAD
The writable stream supports various writing methods, including `write()`, `seek()`, and `truncate()`. This gives you fine-grained control over file modifications, enabling use cases like appending to existing files or updating specific portions of a document.

For applications that need to create new files in existing directories, you can also use the `getDirectoryHandle()` method to obtain a directory handle and then create files within that directory:

```javascript
async function createFileInDirectory(directoryHandle, fileName, content) {
  const fileHandle = await directoryHandle.getFileHandle(fileName, { create: true });
  const writable = await fileHandle.createWritable();
  await writable.write(content);
  await writable.close();
  return fileHandle;
}
```

The `create: true` option ensures that the file is created if it doesn't exist. If the file already exists, this option will overwrite it, so you may want to add logic to handle existing files appropriately based on your application's requirements.

## Accessing Directories and Managing Multiple Files

Beyond single file operations, the File System Access API provides robust capabilities for working with entire directories. This is essential for applications like file managers, photo galleries, or development tools that need to organize and process multiple files at once.

To open a directory, use the `showDirectoryPicker()` method, which returns a directory handle:
=======
This example demonstrates the complete workflow for saving a file. First, we call `showSaveFilePicker()` which shows the save dialog to the user. We can suggest a default filename using the `suggestedName` option, and we can also filter the file types that appear in the dialog.

After the user chooses a location and confirms, we receive a file handle. We then call `createWritable()` on this handle to get a writable stream. We write our content to this stream and close it when we are done. The `close()` method is important because it ensures all data is flushed to the disk.

For updating existing files, the process is similar but you would typically obtain the file handle by opening an existing file first. The API allows you to modify files in place, which is useful for applications that need to save changes automatically or support auto-save functionality.

It is worth noting that when saving to an existing file, you might want to check if the user has permission to modify that file. The API provides methods to query and request write permission explicitly:

```javascript
async function ensureWritePermission(fileHandle) {
  const options = { mode: 'readwrite' };
  
  if ((await fileHandle.queryPermission(options)) === 'granted') {
    return true;
  }
  
  if ((await fileHandle.requestPermission(options)) === 'granted') {
    return true;
  }
  
  return false;
}
```

This helper function checks whether the handle already has write permission, and if not, requests it from the user. This pattern is useful when you are working with a file handle that was obtained earlier, such as when your application resumes after being closed and reopened.

## Working with Directories

The File System Access API truly shines when it comes to working with directories. The `showDirectoryPicker()` method allows users to select an entire directory, giving your application access to all the files and subdirectories within it. This capability opens up possibilities for building file managers, media libraries, document organization tools, and more.

Here is how you can open a directory and list its contents:
>>>>>>> consumer/a24-chrome-file-system-access-api

```javascript
async function openDirectory() {
  const dirHandle = await window.showDirectoryPicker();
<<<<<<< HEAD
  return dirHandle;
}
```

When a user selects a directory, your application gains the ability to enumerate its contents, read files, and create new files within that directory. However, note that accessing individual files within the directory still requires user permission for each file operation.

You can iterate through directory contents using the `values()` method, which returns an async iterator of directory entries:

```javascript
async function listDirectoryContents(dirHandle) {
  const entries = [];
  for await (const entry of dirHandle.values()) {
    entries.push({
      name: entry.name,
      kind: entry.kind, // 'file' or 'directory'
      handle: entry,
    });
  }
  return entries;
}
```

Each entry has a `kind` property that indicates whether it's a file or directory, along with a handle that you can use for further operations. This information is crucial for building user interfaces that display folder structures or for implementing recursive file processing.

Working with directories also enables powerful batch operations. For example, you can process all files in a folder:

```javascript
async function processAllFiles(dirHandle) {
  for await (const entry of dirHandle.values()) {
    if (entry.kind === 'file') {
      const file = await entry.getFile();
      // Process each file here
      console.log(`Processing: ${file.name}`);
=======
  
  for await (const entry of dirHandle.values()) {
    console.log('Entry name:', entry.name);
    console.log('Entry kind:', entry.kind); // 'file' or 'directory'
    
    if (entry.kind === 'file') {
      const file = await entry.getFile();
      console.log('File size:', file.size);
>>>>>>> consumer/a24-chrome-file-system-access-api
    }
  }
}
```

<<<<<<< HEAD
When implementing directory access in your application, consider how other Chrome extensions might interact with your file operations. For instance, if you're building a productivity application that works with many files simultaneously, you should be aware that extensions like Tab Suspender Pro may affect how your application runs in the background. Design your file handling to be resilient and save work frequently to prevent data loss.

## Implementing Drag and Drop Functionality

The File System Access API integrates seamlessly with the HTML5 Drag and Drop API, enabling intuitive file interactions where users can drag files from their desktop directly into your web application. This creates a more fluid user experience compared to traditional file picker dialogs.

To implement drag and drop, you'll need to add event listeners for the dragover and drop events on a drop zone element:
=======
This code opens the directory picker, and once the user selects a directory, it iterates through all entries within that directory. The `values()` method returns an async iterator that yields each entry in the directory. Each entry has a `kind` property that indicates whether it is a file or a directory, and you can use `getFile()` to get additional information about files.

You can also create new files and directories within an existing directory handle:

```javascript
async function createFileInDirectory(dirHandle, filename, content) {
  const fileHandle = await dirHandle.getFileHandle(filename, { create: true });
  const writable = await fileHandle.createWritable();
  await writable.write(content);
  await writable.close();
}

async function createSubdirectory(dirHandle, dirname) {
  const subDirHandle = await dirHandle.getDirectoryHandle(dirname, { create: true });
  return subDirHandle;
}
```

The `{ create: true }` option is key here. When you request a file or directory handle with this option, it will be created if it does not already exist. If the file or directory already exists, this option simply returns the existing handle without modifying it.

Working with directories is particularly powerful when combined with recursive operations. You can build functions that traverse entire directory trees, processing each file along the way. This is essential for applications like photo organizers, document processors, or backup tools that need to operate on large numbers of files.

## Implementing Drag and Drop Functionality

Another powerful feature of the File System Access API is its integration with the HTML5 Drag and Drop API. This allows users to drag files from their desktop directly into your web application, providing an intuitive and familiar interaction pattern. Combined with the file system access capabilities, you can create applications that seamlessly handle dropped files.

When a user drags files onto a drop zone in your application, you can access those files through the drag event's data transfer object. Here is a basic implementation:
>>>>>>> consumer/a24-chrome-file-system-access-api

```javascript
const dropZone = document.getElementById('dropZone');

dropZone.addEventListener('dragover', (e) => {
  e.preventDefault();
  e.stopPropagation();
  dropZone.classList.add('drag-over');
});

<<<<<<< HEAD
dropZone.addEventListener('drop', async (event) => {
  event.preventDefault();
  const items = event.dataTransfer.items;
  
  for (const item of items) {
    if (item.kind === 'file') {
      const fileHandle = await item.getAsFileSystemHandle();
      if (fileHandle.kind === 'file') {
        const file = await fileHandle.getFile();
        console.log(`Dropped file: ${file.name}`);
        // Process the dropped file
=======
dropZone.addEventListener('dragleave', (e) => {
  e.preventDefault();
  e.stopPropagation();
  dropZone.classList.remove('drag-over');
});

dropZone.addEventListener('drop', async (e) => {
  e.preventDefault();
  e.stopPropagation();
  dropZone.classList.remove('drag-over');
  
  const items = e.dataTransfer.items;
  
  for (const item of items) {
    if (item.kind === 'file') {
      const file = item.getAsFile();
      console.log('Dropped file:', file.name);
      
      // If available, get the file system handle
      if (item.webkitGetAsEntry) {
        const entry = item.webkitGetAsEntry();
        if (entry) {
          await processEntry(entry);
        }
      }
    }
  }
});

async function processEntry(entry) {
  if (entry.isFile) {
    console.log('This is a file:', entry.name);
  } else if (entry.isDirectory) {
    console.log('This is a directory:', entry.name);
  }
}
```

This implementation creates a complete drag-and-drop experience. The `dragover` and `dragleave` events handle the visual feedback, showing the user when they are dragging a file over the drop zone. The `drop` event processes the files when they are released.

The key to getting file system handles from dropped files is the `webkitGetAsEntry()` method, which is available in Chrome and other Chromium-based browsers. This method returns a `FileSystemEntry` object that provides information about the dropped item, including whether it is a file or directory.

For applications that need full read and write access to dropped files, you can combine the drag-and-drop approach with the File System Access API. When a user drops a file, you can request permission to access it and then use the file system methods to read or modify it:

```javascript
dropZone.addEventListener('drop', async (e) => {
  e.preventDefault();
  
  const files = e.dataTransfer.files;
  
  for (const file of files) {
    // Try to get a file system handle if available
    if (file.handle) {
      const permission = await file.handle.queryPermission({ mode: 'readwrite' });
      if (permission === 'granted') {
        console.log('We have write access to:', file.name);
>>>>>>> consumer/a24-chrome-file-system-access-api
      }
    }
  }
});
```

<<<<<<< HEAD
The key to integrating drag and drop with the File System Access API is the `getAsFileSystemHandle()` method, which extracts a file system handle from a dropped item. This handle works just like handles obtained through file pickers, allowing you to read, write, or manipulate the dropped files.

For applications that need to handle multiple dropped files or directories, you can implement more sophisticated logic:

```javascript
async function handleDroppedItems(items) {
  const results = [];
  
  for (const item of items) {
    if (item.kind === 'file') {
      const handle = await item.getAsFileSystemHandle();
      if (handle.kind === 'file') {
        results.push({ type: 'file', name: handle.name, handle });
      } else if (handle.kind === 'directory') {
        results.push({ type: 'directory', name: handle.name, handle });
      }
    }
  }
  
  return results;
}
```

This approach allows you to differentiate between files and directories in the drop event, enabling different handling logic for each type. For directories, you might want to recursively process their contents or display them in a tree view.

Visual feedback is important for drag and drop interfaces. Consider implementing highlighting on the drop zone when files are dragged over it, and provide clear feedback when files are successfully processed. You can use the `dragenter` and `dragleave` events to manage these visual states.

## Error Handling and Permission Management

Robust error handling is essential when working with the File System Access API, as file operations can fail for various reasons including user cancellation, permission issues, or files being moved or deleted. Your application should handle these scenarios gracefully to maintain a positive user experience.
=======
This pattern allows your application to not only read dropped files but also modify them in place, providing a seamless experience similar to native desktop applications.

## Browser Support and Feature Detection

Before using the File System Access API in your projects, it is important to understand its browser support and implement feature detection. While the API is available in Chrome, Edge, and other Chromium-based browsers, it is not yet supported in Firefox, Safari, or other browsers. You should always check for API availability before attempting to use it.

Here is a simple feature detection pattern:

```javascript
function isFileSystemAccessSupported() {
  return 'showOpenFilePicker' in window;
}

if (isFileSystemAccessSupported()) {
  console.log('File System Access API is supported!');
} else {
  console.log('File System Access API is not supported in this browser');
  // Fall back to traditional file input approach
}
```

For browsers that do not support the API, you can fall back to using traditional file inputs. While the user experience is not as smooth, your application will still function across all browsers. You might also consider using progressive enhancement, where you provide basic functionality to all users and enhanced features to those with API support.

## Security Considerations and Best Practices

The File System Access API includes several security mechanisms to protect users. Understanding these will help you build more secure applications and avoid common pitfalls. First and foremost, the API requires a user gesture to invoke any file picker. This means file dialogs cannot be opened programmatically without an explicit user action, such as a click or key press.

Permissions are another critical security feature. When you first access a file or directory, the browser prompts the user to grant permission. This permission is tied to the origin of your application and can be revoked by the user at any time. You should always handle the case where permission is denied gracefully.

It is also important to handle errors properly. The File System Access API can throw various errors, such as when the user cancels a file dialog, when permission is denied, or when the file no longer exists. Always wrap your API calls in try-catch blocks:
>>>>>>> consumer/a24-chrome-file-system-access-api

```javascript
async function safeOpenFile() {
  try {
    const [fileHandle] = await window.showOpenFilePicker();
<<<<<<< HEAD
    return fileHandle;
  } catch (error) {
    switch (error.name) {
      case 'AbortError':
        // User cancelled the picker
        console.log('File selection cancelled');
        return null;
      case 'NotAllowedError':
        alert('Permission denied. Please grant access to continue.');
        break;
      case 'NotFoundError':
        alert('File no longer exists at the specified location.');
        break;
      default:
        console.error('Error opening file:', error);
=======
    return await fileHandle.getFile();
  } catch (error) {
    if (error.name === 'AbortError') {
      console.log('User cancelled the file picker');
    } else {
      console.error('Error opening file:', error);
>>>>>>> consumer/a24-chrome-file-system-access-api
    }
    return null;
  }
}
```

<<<<<<< HEAD
The File System Access API uses the DOMException interface for error reporting, with error names that indicate the type of failure. Understanding these error types allows you to provide appropriate feedback to users and handle each scenario appropriately.
=======
## Combining with Extensions for Enhanced Productivity

The File System Access API becomes even more powerful when combined with Chrome extensions. Extensions have additional capabilities that can enhance file handling workflows. For example, you could build an extension that uses the File System Access API to manage project files while also leveraging other extension APIs for enhanced functionality.

This is similar to how **Tab Suspender Pro** demonstrates the power of combining browser extension capabilities with user-focused features. While Tab Suspender Pro focuses on tab management and memory optimization, the same principle applies to file handling: by combining multiple APIs and features, you can create truly productivity-enhancing tools that go beyond what a simple web application can do.

Extensions can also persist file handles across browser sessions, maintain state more reliably, and interact with other browser features in ways that regular web pages cannot. This makes them ideal for building sophisticated file management tools, development environments, and productivity applications.
>>>>>>> consumer/a24-chrome-file-system-access-api

Permissions can also change over time. Users may revoke access through browser settings, and your application should check permissions before attempting operations:

<<<<<<< HEAD
```javascript
async function checkPermission(fileHandle, readWrite = 'read') {
  const options = {};
  if (readWrite === 'readwrite') {
    options.mode = 'readwrite';
  }
  
  const permission = await fileHandle.queryPermission(options);
  if (permission === 'granted') {
    return true;
  } else if (permission === 'prompt') {
    const newPermission = await fileHandle.requestPermission(options);
    return newPermission === 'granted';
  }
  return false;
}
```

This function checks whether your application has the necessary permission to work with a file handle, and if not, prompts the user to grant access. Always verify permissions before performing file operations to avoid unexpected errors.

When handling sensitive files or large batches of files, implement additional safeguards such as confirming overwrite operations, providing undo capabilities, and maintaining backup copies. These practices help prevent data loss and build user trust in your application.

## Best Practices and Performance Considerations

When implementing the File System Access API, following best practices ensures your application remains performant, secure, and user-friendly. Consider the following recommendations for optimal results.

First, always request the minimum permissions necessary for your application to function. If you only need to read files, don't request write access. This principle of least privilege improves security and makes users more likely to grant permissions.

For applications that work with large files, use streaming operations rather than loading entire files into memory:

```javascript
async function streamLargeFile(fileHandle, processor) {
  const file = await fileHandle.getFile();
  const stream = file.stream();
  const reader = stream.getReader();
  
  while (true) {
    const { done, value } = await reader.read();
    if (done) break;
    await processor(value);
  }
}
```

This approach allows you to process files of any size without running into memory limitations, which is particularly important for applications that handle media files or large datasets.

When storing file handles for later use, prefer IndexedDB over localStorage for better security and capacity:

```javascript
async function saveHandleToIndexedDB(db, handle) {
  const serialized = await handle.serialize();
  const transaction = db.transaction(['handles'], 'readwrite');
  const store = transaction.objectStore('handles');
  await store.put({ id: 'recent', handle: serialized });
}

async function getHandleFromIndexedDB(db) {
  const transaction = db.transaction(['handles'], 'readonly');
  const store = transaction.objectStore('handles');
  const result = await store.get('recent');
  if (result && result.handle) {
    return await window.restoreFileHandle(result.handle);
  }
  return null;
}
```

Finally, consider the user experience around file operations. Provide clear progress indicators for long operations, offer keyboard shortcuts for common file operations, and maintain recent files lists to help users quickly access their work. These considerations transform basic file handling into a polished, professional experience.
=======
The Chrome File System Access API represents a significant advancement in web capabilities, bringing file system access to web applications in a secure and user-controlled manner. Through this API, you can open files with full read and write access, save files to any location on the user's system, work with entire directories, and implement intuitive drag-and-drop interfaces.

The key to using this API effectively lies in understanding its capabilities and limitations. Always implement feature detection to provide fallback experiences for unsupported browsers. Handle errors gracefully and respect user permissions. Use the API in combination with other web technologies to build rich, interactive applications.

As browser technology continues to evolve, we can expect the File System Access API to become more widely supported and more powerful. By learning it now, you are positioning yourself to build the next generation of web applications that feel as capable as native desktop software.
>>>>>>> consumer/a24-chrome-file-system-access-api

Built by theluckystrike — More tips at [zovo.one](https://zovo.one)
