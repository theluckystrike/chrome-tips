---
layout: "default"
title: "Chrome Web Bluetooth API Guide — Connect Devices Directly in Your Browser"
description: "Learn how to use the Chrome Web Bluetooth API to connect Bluetooth devices directly from your browser. Covers device pairing, GATT services, characteristics,..."
date: "2026-03-11"
last_modified_at: "2026-03-11"
permalink: "chrome-web-bluetooth-api-guide"
categories: "[development, bluetooth, web-api]"
tags: "[chrome-web-bluetooth-api, web-bluetooth, bluetooth-gatt, device-pairing, web-development]"
author: "theluckystrike"
---
# Chrome Web Bluetooth API Guide — Connect Devices Directly in Your Browser

<<<<<<< HEAD
<<<<<<< HEAD
=======
>>>>>>> consumer/a65-chrome-web-bluetooth-api-guide
The Chrome Web Bluetooth API represents one of the most exciting additions to browser capabilities in recent years. It enables web developers to create applications that can communicate directly with Bluetooth Low Energy (BLE) devices directly from the browser, eliminating the need for native applications or plugins. This comprehensive guide will walk you through everything you need to know to build robust Bluetooth-enabled web applications using Chrome.

## Understanding Web Bluetooth Fundamentals

Web Bluetooth is a JavaScript API that allows websites to discover and communicate with nearby Bluetooth devices. Unlike traditional Bluetooth that requires native applications, Web Bluetooth works entirely through the browser, making it accessible to any website running in Chrome or other Chromium-based browsers. The API follows the Bluetooth 4.0+ specification and supports the Generic Attribute Profile (GATT) for communicating with BLE devices.

The fundamental architecture of Web Bluetooth revolves around three core concepts: devices, services, and characteristics. Devices are the physical Bluetooth peripherals you want to connect to, such as heart rate monitors, fitness trackers, or IoT sensors. Services are collections of related characteristics that define what a device can do. Characteristics are individual data points within a service that you can read, write, or subscribe to for notifications.

One of the most powerful aspects of the Web Bluetooth API is its security-first approach. The API only works over HTTPS, ensuring that all communication between your website and Bluetooth devices is encrypted. Additionally, Chrome requires explicit user consent before any device connection, giving users full control over which websites can access their Bluetooth devices.

## Device Pairing and Discovery

The first step in working with Web Bluetooth is discovering and connecting to devices. Chrome provides the `navigator.bluetooth.requestDevice()` method as the entry point for device discovery. This method triggers a browser-native dialog that shows the user all nearby discoverable BLE devices, allowing them to select which device to connect to.
<<<<<<< HEAD
=======
The Chrome Web Bluetooth API opens up exciting possibilities for web developers and users alike. This powerful API enables websites to communicate directly with Bluetooth devices, eliminating the need for native applications or browser extensions. Whether you're building a web app to interact with fitness trackers, smart home devices, medical equipment, or industrial sensors, the Web Bluetooth API provides a standardized way to connect and exchange data.

In this comprehensive guide, we'll walk through everything you need to know to get started with the Chrome Web Bluetooth API, from basic device discovery to advanced GATT operations and security best practices.

## What Is the Web Bluetooth API?

The Web Bluetooth API is a JavaScript API that allows websites to discover and communicate with nearby Bluetooth devices using the Generic Attribute Profile (GATT) protocol. Originally developed by Google and now standardized by the W3C, this API brings the power of Bluetooth Low Energy (BLE) to the web platform.

Before this API existed, interacting with Bluetooth devices required native applications installed on the user's device. Now, users can simply visit a website and connect to compatible hardware without installing anything. This opens up new possibilities for cross-platform applications, IoT dashboards, and accessibility tools.

The API supports a wide range of devices, including heart rate monitors, blood pressure cuffs, glucose meters, weight scales, environmental sensors, beacons, and many more. Chrome's implementation follows the Bluetooth 4.0 and 5.0 specifications, ensuring broad compatibility with modern BLE devices.

## Browser Requirements and Enabling the API

The Web Bluetooth API is currently supported in Chrome, Edge, Opera, and Samsung Internet Browser. Firefox and Safari have not implemented this API as of this writing, so you'll need to account for this when building cross-browser applications.

To use the Web Bluetooth API, your site must be served over HTTPS. This is a strict security requirement — the API will not function over HTTP, even on localhost. During development, you can use localhost or 127.0.0.1 without HTTPS, but for production deployments, a valid SSL certificate is mandatory.

