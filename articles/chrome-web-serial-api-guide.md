---
layout: post
title: "Chrome Web Serial API Guide"
<<<<<<< HEAD
description: "Learn how to use the Chrome Web Serial API for serial port communication with Arduino, microcontrollers, and external devices. Complete guide covering baudrate settings, port access, and practical examples."
date: 2026-01-20
categories: [development, hardware, chrome]
tags: [chrome-web-serial-api, serial-port, arduino, microcontroller, baudrate, chrome-extensions, web-development]
=======
description: "Learn how to use the Chrome Web Serial API to connect your browser to Arduino, microcontrollers, and serial devices. Complete guide covering port access, baudrate settings, and practical examples."
date: 2026-01-15
categories: [development, hardware, chrome-api]
tags: [chrome-web-serial-api, arduino, microcontroller, serial-port, browser-hardware]
>>>>>>> consumer/a42-chrome-web-serial-api-guide
author: theluckystrike
---

# Chrome Web Serial API Guide

<<<<<<< HEAD
The **Chrome Web Serial API** represents a groundbreaking advancement in web development, enabling web applications to communicate directly with serial devices such as **Arduino** boards, microcontrollers, and other hardware connected via USB or serial ports. This capability opens up incredible possibilities for developers, makers, and hobbyists who want to create web-based interfaces for hardware projects without requiring native applications or browser extensions.

In this comprehensive guide, we'll explore everything you need to know about the Chrome Web Serial API, from basic concepts to practical implementation examples. Whether you're building a home automation system, a robotics controller, or simply want to read data from sensors connected to an Arduino, this guide will walk you through the entire process.

## What is the Chrome Web Serial API?

The **Chrome Web Serial API** is a JavaScript API that allows web pages to communicate with serial devices connected to a user's computer. Part of the Web Serial API standard, it provides a way for websites to send and receive data through a serial port, just like desktop applications have been able to do for decades.

This API bridges the gap between web applications and physical hardware, enabling scenarios that were previously impossible in the browser. Before its introduction, developers had to rely on native applications, browser extensions, or workarounds to connect web apps to hardware devices. Now, with just a few lines of JavaScript, you can establish direct communication with serial devices.

The API works by providing a way to request access to serial ports, open connections, read data from them, and write data to them. It handles the low-level details of serial communication, including **baudrate settings**, data bits, stop bits, and parity, allowing developers to focus on their application logic.
=======
The **Chrome Web Serial API** represents a groundbreaking advancement in web development, enabling web browsers to communicate directly with serial devices like Arduino boards, microcontrollers, and other hardware. This capability opens up incredible possibilities for developers, hobbyists, and educators who want to create web-based interfaces for physical computing projects. In this comprehensive guide, we'll explore everything you need to know about the Web Serial API, from basic concepts to practical implementation.

## Understanding the Web Serial API

The Web Serial API is a JavaScript API that allows web pages to read from and write to serial devices connected to a user's computer via USB or Bluetooth. Unlike traditional serial communication that required specialized desktop applications, this API brings hardware connectivity directly into the browser, making it easier than ever to build interactive web applications that interface with physical devices.

Before the Web Serial API, developers had to rely on browser extensions or native applications to establish serial communication. This created friction for users who needed to install additional software and for developers who had to maintain separate codebases. The Web Serial API solves these problems by providing a standardized way to communicate with serial devices directly from web applications.

The API works by leveraging the Serial interface in JavaScript, which provides methods for detecting available ports, opening and closing connections, reading data, and writing data. When a web page needs to communicate with a serial device, it first requests access to the port, and the browser presents a user prompt asking permission to connect to the device. This security feature ensures that users have explicit control over which devices can access their hardware.
>>>>>>> consumer/a42-chrome-web-serial-api-guide

## Browser Support and Requirements

<<<<<<< HEAD
As of early 2026, the **Chrome Web Serial API** is available in Chrome, Edge, and other Chromium-based browsers. Firefox and Safari have not yet implemented this feature, so if you need cross-browser support, you'll need to provide fallback solutions or rely on browser-specific implementations.

To use the API, your website must be served over a secure context (HTTPS) or from localhost. This security requirement ensures that malicious websites cannot arbitrarily access serial ports without user permission. When your page attempts to access a serial port, the browser will prompt the user to select which port to use and confirm their intention to allow the connection.

