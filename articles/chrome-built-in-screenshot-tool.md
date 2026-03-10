---
layout: post
title: "Chrome Built-In Screenshot Tool"
description: "Learn how to use Chrome's built-in screenshot capabilities including full page capture, area selection, node screenshot, and DevTools capture for efficient screen capturing."
date: 2026-01-15
categories: [tutorials, chrome, productivity]
tags: [chrome-screenshot, browser-tools, devtools, screen-capture, productivity]
author: theluckystrike
---

# Chrome Built-In Screenshot Tool

When you need to capture a screenshot in Chrome, you might immediately think of third-party extensions or external screenshot tools. However, Google Chrome comes equipped with powerful built-in screenshot capabilities that many users are unaware of. These native features can handle most screenshot needs without requiring additional software, making your workflow more efficient and secure. Whether you need to capture an entire webpage, select a specific region, capture a particular element, or use advanced DevTools features, Chrome has you covered.

In this comprehensive guide, we will explore all the built-in screenshot options available in Chrome, from the simplest methods to more advanced techniques using the Developer Tools. By the end, you will have a complete understanding of how to capture exactly what you need, exactly when you need it.

## Understanding Chrome's Native Screenshot Capabilities

Chrome's built-in screenshot functionality has evolved significantly over the years. While the browser does not have a dedicated "screenshot button" like some mobile devices, it provides multiple ways to capture your screen content through keyboard shortcuts and developer tools. These methods are particularly useful for web developers, designers, content creators, and anyone who needs to quickly capture browser-based content.

The main advantages of using Chrome's built-in screenshot tools include no need for external extensions (reducing security risks and browser overhead), instant availability without installation, high-quality captures that preserve page fidelity, and support for advanced capture modes that extensions often struggle with.

## Full Page Capture: Capturing Entire Webpages

One of the most common screenshot needs is capturing an entire webpage that extends beyond the visible viewport. Chrome provides a straightforward way to accomplish this through its Developer Tools.

### Using the Command Menu Method

The fastest way to capture a full page screenshot is through Chrome's Command Menu. Here's how to do it:

First, open the webpage you want to capture. Next, open Developer Tools by pressing F12, or right-click anywhere on the page and select "Inspect." Once the DevTools panel is open, press Ctrl+Shift+P (or Cmd+Shift+P on Mac) to open the Command Menu.

In the Command Menu, type "screenshot" to filter the available commands. You will see options including "Capture full size screenshot" and "Capture screenshot." Select "Capture full size screenshot" and press Enter.

Chrome will instantly capture the entire webpage, including all content that scrolls below the fold, and save it to your Downloads folder as a PNG file. This method preserves the full length of the page exactly as it appears when fully rendered.

### Why Full Page Screenshots Are Useful

Full page screenshots are invaluable in many situations. Web developers use them to document bug reports and show clients how pages appear. Content creators capture entire articles for offline reading or reference. Researchers gather information from multiple pages without needing to visit them repeatedly. And business professionals use full page captures for archiving important web content.

The quality of these captures is excellent because Chrome renders the page fully before capturing, ensuring that all images, fonts, and styling are correctly included. This is particularly important for capturing dynamically loaded content that might appear as you scroll.

## Area Selection: Capturing Specific Regions

Sometimes you do not need an entire webpage—just a specific section or element. While Chrome does not have a built-in point-and-click region selector in the traditional sense, there are several approaches you can use.

### Using the Capture Screenshot Command
<<<<<<< HEAD
=======

Similar to the full page capture, you can use the Command Menu to capture a viewport screenshot. This captures only what is currently visible in your browser window, without scrolling. This is useful for capturing specific sections of a page that fit within your viewport.

To use this method, open Developer Tools, press Ctrl+Shift+P to open the Command Menu, type "screenshot," and select "Capture screenshot." The image will be saved to your Downloads folder.

### Third-Party Solutions for Region Selection

While Chrome's native tools do not include a freeform region selector, if you need this functionality regularly, you might consider using a lightweight extension specifically designed for area selection. However, for basic needs, the viewport capture method combined with cropping in any image editor provides similar results.

One practical tip is to adjust your browser window size to frame exactly the content you want to capture, then use the viewport screenshot command. This gives you precise control over what gets captured without needing additional tools.
>>>>>>> consumer/a51-chrome-built-in-screenshot-tool