Users must also explicitly grant permission for each website that wants to use Bluetooth. Chrome will prompt the user with a device selection dialog, and the user must choose a device and confirm the connection. This user-mediated approach ensures that users maintain control over which devices their browser can access.

## Discovering and Connecting to Devices

The first step in working with Bluetooth devices is discovering what's available. The Web Bluetooth API provides the `navigator.bluetooth.requestDevice()` method for this purpose. This method triggers Chrome's device selection UI, where users can choose from nearby devices.

Here's a basic example of how to request a device:
>>>>>>> consumer/a49-chrome-web-bluetooth-api-guide
=======
>>>>>>> consumer/a65-chrome-web-bluetooth-api-guide

```javascript
async function discoverDevice() {
  try {
    const device = await navigator.bluetooth.requestDevice({
<<<<<<< HEAD
<<<<<<< HEAD
      filters: [{ services: ['battery_service'] }],
      optionalServices: ['device_information']
    });
    
    console.log('Selected device:', device.name);
    return device;
  } catch (error) {
    console.error('Device selection failed:', error);
=======
      filters: [
        { services: ['battery_service'] }
      ],
      optionalServices: ['device_information']
    });
    
    console.log('Device selected:', device.name);
    console.log('Device ID:', device.id);
    
    return device;
  } catch (error) {
    console.error('Error requesting device:', error);
>>>>>>> consumer/a49-chrome-web-bluetooth-api-guide
=======
      filters: [{ services: ['battery_service'] }],
      optionalServices: ['device_information']
    });
    
    console.log('Selected device:', device.name);
    return device;
  } catch (error) {
    console.error('Device selection failed:', error);
>>>>>>> consumer/a65-chrome-web-bluetooth-api-guide
  }
}
```

<<<<<<< HEAD
<<<<<<< HEAD
=======
>>>>>>> consumer/a65-chrome-web-bluetooth-api-guide
The `requestDevice()` method accepts an options object where you can specify which services your application needs. Using the `filters` property restricts the displayed devices to those advertising the specified services, making it easier for users to find the right device. The `optionalServices` property lists services you would like to access but don't require for the connection to succeed.

When designing your device discovery experience, consider providing clear instructions to users about what type of device they should look for. The browser's device selection dialog shows the device's advertised name, which might not always be intuitive. You can improve user experience by providing guidance in your application's UI about what device to select.

After receiving a device reference from `requestDevice()`, you need to establish a connection using the `gatt.connect()` method. This returns a `BluetoothRemoteGATTServer` object that serves as your gateway to the device's GATT server:

```javascript
async function connectToDevice(device) {
  const server = await device.gatt.connect();
  console.log('Connected to GATT server');
  return server;
}
```

It's important to handle disconnection events properly. Devices can disconnect due to range issues, low battery, or user action. You can listen for the disconnection event and implement reconnection logic:

```javascript
device.addEventListener('gattserverdisconnected', () => {
  console.log('Device disconnected');
  // Implement reconnection logic here
});
```

## Working with GATT Services

Once connected to a device's GATT server, you can begin exploring the services it offers. Each BLE device typically provides multiple services, with some being standard (like battery service or heart rate service) and others being manufacturer-specific. The Web Bluetooth API provides methods to discover and access these services.

To get a specific service, use the `getPrimaryService()` method with the service's UUID:

```javascript
async function getBatteryService(server) {
  const service = await server.getPrimaryService('battery_service');
  return service;
}
```

Standard Bluetooth services have well-defined UUIDs that are short and memorable. For example, the Battery Service uses 'battery_service', the Heart Rate Service uses 'heart_rate', and the Device Information Service uses 'device_information'. For manufacturer-specific services, you must use the full 128-bit UUID.

When you need to work with multiple services, you can use `getPrimaryServices()` to retrieve all available services:

```javascript
async function listAllServices(server) {
  const services = await server.getPrimaryServices();
  for (const service of services) {
    console.log('Service UUID:', service.uuid);
  }
  return services;
}
```

Understanding service structures is crucial for building reliable applications. Many devices implement multiple services that work together. For instance, a fitness tracker might provide heart rate monitoring, step counting, and battery status through separate services. Your application needs to handle cases where expected services might not be available.

## Reading and Writing Characteristics

