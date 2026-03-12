---
layout: post
title: How to Fix Chrome Downloads Stuck at 100 Percent
description: Chrome download shows 100% complete but won't finish? Learn practical
  solutions to fix stuck downloads in Chrome, from clearing history to checking settings.
date: 2026-01-15
categories:
- chrome
- downloads
- troubleshooting
tags:
- chrome-downloads
- browser-fix
- download-issues
- troubleshooting
author: theluckystrike
last_modified_at: '2026-03-11'
permalink: chrome-downloads-stuck-at-100-percent
---
# How to Fix Chrome Downloads Stuck at 100 Percent

You've been there before. You're downloading an important file—maybe a work document, software installer, or that movie you wanted to watch offline. The progress bar creeps up steadily, and then it hits 100%. You wait. And wait. But the file never opens, and Chrome keeps showing that the download is "complete" without actually giving you the file.

This frustrating issue is more common than you might think, and it can happen for several reasons. The good news is that there are multiple ways to fix it, and we'll walk through each one step by step.

## Why Do Downloads Get Stuck at 100 Percent?

Before we dive into solutions, it helps to understand what's happening. When Chrome says a download is "complete" but the file hasn't appeared, it usually means one of several things:

- **Chrome hasn't moved the file** from its temporary location to your chosen download folder
- **An antivirus program** is scanning the file and blocking it
- **A browser extension** is interfering with the download process
- **Chrome's download cache** is corrupted
- **The download was interrupted** but Chrome didn't update the status correctly

Now let's fix it.

## Solution 1: Check Your Download Folder First

Before trying any technical fixes, verify that the file isn't already sitting in your downloads folder:

**For Windows:**
1. Press `Win + R` to open the Run dialog
2. Type `%userprofile%\Downloads` and press Enter
3. Look for your file there

**For Mac:**
1. Open Finder
2. Click on "Downloads" in the sidebar
3. Check for your file

If the file is there but has a `.crdownload` extension (Chrome's temporary download extension), the download actually didn't complete. If it has your expected extension but won't open, try Solution 2.

## Solution 2: Clear Chrome's Download History

Chrome keeps a record of all downloads, and sometimes this history gets corrupted. Clearing it can force Chrome to properly finalize stuck downloads:

1. Open Chrome and press `Ctrl + H` (Windows) or `Cmd + Y` (Mac) to open History
2. Click "Clear browsing data" on the left sidebar
3. Select the "Advanced" tab
4. Check "Download history" (you can uncheck everything else)
5. Set the time range to "All time"
6. Click "Clear data"
7. Restart Chrome and try downloading again

This simple step fixes the issue in many cases.

## Solution 3: Disable Antivirus Scanning (Temporarily)

If you use Windows Defender, McAfee, Norton, or another antivirus program, it might be scanning downloaded files and preventing Chrome from completing the transfer. This is especially common with executable files (.exe, .msi) and compressed archives (.zip, .rar).

To test if this is the cause:

**For Windows Defender:**
1. Open Windows Security
2. Go to "Virus & threat protection"
3. Click "Manage settings" under Virus & threat protection settings
4. Turn off "Real-time protection" temporarily
5. Try downloading the file again

**For third-party antivirus:**
Look for a setting called "Scan downloads" or "File shield" and disable it temporarily.

**Important:** Remember to re-enable your antivirus after testing. This is only a diagnostic step.

## Solution 4: Check for Problematic Extensions

Browser extensions can sometimes interfere with downloads. To test if an extension is causing the issue:

1. Click the three dots (menu) in Chrome → More tools → Extensions
2. Toggle off all extensions
3. Try downloading the file again

If the download works after disabling extensions, enable them one by one to identify the culprit. Common problematic extensions include ad blockers, download managers, and VPN extensions.

For users who want a cleaner browsing experience without extension conflicts, **Tab Suspender Pro** can help manage your tabs more efficiently. While it doesn't directly fix download issues, it reduces browser clutter and can prevent conflicts that arise from having too many extensions active.

## Solution 5: Reset Chrome Settings

If the above solutions haven't worked, resetting Chrome to its default settings can fix deeper issues:

1. Click the three dots → Settings
2. Scroll down and click "Advanced"
3. Under "Reset and clean up," click "Reset settings to their original defaults"
4. Click "Reset settings" to confirm
5. Restart Chrome

This won't delete your bookmarks or passwords, but it will reset your startup pages, search engine, and pinned tabs.

## Solution 6: Manually Find the Temporary File

Chrome downloads files to a temporary location before moving them to your final destination. If the download got stuck, the file might still exist in this temporary location:

**For Windows:**
1. Go to `C:\Users\[YourUsername]\AppData\Local\Temp`
2. Look for files with `.crdownload` extension
3. If you find your file, copy it to your downloads folder and remove the `.crdownload` extension

**For Mac:**
1. Open Finder and press `Cmd + Shift + G`
2. Type `/private/var/folders/` and press Enter
3. Search for your filename or look for `.crdownload` files

This is a last-resort method but can save you from re-downloading large files.

## Solution 7: Use Chrome's Built-in Download Manager

Chrome has a built-in download manager that can help manage stuck downloads:

1. Press `Ctrl + J` (Windows) or `Cmd + Shift + J` (Mac) to open the Downloads page
2. Find your stuck download
3. Click the "X" to cancel it, then click "Resume" or try downloading again
4. If those options don't work, click the three dots next to the download and select "Remove from list," then download again

## Preventing Future Stuck Downloads

Once you've fixed the current issue, here are some tips to prevent it from happening again:

- **Keep Chrome updated** — Older versions sometimes have download bugs
- **Don't close Chrome while downloading** — Let the download finish completely
- **Check your internet connection** — Unstable connections can cause incomplete downloads
- **Avoid downloading to network drives** — Download to your local drive first, then move the file

## What If Nothing Works?

If you've tried all these solutions and downloads are still stuck:

- Try using a different browser temporarily (Firefox, Edge) to download the file
- Check if your hard drive is full
- Try downloading a different file to see if the issue is file-specific
- Run Chrome as administrator (Windows) by right-clicking the Chrome icon and selecting "Run as administrator"

## Final Thoughts

Chrome downloads stuck at 100 percent are annoying, but they're usually fixable. Start with the simplest solutions—checking your download folder and clearing download history—before moving to more involved fixes like resetting Chrome or hunting for temporary files.

For users who frequently download large files, keeping your browser organized can help prevent conflicts. Consider using **Tab Suspender Pro** to manage your open tabs efficiently, reducing browser overhead and potential extension conflicts that might interfere with downloads.

With these solutions in hand, you should be able to get your files downloaded and moving again.

Built by theluckystrike — More tips at [zovo.one](https://zovo.one)