Similar to the full page capture, you can use the Command Menu to capture a viewport screenshot. This captures only what is currently visible in your browser window, without scrolling. This is useful for capturing specific sections of a page that fit within your viewport.

<<<<<<< HEAD
To use this method, open Developer Tools, press Ctrl+Shift+P to open the Command Menu, type "screenshot," and select "Capture screenshot." The image will be saved to your Downloads folder.

### Third-Party Solutions for Region Selection

While Chrome's native tools do not include a freeform region selector, if you need this functionality regularly, you might consider using a lightweight extension specifically designed for area selection. However, for basic needs, the viewport capture method combined with cropping in any image editor provides similar results.

One practical tip is to adjust your browser window size to frame exactly the content you want to capture, then use the viewport screenshot command. This gives you precise control over what gets captured without needing additional tools.

## Node Screenshot: Capturing Individual Elements

Chrome's Developer Tools offer a powerful feature that allows you to capture screenshots of specific elements on a webpage. This is incredibly useful for designers and developers who need to isolate particular components.

### How to Capture a Node Screenshot

To capture a specific element, first open Developer Tools and switch to the Elements panel. You can do this by pressing F12 and clicking the Elements tab, or by pressing Ctrl+Shift+I (Cmd+Shift+I on Mac) and selecting Elements.

Navigate through the DOM tree to find the element you want to capture, or use the select tool (the arrow icon in the top-left of the DevTools panel) to click on any element in the page. When you have selected the desired element, right-click on it in the Elements panel and select "Capture node screenshot."

Chrome will immediately save an image of just that specific element to your Downloads folder. This is particularly useful for capturing buttons, cards, navigation elements, or any other component in isolation.

### Practical Applications for Node Screenshots

Node screenshots are invaluable for creating design documentation, building component libraries, reporting UI bugs, and sharing specific UI elements with team members. Instead of cropping a full page screenshot, you can capture exactly what you need with a single click.

This feature also helps when you need to compare elements across different pages or when documenting the structure of a particularly complex webpage component.

## DevTools Capture: Advanced Screenshot Techniques

Beyond the basic screenshot commands, Chrome's Developer Tools offer several advanced capture options that give you even more control over your screenshots.

### Accessing More Capture Options

In the Command Menu (Ctrl+Shift+P or Cmd+Shift+P), you can explore all available screenshot options by typing "capture." You will find options such as:

- **Capture full size screenshot**: Captures the entire scrollable area of the page
- **Capture screenshot**: Captures only the visible viewport
- **Capture node screenshot**: Captures the currently selected DOM node
- **Capture media screenshot**: Specifically for capturing video frames or canvas elements

Each of these serves different purposes, and understanding when to use each one will make you much more efficient at capturing web content.

### Using the Layers Panel for Complex Captures

For more advanced users, the Layers panel in DevTools can help you capture complex page elements that might be difficult to isolate otherwise. By understanding the layered structure of a webpage, you can better select and capture specific components.

### Taking Screenshots Without DevTools Visible
=======
Chrome's Developer Tools offer a powerful feature that allows you to capture screenshots of specific elements on a webpage. This is incredibly useful for designers and developers who need to isolate particular components.

### How to Capture a Node Screenshot

To capture a specific element, first open Developer Tools and switch to the Elements panel. You can do this by pressing F12 and clicking the Elements tab, or by pressing Ctrl+Shift+I (Cmd+Shift+I on Mac) and selecting Elements.

Navigate through the DOM tree to find the element you want to capture, or use the select tool (the arrow icon in the top-left of the DevTools panel) to click on any element in the page. When you have selected the desired element, right-click on it in the Elements panel and select "Capture node screenshot."

Chrome will immediately save an image of just that specific element to your Downloads folder. This is particularly useful for capturing buttons, cards, navigation elements, or any other component in isolation.

### Practical Applications for Node Screenshots

Node screenshots are invaluable for creating design documentation, building component libraries, reporting UI bugs, and sharing specific UI elements with team members. Instead of cropping a full page screenshot, you can capture exactly what you need with a single click.

This feature also helps when you need to compare elements across different pages or when documenting the structure of a particularly complex webpage component.

## DevTools Capture: Advanced Screenshot Techniques

Beyond the basic screenshot commands, Chrome's Developer Tools offer several advanced capture options that give you even more control over your screenshots.

