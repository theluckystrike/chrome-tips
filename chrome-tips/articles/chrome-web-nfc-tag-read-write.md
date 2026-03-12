---
layout: default
title: Chrome Web NFC Tag Read and Write - Complete Guide
description: Learn how to use Chrome Web NFC API to read and write NFC tags directly from your browser. A practical guide with code examples and real-world applications.
---

# Chrome Web NFC Tag Read and Write: A Practical Guide

Chrome Web NFC capability represents one of the most exciting advancements in browser technology, allowing web developers to create applications that can communicate directly with NFC tags. This technology opens up a wide range of possibilities for interactive web experiences, from retail applications to event management systems.

## What Is Chrome Web NFC?

The Web NFC API enables web pages to read and write NFC tags through the browser. NFC (Near Field Communication) uses short-range wireless technology to exchange data between devices when they are placed close together, typically within 4 centimeters or less.

Chrome became the first browser to implement Web NFC support, making it available on Android devices running Chrome 89 and later. This feature allows web developers to build Progressive Web Apps (PWAs) that can interact with physical NFC tags without requiring a native application.

## Device and Browser Requirements

Before building NFC-enabled web applications, you need to ensure your target devices meet the necessary requirements. Web NFC works exclusively on mobile devices with NFC hardware, and it requires Chrome on Android.

Your users will need:
- An Android device with NFC capability
- Chrome 89 or later version
- A secure context (HTTPS) for the website
- Explicit user permission to access NFC

Desktop browsers do not support Web NFC because they lack NFC hardware. However, the API is designed to gracefully degrade on unsupported devices, allowing you to provide alternative experiences.

## How to Read NFC Tags in Chrome

Reading NFC tags with the Web NFC API involves checking for browser support, requesting permission, and then scanning for tags. Here is a practical example:

```javascript
async function startNfcScan() {
  if (!('NDEFReader' in window)) {
    console.log('Web NFC is not supported in this browser');
    return;
  }

  const ndef = new NDEFReader();

  try {
    await ndef.scan();
    console.log('Scan started successfully');

    ndef.onreading = event => {
      const decoder = new TextDecoder();
      for (const record of event.message.records) {
        console.log('Record type:', record.recordType);
        console.log('Data:', decoder.decode(record.data));
      }
    };
  } catch (error) {
    console.error('Error starting NFC scan:', error);
  }
}
```

The scan method initiates the NFC polling process. When a compatible tag comes into range, the onreading event handler receives an NDEFMessage object containing the tag's records. Each record has a recordType, mediaType, and data property that you can process according to your application's needs.

## Writing Data to NFC Tags

Writing to NFC tags follows a similar pattern to reading. You create an NDEFReader instance and call the write method with the data you want to store:

```javascript
async function writeToNfcTag(message) {
  if (!('NDEFReader' in window)) {
    console.log('Web NFC is not supported');
    return;
  }

  const ndef = new NDEFReader();

  try {
    await ndef.write(message);
    console.log('Data written successfully');
  } catch (error) {
    console.error('Write failed:', error);
  }
}

// Example usage
writeToNfcTag({
  records: [
    { recordType: 'text', data: 'Hello from Chrome Web NFC!' }
  ]
});
```

When writing data, keep in mind that NFC tags have limited storage capacity. Most standard NDEF tags can hold between 144 bytes and several kilobytes, depending on the tag type. Text records are typically encoded in UTF-8, so account for this when planning your data structure.

## Permissions and User Interaction

Web NFC requires explicit user permission before the browser can access NFC functionality. The permission request happens automatically when you call the scan or write methods for the first time.

Chrome displays a permission prompt asking the user to allow or deny NFC access. The user must actively grant permission, and this permission persists only for the current session. If you need ongoing access, you will need to request permission again in subsequent visits.

The permission model ensures users maintain control over their NFC hardware. However, it also means your application should handle permission denial gracefully. Always provide clear instructions to users about why NFC access is needed and what benefits it provides.

## Practical Applications

The ability to read and write NFC tags from a web browser creates numerous practical applications across different industries.

In retail environments, businesses can use Web NFC to create smart product labels. Customers could scan a tag on a product to access detailed information, pricing history, or demonstration videos without downloading a dedicated app.

Event organizers can implement check-in systems using NFC wristbands or badges. Attendees simply tap their badge against a staff member's device, and the system instantly records their presence. This approach is faster than QR codes and works reliably even in crowded venues.

For productivity enthusiasts, combining NFC tags with tools like **Tab Suspender Pro** creates powerful automation workflows. You could tap an NFC tag to automatically open a specific set of tabs, trigger a reading mode extension, or activate a focused browsing session for work tasks.

Inventory management becomes significantly easier when workers can scan tags to update stock levels or locate items. Since Web NFC works in the browser, you can build lightweight inventory systems without app store approval processes.

## Testing Your Implementation

Testing Web NFC applications requires physical NFC tags and a compatible Android device. Chrome DevTools provides emulation capabilities that can help during development, but real-world testing remains essential.

For testing, purchase NFC stickers or tags formatted for NDEF. You can find affordable options online or at electronics stores. Common formats include NTAG213, NTAG215, and NTAG216, which vary in storage capacity.

When debugging, use Chrome's remote debugging features to inspect NFC events. The console will display information about scanned tags, successful writes, and any errors that occur during communication.

## Limitations and Considerations

While Web NFC offers powerful capabilities, developers should understand its current limitations.

The API is available only on Android Chrome, meaning iOS users cannot access NFC functionality through Safari. This limitation significantly impacts the potential audience for NFC-enabled web applications.

NFC communication requires very close proximity, typically less than 4 centimeters. This constraint makes the technology unsuitable for scenarios requiring longer-range interaction.

Security considerations are important when implementing Web NFC. Always validate data read from tags, as malicious tags could potentially contain harmful content. Similarly, when writing sensitive information to tags, consider whether the physical tag could be accessed by unauthorized individuals.

Battery consumption increases during NFC scanning, so consider providing users with controls to start and stop scanning rather than leaving NFC active continuously.

## The Future of Web NFC

Browser NFC support continues to evolve, with discussions ongoing about expanding availability to other platforms. The Web NFC Community Group is working on specification improvements that could bring additional features and better cross-browser compatibility.

As Progressive Web Apps gain more capabilities and browser vendors continue to implement new APIs, web-based NFC solutions will become increasingly viable for production use cases. Keeping up with browser release notes helps you stay informed about new features and compatibility improvements.

Chrome Web NFC represents a significant step toward bridging the gap between web applications and physical objects. By understanding how to read and write NFC tags in Chrome, you can create innovative experiences that combine the accessibility of the web with the tangible interaction of physical tags.

Built by theluckystrike — More tips at [zovo.one](https://zovo.one)