One important consideration is that the API requires a user gesture to initiate the port request. This means you cannot automatically connect to a serial port when a page loads; instead, the user must click a button or perform some other explicit action to trigger the connection process.

## Understanding Serial Communication Basics

Before diving into the API itself, it's helpful to understand some fundamental concepts about serial communication. **Serial communication** is a method of transmitting data one bit at a time over a communication channel or computer bus. It's been a standard method for connecting computers to peripherals for decades.

When working with **Arduino** and microcontrollers, you'll typically use UART (Universal Asynchronous Receiver/Transmitter) communication. This asynchronous serial communication doesn't require a shared clock between the transmitting and receiving devices; instead, they agree on a communication speed beforehand.

The **baudrate** is a crucial setting that determines how fast data is transmitted over the serial connection. Common baudrate values include 9600, 19200, 38400, 57600, and 115200 bits per second. The Arduino IDE defaults to 9600 baud, which is a good starting point for most projects. Higher baudrates allow for faster data transfer but may introduce errors if the connecting wires are too long or the devices aren't properly grounded.

Other important serial parameters include:
- **Data bits**: Typically 8 data bits per frame
- **Stop bits**: Usually 1 or 2 stop bits
- **Parity**: Can be none, odd, or even
- **Flow control**: Usually disabled for simple Arduino projects

For most Arduino projects, the default settings of 8 data bits, no parity, and 1 stop bit (often abbreviated as "8N1") work perfectly fine.

## Requesting Serial Port Access

The first step in using the Chrome Web Serial API is to request access to a serial port. This is done using the `navigator.serial.requestPort()` method, which returns a Promise that resolves to a `SerialPort` object representing the selected port.

Here's a basic example of how to request port access:

```javascript
async function connectToSerialPort() {
  try {
    const port = await navigator.serial.requestPort();
    console.log('Port selected:', port.getInfo());
    return port;
  } catch (error) {
    console.error('Error requesting port:', error);
  }
}
```

When this code executes, Chrome will display a dialog showing available serial ports. The user can select which port to use and then confirm their choice. If the user cancels the dialog, the Promise will be rejected, so you'll need to handle that case gracefully.

You can also filter the available ports based on their properties. For example, if you want to only show ports with a specific USB vendor ID (useful if you have multiple devices connected), you can pass filters to the `requestPort()` method:

```javascript
const port = await navigator.serial.requestPort({
  filters: [
    { usbVendorId: 0x2341 } // Arduino vendor ID
  ]
});
```

This is particularly useful in production applications where you know exactly what type of device you're connecting to.

## Opening and Configuring the Connection

Once you have a `SerialPort` object, you need to open it before you can send or receive data. The `open()` method accepts a configuration object where you can specify the **baudrate** and other serial parameters:

```javascript
async function openConnection(port, baudRate = 9600) {
  try {
    await port.open({
      baudRate: baudRate,
      dataBits: 8,
      stopBits: 1,
      parity: 'none',
      bufferSize: 1024 // Buffer size for reading/writing
    });
    console.log('Port opened successfully');
  } catch (error) {
    console.error('Error opening port:', error);
  }
}
```

The **baudRate** parameter is the most important setting here. It must match the baudrate configured on your Arduino or microcontroller, otherwise, you'll receive garbled data or no data at all. If you're using the Arduino `Serial.begin(9600)` function, use `baudRate: 9600`. For faster communication, you might use `Serial.begin(115200)` and set `baudRate: 115200` in your JavaScript.

It's worth noting that some older devices may not support certain baudrates, and the actual baudrate might be rounded to the nearest supported value. Most modern devices and the Chrome API handle this gracefully, but it's something to be aware of if you're working with legacy hardware.

## Reading Data from Serial Ports

After opening the connection, you can start reading data from the port. The Chrome Web Serial API uses streams for reading data, which provides a modern and efficient way to handle incoming data. You'll use a `ReadableStream` to read data from the serial port:

```javascript
async function readFromPort(port) {
  const decoder = new TextDecoderStream();
  const readableStream = port.readable.pipeThrough(decoder);
  
  const reader = readableStream.getReader();
  
  try {
    while (true) {
      const { value, done } = await reader.read();
      
      if (done) {
        // The stream has been cancelled
        break;
      }
      
      if (value) {
        console.log('Received:', value);
        // Process your data here
      }
    }
  } catch (error) {
    console.error('Error reading from port:', error);
  } finally {
    reader.releaseLock();
  }
}
```