### Accessing More Capture Options

In the Command Menu (Ctrl+Shift+P or Cmd+Shift+P), you can explore all available screenshot options by typing "capture." You will find options such as:

- **Capture full size screenshot**: Captures the entire scrollable area of the page
- **Capture screenshot**: Captures only the visible viewport
- **Capture node screenshot**: Captures the currently selected DOM node
- **Capture media screenshot**: Specifically for capturing video frames or canvas elements

Each of these serves different purposes, and understanding when to use each one will make you much more efficient at capturing web content.

### Using the Layers Panel for Complex Captures

For more advanced users, the Layers panel in DevTools can help you capture complex page elements that might be difficult to isolate otherwise. By understanding the layered structure of a webpage, you can better select and capture specific components.

### Taking Screenshots Without DevTools Visible

When you capture screenshots using the methods above, Chrome automatically hides the DevTools interface from the final image. This means your screenshots look clean and professional, without any debugging panels visible. This is particularly important when capturing content for presentations, documentation, or client deliverables.

## Performance Considerations and Best Practices

While Chrome's built-in screenshot tools are powerful, there are some best practices to keep in mind for optimal results.

### Page Loading and Dynamic Content

For full page screenshots, ensure the page is fully loaded before capturing. If the page has lazy-loaded images or infinite scroll content, you may need to scroll through the entire page first to ensure everything is rendered. Some pages may require waiting for animations to complete or for JavaScript to finish executing.

### High Resolution Displays

On high DPI (Retina) displays, Chrome's screenshots are captured at the device pixel ratio, resulting in higher resolution images. This is generally beneficial as it provides crisp, detailed screenshots, but be aware that these images will be larger in file size.

### File Management

By default, Chrome saves screenshots to your Downloads folder with filenames like "screenshot.png" or "fullpage.png." If you capture multiple screenshots, Chrome will add timestamps to prevent overwriting. For better organization, consider moving screenshots to dedicated folders immediately after capture.

## Combining with Other Tools for Enhanced Workflow

While Chrome's built-in tools are powerful, they work even better when combined with other productivity strategies. For instance, if you find yourself taking many screenshots throughout the day, your browser may have numerous tabs open, which can impact performance.

**Tab Suspender Pro** is a Chrome extension that can help manage your open tabs more efficiently. By automatically suspending tabs you are not actively using, it reduces memory usage and can make your browser feel snappier. This is particularly useful when you are working on projects that require frequent screenshotting and need to keep reference pages open without bogging down your system.

Using a combination of Chrome's built-in screenshot tools and thoughtful tab management creates a more efficient workflow. You can keep your reference materials accessible while maintaining smooth browser performance.

## Troubleshooting Common Issues

Sometimes screenshots may not turn out as expected. Here are solutions to common problems:

If your screenshot appears blank or incomplete, the page may not have finished loading. Wait for all images to appear and any animations to complete before capturing. Some websites load content dynamically as you scroll, so you may need to scroll through the entire page first to ensure everything is rendered. Pages with lazy-loaded images are particularly prone to this issue, as images below the fold may not have been fetched when you take the screenshot.

If you see a "Capture failed" message, try reloading the page and ensuring Developer Tools is properly open. Sometimes the DevTools panel needs to be fully initialized before screenshots can be captured. Try closing and reopening Developer Tools, then attempt the capture again.

If the screenshot quality seems poor, make sure you are not using any browser zoom (Ctrl+0 to reset to 100%) and that you are capturing at your monitor's native resolution. Zoom levels other than 100% can sometimes affect the captured image quality or dimensions.

If you are trying to capture a page with lots of dynamic content and the screenshot seems to cut off unexpectedly, try scrolling to the bottom of the page manually first to trigger all content loading, then capture the full page screenshot. Some single-page applications and infinite scroll sites require this extra step.

If the captured image appears too large or too small, this could be due to your display scaling settings. On Windows, you can adjust the scale settings in Display preferences. On Mac, check your Retina display settings. The screenshots will capture at your current display resolution, which may differ from what you expect.

## Keyboard Shortcuts Reference

Mastering the keyboard shortcuts for Chrome's screenshot capabilities will significantly speed up your workflow. Here is a comprehensive reference of all the key combinations you need to know:

