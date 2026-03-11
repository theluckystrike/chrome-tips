---
layout: post
title: "Chrome File System Access API Guide"
description: "Learn how to use the Chrome File System Access API to open, save, and manage files directly in your browser with full read and write capabilities."
date: 2026-01-20
categories: [chrome, extensions, developer, api]
tags: [chrome-file-system-access-api, file-api, browser-files, web-development]
author: theluckystrike
---

# Chrome File System Access API Guide

The Chrome File System Access API represents one of the most significant advancements in web browser capabilities in recent years. This powerful API enables web applications to read, write, and modify files on a user's local device without requiring them to first upload files to a server. For developers building productivity tools, text editors, image editors, or any application that works with user files, this API opens up possibilities that were previously limited to native desktop applications.

In this comprehensive guide, we will explore the four primary capabilities of the File System Access API: opening files, saving files, directory access, and implementing drag-and-drop functionality. By the end, you will have a solid understanding of how to integrate these features into your own web applications.

## What is the Chrome File System Access API?

The File System Access API is a web API that allows websites to interact with the local file system of a user's device. Unlike the traditional HTML file input element, which only allows users to select files for upload, the File System Access API provides deeper access to files and directories. Users must explicitly grant permission for a website to access their files, ensuring that the API respects user privacy and security.

This API is particularly useful for building web-based applications that need to handle large files, work offline, or provide a seamless experience comparable to desktop software. Applications like online code editors, document processors, and graphic design tools can benefit enormously from these capabilities.

## Opening Files with the File System Access API

The first and most common use case for the File System Access API is opening existing files from the user's device. This functionality replaces the traditional file picker with a more capable and flexible approach.

### The showOpenFilePicker Method

To open a file, you use the `showOpenFilePicker()` method, which displays a native file picker dialog to the user. This method returns an array of file system file handles, giving you access to the selected files. Here is a basic example of how to implement file opening:

```javascript
async function openFile() {
  try {
    const [fileHandle] = await window.showOpenFilePicker();
    const file = await fileHandle.getFile();
    const contents = await file.text();
    console.log('File contents:', contents);
    return contents;
  } catch (error) {
    console.log('File selection cancelled or error occurred:', error);
  }
}
```

This code triggers a file picker that allows the user to select a single file. Once selected, you can read the file's contents using the `getFile()` method, which returns a File object. From there, you can read the content using methods like `text()`, `arrayBuffer()`, or `stream()`, depending on your needs.

### Configuring File Picker Options

The `showOpenFilePicker()` method accepts an options object that lets you customize the file picker behavior. You can specify allowed file types, whether multiple files can be selected, and other preferences:

```javascript
const options = {
  types: [
    {
      description: 'Text Files',
      accept: {
        'text/plain': ['.txt', '.md', '.json']
      }
    },
    {
      description: 'All Files',
      accept: {
        '*/*': ['*']
      }
    }
  ],
  excludeAcceptAllOption: false,
  multiple: false
};

const [fileHandle] = await window.showOpenFilePicker(options);
```

This configuration allows users to filter by text files or view all files. The `multiple` option can be set to `true` if you want to allow selecting multiple files at once. When multiple files are selected, the method returns an array of file handles rather than a single handle.

### Reading File Contents

Once you have a file handle, you can read its contents in various ways. For text files, `text()` is straightforward. For binary files like images, you might use `arrayBuffer()`:

```javascript
const file = await fileHandle.getFile();
const buffer = await file.arrayBuffer();
const imageData = new Uint8Array(buffer);
```

You can also work with the file's metadata, including its name, size, and last modified date:

```javascript
console.log('File name:', file.name);
console.log('File size:', file.size);
console.log('Last modified:', new Date(file.lastModified));
```

## Saving Files with the File System Access API

Saving files is equally important for applications that need to persist user data. The File System Access API makes it possible to save files directly to the user's chosen location, eliminating the need for download prompts.

### The showSaveFilePicker Method

To save a file, you use the `showSaveFilePicker()` method, which displays a save dialog where users can choose where to save their file and what to name it:

