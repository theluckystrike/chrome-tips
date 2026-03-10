---
layout: post
title: "Chrome File System Access API Guide"
description: "Learn how to use the Chrome File System Access API to open files, save files, access directories, and implement drag and drop functionality in your web applications."
date: 2026-01-15
categories: [extensions, development, api]
tags: [chrome-api, file-system, web-development, javascript]
author: theluckystrike
---

# Chrome File System Access API Guide

The Chrome File System Access API represents one of the most significant advancements in web development for handling local files directly from the browser. This powerful API enables web applications to read, write, and manage files and directories on a user's local system without requiring them to upload anything to a server. For developers building productivity tools, code editors, image editors, or any application that benefits from deep file system integration, understanding this API opens up tremendous possibilities.

## What Is the File System Access API?

The File System Access API is a web API that allows websites to interact with the local file system in a secure and user-controlled manner. Unlike traditional file input elements that require users to select files through a system dialog and then upload them to a server, the File System Access API lets users grant websites direct read and write access to specific files and folders on their device.

This capability bridges the gap between web applications and native desktop applications. Previously, web developers were limited to the relatively cumbersome process of using file input elements, reading file contents into memory, processing them, and then requiring users to download the results. With the File System Access API, you can create true local-first applications that feel as responsive and capable as their desktop counterparts.

The API is currently supported in Chrome, Edge, and other Chromium-based browsers, making it a viable choice for many real-world applications. It provides three main capabilities: opening files for reading, saving files (either by creating new files or modifying existing ones), and accessing directory contents for batch operations.

## Opening Files with the API

The most fundamental operation in the File System Access API is opening a file. This allows users to select a file from their local system and grant your web application access to read its contents. The primary method for this is the `showOpenFilePicker()` function, which displays a native file picker dialog and returns a handle to the selected file.

To open a file, you call `showOpenFilePicker()` with configuration options that specify what types of files your application can handle. The method returns an array of file system file handles, even though most use cases involve selecting a single file. Each handle provides access to the file's data and metadata.

```javascript
async function openFile() {
  const [fileHandle] = await window.showOpenFilePicker({
    types: [{
      description: 'Text Files',
      accept: {
        'text/plain': ['.txt', '.md', '.json'],
      },
    }],
    multiple: false,
  });
  
  const file = await fileHandle.getFile();
  const contents = await file.text();
  return contents;
}
```

This example demonstrates opening a text file. The `types` option defines what file types appear in the picker, filtered by description and MIME type. Users can still select other file types if they choose to, but the filtered types will be prioritized in the dialog.

The returned handle is not the file contents itself but rather a reference to the file on disk. This is important because it means you can read the file contents multiple times without keeping everything in memory. When you need the actual content, you call `getFile()` to get a File object, then use standard File API methods like `text()`, `arrayBuffer()`, or `stream()` to read the contents.

One of the key benefits of this approach is that the file handle persists. You can store it (for example, in IndexedDB or using the File System Access Handle Storage API) and request access again later without requiring the user to reselect the file. This enables features like "recent files" lists that remember which documents the user was working on.

## Saving Files Using the API

Saving files is where the File System Access API truly shines for building productivity applications. The `showSaveFilePicker()` function allows users to choose where to save a file, either creating a new file or overwriting an existing one. This is essential for applications that generate documents, images, or any other type of output that users want to keep.

```javascript
async function saveFile(content) {
  const fileHandle = await window.showSaveFilePicker({
    suggestedName: 'document.txt',
    types: [{
      description: 'Text Files',
      accept: {
        'text/plain': ['.txt'],
      },
    }],
  });
  
  const writable = await fileHandle.createWritable();
  await writable.write(content);
  await writable.close();
}
```

This example shows how to save content to a new file. The `suggestedName` parameter provides a default filename that the user can change. The `createWritable()` method returns a writable stream that you can use to write data to the file. After writing, you must close the writable stream to ensure all data is flushed to disk.

What makes this particularly powerful is the ability to modify existing files. If the user selects an existing file through the save dialog (or if you programmatically pass an existing file handle), the API will ask for permission to modify that file. Users maintain full control over which files can be modified, and Chrome displays clear indicators in the address bar when a site has write access to a file.

The write operation supports various data types, including strings, Blob objects, and ArrayBuffer instances. For large files, streaming writes are supported, which prevents memory issues when dealing with substantial amounts of data.