For accessing Developer Tools, the primary shortcut is F12, or you can use Ctrl+Shift+I on Windows and Cmd+Shift+I on Mac. This opens the Developer Tools panel where all screenshot functionality is housed.

Once Developer Tools is open, press Ctrl+Shift+P on Windows or Cmd+Shift+P on Mac to open the Command Menu. This is your gateway to all screenshot commands. Simply type "screenshot" to filter the available options.

For quick viewport screenshots without opening the Command Menu, you can also use the More tools menu within Developer Tools. Click the three dots in the upper right of the DevTools panel, select "More tools," and then "Capture screenshot" for a quick viewport capture.

The Escape key is useful for closing Developer Tools quickly once you have captured your screenshot.
>>>>>>> consumer/a51-chrome-built-in-screenshot-tool

When you capture screenshots using the methods above, Chrome automatically hides the DevTools interface from the final image. This means your screenshots look clean and professional, without any debugging panels visible. This is particularly important when capturing content for presentations, documentation, or client deliverables.

<<<<<<< HEAD
## Performance Considerations and Best Practices

While Chrome's built-in screenshot tools are powerful, there are some best practices to keep in mind for optimal results.

### Page Loading and Dynamic Content

For full page screenshots, ensure the page is fully loaded before capturing. If the page has lazy-loaded images or infinite scroll content, you may need to scroll through the entire page first to ensure everything is rendered. Some pages may require waiting for animations to complete or for JavaScript to finish executing.

### High Resolution Displays

On high DPI (Retina) displays, Chrome's screenshots are captured at the device pixel ratio, resulting in higher resolution images. This is generally beneficial as it provides crisp, detailed screenshots, but be aware that these images will be larger in file size.

### File Management

By default, Chrome saves screenshots to your Downloads folder with filenames like "screenshot.png" or "fullpage.png." If you capture multiple screenshots, Chrome will add timestamps to prevent overwriting. For better organization, consider moving screenshots to dedicated folders immediately after capture.

## Combining with Other Tools for Enhanced Workflow

While Chrome's built-in tools are powerful, they work even better when combined with other productivity strategies. For instance, if you find yourself taking many screenshots throughout the day, your browser may have numerous tabs open, which can impact performance.

**Tab Suspender Pro** is a Chrome extension that can help manage your open tabs more efficiently. By automatically suspending tabs you are not actively using, it reduces memory usage and can make your browser feel snappier. This is particularly useful when you are working on projects that require frequent screenshotting and need to keep reference pages open without bogging down your system.

Using a combination of Chrome's built-in screenshot tools and thoughtful tab management creates a more efficient workflow. You can keep your reference materials accessible while maintaining smooth browser performance.

## Troubleshooting Common Issues

Sometimes screenshots may not turn out as expected. Here are solutions to common problems:

If your screenshot appears blank or incomplete, the page may not have finished loading. Wait for all images to appear and any animations to complete before capturing. Some websites load content dynamically as you scroll, so you may need to scroll through the entire page first to ensure everything is rendered. Pages with lazy-loaded images are particularly prone to this issue, as images below the fold may not have been fetched when you take the screenshot.

If you see a "Capture failed" message, try reloading the page and ensuring Developer Tools is properly open. Sometimes the DevTools panel needs to be fully initialized before screenshots can be captured. Try closing and reopening Developer Tools, then attempt the capture again.

If the screenshot quality seems poor, make sure you are not using any browser zoom (Ctrl+0 to reset to 100%) and that you are capturing at your monitor's native resolution. Zoom levels other than 100% can sometimes affect the captured image quality or dimensions.

If you are trying to capture a page with lots of dynamic content and the screenshot seems to cut off unexpectedly, try scrolling to the bottom of the page manually first to trigger all content loading, then capture the full page screenshot. Some single-page applications and infinite scroll sites require this extra step.

If the captured image appears too large or too small, this could be due to your display scaling settings. On Windows, you can adjust the scale settings in Display preferences. On Mac, check your Retina display settings. The screenshots will capture at your current display resolution, which may differ from what you expect.

## Keyboard Shortcuts Reference

Mastering the keyboard shortcuts for Chrome's screenshot capabilities will significantly speed up your workflow. Here is a comprehensive reference of all the key combinations you need to know:

For accessing Developer Tools, the primary shortcut is F12, or you can use Ctrl+Shift+I on Windows and Cmd+Shift+I on Mac. This opens the Developer Tools panel where all screenshot functionality is housed.

