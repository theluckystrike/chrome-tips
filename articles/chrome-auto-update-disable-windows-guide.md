---
layout: post
title: How to Disable Chrome Auto Update on Windows
description: A complete guide to stopping Chrome's automatic updates on Windows. Learn
  multiple methods to control when Chrome updates, including registry edits and group...
date: 2026-01-15
categories:
- tutorials
- chrome
- windows
tags:
- chrome-auto-update
- disable-update
- windows-tutorial
- chrome-settings
author: theluckystrike
last_modified_at: 2026-03-12
permalink: chrome-auto-update-disable-windows-guide
---
# How to Disable Chrome Auto Update on Windows

Google Chrome automatically updates itself to ensure you have the latest security patches, performance improvements, and feature additions. While this is generally beneficial for most users, there are valid reasons why you might want to control when Chrome updates. Perhaps you need to maintain compatibility with specific extensions, prefer to test updates in a controlled environment, or manage updates across multiple workstations in an organization. This guide will walk you through several methods to disable or control Chrome auto-update on Windows.

## Why Disable Chrome Auto Update?

Before we dive into the methods, let's understand why you might want to disable Chrome's automatic updates. In enterprise environments, IT administrators often need to test new browser versions before rolling them out across the organization. Unexpected updates can sometimes introduce compatibility issues with internal web applications or specific browser extensions that your workflow depends on.

Individual users might also have preferences about update timing. Perhaps you have limited internet bandwidth during certain hours, or you simply want to avoid the slight performance impact that can occur during an update. Some users also prefer to manually control their software to ensure stability, especially when using Chrome for specialized tasks.

## Method 1: Using the Google Update Registry Keys

The most straightforward method to disable Chrome auto-update on Windows involves modifying the Windows Registry. This approach works for both individual users and system-wide configurations.

First, open the Registry Editor by pressing Windows key + R, typing "regedit", and pressing Enter. Navigate to the following path depending on whether you want to apply this for the current user or all users on the system:

For current user only:
```
HKEY_CURRENT_USER\Software\Google\Chrome
```

For all users on the computer:
```
HKEY_LOCAL_MACHINE\Software\Google\Chrome
```

If the "Chrome" key does not exist, you may need to create it. Right-click on the parent key, select "New" and then "Key", and name it "Chrome". Within this key, create a new DWORD value named "UpdateURL" and set its value to an empty string or a non-functional URL. This effectively breaks the update check mechanism.

For a more complete solution that prevents the Google Update service from updating Chrome, create a new key named "Update" under the Chrome key, and within it, create a DWORD value named "UpdatePolicy" set to "1". Additionally, create a DWORD named "Standard" set to "0". This tells Google Update to not apply any updates.

After making these changes, restart your computer for the modifications to take effect.

## Method 2: Using Group Policy Editor

If you're using Windows 10 Pro, Enterprise, or Windows 11 Pro, you can use the Local Group Policy Editor for a more controlled approach. This method is particularly useful in organizational settings where you want to manage browser updates centrally.

Press Windows key + R, type "gpedit.msc", and press Enter. Navigate to Computer Configuration > Administrative Templates > Google > Google Chrome. Look for the "Update policy" setting in the right pane.

Double-click on "Update policy" and select "Enabled". You will then have several options to choose from:

- **Always allow updates**: This is the default behavior.
- **Always block updates**: Completely prevents Chrome from updating.
- **Allow updates but defer when they can be applied**: Lets you specify a deferral period in days.

Select "Always block updates" if you want to completely disable auto-updates. Click OK and close the Group Policy Editor. The changes will apply during the next Group Policy refresh cycle, or you can run "gpupdate /force" in Command Prompt to apply immediately.

## Method 3: Disabling the Google Update Service

Another effective method involves disabling the Google Update service that runs in the background and handles Chrome updates. This service runs silently and checks for updates periodically.

Press Windows key + R, type "services.msc", and press Enter to open the Services Manager. Look for "Google Update Service (gupdate)" and "Google Update Service (gupdateSvc)" in the list. Double-click on each service, change the "Startup type" to "Disabled", and click "Stop" to halt the service if it's currently running.

This method prevents Chrome from checking for updates entirely. However, note that this will also prevent updates to other Google applications that use the same update mechanism.

## Method 4: Blocking Updates at the Firewall Level

For organizations with more stringent control requirements, blocking Chrome's update servers at the firewall level provides another layer of control. This approach prevents any Chrome installation on the network from reaching Google's update servers.

You would need to block the following domains at your firewall or router level:

- clients2.google.com
- update.google.com
- dl.google.com
- tools.google.com

This method ensures that Chrome cannot check for or download updates, regardless of any settings changed on individual machines. It's particularly effective for networks where you want uniform control across all devices.

## Managing Extensions and Tab Memory

While you're controlling Chrome updates, you might also want to optimize how Chrome manages its resources. Browser extensions can significantly impact Chrome's performance and memory usage, especially when you have many tabs open.

Consider using extensions like **Tab Suspender Pro** to automatically suspend inactive tabs and reduce memory consumption. This can be particularly helpful if you're running older hardware or need Chrome to remain lightweight for your specific use case. Tab Suspender Pro intelligently identifies tabs you haven't used recently and puts them to sleep, freeing up RAM for your active browsing sessions.

## Reverting Your Changes

If you decide you want Chrome to update automatically again, simply reverse the methods above. For registry changes, delete the keys or values you created. For Group Policy, set the update policy back to "Not configured" or "Always allow updates". For services, change the startup type back to "Automatic" and start the service.

## Conclusion

Controlling Chrome auto-update on Windows is straightforward with these multiple methods. Whether you need enterprise-level control through Group Policy, prefer registry modifications for individual machines, or want to block updates at the network level, there's an approach that fits your needs. Remember that keeping Chrome updated is generally recommended for security reasons, so consider periodically checking for updates manually if you've disabled automatic updates for an extended period.

---



## Related Articles
- [Chrome Slower After Windows Update Fix](/chrome-slower-after-windows-update-fix)
- [How to Stop Chrome Auto Update](/chrome-auto-update-how-to-stop)
- [Chrome Slow on Windows 11 After Update: Practical Fixes](/chrome-slow-on-windows-11-after-update)

Built by theluckystrike — More tips at [zovo.one](https://zovo.one)


## Related Articles

- [chrome topics api explained simply](/articles/chrome-topics-api-explained-simply/)
- [Chrome for Babbel Web App Tips](/articles/chrome-for-babbel-web-app-tips/)
- [Chrome Service Workers List How to View](/articles/chrome-service-workers-list-how-to-view/)