This code sets up a continuous reading loop that processes data as it arrives. The `TextDecoderStream` converts the raw bytes received from the serial port into JavaScript strings, which is typically what you want when communicating with Arduino or microcontroller projects that send text data.

In your Arduino sketch, you would send data using `Serial.println()` or similar functions:

```cpp
void setup() {
  Serial.begin(9600);
}

void loop() {
  Serial.println("Hello from Arduino!");
  delay(1000);
}
```

When the Arduino sends "Hello from Arduino!\r\n", your JavaScript code will receive "Hello from Arduino!" as the `value`.

## Writing Data to Serial Ports

Sending data to your serial device is equally straightforward. You'll use a `WritableStream` to write data to the port:

```javascript
async function writeToPort(port, data) {
  const encoder = new TextEncoderStream();
  const writableStream = encoder.writable;
  const writer = writableStream.getWriter();
  
  try {
    await writer.write(data);
    console.log('Data sent:', data);
  } catch (error) {
    console.error('Error writing to port:', error);
  } finally {
    writer.releaseLock();
  }
}
```

Combined with reading, this allows for bidirectional communication. For example, you could send commands from your web interface to control an Arduino:

```javascript
// Send command to turn on LED
await writeToPort(port, "LED_ON\n");

// Send command to turn off LED  
await writeToPort(port, "LED_OFF\n");
```

On the Arduino side, you would parse these commands:
=======
As of now, the Web Serial API is available in Chrome, Edge, and other Chromium-based browsers. Firefox and Safari have not yet implemented this API, so if you need to support those browsers, you'll need to provide fallback solutions or encourage users to use a compatible browser.

To use the Web Serial API, your web page must be served over a secure context (HTTPS) or from localhost. This requirement exists because serial communication can access sensitive hardware, and secure contexts help protect users from malicious websites attempting to access their devices without proper authorization.

Additionally, the user must explicitly grant permission for your website to access serial ports. This is an important security measure that prevents unauthorized access to connected devices. The browser will display a dialog asking the user to select which port they want to connect to, and the user must choose the correct device from the list of available ports.

## Connecting to Arduino and Microcontrollers

One of the most exciting applications of the Web Serial API is connecting to **Arduino** boards and other microcontrollers. These devices are incredibly popular among hobbyists and educators because they provide an accessible way to create interactive electronics projects. With the Web Serial API, you can create web-based dashboards, control panels, and monitoring interfaces for your Arduino projects.

To connect your Arduino to a web browser, you'll need to first upload a sketch (program) to the Arduino that communicates over serial. The standard Arduino IDE includes built-in serial communication capabilities, making it easy to send and receive data. Here's a simple Arduino sketch that echoes back any data it receives:
>>>>>>> consumer/a42-chrome-web-serial-api-guide

```cpp
void setup() {
  Serial.begin(9600);
}

void loop() {
<<<<<<< HEAD
  if (Serial.available() > 0) {
    String command = Serial.readStringUntil('\n');
    
    if (command == "LED_ON") {
      digitalWrite(LED_BUILTIN, HIGH);
      Serial.println("LED turned on");
    } else if (command == "LED_OFF") {
      digitalWrite(LED_BUILTIN, LOW);
      Serial.println("LED turned off");
    }
=======
  if (Serial.available()) {
    char incomingByte = Serial.read();
    Serial.write(incomingByte);
>>>>>>> consumer/a42-chrome-web-serial-api-guide
  }
}
```

<<<<<<< HEAD
This creates a simple but powerful communication protocol between your web application and hardware.

## Handling Connection State and Errors

Proper error handling is crucial when working with serial ports, as connections can fail for various reasons: the device might be unplugged, the port might become unavailable, or communication errors might occur. Your application should handle these situations gracefully.

The `SerialPort` object emits events that you can listen to:

```javascript
port.addEventListener('disconnect', (event) => {
  console.log('Port disconnected:', event.target);
  // Handle disconnection - maybe show a notification to the user
});

port.addEventListener('connect', (event) => {
  console.log('Port connected:', event.target);
  // Optionally auto-reconnect or prompt the user
});
```

It's also important to properly close the connection when your application no longer needs it:

```javascript
async function closeConnection(port) {
  try {
    await port.close();
    console.log('Port closed successfully');
=======
This sketch initializes serial communication at a baud rate of 9600 and echoes back any bytes received. The baud rate is crucial for proper communication, and both your Arduino and web application must use the same value. We'll discuss baud rate configuration in detail later in this guide.

On the web side, you can use the Web Serial API to connect to your Arduino and start sending commands. The connection process involves requesting a port, opening the connection with the appropriate parameters, and then reading from or writing to the serial stream. Here's a basic example:

```javascript
async function connectToArduino() {
  const port = await navigator.serial.requestPort();
  await port.open({ baudRate: 9600 });
  
  const reader = port.readable.getReader();
  
  while (true) {
    const { value, done } = await reader.read();
    if (done) break;
    console.log(new TextDecoder().decode(value));
  }
}
```

This code requests access to a serial port, opens it at 9600 baud, and continuously reads data from the Arduino. The received bytes are decoded as text and logged to the console.

## Understanding Baud Rate Settings

**Baudrate** is one of the most critical settings when working with serial communication. It refers to the number of signal changes or symbols transmitted per second and determines how fast data travels between your computer and the connected device. Choosing the correct baud rate is essential for reliable communication.

Common baud rates include 9600, 19200, 38400, 57600, and 115200. The Arduino default baud rate of 9600 is popular because it works well for most basic projects and is less prone to transmission errors at longer cable distances. Higher baud rates like 115200 allow for faster data transfer but require shorter cables and may be more susceptible to interference.

When configuring your web application to connect to a serial device, you must match the baud rate setting on your device. If the baud rates don't match, you'll receive garbled or incorrect data. The Web Serial API allows you to specify the baud rate when opening the port:

```javascript
await port.open({ baudRate: 115200 });
```

Some devices also support other serial parameters like data bits, stop bits, and parity. The Web Serial API defaults to 8 data bits, 1 stop bit, and no parity (often written as "8N1"), which is the most common configuration. Most Arduino boards use these defaults, so you typically don't need to specify additional parameters.

It's worth noting that some microcontrollers can automatically detect or negotiate baud rates, but this is not universal. When in doubt, check your device's documentation for the recommended baud rate and serial configuration.

## Reading and Writing Data

Once you've established a connection to your serial device, you can start exchanging data. The Web Serial API provides streams for reading and writing, which makes it compatible with JavaScript's stream APIs and allows for efficient, non-blocking communication.

Reading data from a serial device typically involves creating a reader from the port's readable stream and then reading chunks of data in a loop. Data often comes in as an ArrayBuffer, which you can convert to different formats depending on your needs:

```javascript
const reader = port.readable.getReader();

async function readData() {
  try {
    while (true) {
      const { value, done } = await reader.read();
      if (done) break;
      
      // Convert to string
      const text = new TextDecoder().decode(value);
      console.log('Received:', text);
      
      // Or work with raw bytes
      const bytes = new Uint8Array(value);
      console.log('Bytes:', bytes);
    }
>>>>>>> consumer/a42-chrome-web-serial-api-guide
  } catch (error) {
    console.error('Error closing port:', error);
  }
}
<<<<<<< HEAD
```

When closing a port that has active readers or writers, you should first cancel them:

```javascript
await reader.cancel();
await writer.close();
await port.close();
```

## Practical Example: Arduino Temperature Monitor

Let's put everything together with a practical example. Imagine you have an Arduino with a temperature sensor, and you want to display the readings in a web page. Here's how you might implement this.

First, the Arduino sketch reads the temperature and sends it over serial:

```cpp
int sensorPin = A0;

void setup() {
  Serial.begin(9600);
}

void loop() {
  int reading = analogRead(sensorPin);
  float voltage = reading * 5.0 / 1024.0;
  float temperature = (voltage - 0.5) * 100;
  
  Serial.println(temperature);
  delay(1000);
}
```

Then, the web application reads these values and displays them:

```html
<!DOCTYPE html>
<html>
<head>
  <title>Temperature Monitor</title>
  <style>
    body { font-family: sans-serif; padding: 20px; }
    #temperature { font-size: 48px; color: #e74c3c; }
    #status { color: #7f8c8d; }
  </style>