Once Developer Tools is open, press Ctrl+Shift+P on Windows or Cmd+Shift+P on Mac to open the Command Menu. This is your gateway to all screenshot commands. Simply type "screenshot" to filter the available options.

For quick viewport screenshots without opening the Command Menu, you can also use the More tools menu within Developer Tools. Click the three dots in the upper right of the DevTools panel, select "More tools," and then "Capture screenshot" for a quick viewport capture.

The Escape key is useful for closing Developer Tools quickly once you have captured your screenshot.

Extensions can offer additional features like automatic cloud upload, annotation tools, delayed capture, scrolling capture of non-webpage content, and integration with other services. However, for basic webpage capture needs, Chrome's built-in tools are more than sufficient and offer the benefit of not requiring additional browser resources. Many screenshot extensions are resource-heavy, running in the background and consuming memory even when you're not taking screenshots. This can slow down your browser, especially on computers with limited RAM.

While Chrome's built-in screenshot tools are capable, you might wonder how they compare to popular third-party screenshot extensions and applications. Understanding this comparison can help you choose the right tool for your specific needs.

Chrome's native tools excel in several areas. They require no additional permissions, making them more secure and privacy-focused. There is no need to trust third-party developers with access to your browsing data. The captures are consistently high quality because they come directly from Chrome's rendering engine. There is no extension overhead or performance impact on your browser. Finally, these tools work offline and do not require an internet connection.

Third-party solutions often offer additional features that Chrome's built-in tools do not provide. These may include annotation and editing capabilities built directly into the screenshot tool, cloud storage integration for automatic backup, share functionality for quick sending to colleagues, and advanced region selection with freeform drawing tools.

However, for many users, Chrome's built-in tools provide more than enough functionality. The key is to assess your specific needs. If you primarily need quick captures for documentation, bug reporting, or reference, Chrome's native tools are likely sufficient. If you need extensive editing, annotations, or sharing features, a third-party solution might be worth considering.

=======
While Chrome's built-in screenshot tools are capable, you might wonder how they compare to popular third-party screenshot extensions and applications. Understanding this comparison can help you choose the right tool for your specific needs.

Chrome's native tools excel in several areas. They require no additional permissions, making them more secure and privacy-focused. There is no need to trust third-party developers with access to your browsing data. The captures are consistently high quality because they come directly from Chrome's rendering engine. There is no extension overhead or performance impact on your browser. Finally, these tools work offline and do not require an internet connection.

Third-party solutions often offer additional features that Chrome's built-in tools do not provide. These may include annotation and editing capabilities built directly into the screenshot tool, cloud storage integration for automatic backup, share functionality for quick sending to colleagues, and advanced region selection with freeform drawing tools.

However, for many users, Chrome's built-in tools provide more than enough functionality. The key is to assess your specific needs. If you primarily need quick captures for documentation, bug reporting, or reference, Chrome's native tools are likely sufficient. If you need extensive editing, annotations, or sharing features, a third-party solution might be worth considering.

>>>>>>> consumer/a51-chrome-built-in-screenshot-tool
## Specialized Use Cases

Beyond the basic screenshot scenarios, Chrome's built-in tools can handle several specialized use cases that you might find helpful in specific situations.

### Capturing Password-Protected Pages

Chrome's screenshot tools can capture password-protected pages just as easily as public pages, as long as you are already logged in. This is useful for capturing account settings pages, private dashboards, or membership-only content for documentation purposes. Simply log in to the site normally, navigate to the page you want to capture, and use the screenshot commands as usual.

### Capturing Animated Content

When capturing pages with animations, timing is important. For best results, wait until all animations have completed their cycles before taking your screenshot. If the page has repeating animations, consider using browser Developer Tools to pause JavaScript execution before capturing, which will freeze all animations in place.

### Capturing Print Layouts

If you want to preview how a webpage might look when printed, you can use Chrome's print preview feature in conjunction with screenshots. First, go to the page you want to capture, press Ctrl+P (or Cmd+P on Mac) to open the print preview, and then capture a screenshot of that view. This is particularly useful for documenting how articles or reports will appear in print.

### Capturing Mobile Viewports