```javascript
async function saveFile(content, suggestedName = 'document.txt') {
  try {
    const fileHandle = await window.showSaveFilePicker({
      suggestedName: suggestedName,
      types: [
        {
          description: 'Text Document',
          accept: {
            'text/plain': ['.txt']
          }
        }
      ]
    });
    
    const writable = await fileHandle.createWritable();
    await writable.write(content);
    await writable.close();
    
    console.log('File saved successfully');
  } catch (error) {
    console.log('Save cancelled or error occurred:', error);
  }
}
```

This example demonstrates the complete save workflow. The `createWritable()` method returns a writable stream that you can use to write content to the file. After writing, always call `close()` to ensure the file is properly saved and any resources are released.

### Overwriting Existing Files

If a user selects an existing file, the API will prompt them to confirm whether they want to overwrite it. This behavior is built into the native file picker and helps prevent accidental data loss. However, you can also programmatically check if you are about to overwrite a file and handle that situation appropriately:

```javascript
const fileHandle = await window.showSaveFilePicker({
  suggestedName: 'document.txt'
});

// Check if the file already exists
const file = await fileHandle.getFile();
if (fileHandle.name) {
  console.log('This will overwrite an existing file');
}
```

### Updating Existing Files

One of the most powerful features of the File System Access API is the ability to update existing files without requiring the user to choose a new location each time. When you have a file handle from a previous `showOpenFilePicker()` or `showSaveFilePicker()` call, you can write to it directly:

```javascript
let fileHandle = null;

// First, open a file and remember the handle
async function openAndRemember() {
  const [handle] = await window.showOpenFilePicker();
  fileHandle = handle;
}

// Later, save to the same file
async function saveToExisting() {
  if (!fileHandle) {
    console.log('No file handle available');
    return;
  }
  
  const writable = await fileHandle.createWritable();
  await writable.write('Updated content');
  await writable.close();
}
```

This capability makes applications much more convenient to use, as users do not need to navigate to their file location every time they want to save changes.

## Directory Access with the File System Access API

Beyond individual files, the File System Access API supports working with entire directories. This is particularly useful for applications like file managers, photo galleries, or code editors that need to organize multiple files.

### Opening a Directory

To access a directory, you use the `showDirectoryPicker()` method, which displays a directory selection dialog:

```javascript
async function openDirectory() {
  try {
    const dirHandle = await window.showDirectoryPicker();
    
    // List files in the directory
    for await (const entry of dirHandle.values()) {
      console.log(entry.name, entry.kind);
    }
  } catch (error) {
    console.log('Directory selection cancelled:', error);
  }
}
```

The directory handle provides methods to iterate through entries using `values()` and `keys()`. Each entry has a `name` property and a `kind` property that indicates whether it is a file or directory.

### Reading Directory Contents Recursively

To read all files in a directory and its subdirectories, you can create a recursive function:

```javascript
async function readDirectoryRecursive(dirHandle, path = '') {
  const entries = [];
  
  for await (const entry of dirHandle.values()) {
    const entryPath = path + '/' + entry.name;
    
    if (entry.kind === 'file') {
      const file = await entry.getFile();
      entries.push({
        name: entry.name,
        path: entryPath,
        kind: 'file',
        size: file.size,
        lastModified: file.lastModified
      });
    } else if (entry.kind === 'directory') {
      const subEntries = await readDirectoryRecursive(entry, entryPath);
      entries.push({
        name: entry.name,
        path: entryPath,
        kind: 'directory',
        children: subEntries
      });
    }
  }
  
  return entries;
}
```

This recursive approach allows you to build complete file trees, which is invaluable for applications that need to display or manage folder structures.

### Creating New Files and Directories

The directory handle also allows you to create new files and subdirectories:

```javascript
async function createNewFile(dirHandle, fileName, content) {
  const fileHandle = await dirHandle.getFileHandle(fileName, { create: true });
  const writable = await fileHandle.createWritable();
  await writable.write(content);
  await writable.close();
}

async function createNewDirectory(dirHandle, dirName) {
  await dirHandle.getDirectoryHandle(dirName, { create: true });
}
```

The `{ create: true }` option tells the API to create the file or directory if it does not already exist. If the file or directory already exists, these methods will return a handle to the existing one.

## Drag and Drop Functionality

The File System Access API works seamlessly with the HTML5 Drag and Drop API, enabling powerful interactions where users can drag files from their desktop directly into a web application.

### Handling Drop Events

To implement drag and drop, you listen for the `drop` event on a designated drop zone:

