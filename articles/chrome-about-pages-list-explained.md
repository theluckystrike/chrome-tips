---
layout: post
title: "Chrome About Pages List Explained"
description: "The complete list of Chrome internal pages (chrome:// URLs) with explanations of what each one does and when to use it."
---

Chrome has over 60 internal pages accessible through `chrome://` URLs. Type `chrome://about` in the address bar to see the full list for your version. Here are the most useful ones organized by category, with specific explanations of what each page shows and when you would actually need it.

## Settings and Configuration Pages

| Page | What It Does |
|------|-------------|
| `chrome://settings` | Main settings hub — appearance, search engine, startup behavior, privacy, downloads, languages, accessibility |
| `chrome://settings/passwords` | View, search, edit, and export saved passwords and passkeys |
| `chrome://settings/searchEngines` | Add custom search shortcuts (e.g., keyword `gh` for GitHub search) |
| `chrome://settings/performance` | Memory Saver and Energy Saver controls — set inactivity timers, whitelist sites |
| `chrome://settings/adPrivacy` | Privacy Sandbox controls — Topics API, site-suggested ads, ad measurement |
| `chrome://settings/content` | Per-site permissions: camera, microphone, location, notifications, pop-ups, JavaScript |
| `chrome://settings/help` | Shows your Chrome version number and checks for updates |

## Extension and App Management

| Page | What It Does |
|------|-------------|
| `chrome://extensions` | Enable, disable, remove, and configure extensions. Toggle Developer Mode to load unpacked extensions |
| `chrome://apps` | Lists installed Chrome Apps (legacy — Chrome Apps were deprecated in 2022, but some may still appear) |
| `chrome://web-app-internals` | Debug info for installed Progressive Web Apps (PWAs) |

## Browsing Data

| Page | What It Does |
|------|-------------|
| `chrome://history` | Full browsing history with search. Shows date, time, and page title for every visit |
| `chrome://downloads` | Lists all downloaded files with status, file path, and download URL |
| `chrome://bookmarks` | Bookmark manager — organize folders, drag-and-drop reorder, import/export as HTML |

## Diagnostics and Debugging

These pages are where Chrome gets interesting for troubleshooting:

**`chrome://flags`** — Access 350+ experimental features. Each flag has a description, a dropdown to enable/disable, and a link to the Chromium bug tracker for context. Changes require a browser relaunch. If something breaks, the "Reset all" button at the top reverts every flag to default.

**`chrome://net-internals`** — Network diagnostics toolkit:
- **DNS** tab: view and clear Chrome's DNS cache (separate from your OS DNS cache)
- **Sockets** tab: see active connections, close stuck sockets
- **HSTS** tab: query and delete HSTS/HPKP domain entries — useful when a site's HTTPS certificate has changed
- **Events** tab: real-time log of network events for debugging connection failures

**`chrome://gpu`** — Shows whether hardware acceleration is active, which GPU Chrome detected, which graphics features are enabled/disabled, and any driver issues. Essential for diagnosing rendering problems, video playback failures, or WebGL errors.

**`chrome://crashes`** — Lists recent crash reports with timestamps and crash IDs. You can click "Send now" to submit a crash report to Google, or use the crash ID when filing a bug at crbug.com.

**`chrome://discards`** — Shows the lifecycle state of every tab: active, frozen, or discarded. Tabs transition from active → frozen (JavaScript paused) → discarded (tab unloaded from memory). This page shows exactly when each transition happened and why.

**`chrome://inspect`** — Lists inspectable targets: open tabs, service workers, extensions, and connected Android devices. Click "inspect" next to any target to open DevTools for it. The "Devices" section lets you debug Chrome on a USB-connected Android phone from your desktop.

**`chrome://process-internals`** — Shows Chrome's process model: which sites share a process, which get their own, and why. Useful for understanding site isolation behavior.

## System Information

| Page | What It Does |
|------|-------------|
| `chrome://version` | Chrome version, OS, V8 JavaScript engine version, command-line flags, profile path, executable path |
| `chrome://system` | Full system information dump (primarily useful on Chrome OS; limited on Windows/Mac) |
| `chrome://sandbox` | Shows sandbox status for each Chrome process type — all should show "Yes" for security |
| `chrome://policy` | Lists all active enterprise policies applied by your organization. Empty if you are not on a managed device |

## Accessibility and User Facing

| Page | What It Does |
|------|-------------|
| `chrome://accessibility` | Toggle accessibility features per-tab or globally. Shows accessibility tree structure |
| `chrome://interstitials` | Preview Chrome's warning pages (SSL errors, malware, phishing) — useful for documentation or testing |
| `chrome://terms` | Chrome Terms of Service |
| `chrome://credits` | Lists all open-source libraries Chrome uses, with license text |

## Pages You Should Know About

If you only remember 5 internal pages, make it these:

1. **`chrome://flags`** — Try experimental features before they ship
2. **`chrome://net-internals/#dns`** — Clear Chrome's DNS cache when sites will not load (different from flushing your OS DNS)
3. **`chrome://discards`** — See which tabs Chrome has suspended and why
4. **`chrome://settings/performance`** — Configure Memory Saver behavior
5. **`chrome://about`** — The master list when you forget any of the above

---

Tips from the team behind Tab Suspender Pro and the Zovo extension suite at zovo.one