Characteristics are where the actual data lives in the GATT hierarchy. Each characteristic has a value that can be read, written, or both. Some characteristics also support notifications, allowing your application to receive updates when the value changes without continuously polling.

Reading a characteristic value is straightforward with the `readValue()` method:

```async function readBatteryLevel(service) {
  const characteristic = await service.getCharacteristic('battery_level');
  const value = await characteristic.readValue();
  const batteryLevel = value.getUint8(0);
  console.log('Battery level:', batteryLevel + '%');
  return batteryLevel;
}
```

The returned value is a DataView object, which allows you to read the raw bytes in various formats depending on the characteristic's specification. For single-byte values like battery level, `getUint8(0)` retrieves the first byte. More complex data types require different reading methods.

Writing to characteristics uses the `writeValue()` method:

```javascript
async function writeToCharacteristic(characteristic, data) {
  const encoder = new TextEncoder();
  const encodedData = encoder.encode(data);
  await characteristic.writeValue(encodedData);
  console.log('Data written successfully');
}
```

When writing data, you can choose between two write types: "write" and "write-with-response". The default is "write-with-response", where the device acknowledges receipt of the data. Use "write" (without response) for operations where speed is more important than reliability, as it doesn't wait for acknowledgment:

```javascript
await characteristic.writeValue(data, { writeType: 'write-without-response' });
```

## Subscribing to Notifications and Indications

One of the most powerful features of GATT is the ability to subscribe to characteristic notifications. This allows your application to receive real-time updates whenever the device's characteristic value changes, without repeatedly reading the value.

To enable notifications, you need to start notifications on the characteristic:

