---
layout: post
title: "Chrome File System Access API Guide"
description: "Learn how to use the Chrome File System Access API to open, save, and manage files and directories directly from your web applications."
date: 2026-01-15
categories: [development, api, chrome]
tags: [chrome-file-system-access-api, file-api, web-development, browser-api]
author: theluckystrike
---

# Chrome File System Access API Guide

The Chrome File System Access API represents one of the most significant advancements in web development capabilities in recent years. This powerful API enables web applications to interact with the local file system in ways that were previously impossible without requiring users to upload or download files through traditional input elements. If you are building web applications that need to read, write, or manage files and directories, this guide will walk you through everything you need to know to get started.

## What is the File System Access API?

The File System Access API is a web API that allows web applications to read from and write to files and directories on the user's local device. Unlike the traditional file input element, which only lets users select files for upload, the File System Access API provides a much more powerful and flexible interface for file operations.

This API is particularly useful for web-based code editors, document editors, image editors, and any application that needs to work with files without requiring a full desktop application. It bridges the gap between web and native applications, giving web developers capabilities that were once exclusive to native software.

One of the key benefits of this API is that it maintains user control over their files. Unlike traditional file uploads where files are copied to a server, the File System Access API allows applications to work directly with files on the user's device. This means better performance, offline capability, and enhanced privacy since files don't necessarily need to leave the user's computer.

Browser support for the File System Access API has been growing, with Chrome being the primary browser that fully supports this feature. Other Chromium-based browsers like Edge also support it, while Firefox and Safari have limited or experimental support. As a developer, you should implement appropriate fallbacks and provide clear user feedback when the API is not available.

## Opening Files with the File System Access API

The most fundamental operation with the File System Access API is opening files. This process is straightforward and provides a much better user experience than the traditional file input element. When you call the file picker, users see the same native file dialog they would see when using a desktop application.

To open a file, you use the `showOpenFilePicker()` method, which is part of the window's filesystem object. This method returns an array of FileSystemFileHandle objects, each representing a file the user has selected. The method accepts an options object that lets you configure the file picker behavior.

```javascript
async function openFile() {
  try {
    const [fileHandle] = await window.showOpenFilePicker({
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
            '*/*': ['.*']
          }
        }
      ],
      multiple: false
    });
    
    const file = await fileHandle.getFile();
    const contents = await file.text();
    console.log('File contents:', contents);
    return fileHandle;
  } catch (err) {
    console.error('Error opening file:', err);
  }
}
```

The `types` option in the configuration object allows you to define what types of files users can select. This works similarly to the accept attribute on traditional file input elements but provides a more descriptive interface. You can define multiple file types with descriptions that help users understand what they are selecting.

You can also allow users to select multiple files by setting `multiple: true`. When you do this, the returned array will contain multiple file handles instead of just one. This is useful for batch operations or applications that need to work with multiple files simultaneously.

After obtaining a file handle, you can read the file's contents using the standard File API. The `getFile()` method returns a File object that you can read using methods like `text()`, `arrayBuffer()`, or by creating a FileReader. The file handle also preserves information about the file, including its name and last modified date.

## Saving Files to the File System

Saving files is equally important, and the File System Access API makes this process seamless. The `showSaveFilePicker()` method opens a save dialog where users can choose where to save their file and what to name it.

```javascript
async function saveFile(contents, suggestedName = 'document.txt') {
  try {
    const fileHandle = await window.showSaveFilePicker({
      suggestedName: suggestedName,
      types: [
        {
          description: 'Text File',
          accept: {
            'text/plain': ['.txt']
          }
        },
        {
          description: 'Markdown File',
          accept: {
            'text/markdown': ['.md']
          }
        }
      ]
    });
    
    const writable = await fileHandle.createWritable();
    await writable.write(contents);
    await writable.close();
    
    console.log('File saved successfully');
  } catch (err) {
    console.error('Error saving file:', err);
  }
}
```

The save picker supports a `suggestedName` parameter that provides a default filename to the user. They can accept this suggestion or change it to something else. The types configuration works the same way as the open picker, helping users understand what type of file they are creating.

The `createWritable()` method is key to saving files. It returns a FileSystemWritableFileStream that you can write to using standard stream methods. After writing your content, it's important to call `close()` to ensure all data is flushed to disk. The API handles buffering automatically, but properly closing the stream ensures data integrity.

One powerful feature of the save functionality is that you can update existing files. If the user selects an existing file, the API will overwrite it with the new content. This makes it easy to implement save functionality that feels natural to users who are accustomed to desktop applications.

## Working with Directories

Beyond individual files, the File System Access API supports directory operations, which opens up even more possibilities for web applications. You can allow users to select a directory and then read its contents, create new files within it, or traverse the directory structure.

To open a directory, use the `showDirectoryPicker()` method:

```javascript
async function openDirectory() {
  try {
    const dirHandle = await window.showDirectoryPicker();
    
    for await (const entry of dirHandle.values()) {
      console.log(`${entry.kind}: ${entry.name}`);
    }
    
    return dirHandle;
  } catch (err) {
    console.error('Error opening directory:', err);
  }
}
```

