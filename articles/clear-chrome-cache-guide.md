---
layout: guide
title: "How to Clear Chrome Cache: Every Method on Every Platform (2026)"
description: "How to clear Chrome cache on desktop, mobile, and ChromeOS. Covers keyboard shortcuts, selective cache clearing, DevTools cache, automated clearing, and when clearing cache actually helps."
date: 2026-03-18
last_modified_at: 2026-03-18
permalink: /clear-chrome-cache-guide/
categories: [premium-guide, browser-optimization]
tags: [chrome, clear chrome cache, chrome cache, browser cache, clear browsing data, chrome performance, premium guide]
author: Michael Lip
target_keyword: "clear chrome cache"
word_count: 3850
reading_time: "17 min"
premium: true
last_verified: 2026-03-18
chrome_version_tested: 134
---

> **17 min read** | 3850 words | By Michael Lip

Written by Michael Lip | Last tested: March 2026 | Chrome 134 stable

> **Last verified: March 2026** -- All steps tested on Chrome 134 (latest stable).

# How to Clear Chrome Cache: Every Method on Every Platform

Knowing how to clear Chrome cache is one of those browser skills that sounds simple but gets complicated fast. Chrome maintains multiple caches -- the HTTP cache, the back-forward cache, the DNS cache, the service worker cache, the shader cache, and the code cache -- and the standard "Clear browsing data" dialog only touches one of them. The method you need depends on what problem you are actually trying to solve.

A stale cached CSS file that makes a website look broken requires a different clearing method than a cached API response returning outdated data, which is different again from a cached DNS entry pointing to the wrong server. This guide covers every method for clearing Chrome cache on Windows, macOS, Linux, ChromeOS, Android, and iOS, including the ones you will not find in Chrome's settings menu.

## Table of Contents

