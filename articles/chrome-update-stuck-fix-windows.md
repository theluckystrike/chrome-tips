---
layout: default
title: Chrome Update Stuck? Here's How to Fix It on Windows
description: Is your Chrome update stuck on Windows? Discover proven methods to get
  Chrome updating again, from simple restarts to advanced troubleshooting steps effectively.
date: 2026-01-15
last_modified_at: '2026-03-12'
permalink: chrome-update-stuck-fix-windows
categories:
- chrome
- windows
- troubleshooting
tags:
- chrome-update
- windows-tips
- browser-fix
- chrome-stuck
author: theluckystrike
---

# Chrome Update Stuck? Here's How to Fix It on Windows

Chrome updates are essential for security, performance, and accessing the latest features. But sometimes, the update process gets stuck, leaving you with a browser that won't finish updating. If you're staring at a frozen "Updating Chrome" message or your browser simply won't launch after an update attempt, this guide will help you get Chrome working again.

## Why Does Chrome Get Stuck During Updates?

Before we jump into fixes, understanding what causes update problems helps you prevent them in the future. Chrome updates can stall for several reasons:

- **Interrupted download**: Poor internet connection or network interruption during the update download
- **Conflicting software**: Security software or other programs interfering with Chrome's update process
- **Corrupted files**: Previous update attempts leaving behind damaged files
- **Insufficient permissions**: Windows not allowing Chrome to modify necessary files
- **Outdated system**: Windows itself may need updates that affect browser compatibility

Now, let's work through the solutions, starting with the simplest.

## Method 1: Restart Your Computer

It sounds obvious, but a simple restart often resolves update issues. When Chrome gets stuck, some processes may be running in the background that prevent the update from completing.

Save your work, close all programs, and restart your computer. After it boots back up, open Chrome again. The browser should either complete the update automatically or at least give you a clearer error message if the problem persists.

This method works for about 30% of update stuck scenarios, so it's always worth trying first before moving to more involved solutions.

## Method 2: Close Chrome Completely and Try Again

Sometimes Chrome appears stuck but is actually just waiting. The browser might have partially updated and is waiting for certain processes to finish. Here's what to do:

**Step 1:** Press Ctrl+Shift+Esc to open Task Manager

**Step 2:** Look for any Chrome processes running (chrome.exe, Google Chrome, or processes with "Chrome" in the name)

**Step 3:** Select each Chrome process and click "End Task" to close them all

**Step 4:** Wait a few seconds, then try opening Chrome again

Make sure you close all Chrome windows and background processes. Even an icon in your system tray can keep update processes running.

## Method 3: Run Chrome Cleanup Tool

Google provides a built-in cleanup tool that can fix various Chrome issues, including update problems. While it's primarily designed to remove malware and unwanted software, it also helps with corrupted files that cause update failures.

**Step 1:** Go to Settings in Chrome (click the three dots, then Settings)

**Step 2:** Scroll down and click "Advanced"

**Step 3:** Under "Reset and clean up," click "Clean up computer"

**Step 4:** Click "Find" to run the cleanup tool

Wait for the scan to complete. If it finds any issues, follow the prompts to remove problematic software. After this, try updating Chrome again through the menu (three dots > Help > About Google Chrome).

## Method 4: Delete the Update Folder

Chrome stores update files in a specific folder on your computer. If these files become corrupted, they can cause the update to hang. Deleting this folder forces Chrome to download fresh update files.

**Step 1:** Close Chrome completely (use Task Manager as shown in Method 2)

**Step 2:** Press Windows+R to open the Run dialog

**Step 3:** Type the following path and press Enter:
```
%ProgramData%\Google\Chrome\Application
```

**Step 4:** Look for a folder named after the Chrome version (like "120.0.6099.130")

**Step 5:** If you see a file called "installer" inside, delete that entire version folder

**Step 6:** Also check this path:
```
%LocalAppData%\Google\Chrome\Application
```

Delete any version folders you find there as well

**Step 7:** Restart Chrome and let it download a fresh update

## Method 5: Reinstall Chrome

When other methods fail, a clean reinstall is often the fastest solution. This removes all corrupted files and gives you a fresh start with the latest version.

**Step 1:** Go to Windows Settings > Apps > Apps & features

**Step 2:** Find Google Chrome in the list

**Step 3:** Click it and select "Uninstall"

**Step 4:** Follow the prompts to remove Chrome completely

**Step 5:** Download the latest Chrome from the official website (google.com/chrome)

**Step 6:** Run the installer and let it complete

This method preserves your bookmarks, history, and passwords because they're stored in your Google account. Just make sure you're signed into Chrome before uninstalling.

## Method 6: Check Windows Update

Sometimes the issue isn't with Chrome at all—it's with Windows itself. An outdated Windows installation can cause compatibility issues with Chrome updates.

**Step 1:** Go to Windows Settings > Windows Update

**Step 2:** Click "Check for updates"

**Step 3:** Install any available updates

**Step 4:** Restart your computer if prompted

After updating Windows, try updating Chrome again. This resolves the issue surprisingly often, especially on systems that haven't been updated in a while.

## Method 7: Run SFC and DISM Scans

Windows has built-in tools to repair system files that might be causing problems. These scans can fix underlying issues that affect Chrome's ability to update.

**Step 1:** Open Command Prompt as administrator (right-click Start, select "Windows Terminal (Admin)" or "Command Prompt (Admin)")

**Step 2:** Type the following command and press Enter:
```
sfc /scannow
```

**Step 3:** Wait for the scan to complete (this may take several minutes)

**Step 4:** After that finishes, type:
```
DISM /Online /Cleanup-Image /RestoreHealth
```

**Step 5:** Restart your computer after both commands finish

These tools scan and repair corrupted system files that could be interfering with Chrome updates.

## Preventing Future Update Issues

Once you've fixed the current problem, take these steps to prevent it from happening again:

- **Keep Windows updated** — regular system updates prevent compatibility issues
- **Use a stable internet connection** — avoid updating Chrome over unstable Wi-Fi
- **Don't interrupt updates** — let Chrome finish updating before closing your computer
- **Keep antivirus updated** — outdated security software sometimes blocks legitimate updates

## A Note on Browser Performance

After getting your Chrome update working again, you might notice the browser feels slower, especially if you've been using it for a long time. This is normal as Chrome accumulates data and extensions over time.

If your browser feels sluggish after an update, consider using **Tab Suspender Pro**, a Chrome extension that automatically suspends tabs you're not actively using. This frees up memory and can significantly improve performance, particularly on computers with limited RAM.

## When to Seek Further Help

If you've tried all these methods and Chrome still won't update, you may be dealing with a more serious issue:

- A hardware problem with your hard drive or memory
- Deeply corrupted Windows installation
- Specific enterprise policies blocking updates

In these cases, consider reaching out to Google Chrome support or your computer manufacturer for additional assistance.

## Final Thoughts

A stuck Chrome update is frustrating, but it's usually fixable. Start with the simple solutions (restart, close Chrome processes) and move to more involved steps only if needed. Most users find that Method 2 or Method 4 resolves their issue quickly.

Keeping Chrome updated ensures you have the latest security patches and features, so it's worth taking a few minutes to get the update process working again.

## Related Articles

- [How to Check If Chrome Is Up to Date](/chrome-tips/how-to-check-if-chrome-is-up-to-date/)
- [Chrome Update Failed Error 7 Fix](/chrome-tips/chrome-update-failed-error-7-fix/)
- [How to Stop Chrome Auto Update](/chrome-tips/chrome-auto-update-how-to-stop/)


Built by theluckystrike — More tips at [zovo.one](https://zovo.one)