The directory handle provides several methods for interacting with the directory contents. The `values()` method returns an async iterator that yields entries for each file and subdirectory within the selected directory. Each entry has a `kind` property that indicates whether it is a file or directory, and a `name` property with the entry's name.

You can also create new files and directories within an opened directory:

```javascript
async function createFileInDirectory(dirHandle, fileName, contents) {
  const fileHandle = await dirHandle.getFileHandle(fileName, { create: true });
  const writable = await fileHandle.createWritable();
  await writable.write(contents);
  await writable.close();
}

async function createSubdirectory(dirHandle, dirName) {
  const subDirHandle = await dirHandle.getDirectoryHandle(dirName, { create: true });
  return subDirHandle;
}
```

The `getFileHandle()` and `getDirectoryHandle()` methods accept an options object with a `create` parameter. When set to `true`, these methods will create the file or directory if it doesn't exist. This makes it straightforward to implement features like creating new files or folders within a project directory.

For applications like code editors or file managers, the ability to work with directories is transformative. Users can open their entire project folder and navigate through files naturally, just as they would with a desktop application.

## Implementing Drag and Drop Functionality

Drag and drop is an intuitive way for users to interact with files, and the File System Access API integrates well with the HTML5 drag and drop API. You can combine these APIs to create powerful interfaces where users can drag files from their desktop directly into your web application.

The key to implementing drag and drop with file system access is handling the `drop` event and accessing the files through the DataTransfer object:

```javascript
const dropZone = document.getElementById('dropZone');

dropZone.addEventListener('dragover', (e) => {
  e.preventDefault();
  dropZone.classList.add('drag-over');
});

dropZone.addEventListener('dragleave', (e) => {
  e.preventDefault();
  dropZone.classList.remove('drag-over');
});

dropZone.addEventListener('drop', async (e) => {
  e.preventDefault();
  dropZone.classList.remove('drag-over');
  
  const items = e.dataTransfer.items;
  
  for (const item of items) {
    if (item.kind === 'file') {
      const file = item.getAsFile();
      console.log('Dropped file:', file.name);
      
      // If available, get the file system handle for write access
      if (item.webkitGetAsEntry) {
        const entry = item.webkitGetAsEntry();
        if (entry && entry.isFile) {
          // Handle the file
        }
      }
    }
  }
});
```

For the most complete integration, you can use the `DataTransferItem.getAsFileSystemHandle()` method, which is part of the File System Access API extension to the drag and drop API. This method returns a FileSystemFileHandle or FileSystemDirectoryHandle, giving you full read and write access to dropped items:

```javascript
dropZone.addEventListener('drop', async (e) => {
  e.preventDefault();
  
  const items = e.dataTransfer.items;
  
  for (const item of items) {
    if (item.kind === 'file') {
      try {
        const handle = await item.getAsFileSystemHandle();
        
        if (handle.kind === 'file') {
          const file = await handle.getFile();
          console.log('File handle obtained for:', file.name);
          
          // Now you can read or write to this file
        } else if (handle.kind === 'directory') {
          console.log('Directory dropped:', handle.name);
          
          // You can traverse the directory
          for await (const entry of handle.values()) {
            console.log('  -', entry.name);
          }
        }
      } catch (err) {
        console.error('Error getting handle:', err);
      }
    }
  }
});
```

This approach provides a much richer experience than traditional drag and drop, which only gives you read access to file contents. With file system handles, you can potentially modify files that users drop into your application, enabling workflows that feel completely native.

## Handling Permissions and Security

Security is a crucial consideration when working with the File System Access API. The API is designed to require explicit user permission before any file operations can occur. Users must intentionally choose to open files or directories through the picker dialogs.

However, permissions are not granted indefinitely. After a page is closed or a certain amount of time passes, you may need to request permission again to access previously opened files:

```javascript
async function requestPermission(fileHandle) {
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

The `queryPermission()` method lets you check the current permission status without prompting the user, while `requestPermission()` will prompt the user if permission hasn't been granted yet. This two-step approach is useful for providing a good user experience—you can check first and only ask if necessary.

You should always handle permission denials gracefully. If a user denies permission or closes the picker without selecting anything, your application should respond appropriately without confusing error messages. The API throws an AbortError when users cancel operations, which you can distinguish from other errors.

For directory handles, you can also check and request permission to traverse subdirectories:

```javascript
async function checkDirPermission(dirHandle) {
  try {
    for await (const entry of dirHandle.values()) {
      // This implicitly requests permission if needed
    }
    return true;
  } catch (err) {
    if (err.name === 'NotAllowedError') {
      return false;
    }
    throw err;
  }
}
```

## Practical Example: A Simple Text Editor

To tie everything together, let's look at a practical example of how you might build a simple text editor using the File System Access API. This demonstrates how all the pieces work together in a real application:

```javascript
class SimpleTextEditor {
  constructor() {
    this.currentHandle = null;
    this.isModified = false;
  }
  