```javascript
async function subscribeToHeartRate(characteristic) {
  await characteristic.startNotifications();
  
  characteristic.addEventListener('characteristicvaluechanged', (event) => {
    const value = event.target.value;
    const heartRate = value.getUint8(1); // First byte is flags
    console.log('Heart rate:', heartRate);
<<<<<<< HEAD
=======
The `filters` option is crucial — it tells Chrome which types of devices to show in the selection dialog. You can filter by the services a device provides, by device name using the `namePrefix` filter, or by manufacturer data. Using specific filters improves the user experience by showing only relevant devices rather than every BLE device in range.

The `optionalServices` array is equally important. It specifies additional GATT services you might want to access but aren't required for the initial connection. Including services here avoids connection failures if you later try to access them.

## Understanding GATT Services and Characteristics

Bluetooth Low Energy devices organize their data using the Generic Attribute Profile (GATT) structure. At the top level, a device provides one or more **services**. Each service contains **characteristics**, which are the actual data containers. Characteristics can be read, written, or subscribed to for notifications.

Every service and characteristic is identified by a Universally Unique Identifier (UUID). The Bluetooth Special Interest Group (SIG) defines standard UUIDs for common device types — for example, the Battery Service has UUID `0x180F`, while the Heart Rate Service is `0x180D`. Manufacturers can also define custom UUIDs for proprietary services and characteristics.

To interact with a device's GATT features, you need to connect to its GATT server. Here's how to establish that connection:

```javascript
async function connectToGATT(device) {
  const server = await device.gatt.connect();
  console.log('Connected to GATT server');
  
  // Example: Read battery level
  const batteryService = await server.getPrimaryService('battery_service');
  const batteryLevel = await batteryService.getCharacteristic('battery_level');
  
  const value = await batteryLevel.readValue();
  const batteryPercent = value.getUint8(0);
  console.log('Battery level:', batteryPercent + '%');
  
  return server;
}
```

The `getPrimaryService()` method retrieves a service by its UUID, and `getCharacteristic()` does the same for a characteristic within that service. Once you have a reference to a characteristic, you can read its value, write to it, or subscribe to notifications.

## Reading and Writing Characteristics

Reading from a characteristic is straightforward using the `readValue()` method, which returns a DataView containing the raw bytes. You'll need to parse these bytes according to the characteristic's specification. Many standard Bluetooth characteristics follow specific data formats documented in the Bluetooth SIG specifications.

For example, the Heart Rate Measurement characteristic returns data in a specific format where the first byte contains flags, and subsequent bytes contain heart rate data. Parsing this requires understanding the bit flags:

```javascript
async function readHeartRate() {
  const device = await navigator.bluetooth.requestDevice({
    filters: [{ services: ['heart_rate'] }]
  });
  
  const server = await device.gatt.connect();
  const service = await server.getPrimaryService('heart_rate');
  const characteristic = await service.getCharacteristic('heart_rate_measurement');
  
  // Read the current value
  const value = await characteristic.readValue();
  const flags = value.getUint8(0);
  const heartRate = flags & 0x1 ? value.getUint16(1) : value.getUint8(1);
  
  console.log('Heart Rate:', heartRate, 'bpm');
}
```

Writing to characteristics works similarly, but you need to construct a proper ArrayBuffer or DataView with the data you want to send:

```javascript
async function writeToCharacteristic(serviceUUID, charUUID, data) {
  const device = await navigator.bluetooth.requestDevice({
    filters: [{ services: [serviceUUID] }]
  });
  
  const server = await device.gatt.connect();
  const service = await server.getPrimaryService(serviceUUID);
  const characteristic = await service.getCharacteristic(charUUID);
  
  // Convert string to ArrayBuffer
  const encoder = new TextEncoder();
  const dataBuffer = encoder.encode(data);
  
  await characteristic.writeValue(dataBuffer);
  console.log('Data written successfully');
}
```

Note that some characteristics are read-only, some are write-only, and some support both operations. The characteristic's properties determine what operations are allowed. Attempting to write to a read-only characteristic will result in an error.

## Subscribing to Notifications

Many Bluetooth devices work best when you subscribe to notifications rather than repeatedly polling for data. Notifications allow the device to push updates to your web app whenever the data changes, which is more efficient and provides real-time responsiveness.

To receive notifications, you need to start the notification service on a characteristic and add an event listener:

```javascript
async function subscribeToNotifications(characteristic) {
  await characteristic.startNotifications();
  
  characteristic.addEventListener('characteristicvaluechanged', (event) => {
    const value = event.target.value;
    // Parse the value based on the characteristic specification
    const data = parseMyData(value);
    console.log('Received update:', data);
  });
  
  console.log('Notifications enabled');
}
```

When you no longer need updates, you can stop notifications with `stopNotifications()`. It's good practice to stop notifications when you're done, especially if you're connecting to multiple devices or the page is being unloaded.

```javascript
async function unsubscribeFromNotifications(characteristic) {
  await characteristic.stopNotifications();
  characteristic.removeEventListener('characteristicvaluechanged', handler);
  console.log('Notifications disabled');
}
```

## Device Disconnection Handling

Properly handling disconnection is crucial for building robust Bluetooth web applications. Devices can disconnect for various reasons — the user might walk out of range, the device battery might die, or the user might manually disconnect through Chrome's settings.

The Web Bluetooth API provides the `gattserverdisconnected` event on the device object:

```javascript
function handleDisconnection(device) {
  device.addEventListener('gattserverdisconnected', (event) => {
    console.log('Device disconnected');
    
    // Attempt to reconnect if needed
    if (shouldReconnect) {
      reconnectToDevice(device);
    }
>>>>>>> consumer/a49-chrome-web-bluetooth-api-guide
=======
>>>>>>> consumer/a65-chrome-web-bluetooth-api-guide
  });
}
```

<<<<<<< HEAD
<<<<<<< HEAD
=======
>>>>>>> consumer/a65-chrome-web-bluetooth-api-guide
The notification event contains the new characteristic value, which you parse just like a read value. It's important to note that notifications can arrive rapidly depending on the device and what it's measuring. Your event handler should be efficient to avoid blocking the main thread.

When you no longer need notifications, always stop them to conserve resources:

```javascript
await characteristic.stopNotifications();
```

Indications are similar to notifications but require acknowledgment from the client. While less common, some devices use indications for critical data that must be reliably delivered. The API handles indications similarly to notifications, but you should be aware of the additional overhead.

## Security Best Practices

Security is paramount when building Bluetooth-enabled web applications. The Web Bluetooth API includes several built-in security features, but developers must also follow best practices to ensure user data remains protected.

Always use HTTPS. The Web Bluetooth API is only available in secure contexts, which means your site must be served over HTTPS (or from localhost during development). This requirement protects against man-in-the-middle attacks where an attacker could intercept communication between your application and the device.

Implement proper error handling for security-related scenarios:

```javascript
async function safeDeviceRequest() {
  try {
    const device = await navigator.bluetooth.requestDevice({
      filters: [{ services: ['heart_rate'] }]
    });
    return device;
  } catch (error) {
    if (error.name === 'NotFoundError') {
      console.log('No devices found matching criteria');
    } else if (error.name === 'SecurityError') {
      console.log('Connection blocked due to security policy');
    } else if (error.name === 'AbortError') {
      console.log('User cancelled the request');
<<<<<<< HEAD
=======
You can also check the connection state at any time using the `gatt.connected` property. This is useful for UI updates or before attempting operations that require an active connection.

## Security Considerations

Security is paramount when working with Bluetooth devices, especially those that handle sensitive data like health information. The Web Bluetooth API includes several security mechanisms to protect users.

First, as mentioned earlier, all Web Bluetooth operations require an HTTPS connection. This prevents man-in-the-middle attacks where an attacker might intercept data between your site and the device.

Second, users must explicitly grant permission for each device connection. Chrome's device chooser shows the device name and the services being requested, giving users informed consent. Users can revoke access at any time through Chrome's site settings.

Third, the API is restricted to top-level frames — you cannot use Web Bluetooth in iframes. This prevents malicious sites from embedding your Bluetooth-enabled site and intercepting data. If you need to use Web Bluetooth in a nested context, the top-level page must explicitly allow it.

For applications handling sensitive data, consider implementing additional security measures. Validate all data received from devices, as it could be malformed or intentionally manipulated. When transmitting sensitive information, ensure the device supports encrypted connections if possible.

## Practical Application: Tab Suspender Pro

One interesting real-world application of browser APIs and Bluetooth integration isTab Suspender Pro, a Chrome extension that helps manage browser resource usage. While Tab Suspender Pro primarily focuses on suspending inactive tabs to save memory and CPU, the concepts of efficient device communication and resource management are similar.

When building Bluetooth-enabled web applications, the lessons from tab management become valuable. Just as Tab Suspender Pro optimizes resource usage by selectively suspending tabs, your Bluetooth web app should manage its connections efficiently. Connect to devices only when needed, disconnect when idle, and use notifications instead of constant polling to minimize battery consumption on both the device and the user's computer.

Additionally, Tab Suspender Pro demonstrates good practices in handling browser state changes. If a user's computer goes to sleep or the tab becomes hidden, your Bluetooth application should gracefully handle the situation — either by maintaining the connection intelligently or by reconnecting when the tab becomes active again.

## Error Handling and Debugging

Working with Bluetooth introduces new categories of errors that you need to handle gracefully. Common errors include device not found, connection failed, service not found, characteristic not found, and operation not permitted.

Always wrap your Bluetooth operations in try-catch blocks and provide meaningful error messages to users:

```javascript
async function safeBluetoothOperation() {
  try {
    // Your Bluetooth code here
  } catch (error) {
    if (error.name === 'NotFoundError') {
      console.error('No device found. Make sure your device is powered on and in range.');
    } else if (error.name === 'SecurityError') {
      console.error('Permission denied. Check your site permissions in Chrome settings.');
    } else if (error.name === 'NetworkError') {
      console.error('Connection lost. Try reconnecting to the device.');
    } else {
      console.error('Bluetooth error:', error.message);
>>>>>>> consumer/a49-chrome-web-bluetooth-api-guide
=======
>>>>>>> consumer/a65-chrome-web-bluetooth-api-guide
    }
  }
}
```

<<<<<<< HEAD
<<<<<<< HEAD
=======
>>>>>>> consumer/a65-chrome-web-bluetooth-api-guide
Be mindful of the permissions you request. Only ask for the services and characteristics your application actually needs. Requesting unnecessary permissions can make users suspicious and may be flagged by security auditors. Chrome also enforces policies that limit which origins can use the Web Bluetooth API, so check your browser's enterprise policies if you encounter issues.

Handle device disconnection gracefully and consider implementing reconnection logic for applications that depend on continuous communication. However, avoid aggressive reconnection attempts that could drain the device's battery or cause user frustration.

## Real-World Application: Tab Suspender Pro Integration

One innovative application of Web Bluetooth is extending browser extensions with device-triggered actions. For example, Tab Suspender Pro, a popular Chrome extension that manages tab resources, could theoretically integrate with physical Bluetooth buttons or triggers to suspend or restore tabs based on external events.

Imagine a scenario where a user has a Bluetooth remote control paired with their computer. Using the Web Bluetooth API, Tab Suspender Pro could listen for specific button presses and automatically suspend inactive tabs when the user presses a "focus" button, or restore all suspended tabs when pressing "restore." This creates a seamless workflow where physical controls interact with browser functionality, demonstrating the practical potential of Web Bluetooth beyond traditional device data monitoring.

Such integrations open up possibilities for accessibility improvements, workflow automation, and novel user experiences that bridge the physical and digital worlds. As more devices become Bluetooth-enabled, the potential for creative applications continues to grow.

## Browser Compatibility and Limitations

While Chrome leads the way in Web Bluetooth support, browser compatibility remains a consideration. The Web Bluetooth API is available in Chrome 56+, Opera 43+, and Edge 79+. Firefox and Safari have not implemented the API as of this writing, though there are ongoing discussions about potential future support.

When building cross-browser applications, use feature detection:

```javascript
if ('bluetooth' in navigator) {
  // Web Bluetooth is available
  console.log('Web Bluetooth API is supported');
} else {
  // Provide fallback experience
  console.log('Web Bluetooth is not supported in this browser');
}
```

Some enterprise environments may block Web Bluetooth through Chrome Enterprise policies. If your application doesn't work in a corporate setting, check with the IT department about Bluetooth policies.

Be aware that the Web Bluetooth API has certain limitations compared to native Bluetooth applications. For example, you cannot connect to classic Bluetooth devices (BR/EDR), only BLE devices. The API also doesn't support broadcasting or acting as a peripheral, only connecting to existing peripherals.

## Conclusion

The Chrome Web Bluetooth API opens up tremendous possibilities for web developers to create innovative applications that interact with the physical world. From health monitoring apps communicating with fitness devices to industrial IoT dashboards connecting to sensors, the ability to access Bluetooth devices from the browser transforms what's possible on the web.
<<<<<<< HEAD
=======



## Related Articles
- [Chrome Web NFC API Guide](/chrome-web-nfc-api-guide)
- [Chrome Web Serial API Guide](/chrome-web-serial-api-guide)
- [Chrome Web USB API Guide](/chrome-web-usb-api-guide)

As browser support continues to expand and more devices become Bluetooth-enabled, now is the perfect time to explore what Web Bluetooth can do for your projects. Start with simple read operations, then progressively implement more complex features as you become comfortable with the API.
=======
For debugging, Chrome's built-in Bluetooth debugger is invaluable. Navigate to `chrome://bluetooth-internals` to see all discovered devices, active connections, GATT services, and characteristic values in real-time. This tool makes it much easier to understand what's happening at each step of the communication process.

## Best Practices for Production Applications

When deploying Web Bluetooth applications to production, keep these best practices in mind. First, always provide clear user instructions. Not all users are familiar with Bluetooth, so explain what they need to do, what permissions they're granting, and what to expect.

Second, implement fallback experiences for browsers that don't support Web Bluetooth. Show a friendly message explaining that the feature requires a supported browser, or offer alternative ways to achieve the same functionality.

Third, test with real devices extensively. Emulators can only go so far — real-world Bluetooth behavior can vary based on device firmware, interference, and other factors. Test with multiple devices from different manufacturers if possible.

Finally, stay up to date with the API. The Web Bluetooth specification continues to evolve, and browser implementations may change. Subscribe to the Chromium dev blog and W3C Web Bluetooth community group for updates.

## Conclusion

The Chrome Web Bluetooth API represents a significant advancement in web capabilities, enabling direct communication between web applications and Bluetooth Low Energy devices. By understanding device discovery, GATT services and characteristics, secure connection handling, and proper error management, you can build powerful applications that interact with the physical world through the browser.
>>>>>>> consumer/a49-chrome-web-bluetooth-api-guide

From health and fitness tracking to IoT dashboards and industrial applications, the possibilities are vast. As browser support expands and the specification matures, Web Bluetooth will become an increasingly important tool in every web developer's toolkit.

Remember to prioritize security, handle edge cases gracefully, and always put the user in control of their device connections. With these principles in place, you're well on your way to building excellent Bluetooth-enabled web experiences.

## Related Articles
- [Chrome Fetch API Complete Guide](/chrome-fetch-api-complete-guide)
- [Chrome Vibration API: A Complete Guide for Mobile Web Developers](/chrome-vibration-api-mobile-web)
- [Chrome Topics API Guide](/chrome-topics-api-guide)