</head>
<body>
  <h1>Temperature Monitor</h1>
  <p>Current temperature: <span id="temperature">--</span>°C</p>
  <p>Status: <span id="status">Click Connect to start</span></p>
  <button id="connectBtn">Connect to Arduino</button>
  
  <script>
    let port;
    
    document.getElementById('connectBtn').addEventListener('click', async () => {
      port = await navigator.serial.requestPort();
      await port.open({ baudRate: 9600 });
      
      document.getElementById('status').textContent = 'Connected';
      document.getElementById('connectBtn').disabled = true;
      
      const decoder = new TextDecoderStream();
      const readableStream = port.readable.pipeThrough(decoder);
      const reader = readableStream.getReader();
      
      while (true) {
        const { value, done } = await reader.read();
        if (done) break;
        if (value) {
          const temp = parseFloat(value.trim());
          if (!isNaN(temp)) {
            document.getElementById('temperature').textContent = temp.toFixed(1);
          }
        }
      }
    });
  </script>
</body>
</html>
```

This example demonstrates how a few lines of JavaScript can create a real-time hardware interface.

## Performance Considerations and Best Practices

When building applications with the Chrome Web Serial API, there are several best practices to keep in mind for optimal performance and reliability.

**Buffer management** is important for high-throughput applications. The `bufferSize` option in `port.open()` controls the size of the internal buffer. Larger buffers can handle bursts of data more effectively but use more memory. For most projects, the default or a modest buffer size works well.

If you're building something like **Tab Suspender Pro** that manages background tabs or handles multiple connections, you might want to consider the impact of serial connections on system resources. Active serial connections can consume power and system resources, so it's good practice to close connections when they're not actively needed.

**Error recovery** is another important consideration. Serial connections can fail unexpectedly, and your application should be prepared to handle reconnection gracefully. Implementing automatic reconnection with exponential backoff can make your application more robust.

```javascript
async function connectWithRetry(port, maxRetries = 3) {
  for (let i = 0; i < maxRetries; i++) {
    try {
      await port.open({ baudRate: 9600 });
      return true;
    } catch (error) {
      console.log(`Connection attempt ${i + 1} failed, retrying...`);
      await new Promise(resolve => setTimeout(resolve, 1000 * (i + 1)));
    }
  }
  return false;
}
```

## Security Considerations

While the Chrome Web Serial API includes built-in security measures, there are still best practices you should follow. Always use secure contexts (HTTPS) when deploying applications that use this API. Be thoughtful about what data you transmit over serial connections, especially if it includes sensitive information.

When connecting to devices like Arduino or microcontrollers, ensure that your device firmware validates incoming commands to prevent unauthorized actions. Even though the browser limits which ports your web page can access, any software running on the user's computer could theoretically connect to the serial port directly.

## Conclusion

The Chrome Web Serial API transforms what's possible in web development, enabling direct communication between web applications and hardware devices like **Arduino** boards and **microcontrollers**. By understanding how to manage serial port access, configure **baudrate settings**, and implement bidirectional communication, you can build powerful web-based interfaces for hardware projects.

From simple temperature monitors to complex robotics controllers, the possibilities are virtually endless. The key is starting with a solid understanding of the API fundamentals and then building up to more advanced implementations as needed.

As browser support continues to improve and more developers discover the potential of this API, we'll likely see an explosion of innovative web-hardware hybrid applications. Whether you're a maker building your next project or a developer creating commercial hardware interfaces, the Chrome Web Serial API provides the tools you need to bring your ideas to life.
=======
```

Writing data is similarly straightforward. You create a writer from the port's writable stream and then write your data:

```javascript
const writer = port.writable.getWriter();

async function sendCommand(command) {
  const encoder = new TextEncoder();
  const data = encoder.encode(command + '\n');
  await writer.write(data);
}

// Send commands to Arduino
await sendCommand('LED_ON');
await sendCommand('GET_TEMPERATURE');
```

The ability to send commands and receive responses enables you to build interactive control panels for your hardware projects. You can create web interfaces with buttons, sliders, and other controls that send specific commands to your microcontroller, which then executes the corresponding actions.

## Practical Applications and Use Cases

The Web Serial API enables a wide range of practical applications. One of the most common use cases is building custom dashboards for monitoring sensor data. For example, you could connect a temperature and humidity sensor to an Arduino and create a web page that displays real-time readings, charts, and historical data.

