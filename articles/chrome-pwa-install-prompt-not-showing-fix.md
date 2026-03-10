---
layout: post
title: "Chrome PWA Install Prompt Not Showing Fix"
description: "Your PWA install prompt won't appear? Learn why this happens and how to fix it with simple steps."
date: 2026-01-15
categories: [pwa, chrome, tips]
tags: [pwa, chrome, install-prompt, progressive-web-app]
author: theluckystrike
---

# Chrome PWA Install Prompt Not Showing Fix

Chrome PWA install prompt not showing is one of the most common issues developers and users face when working with progressive web apps. You have built a PWA that meets all the requirements, added a manifest file, registered a service worker, and yet the install prompt never appears for your users. This can be frustrating, especially when you have put in the work to make your app installable. The good news is that this is usually caused by a handful of common issues, and most of them have straightforward fixes.

Let me walk you through why this happens and what you can do to get that install prompt showing up for your users.

## Why the Install Prompt Does Not Appear

Before diving into fixes, it helps to understand what triggers the install prompt in Chrome. For Chrome to show the install prompt, your web app must meet several criteria defined by Google's PWA standards. The browser needs to detect that your site is installable, which means it must be served over HTTPS, have a valid web app manifest with at least the name, short name, icons, start URL, and display mode, and include a service worker that handles a fetch event.

Chrome also has its own additional requirements. The PWA must not be already installed on the user's device. The user must have engaged with the site for at least a few seconds. The site must meet a minimum size requirement and have at least one icon that is at least 192x192 pixels. If any of these requirements are not met, Chrome will simply not show the prompt.

Another common reason the install prompt does not show is that the browser has already shown the prompt and the user dismissed it. Chrome remembers this dismissal, and unless you explicitly call the prompt again in your code, it will not appear on subsequent visits. This is actually by design to prevent annoying users with repeated prompts, but it can be confusing if you are testing your PWA.

## Check Your Web App Manifest

The manifest file is the heart of your PWA installability. If this file is missing, malformed, or does not contain the required fields, Chrome will not consider your app installable. Open your browser's developer tools and go to the Application tab to check your manifest. Look for any errors or warnings related to the manifest file.

Make sure your manifest includes all required fields. The name and short_name are essential, and Chrome may not show the prompt if the short name is missing. The start URL must point to a valid page that loads correctly. The icons array must contain at least one icon that is 192x192 pixels or larger, and it is highly recommended to include a 512x512 icon as well. The display property should be set to standalone, fullscreen, or minimal-ui. The theme_color and background_color should also be defined.

If you are using a relative path for your icons, make sure those icon files actually exist on your server. A broken icon link will prevent the install prompt from appearing.

## Verify Your Service Worker

The service worker is the other critical piece of the PWA puzzle. Chrome requires a service worker to be registered and active before it will show the install prompt. Open the Application tab in developer tools and check the Service Workers section. You should see your service worker registered and running.

Make sure your service worker is handling fetch events. A minimal service worker that does nothing will not satisfy Chrome's requirements. You need at least a basic fetch event handler that returns responses. Also, ensure that your service worker is successfully caching your app shell and essential resources. If the service worker fails to load or throws errors, Chrome will not show the install prompt.

One useful tip is to use the Lighthouse tool built into Chrome. Run a Lighthouse audit on your site and look for the PWA section. It will tell you exactly which PWA requirements are not being met, making it much easier to identify the problem.

## User Engagement Requirements

Chrome has specific requirements around user engagement that can prevent the prompt from showing. The user must have interacted with the domain for at least 30 seconds across at least two separate visits. This is designed to prevent sites from showing prompts immediately upon loading.

If you are testing in incognito mode, be aware that incognito windows are treated differently, and the install prompt may not appear at all in some cases. Also, if your PWA is already installed on the device, Chrome will not show the prompt again.

## Manually Triggering the Prompt

If you want more control over when the prompt appears, you can listen for the beforeinstallprompt event in your JavaScript code and trigger the prompt yourself. This gives you the ability to show a custom install button that appears only when the browser determines the app is installable.

Here is how it works. You add an event listener for beforeinstallprompt and prevent the default behavior. When the user clicks your custom install button, you call prompt on the event object. The browser will then show its native install dialog. This approach puts you in control of the user experience and ensures the prompt appears at the right time.

This is actually the approach taken by many professional web apps, including Tab Suspender Pro, which provides a smooth installation experience for users. By handling the prompt yourself, you can avoid the timing issues that sometimes cause the automatic prompt to not appear.

## Testing and Debugging

When troubleshooting the install prompt, start by clearing your browser data for the site. Go to chrome://apps in Chrome and remove your PWA if it is already installed. Then clear the site data including service workers and storage. Restart Chrome and visit your site again.

Use the Application panel in developer tools to monitor what's happening. Check the Manifest section for any errors. Look at the Service Workers section to confirm your worker is running. The Console may also show relevant messages about why the install prompt is not appearing.

Testing on different devices and browsers can also help. The install prompt behavior varies between Chrome on desktop, Chrome on Android, and other browsers. What works in one environment may not work in another.

## Final Thoughts

If your Chrome PWA install prompt is not showing, go through the checklist above. Verify your manifest is complete, your service worker is working, and you are meeting all of Chrome's requirements. Use Lighthouse to audit your PWA and address any issues it flags.

Remember that you have control over the prompt through the beforeinstallprompt event. Taking manual control of the install experience often provides a better user experience anyway. Your users will appreciate a clear, well-timed install button rather than a prompt that appears at unpredictable times.

Built by theluckystrike — More tips at [zovo.one](https://zovo.one)