  async open() {
    try {
      const [handle] = await window.showOpenFilePicker({
        types: [{
          description: 'Text Files',
          accept: { 'text/plain': ['.txt', '.md', '.js', '.html', '.css'] }
        }]
      });
      
      this.currentHandle = handle;
      const file = await handle.getFile();
      const contents = await file.text();
      
      this.loadContent(contents);
      this.updateTitle(file.name);
    } catch (err) {
      if (err.name !== 'AbortError') {
        console.error('Error opening file:', err);
      }
    }
  }
  
  async save() {
    if (!this.currentHandle) {
      return this.saveAs();
    }
    
    try {
      const writable = await this.currentHandle.createWritable();
      await writable.write(this.getContent());
      await writable.close();
      this.isModified = false;
    } catch (err) {
      console.error('Error saving file:', err);
    }
  }
  
  async saveAs() {
    try {
      const handle = await window.showSaveFilePicker({
        suggestedName: 'untitled.txt',
        types: [{
          description: 'Text Files',
          accept: { 'text/plain': ['.txt'] }
        }]
      });
      
      this.currentHandle = handle;
      await this.save();
      const file = await handle.getFile();
      this.updateTitle(file.name);
    } catch (err) {
      if (err.name !== 'AbortError') {
        console.error('Error saving file:', err);
      }
    }
  }
  
  loadContent(text) {
    document.getElementById('editor').value = text;
    this.isModified = false;
  }
  
  getContent() {
    return document.getElementById('editor').value;
  }
  
  updateTitle(name) {
    document.title = `${name} - Simple Editor`;
  }
}
```

This example shows how to implement open, save, and save-as functionality using the File System Access API. The editor maintains a reference to the current file handle, which allows users to make changes and save them back to the same location without having to choose where to save each time.

## Performance Considerations and Best Practices

When working with the File System Access API, there are several best practices and performance considerations to keep in mind. First, always use streaming methods for large files rather than trying to read everything into memory at once. The `createWritable()` method returns a stream that handles buffering automatically.

For very large files, consider using the FileSystemWritableFileStream in combination with chunked reading and writing:

```javascript
async function copyFileWithProgress(sourceHandle, destHandle) {
  const sourceFile = await sourceHandle.getFile();
  const writable = await destHandle.createWritable();
  
  const reader = sourceFile.stream().getReader();
  
  while (true) {
    const { done, value } = await reader.read();
    
    if (done) {
      break;
    }
    
    await writable.write(value);
    // Update progress indicator here
  }
  
  await writable.close();
}
```

This approach allows you to process files of any size without running into memory limitations. It also enables progress reporting, which improves the user experience for long operations.

Another important consideration is error handling. File system operations can fail for many reasons, including the file being deleted or modified by another application, permission issues, or hardware errors. Always wrap file operations in try-catch blocks and provide meaningful error messages to users.

## Browser Support and Fallbacks

While the File System Access API is powerful, it's important to implement fallbacks for browsers that don't support it. The traditional file input element and the download attribute can provide basic functionality:

```javascript
async function openFileWithFallback() {
  if ('showOpenFilePicker' in window) {
    return openFileWithAPI();
  } else {
    return openFileWithInput();
  }
}

function openFileWithInput() {
  return new Promise((resolve) => {
    const input = document.createElement('input');
    input.type = 'file';
    
    input.addEventListener('change', (e) => {
      const file = e.target.files[0];
      resolve(file);
    });
    
    input.click();
  });
}
```

For saving files in browsers without API support, you can create a blob URL and trigger a download:

```javascript
function downloadFile(content, filename) {
  const blob = new Blob([content], { type: 'text/plain' });
  const url = URL.createObjectURL(blob);
  
  const a = document.createElement('a');
  a.href = url;
  a.download = filename;
  a.click();
  
  URL.revokeObjectURL(url);
}
```

These fallbacks won't provide the same seamless experience as the File System Access API, but they ensure your application remains functional across all browsers.

## The Future of File System Access on the Web

The File System Access API represents a significant step forward in blurring the lines between web and native applications. As browser support continues to expand and more developers adopt these capabilities, we can expect to see increasingly sophisticated web applications that rival their desktop counterparts.

If you're building applications that work with files, this API is an essential tool in your arsenal. Whether you're creating a code editor, a document processor, a media editor, or any application that manages user files, the File System Access API provides the foundation you need.

For Chrome extension developers, this API opens up even more possibilities. Extensions can leverage these capabilities to provide rich file management features, and they're particularly useful when combined with other extension APIs. If you're developing productivity extensions like **Tab Suspender Pro**, which helps users manage browser tabs and improve performance, you might consider adding features that export or backup user settings to local files using this API.

The ability to persist data locally without relying on cloud services gives users more control over their information and can improve application performance, especially in scenarios with limited or no internet connectivity. This aligns well with the growing demand for privacy-conscious applications that minimize data transmission.

As with any powerful API, it's important to use the File System Access API responsibly. Always be transparent about what data you're accessing and why, handle errors gracefully, and provide users with control over their files. When used thoughtfully, this API enables experiences that were previously impossible on the web while respecting user privacy and security.

---

Built by theluckystrike — More tips at [zovo.one](https://zovo.one)