Another popular application is controlling actuators and motors from a web interface. Whether you're building a robot, a home automation system, or an art installation, you can use the Web Serial API to send commands from your web page to control servos, relays, LEDs, and other actuators.

Educational tools represent another exciting application. Teachers and educators can use the Web Serial API to create interactive lessons that combine physical computing with web development. Students can build hardware projects and then create web interfaces to control and monitor them, learning valuable skills in both domains.

Some developers have even used the Web Serial API to connect vintage computers and gaming consoles to modern web applications, creating emulators and interfaces for retro hardware. The possibilities are limited only by your imagination.

## Error Handling and Best Practices

Robust error handling is essential when working with serial communication, as many things can go wrong: the device might be disconnected, permissions might be revoked, or data transmission might encounter errors.

Always wrap your serial communication code in try-catch blocks and handle errors gracefully. When errors occur, provide clear feedback to users so they know what happened and what they can do to resolve it. For example, if the connection is lost, you might display a message asking the user to reconnect the device.

It's also important to properly close serial connections when they're no longer needed. Failing to close ports can leave resources tied up and prevent other applications from accessing the device. Always use try-finally blocks or similar patterns to ensure connections are properly closed:

```javascript
async function communicateWithDevice() {
  const port = await navigator.serial.requestPort();
  
  try {
    await port.open({ baudRate: 9600 });
    // Perform communication
  } finally {
    await port.close();
  }
}
```

Another best practice is to implement reconnection logic for scenarios where the device is accidentally disconnected or the browser tab is refreshed. Store the necessary port information and provide a way for users to reconnect without having to re-select the device every time.

## Performance Considerations

When building applications that exchange data frequently with serial devices, performance becomes an important consideration. The Web Serial API uses streams, which allow for efficient, chunk-based data transfer, but you should still be mindful of how you process incoming data.

If you're receiving high-frequency data from your device, consider buffering data before processing it rather than reacting to every single chunk. This can reduce overhead and improve overall performance. Similarly, when sending commands, batch multiple commands together if possible rather than sending them individually.

For applications that require very low latency, you might need to experiment with different baud rates and buffer sizes to find the optimal configuration. Higher baud rates reduce transmission time but may introduce other challenges.

## Browser Extensions and Tab Management

When developing and testing Web Serial API applications, you may find yourself keeping multiple tabs open for debugging, monitoring serial output, and testing your interface. This can consume significant system resources, especially if your serial communication is running continuously.

If you notice your browser becoming sluggish or your serial connection experiencing issues due to system resource constraints, consider using extension management tools to help. **Tab Suspender Pro** is a Chrome extension that automatically suspends tabs you aren't actively using, which can free up memory and CPU resources. This can be particularly helpful when developing serial communication applications that may be running in multiple tabs simultaneously.

Using thoughtful tab management combined with proper resource handling in your application can help ensure smooth, reliable serial communication without impacting your overall browser performance.

## Security Considerations

While the Web Serial API provides powerful capabilities, it's important to understand and implement appropriate security measures. Always serve your applications over HTTPS to protect against man-in-the-middle attacks that could intercept communication with your devices.

Be cautious about the commands your web application sends to connected devices. Since users can modify JavaScript running in their browser, malicious users could potentially send unexpected commands to your hardware. Implement validation and sanity checking on your microcontroller to reject invalid or dangerous commands.

Additionally, be mindful of what data your application logs and stores. Serial communication may contain sensitive information, and you should handle that data appropriately.

## Conclusion

The Chrome Web Serial API represents a significant step forward in bringing hardware connectivity to the web. By enabling direct communication between browsers and serial devices, it opens up endless possibilities for creating interactive hardware projects, educational tools, and industrial applications.

Throughout this guide, we've covered the fundamentals of the Web Serial API, including how to connect to Arduino and microcontrollers, configure baud rate settings, read and write data, and implement best practices for error handling and security. With this knowledge, you're well-equipped to start building your own web-based hardware projects.
>>>>>>> consumer/a42-chrome-web-serial-api-guide

Whether you're a hobbyist experimenting with Arduino, an educator teaching physical computing, or a developer building industrial control systems, the Web Serial API provides a powerful and accessible way to connect your web applications to the physical world. Start experimenting today and see what you can create!

Built by theluckystrike — More tips at [zovo.one](https://zovo.one)