Chrome includes device emulation features that allow you to see how websites appear on mobile devices. You can combine this with screenshot capabilities to capture mobile-specific layouts. In Developer Tools, click the device toggle icon (or press Ctrl+Shift+M / Cmd+Shift+M), select a mobile device from the dropdown, and then use the screenshot commands to capture how the page appears on that device.

## Tips for Professional Results

To get the best possible screenshots using Chrome's built-in tools, consider these professional tips that will help you produce higher quality captures for any purpose.

First, disable unnecessary browser extensions before capturing important screenshots. Some extensions modify page appearance or inject content, which could interfere with clean captures. You can do this temporarily by using Chrome's incognito mode, which disables most extensions by default, or by managing your extensions in the settings menu.

Second, ensure consistent styling by using Chrome's "Reset to default" zoom setting (Ctrl+0) before capturing. Different zoom levels can affect how elements render and may produce unexpected results in your screenshots.

Third, for presentations or documentation, consider using Chrome's custom theme settings to create a cleaner background. You can also use the "Capture node screenshot" feature to isolate exactly the content you need without surrounding elements.

Fourth, when capturing multiple screenshots for a single project, maintain consistent window sizes and viewport dimensions. This creates a more professional and cohesive set of images that look better together in presentations or documentation.

Fifth, take advantage of Chrome's ability to capture before any tracking scripts or analytics have loaded. Since screenshots capture the rendered page state directly, they do not include cookies or tracking elements that might be visible in other capture methods.

## Advanced Techniques for Developers

For web developers and front-end engineers, Chrome's screenshot capabilities offer several advanced techniques that can aid in development workflows and quality assurance processes.

### Using Screenshots for Visual Regression Testing

While dedicated visual regression testing tools exist, you can use Chrome's screenshot capabilities as a simple manual approach. Capture screenshots of pages in different states (before and after changes), then compare them visually to identify unintended changes. This manual approach works well for small projects or occasional checks.

### Documenting Responsive Designs

When building responsive websites, capture screenshots at multiple viewport widths to document how the design adapts. Use the device emulation feature in Developer Tools to quickly switch between common device sizes and capture each layout state.

### Capturing Complex CSS Effects

Modern websites often use complex CSS effects including gradients, shadows, transforms, and animations. Chrome's screenshot tool captures these effects accurately because it uses the actual rendered output. This makes it excellent for documenting creative designs or reporting issues with visual effects.

### Creating Style Guides

Use the node screenshot feature to create component style guides. Capture individual UI elements at various states (hover, active, disabled) to build a comprehensive library of your design system's components. This documentation can be invaluable for maintaining consistency across large projects or teams.

## Security and Privacy Considerations

Using Chrome's built-in screenshot tools provides some security advantages over third-party alternatives that you should be aware of.

Since these tools are built directly into Chrome, they do not require any additional permissions to function. This stands in contrast to many screenshot extensions, which request broad permissions to access all your browsing data. By using only Chrome's native tools, you minimize the potential attack surface on your browser.

Additionally, screenshots taken with Chrome's tools are saved directly to your local Downloads folder. They are not uploaded to any external service, ensuring that sensitive information you capture remains on your device. This is particularly important when capturing pages containing personal information, financial data, or confidential business content.

The fact that these tools are maintained by Google means they receive regular security updates as part of Chrome's normal release cycle. You do not need to worry about outdated screenshot tools containing security vulnerabilities.

## Conclusion

Chrome's built-in screenshot capabilities are surprisingly powerful and can handle most everyday screenshot needs without requiring external extensions. From capturing full webpages to isolating specific elements, these tools provide flexibility and quality that rival dedicated screenshot software.

By mastering the Command Menu shortcuts, understanding the different capture modes, and knowing when to use each method, you can become significantly more efficient at capturing web content. Whether you are a developer documenting your work, a designer sharing UI components, or just someone who occasionally needs to capture a webpage, Chrome has the tools you need.

The built-in screenshot features work seamlessly with Chrome's other productivity features, making them an integral part of any web-based workflow. From basic viewport captures to advanced node-specific screenshots, these tools cover a wide range of use cases without adding any complexity to your browser setup.

Remember to combine these screenshot capabilities with good browsing habits, like managing your tabs effectively with tools such as **Tab Suspender Pro**, for an optimal overall experience. With practice, capturing exactly what you need from the web will become a quick and painless part of your workflow.

Built by theluckystrike — More tips at [zovo.one](https://zovo.one)