```javascript
const dropZone = document.getElementById('drop-zone');

dropZone.addEventListener('dragover', (event) => {
  event.preventDefault();
  event.dataTransfer.dropEffect = 'copy';
});

dropZone.addEventListener('drop', async (event) => {
  event.preventDefault();
  
  const items = event.dataTransfer.items;
  
  for (const item of items) {
    if (item.kind === 'file') {
      const file = item.getAsFile();
      console.log('Dropped file:', file.name);
      
      // Process the file
      const content = await file.text();
      console.log('Content:', content);
    }
  }
});
```

The `dragover` event must call `preventDefault()` to indicate that the drop zone accepts files. The `dropEffect` property gives users visual feedback about what will happen when they drop the files.

### Using File System Access API with Drag and Drop

For more advanced capabilities, you can combine drag and drop with the File System Access API to get a file handle rather than just a File object:

```javascript
dropZone.addEventListener('drop', async (event) => {
  event.preventDefault();
  
  const items = event.dataTransfer.items;
  
  for (const item of items) {
    if (item.kind === 'file') {
      // Try to get a file system handle
      const entry = item.webkitGetAsEntry();
      
      if (entry.isFile) {
        // This gives us more capabilities than a regular File object
        console.log('Got file entry:', entry.name);
      }
    }
  }
});
```

This approach provides access to additional functionality, though the exact API varies depending on browser support. The File System Access API continues to evolve, and combining it with drag and drop creates intuitive user experiences for file-heavy applications.

## Permission Management

When using the File System Access API, you must understand how permissions work. Users grant permission each time they use a file picker, but if you want to retain access to a file or directory for subsequent operations, you need to request persistent permission.

### Requesting Persistent Permission

By default, permission to access a file or directory is temporary and will expire when the user closes the browser tab. To maintain access across sessions, you can request persistent permission:

```javascript
async function requestPersistentPermission(fileHandle) {
  const options = {
    mode: 'readwrite'
  };
  
  if ((await fileHandle.queryPermission(options)) === 'granted') {
    return true;
  }
  
  if ((await fileHandle.requestPermission(options)) === 'granted') {
    return true;
  }
  
  return false;
}
```

This function first checks if permission is already granted, and if not, requests it from the user. Once granted, the permission persists until the user explicitly revokes it through browser settings.

### Checking Permission Status

You can also check the current permission status before attempting operations:

```javascript
async function checkPermission(fileHandle) {
  const options = {
    mode: 'readwrite'
  };
  
  const status = await fileHandle.queryPermission(options);
  console.log('Permission status:', status);
  
  return status === 'granted';
}
```

Understanding and properly managing permissions is crucial for building trustworthy applications that respect user control over their files.

## Browser Support and Fallbacks

While the File System Access API is powerful, it is important to note that browser support varies. Chrome and Edge offer the most complete support, while other browsers may have limited or no support.

### Feature Detection

Always use feature detection before attempting to use the API:

```javascript
function isFileSystemAccessSupported() {
  return 'showOpenFilePicker' in window;
}

if (isFileSystemAccessSupported()) {
  console.log('File System Access API is supported');
} else {
  console.log('File System Access API is not supported');
}
```

For browsers that do not support the API, you can fall back to traditional approaches like HTML file inputs or downloadable files. This ensures your application works for all users regardless of their browser.

## A Note on Browser Performance

When building applications that work extensively with files, browser performance can become a concern. Managing many open files and tabs can consume significant memory and system resources. If you find that your browser is becoming sluggish while working with file-heavy applications, consider using extension tools to help manage your tabs and resources more efficiently.

For example, **Tab Suspender Pro** is a tool that automatically suspends tabs you are not actively using, reducing memory usage and helping your browser run more smoothly. This can be particularly helpful when you are working with multiple files across several tabs in your web application.

## Conclusion

The Chrome File System Access API represents a major step forward in web development, enabling browser-based applications to rival native desktop software in their ability to work with files. Through the capabilities covered in this guide, you can now implement file opening, saving, directory traversal, and drag-and-drop functionality in your web applications.

Remember to always implement proper permission handling, provide appropriate fallbacks for unsupported browsers, and respect user privacy and security throughout the user experience. With these practices in place, you can build powerful file-handling applications that provide excellent user experiences while maintaining the safety and security that users expect.

Built by theluckystrike — More tips at [zovo.one](https://zovo.one)
