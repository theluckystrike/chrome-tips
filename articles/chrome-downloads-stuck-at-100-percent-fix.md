---
layout: default
title: Chrome Downloads Stuck at 100 Percent Fix
description: Chrome download shows 100% complete but won't finish? Learn practical solutions to fix stuck downloads in Chrome, from clearing history to checking settings.
date: 2026-01-15
permalink: chrome-downloads-stuck-at-100-percent-fix
---

# Chrome Downloads Stuck at 100 Percent Fix

You're downloading an important file—a work document, software installer, or that presentation you need for tomorrow's meeting. The progress bar steadily climbs and finally hits 100%. You wait. And wait. But Chrome keeps showing the download as "complete" without actually giving you the file. This is one of the most frustrating issues Chrome users face, and it happens more often than you'd expect.

The good news is that this problem is usually fixable. There are several proven methods to get your downloads moving again, and we'll work through them from simplest to most involved.

## What Causes Downloads to Get Stuck

Before we look at solutions, it helps to understand what's happening behind the scenes. When Chrome reports a download as complete but the file never appears, several things could be causing the problem.

Chrome downloads files in stages. First, it downloads to a temporary location, then moves the file to your chosen download folder. If something interrupts this final transfer, Chrome may incorrectly report the download as finished while the file remains stuck in limbo.

Other common causes include antivirus software scanning downloaded files and blocking the final transfer, browser extensions interfering with the download process, corrupted download history or cache, and interrupted connections that Chrome doesn't handle gracefully.

Now let's fix it.

## Check Your Download Folder First

Before trying any technical fixes, verify that the file isn't already sitting in your downloads folder. Sometimes the file is there, but you might be looking in the wrong place or the file has a different name than expected.

On Windows, press the Windows key plus R to open the Run dialog, type `%userprofile%\Downloads`, and press Enter. Browse through the files in your downloads folder and look for what you were downloading.

On Mac, open Finder and click "Downloads" in the sidebar. Check whether your file is there. If you see a file with a `.crdownload` extension, that means the download didn't actually complete—Chrome uses this extension for temporary files during active downloads.

## Clear Chrome's Download History

Chrome maintains a history of all downloads, and this history can sometimes become corrupted. When that happens, Chrome may incorrectly report downloads as complete even when they aren't. Clearing this history forces Chrome to properly finalize future downloads.

To clear your download history, press Ctrl+H on Windows or Cmd+Y on Mac to open the History page. Click "Clear browsing data" on the left sidebar. Select the "Advanced" tab and check only "Download history." Set the time range to "All time" and click "Clear data." Restart Chrome and try downloading your file again.

This simple step resolves the issue in many cases, so it's a good place to start.

## Disable Antivirus Scanning Temporarily

If you use Windows Defender, McAfee, Norton, or any other antivirus program, it might be scanning downloaded files and preventing Chrome from completing the transfer. This is especially common with executable files and compressed archives.

To test if your antivirus is causing the problem, temporarily disable real-time protection. On Windows Defender, open Windows Security, go to "Virus & threat protection," click "Manage settings," and turn off "Real-time protection." For third-party antivirus software, look for a setting called "Scan downloads" or "File shield" and disable it temporarily.

After disabling the antivirus, try downloading the file again. If the download completes successfully, you've found the culprit. Remember to re-enable your antivirus protection after testing—this is only a diagnostic step.

## Check for Problematic Extensions

Browser extensions can interfere with downloads in unexpected ways. Some download managers, ad blockers, and VPN extensions have been known to cause stuck downloads.

To test if an extension is causing the problem, click the three dots in Chrome, go to "More tools," and select "Extensions." Toggle off all extensions and try downloading your file again. If the download works, enable extensions one by one to identify which one is causing the issue.

For users who want a cleaner browsing experience without extension conflicts, Tab Suspender Pro can help manage open tabs more efficiently. It reduces browser clutter and can prevent conflicts that arise from having too many extensions active at once.

## Reset Chrome Settings

If the above solutions haven't worked, resetting Chrome to its default settings can fix deeper issues that might be causing stuck downloads.

Click the three dots in Chrome and select "Settings." Scroll down and click "Advanced." Under "Reset and clean up," click "Reset settings to their original defaults" and confirm the reset. This won't delete your bookmarks or passwords, but it will reset your startup pages, search engine, and pinned tabs.

After resetting, restart Chrome and try downloading again.

## Find the Temporary File Manually

Chrome downloads files to a temporary location before moving them to your final destination. If the download got stuck, the file might still exist in this temporary location.

On Windows, go to `C:\Users\[YourUsername]\AppData\Local\Temp` and look for files with the `.crdownload` extension. If you find your file, copy it to your downloads folder and remove the `.crdownload` extension.

On Mac, open Finder, press Cmd+Shift+G, type `/private/var/folders/`, and press Enter. Search for your filename or look for `.crdownload` files. This method can save you from re-downloading large files, though it requires some digging.

## Use Chrome's Built-in Download Manager

Chrome has a built-in download manager that can help with stuck downloads. Press Ctrl+J on Windows or Cmd+Shift+J on Mac to open the Downloads page. Find your stuck download and try clicking "Resume" or cancel it and download again. If those options don't work, click the three dots next to the download and select "Remove from list," then try downloading again.

## Preventing Future Stuck Downloads

Once you've fixed the current issue, a few preventive measures can stop this from happening again.

Keep Chrome updated—older versions sometimes have download bugs that get fixed in newer releases. Don't close Chrome while a download is in progress; let it finish completely. Check your internet connection before starting large downloads, as unstable connections can cause incomplete transfers. Finally, download to your local drive first rather than network drives, then move the file afterward if needed.

## What If Nothing Works

If you've tried all these solutions and downloads are still stuck, consider trying a different browser temporarily to download the file. Check if your hard drive is full, as that can prevent files from being saved. Try downloading a different file to see if the issue is specific to one file. On Windows, right-click the Chrome icon and select "Run as administrator" to see if permission issues are causing the problem.

Chrome downloads stuck at 100 percent are annoying, but they're usually fixable. Start with the simplest solutions and work your way through the more involved fixes. With these methods, you should be able to get your files downloaded and moving again.

Built by theluckystrike — More tips at [zovo.one](https://zovo.one)