A common pattern in applications is to check if you already have permission to write to a file handle before prompting the user again. You can verify permission status using the `queryPermission()` method:

```javascript
async function writeToExistingFile(fileHandle, content) {
  const options = { mode: 'readwrite' };
  
  if ((await fileHandle.queryPermission(options)) === 'granted') {
    const writable = await fileHandle.createWritable();
    await writable.write(content);
    await writable.close();
  } else if ((await fileHandle.requestPermission(options)) === 'granted') {
    const writable = await fileHandle.createWritable();
    await writable.write(content);
    await writable.close();
  }
}
```

This code first checks if the file already has write permission. If not, it requests permission from the user. This creates a smoother user experience by avoiding unnecessary permission prompts.

## Directory Access and Batch Operations

Beyond working with individual files, the File System Access API provides powerful capabilities for accessing entire directories. This is incredibly valuable for applications that need to process multiple files at once, such as photo organizers, code utilities, or backup tools.

The `showDirectoryPicker()` function opens a directory picker and returns a handle to the selected directory. From this handle, you can enumerate all files and subdirectories within:

```javascript
async function handleDirectory() {
  const dirHandle = await window.showDirectoryPicker();
  
  for await (const entry of dirHandle.values()) {
    if (entry.kind === 'file') {
      const file = await entry.getFile();
      console.log(`File: ${file.name} (${file.size} bytes)`);
    } else if (entry.kind === 'directory') {
      console.log(`Directory: ${entry.name}`);
    }
  }
}
```

The `values()` method returns an async iterator that yields each entry in the directory. Each entry has a `kind` property indicating whether it is a file or directory, and a `name` property with its filename. For files, you can call `getFile()` to obtain the File object with metadata like size, modification date, and the ability to read contents.

You can also access nested directories recursively to build complete file trees or process entire directory structures. When working with subdirectories, you need to request appropriate permissions for each directory you want to access:

```javascript
async function processDirectory(dirHandle, depth = 0) {
  for await (const entry of dirHandle.values()) {
    console.log('  '.repeat(depth) + entry.name);
    
    if (entry.kind === 'directory') {
      // Request permission for the subdirectory
      await entry.requestPermission({ mode: 'readwrite' });
      await processDirectory(entry, depth + 1);
    }
  }
}
```

This recursive function processes all contents of a directory and its subdirectories. Note that you must explicitly request permission for each directory you want to access beyond the initially selected folder.

Directory handles also support creating new files and directories within the selected folder:

```javascript
async function createNewFile(dirHandle, filename, content) {
  const fileHandle = await dirHandle.getFileHandle(filename, { create: true });
  const writable = await fileHandle.createWritable();
  await writable.write(content);
  await writable.close();
}

async function createNewDirectory(dirHandle, dirname) {
  await dirHandle.getDirectoryHandle(dirname, { create: true });
}
```

These methods enable applications to act as full-featured file managers, allowing users to organize their files directly through your web application.

## Implementing Drag and Drop Functionality

The File System Access API integrates seamlessly with the HTML5 Drag and Drop API to create intuitive interfaces where users can drag files from their desktop directly into your application. This is particularly useful for web-based image editors, document processors, and data import tools.

When files are dropped onto a drop zone in your application, you receive a DataTransferItemList containing entries that may be file system handles or regular File objects. When using the File System Access API with drag and drop, you can request that the dropped items provide file system handles rather than just file data:

```javascript
const dropZone = document.getElementById('dropZone');

dropZone.addEventListener('drop', async (event) => {
  event.preventDefault();
  
  for (const item of event.dataTransfer.items) {
    if (item.kind === 'file') {
      const entry = item.webkitGetAsEntry();
      
      if (entry) {
        // Handle as file system entry
        if (entry.isFile) {
          const fileHandle = await entry.getAsFileSystemHandle();
          console.log('Dropped file:', fileHandle.name);
        } else if (entry.isDirectory) {
          console.log('Dropped directory:', entry.name);
        }
      } else {
        // Fallback for regular file objects
        const file = item.getAsFile();
        console.log('Dropped file (legacy):', file.name);
      }
    }
  }
});

dropZone.addEventListener('dragover', (event) => {
  event.preventDefault();
});
```

This code sets up a drop zone that accepts files and directories. The `webkitGetAsEntry()` method returns a FileSystemFileEntry or FileSystemDirectoryEntry for items that are part of the file system, allowing you to work with them using the File System Access API patterns described earlier.