1. [When Clearing Cache Actually Helps](#when-clearing-cache-actually-helps)
2. [Desktop: Windows](#desktop-windows)
3. [Desktop: macOS](#desktop-macos)
4. [Desktop: Linux](#desktop-linux)
5. [ChromeOS](#chromeos)
6. [Mobile: Android](#mobile-android)
7. [Mobile: iOS](#mobile-ios)
8. [Keyboard Shortcuts Quick Reference](#keyboard-shortcuts-quick-reference)
9. [Selective Cache Clearing](#selective-cache-clearing)
10. [DevTools Cache Methods](#devtools-cache-methods)
11. [Automated Cache Clearing](#automated-cache-clearing)
12. [Understanding Chrome's Cache Architecture](#understanding-chromes-cache-architecture)
13. [FAQ](#faq)

## When Clearing Cache Actually Helps

Before you clear anything, verify that cache is the actual problem. Clearing cache forces Chrome to re-download every resource from every website you visit, which slows down your browsing until the cache rebuilds itself. Clear cache only when you have a specific reason.

**Clear cache when:**
- A website displays outdated content (old CSS, stale images, wrong layout)
- A web application is stuck in a broken state after a recent update
- You are seeing "ERR_CACHE_MISS" or similar cache-related error messages
- Storage space is critically low and you need to free up several gigabytes
- A website login session is corrupted and sign-in/sign-out is not working
- You are a developer testing changes that Chrome is caching aggressively

**Do not clear cache when:**
- Chrome is running slowly (cache actually speeds things up; try closing tabs instead)
- Websites are not loading at all (this is a network issue, not a cache issue)
- You want to "clean up" Chrome (cache data is intentionally there to improve performance)

Chrome's HTTP cache in version 134 uses a dual-keyed caching system partitioned by top-level site. This means cached resources are isolated per website, preventing cross-site tracking through cache probing. The technical details are documented in the [Chromium HTTP cache partitioning design doc](https://www.chromium.org/developers/design-documents/network-stack/http-cache/). This partitioning means that clearing cache for one site does not affect cache for other sites, and vice versa.

## Desktop: Windows

### Method 1: Settings Menu

1. Click the three-dot menu (top-right) or press `Alt+F`
2. Select "Delete browsing data" (or go to `chrome://settings/clearBrowserData`)
3. Choose a time range: "Last hour," "Last 24 hours," "Last 7 days," "Last 4 weeks," or "All time"
4. Check "Cached images and files"
5. Uncheck other options if you only want to clear cache (not cookies, history, etc.)
6. Click "Delete data"

### Method 2: Keyboard Shortcut

Press `Ctrl+Shift+Delete` to open the Clear Browsing Data dialog directly. This skips the settings navigation and is the fastest way to reach the cache clearing interface.

### Method 3: Hard Refresh (Per-Page)

Press `Ctrl+Shift+R` or `Ctrl+F5` to force Chrome to reload the current page while bypassing the cache. This is faster and more targeted than clearing the entire cache when you only need to refresh one page.

### Method 4: Command Line

Clear Chrome's cache files directly from the file system when Chrome is closed:

```powershell
# Stop Chrome first
Stop-Process -Name "chrome" -Force -ErrorAction SilentlyContinue

# Clear HTTP cache
Remove-Item -Recurse -Force "$env:LOCALAPPDATA\Google\Chrome\User Data\Default\Cache\Cache_Data\*"

# Clear code cache
Remove-Item -Recurse -Force "$env:LOCALAPPDATA\Google\Chrome\User Data\Default\Code Cache\*"

# Clear shader cache
Remove-Item -Recurse -Force "$env:LOCALAPPDATA\Google\Chrome\User Data\Default\GPUCache\*"
```

## Desktop: macOS

### Method 1: Settings Menu

1. Click Chrome in the menu bar and select "Delete Browsing Data" or press `Cmd+Shift+Delete`
2. Alternatively, navigate to `chrome://settings/clearBrowserData`
3. Select time range and check "Cached images and files"
4. Click "Delete data"

### Method 2: Hard Refresh (Per-Page)

Press `Cmd+Shift+R` to reload the current page without cache.

### Method 3: Terminal

```bash
# Close Chrome first
pkill -f "Google Chrome"

# Clear HTTP cache
rm -rf ~/Library/Caches/Google/Chrome/Default/Cache/Cache_Data/*

# Alternative path (depends on Chrome version)
rm -rf ~/Library/Application\ Support/Google/Chrome/Default/Cache/Cache_Data/*

# Clear code cache
rm -rf ~/Library/Application\ Support/Google/Chrome/Default/Code\ Cache/*

# Clear GPU shader cache
rm -rf ~/Library/Application\ Support/Google/Chrome/Default/GPUCache/*
```

### Method 4: Finder

1. In Finder, press `Cmd+Shift+G` to open "Go to Folder"
2. Type `~/Library/Application Support/Google/Chrome/Default/Cache/`
3. Select all files and move to Trash
4. Empty Trash

## Desktop: Linux

### Method 1: Settings Menu

Same as Windows/macOS: `Ctrl+Shift+Delete` or navigate to `chrome://settings/clearBrowserData`.

### Method 2: Terminal

```bash
# Close Chrome
pkill chrome

# Clear HTTP cache
rm -rf ~/.config/google-chrome/Default/Cache/Cache_Data/*

# Clear code cache
rm -rf ~/.config/google-chrome/Default/Code\ Cache/*

# Clear GPU cache
rm -rf ~/.config/google-chrome/Default/GPUCache/*

# Check cache size before clearing
du -sh ~/.config/google-chrome/Default/Cache/
```

### Method 3: Using Chromium Instead of Chrome

If you use Chromium (the open-source version), cache paths are different:

```bash
# Chromium cache location
rm -rf ~/.config/chromium/Default/Cache/Cache_Data/*
```

## ChromeOS

ChromeOS does not provide direct file system access to Chrome's cache directories. Use the browser-based method:

1. Press `Ctrl+Shift+Delete`
2. Select time range
3. Check "Cached images and files"
4. Click "Delete data"

ChromeOS also has a system-level cache that can be cleared through a Powerwash (factory reset), but this erases all local data and is only necessary if the OS itself is malfunctioning. For normal cache clearing, the browser method above is sufficient.

### ChromeOS Linux Container Cache

If you have the Linux development environment (Crostini) enabled and run a Chromium instance inside it:

```bash
# Inside the Linux container
rm -rf ~/.config/chromium/Default/Cache/Cache_Data/*
```

## Mobile: Android

### Method 1: Chrome Settings

1. Open Chrome and tap the three-dot menu (top-right)
2. Tap "Settings"
3. Tap "Privacy and security"
4. Tap "Delete browsing data"
5. Select the "Basic" tab
6. Check "Cached images and files"
7. Select your time range
8. Tap "Delete data"

### Method 2: Android System Settings

1. Open Android Settings
2. Go to "Apps" or "Application Manager"
3. Find and tap "Chrome"
4. Tap "Storage"
5. Tap "Clear Cache"

This method clears Chrome's entire cache without opening Chrome itself. It is useful when Chrome is crashing or unresponsive.

### Method 3: Chrome Lite Mode Cache

If you previously used Chrome's Lite Mode (deprecated in Chrome 100+), residual cache from the data-saver proxy may still exist. The standard cache clearing methods remove this data.

### Storage Check

Before clearing, check how much space Chrome's cache is using:

1. Android Settings > Apps > Chrome > Storage
2. "Cache" shows the current cache size
3. "Data" shows all Chrome data including cache

Do not tap "Clear Data" unless you want to reset Chrome completely (removes all settings, bookmarks, and login sessions).

## Mobile: iOS

### Method 1: Chrome Settings

1. Open Chrome and tap the three-dot menu (bottom)
2. Tap "Settings"
3. Tap "Privacy and Security"
4. Tap "Clear Browsing Data"
5. Check "Cached Images and Files"
6. Select time range
7. Tap "Clear Browsing Data"

### Method 2: iOS Settings

1. Open iOS Settings
2. Scroll down and tap "Chrome"
3. There is no cache-specific clear option here; use Chrome's internal settings instead

### Method 3: Offloading the App

If Chrome's cache is using significant storage:

1. iOS Settings > General > iPhone Storage
2. Find Chrome
3. Tap "Offload App" (keeps data, removes the app binary)
4. Reinstall Chrome from the App Store

This effectively clears the cache while preserving bookmarks and login data that are synced to your Google account.

## Keyboard Shortcuts Quick Reference

| Action | Windows/Linux | macOS | ChromeOS |
|--------|--------------|-------|----------|
| Open Clear Browsing Data | `Ctrl+Shift+Delete` | `Cmd+Shift+Delete` | `Ctrl+Shift+Delete` |
| Hard refresh (bypass cache) | `Ctrl+Shift+R` or `Ctrl+F5` | `Cmd+Shift+R` | `Ctrl+Shift+R` |
| Open DevTools | `F12` or `Ctrl+Shift+I` | `Cmd+Option+I` | `Ctrl+Shift+I` |
| Empty cache + hard reload (DevTools open) | Right-click reload button | Right-click reload button | Right-click reload button |

The "Empty cache and hard reload" option only appears when DevTools is open. Right-click the reload button in the toolbar and select it from the context menu. This clears the entire cache for the current site and forces a full page reload.

## Selective Cache Clearing

Clearing all cache is a sledgehammer approach. Chrome provides several ways to clear cache for specific sites or data types.

### Clear Cache for a Single Site

1. Visit the site you want to clear
2. Click the lock/info icon in the address bar (left of the URL)
3. Click "Site settings"
4. Click "Clear data"

This removes all cached data, cookies, and permissions for that specific site only. All other sites retain their cache.

### Clear Cache via DevTools (Per-Site)

1. Open DevTools (`F12`)
2. Go to the "Application" tab
3. In the left sidebar, under "Storage," click "Clear site data"
4. Check the data types you want to clear
5. Click "Clear site data"

This provides the most granular control. You can selectively clear:
- Cache storage (service worker cache)
- Cookies
- IndexedDB
- Local storage
- Session storage
- Web SQL (deprecated)

### Clear Cache by Data Type

In `chrome://settings/clearBrowserData`, switch to the "Advanced" tab for more granular options:

- **Browsing history**: Your visit history
- **Download history**: Record of downloads (not the downloaded files)
- **Cookies and other site data**: Login sessions, preferences
- **Cached images and files**: The HTTP cache
- **Passwords and other sign-in data**: Saved credentials
- **Autofill form data**: Saved form entries
- **Site settings**: Per-site permissions
- **Hosted app data**: Data from Chrome Apps

## DevTools Cache Methods

For web developers, Chrome DevTools provides specialized cache management tools that go far beyond the standard cache clearing dialog.

### Disable Cache While DevTools Is Open

1. Open DevTools (`F12`)
2. Go to the "Network" tab
3. Check "Disable cache"

With this enabled, Chrome will not use cached responses for any network request while DevTools remains open. This applies only to the tab with DevTools -- other tabs still use cache normally. Source: [Chrome DevTools Network features reference](https://developer.chrome.com/docs/devtools/network/reference/)

### Service Worker Cache Inspection

Modern web applications use service workers to cache resources independently of the HTTP cache. These caches persist even when you clear the standard browser cache.

1. Open DevTools > Application tab
2. Under "Cache Storage" in the left sidebar, expand the entries
3. Each service worker cache is listed by name
4. Click a cache to inspect its contents
5. Right-click entries to delete individual cached items

### Application Cache (Deprecated)

AppCache was deprecated in Chrome 84 and removed entirely in Chrome 93. If you are reading old guides that mention clearing AppCache, that step is no longer relevant in Chrome 134.

### Back-Forward Cache (bfcache)

Chrome's back-forward cache stores complete page snapshots in memory so the back and forward buttons load pages instantly. This cache is not cleared by the standard "Clear browsing data" dialog.

To force-clear the bfcache:
1. Navigate to any other website
2. Close the tab
3. Open a new tab

Or disable bfcache entirely for testing:
1. Go to `chrome://flags`
2. Search for "back-forward cache"
3. Set it to "Disabled"

Source: [web.dev bfcache guide](https://web.dev/articles/bfcache)

### DNS Cache

Chrome maintains its own DNS cache separate from the operating system's DNS cache. To clear it:

1. Navigate to `chrome://net-internals/#dns`
2. Click "Clear host cache"

To also clear the socket pool (which can hold stale connection data):

1. Navigate to `chrome://net-internals/#sockets`
2. Click "Close idle sockets"
3. Click "Flush socket pools"

## Automated Cache Clearing

If you want Chrome to manage cache automatically, several approaches are available.

### Clear Cache on Exit

1. Go to `chrome://settings/content/cookies` (or Settings > Privacy and Security > Cookies and other site data)
2. Enable "Clear cookies and site data when you close all windows"

Note: This clears cookies and site data on exit but does not clear the HTTP cache. Chrome does not have a built-in setting to clear HTTP cache on exit.

### Chrome Extension for Automated Cache

Extensions like "Clear Cache" or "Click&Clean" can clear cache on a schedule or with a single toolbar click. These extensions use the `browsingData` API documented at [developer.chrome.com](https://developer.chrome.com/docs/extensions/reference/api/browsingData).

### Command-Line Automation

Set up a scheduled task to clear cache at regular intervals:

```bash
# macOS/Linux: Clear Chrome cache weekly (add to crontab)
0 3 * * 0 pkill -f "Google Chrome" && sleep 5 && rm -rf ~/Library/Application\ Support/Google/Chrome/Default/Cache/Cache_Data/* && echo "Cache cleared $(date)" >> ~/chrome-cache-clear.log
```

```powershell
# Windows: PowerShell script for scheduled cache clearing
$chromePath = "$env:LOCALAPPDATA\Google\Chrome\User Data\Default\Cache\Cache_Data"
if (Test-Path $chromePath) {
    Stop-Process -Name "chrome" -Force -ErrorAction SilentlyContinue
    Start-Sleep -Seconds 5
    Remove-Item -Recurse -Force "$chromePath\*"
    Write-Output "Cache cleared at $(Get-Date)" | Out-File -Append "$env:USERPROFILE\chrome-cache-clear.log"
}
```

### Chrome Flags for Cache Behavior

Some `chrome://flags` entries affect caching behavior:

- `#enable-parallel-downloading`: Does not affect cache but changes how downloads work
- `#back-forward-cache`: Controls the back-forward cache feature
- `#enable-quic`: Affects how cached QUIC connections are handled

## Understanding Chrome's Cache Architecture

Chrome 134 maintains several independent cache systems, each serving a different purpose. Understanding which cache to clear saves time and avoids unnecessary data loss.

### HTTP Cache (Disk Cache)

The primary cache that stores downloaded web resources (HTML, CSS, JavaScript, images, fonts). Located in the `Cache/Cache_Data/` directory. Size is managed automatically by Chrome based on available disk space, typically capping at 256MB to 1GB. This is what the "Cached images and files" option in Clear Browsing Data removes.

Chrome 134 uses cache partitioning (double-keyed cache), meaning cached resources are partitioned by the top-level frame's origin. A resource cached by `site-a.com` will not be reused when the same resource is loaded by `site-b.com`. This is a privacy feature that prevents cache-based tracking. Source: [Chromium cache partitioning](https://developer.chrome.com/blog/http-cache-partitioning/)

### Code Cache

Stores compiled JavaScript and WebAssembly bytecode so Chrome does not need to re-parse and re-compile scripts on subsequent visits. Located in `Code Cache/`. Clearing this cache forces Chrome to recompile all JavaScript, which causes a one-time performance hit.

### GPU Shader Cache

Stores compiled GPU shaders used for hardware-accelerated rendering. Located in `GPUCache/`. Clearing this cache forces Chrome to recompile shaders, which may cause brief visual stuttering on first page loads.

### Service Worker Cache

Controlled by web applications through the Cache API. These caches are stored in `Service Worker/CacheStorage/`. Unlike the HTTP cache, service worker caches are programmatically managed by the website and can persist indefinitely. They must be cleared through DevTools or by the website's own code.

### Back-Forward Cache (bfcache)

An in-memory cache that stores complete page states (DOM, JavaScript execution state, layout) for instant back/forward navigation. This cache is not persisted to disk and is cleared when Chrome closes or when memory pressure forces eviction.

### DNS Cache

An in-memory cache of DNS lookups. Chrome resolves domain names to IP addresses and caches the results to avoid repeated DNS queries. The cache respects TTL (time-to-live) values set by DNS servers. Clear via `chrome://net-internals/#dns`.

### Preconnect and Prefetch Cache

Chrome speculatively preconnects to servers and prefetches resources based on your browsing patterns. These prefetched resources are stored in the standard HTTP cache. Clearing the HTTP cache also removes prefetched content.

## FAQ

### Does clearing Chrome cache delete passwords or bookmarks?

No. Clearing "Cached images and files" only removes the HTTP cache. Your saved passwords, bookmarks, browsing history, and autofill data are stored separately and are not affected. However, if you also check "Cookies and other site data" when clearing, you will be logged out of websites. Always review the checkboxes in the Clear Browsing Data dialog before clicking Delete. Source: [Google Chrome Help](https://support.google.com/chrome/answer/2392709)

### How often should I clear Chrome cache?

For most users, never. Chrome manages its cache automatically, evicting old entries when space is needed. Routine cache clearing slows down your browsing because Chrome must re-download resources that were previously cached. Only clear cache when you have a specific problem -- a website displaying stale content, a web application stuck in a broken state, or a need to free disk space. Source: [web.dev HTTP caching guide](https://web.dev/articles/http-cache)

### Why is Chrome using so much disk space for cache?

Chrome's cache can grow to 256MB-1GB depending on your browsing habits and available disk space. Heavy use of media-rich websites (video streaming, image galleries, social media) fills the cache faster. Chrome automatically limits cache size based on your available disk space, so you typically do not need to intervene. Check cache size at `chrome://settings/clearBrowserData` by switching to the Advanced tab, which shows the data size for each category.

### What is the difference between clearing cache and hard refresh?

Clearing cache removes all cached files for all websites. A hard refresh (`Ctrl+Shift+R` or `Cmd+Shift+R`) bypasses the cache only for the current page you are viewing. Use hard refresh when one specific page is showing stale content. Use cache clearing when the problem affects multiple sites or when you need to free disk space. Source: [Chrome DevTools documentation](https://developer.chrome.com/docs/devtools/)

### Can I clear cache for just one website in Chrome?

Yes. Click the lock or info icon in the address bar, select "Site settings," then click "Clear data." This removes cached data, cookies, and permissions for that single website without affecting any other site's data. Alternatively, open DevTools (F12), go to the Application tab, and use "Clear site data" for more granular control over what gets cleared. Source: [Chrome DevTools Application panel](https://developer.chrome.com/docs/devtools/progressive-web-apps/)