The integration between drag and drop and the File System Access API means you can build applications that accept files through traditional file pickers, drag and drop, or both. Users can choose whichever workflow feels most natural for their situation.

For applications that need to read file contents immediately upon drop, you can combine drag and drop with the file reading capabilities:

```javascript
async function handleDroppedFile(item) {
  const entry = item.webkitGetAsEntry();
  
  if (entry && entry.isFile) {
    const fileHandle = await entry.getAsFileSystemHandle();
    const file = await fileHandle.getFile();
    const content = await file.text();
    return content;
  }
  
  return null;
}
```

This pattern is particularly useful for text editors that want to open dropped files, image editors that need to process dropped images, or any application where opening files is the primary workflow.

## Security Considerations and Best Practices

The File System Access API is designed with security and user privacy as core principles. Unlike older approaches that gave websites broad access to the file system, this API requires explicit user action and permission for every access attempt.

When a site attempts to open or save a file, the browser displays a system dialog that clearly shows which file or directory the site wants to access. Users can grant or deny permission at any time, and they can revoke previously granted permissions through browser settings.

Chrome indicates in the address bar when a site has access to file handles, providing ongoing visibility into which sites can read or modify local files. This visual indicator helps users stay informed about their security status.

For developers, there are several best practices to follow. Always request the minimum permissions necessary for your application's functionality. If you only need to read files, don't request write access. If you only need access to one file, don't request an entire directory.

Handle permission denials gracefully. Users may deny permission for various reasons, and your application should continue to function (perhaps by falling back to traditional file input methods) rather than crashing or displaying confusing errors.

Store file handles securely if your application needs to remember them between sessions. IndexedDB is the recommended storage mechanism, as localStorage has size limits that would quickly become problematic for file handles. When storing handles, be aware that users may move or delete files, so always verify that a handle is still valid before attempting to use it.

Consider implementing auto-save functionality that periodically writes changes to the file system. This protects users from losing work if their browser crashes or if they accidentally close the tab. The File System Access API supports streaming writes that are efficient enough for frequent auto-saves.

## Practical Applications and Use Cases

The File System Access API enables a wide range of powerful applications. Code editors like VS Code for Web can now offer a genuine local development experience where users can open folders directly from their filesystem and edit files in place.

Image editing applications can load images from the local disk, apply edits, and save back to the original file or create new versions. The ability to work with existing files eliminates the friction of exporting and importing between different applications.

Documentation tools can read from and write to local Markdown files, maintaining direct synchronization between the source files and the web application. This creates a seamless workflow for technical writers and documentation maintainers.

Data analysis tools can import large datasets directly from local CSV or JSON files, process them in the browser, and export results to local files without any server round-trips.

For extension developers, the File System Access API opens up possibilities for building more sophisticated tools. If you're developing something like **Tab Suspender Pro**, which helps users manage their browser tabs and improve performance, you could use this API to import and export configuration settings, save tab session data locally, or integrate with local backup systems.

## Browser Support and Fallbacks

While the File System Access API provides powerful capabilities, it is not universally supported across all browsers. Firefox and Safari have not yet implemented the full API, though Firefox has indicated interest and may add support in the future.

For applications that need to work across all browsers, you'll need to implement fallback strategies. The traditional `<input type="file">` element and the File API remain the standard fallback approach. Your application can detect API support using feature detection:

```javascript
if ('showOpenFilePicker' in window) {
  // Use File System Access API
} else {
  // Use traditional file input
}
```

When using fallbacks, try to maintain a consistent user experience as much as possible. The File System Access API offers a more seamless experience, but the core functionality of reading and writing files remains available through traditional methods.

For progressive enhancement, you can use the File System Access API where available while still supporting users on other browsers. This approach lets users with modern browsers enjoy the full experience while ensuring everyone can still use your application.

## Conclusion

The Chrome File System Access API represents a transformative capability for web development. By enabling direct, user-controlled access to local files and directories, it closes the gap between web and native applications in ways that were previously impossible.

The API's three core functions—opening files, saving files, and directory access—provide the foundation for building sophisticated local-first applications. Combined with drag and drop support, you can create intuitive interfaces that feel natural and powerful.

Remember to always prioritize user security by requesting only necessary permissions, handling denials gracefully, and providing clear feedback about what's happening with their files. With these considerations in mind, the File System Access API becomes an incredibly valuable tool for creating web applications that users can genuinely rely on for their daily work.

Built by theluckystrike — More tips at [zovo.one](https://zovo.one)
