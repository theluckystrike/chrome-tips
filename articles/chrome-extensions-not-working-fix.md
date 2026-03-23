---
layout: guide
title: "Chrome Extensions Not Working? 12 Proven Fixes for Every Cause"
description: "Chrome extensions not working after an update? Fix broken extensions caused by MV3 migration, profile corruption, policy blocks, and conflicts with these 12 tested solutions."
date: 2026-03-18
last_modified_at: 2026-03-18
permalink: /chrome-extensions-not-working-fix/
categories: [premium-guide, browser-troubleshooting]
tags: [chrome, chrome extensions not working, extension troubleshooting, manifest v3, chrome extensions, browser fix, premium guide]
author: Michael Lip
target_keyword: "chrome extensions not working"
word_count: 3520
reading_time: "15 min"
premium: true
last_verified: 2026-03-18
chrome_version_tested: 134
---

> 15 min read | 3520 words | By Michael Lip

Written by Michael Lip | Last tested: March 2026 | Chrome 134 stable

> Last verified: March 2026 -- All steps tested on Chrome 134 (latest stable). Extension compatibility data verified against Chrome Web Store.

Chrome Extensions Not Working? 12 Proven Fixes for Every Cause

Your Chrome extensions stopped working. Some show grayed-out icons. Others have disappeared from the toolbar entirely. The extension page says "This extension may have been corrupted," or worse, gives no error at all while silently failing.

When Chrome extensions are not working, the fix depends on why they broke. Chrome 134 enforces Manifest V3 (MV3) as the required extension platform, and extensions that have not migrated from the older Manifest V2 architecture are being actively disabled. But MV3 migration is only one of at least six distinct causes for extension failures, and each requires a different repair approach.

This guide walks through every documented reason extensions stop working in Chrome 134, gives you targeted fixes for each scenario, and shows you how to diagnose the root cause so you apply the right fix on the first attempt.

Table of Contents

1. [Quick Diagnostic: Identify Your Issue](#quick-diagnostic-identify-your-issue)
2. [MV2 to MV3 Migration Issues](#mv2-to-mv3-migration-issues)
3. [Extension Conflicts](#extension-conflicts)
4. [Corrupt Chrome Profile](#corrupt-chrome-profile)
5. [Chrome Policy Blocks](#chrome-policy-blocks)
6. [Reinstall vs. Repair Decision Tree](#reinstall-vs-repair-decision-tree)
7. [Developer Mode Debugging](#developer-mode-debugging)
8. [Chrome 134 Specific Changes](#chrome-134-specific-changes)
9. [FAQ](#faq)

Quick Diagnostic: Identify Your Issue

Before applying fixes, determine which category your problem falls into. Open `chrome://extensions` and check each broken extension for these indicators:

| Symptom | Likely Cause | Jump To |
|---------|-------------|---------|
| "This extension is no longer supported" banner | MV2 deprecation | [MV2 to MV3 Migration](#mv2-to-mv3-migration-issues) |
| Extension toggle is grayed out, cannot enable | Chrome policy block | [Chrome Policy Blocks](#chrome-policy-blocks) |
| "Errors" button visible on extension card | Code error or conflict | [Developer Mode Debugging](#developer-mode-debugging) |
| Extension icon missing from toolbar | Toolbar overflow or disabled | [Quick fixes below](#toolbar-icon-missing) |
| All extensions disabled simultaneously | Profile corruption or update | [Corrupt Chrome Profile](#corrupt-chrome-profile) |
| Extension works intermittently | Memory or conflict issue | [Extension Conflicts](#extension-conflicts) |

Toolbar Icon Missing

If an extension is enabled on `chrome://extensions` but its icon does not appear in the toolbar:

1. Click the puzzle piece icon (Extensions menu) in the toolbar
2. Find the extension in the dropdown
3. Click the pin icon next to it

Chrome 134 unpins extensions from the toolbar during certain update scenarios. This is not a malfunction -- the extension is still running, its icon was just removed from the visible toolbar area.

MV2 to MV3 Migration Issues

The transition from Manifest V2 to Manifest V3 is the single largest source of extension breakage in Chrome 134. Google began this migration in 2023 and has progressively disabled MV2 extensions through a phased rollout documented on the [Chrome Extensions developer blog](https://developer.chrome.com/docs/extensions/develop/migrate).

What Changed Between MV2 and MV3

MV3 replaces persistent background pages with service workers, changes how content scripts inject code, and modifies the permissions model. Key changes affecting end users:

- Background scripts now terminate after 30 seconds of inactivity. Extensions that relied on long-running background processes (password managers, VPNs, ad blockers) had to fundamentally redesign how they operate.
- webRequest API was replaced with declarativeNetRequest. This affects ad blockers and privacy extensions. The new API uses a rule-based system with a maximum of 330,000 static rules and 30,000 dynamic rules per extension. Source: [Chrome declarativeNetRequest docs](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest)
- Remote code execution is banned. Extensions can no longer download and execute JavaScript from external servers. Extensions that loaded scripts dynamically must now bundle all code locally.

How to Check if an Extension is MV2 or MV3

1. Go to `chrome://extensions`
2. Enable "Developer mode" (toggle in the top-right)
3. Each extension card now shows its manifest version
4. MV2 extensions will display a warning banner in Chrome 134

What to Do About Disabled MV2 Extensions

Option 1: Find an MV3 alternative. Many popular extensions have released MV3 versions. Search the Chrome Web Store for the extension name -- the developer may have published an updated version under the same name or a slightly different one.

Option 2: Wait for the developer to update. Check the extension's Chrome Web Store listing for recent reviews and update dates. If the last update was before 2025, the extension is likely abandoned and will not receive an MV3 update.

Option 3: Temporarily re-enable MV2 extensions. Chrome 134 still allows MV2 extensions to be force-enabled through enterprise policies (see [Chrome Policy Blocks](#chrome-policy-blocks) section). This is a stopgap measure -- Google will eventually remove MV2 support entirely.

Ad Blocker Specific MV3 Issues

Ad blockers were the most affected extension category in the MV2-to-MV3 transition. The `declarativeNetRequest` API limits that replaced `webRequest` reduced the number of filter rules available. uBlock Origin responded by releasing "uBlock Origin Lite" as its MV3 version, while the original uBlock Origin remains MV2-only.

If your ad blocker stopped working, install the MV3 version:
- uBlock Origin Lite (MV3): Available on Chrome Web Store
- AdGuard Browser Extension: Updated to MV3
- Ghostery: Updated to MV3

Extension Conflicts

Two or more extensions can interfere with each other when they modify the same web pages, intercept the same network requests, or register the same keyboard shortcuts.

Diagnosing Conflicts

The fastest way to find a conflict is to disable all extensions and re-enable them one at a time:

1. Go to `chrome://extensions`
2. Disable every extension
3. Enable the broken extension alone and test it
4. If it works alone, re-enable other extensions one by one
5. When the broken extension breaks again, the last enabled extension is the conflict

Common Conflict Patterns

- Two ad blockers running simultaneously. Each tries to intercept the same network requests, causing pages to load slowly or break. Use only one ad blocker at a time.
- Multiple new tab page extensions. Only one extension can override the new tab page. Chrome uses the most recently installed one and silently disables the others.
- Two password managers. Both try to autofill the same login forms, causing neither to work correctly. Disable Chrome's built-in password manager if using a third-party one.
- VPN extension plus proxy extension. Both attempt to route traffic through their respective proxies. Only one proxy can be active at a time.

Content Script Collisions

Extensions that inject JavaScript into web pages (content scripts) can collide. If two extensions modify the same DOM elements, both may break. Check `chrome://extensions` and click "Details" on each extension to see which URLs they have permission to access. Extensions with broad permissions like "All sites" are more likely to conflict.

Corrupt Chrome Profile

Profile corruption can disable all extensions simultaneously. This happens when Chrome crashes during a profile write operation, when disk space runs out while Chrome is updating extension data, or when antivirus software quarantines files inside the Chrome profile directory.

Signs of Profile Corruption

- All extensions disabled at once with no explanation
- Chrome showing "Profile error occurred" on startup
- Extension settings reset to defaults
- Chrome asking you to sign in again on every launch

Fix 1: Clear Extension State

```bash
macOS: Remove extension state (keeps extensions installed)
rm -rf ~/Library/Application\ Support/Google/Chrome/Default/Extension\ State/

Windows (PowerShell):
Remove-Item -Recurse "$env:LOCALAPPDATA\Google\Chrome\User Data\Default\Extension State"
```

Restart Chrome after removing this directory. Chrome will rebuild the extension state from the installed extension files.

Fix 2: Reset Extension Permissions

Go to `chrome://settings/content` and scroll to the bottom. Click "Additional content settings" and review each permission category. Corrupted permission data can prevent extensions from accessing the resources they need.

Alternatively, reset all settings: Go to `chrome://settings/reset` and click "Restore settings to their original defaults." This resets the startup page, new tab page, search engine, and pinned tabs, disables all extensions, and clears temporary data. It does not delete bookmarks, history, or saved passwords.

Fix 3: Create a New Profile

If the corruption is severe, create a fresh profile:

1. Click your profile icon in Chrome (top-right)
2. Click "Add" to create a new profile
3. Sign in with your Google account
4. Chrome Sync will restore your extensions, bookmarks, and passwords

The old corrupted profile remains on disk. You can manually copy specific files from it if needed.

Chrome Policy Blocks

Enterprise-managed Chrome installations and some security software can block extensions through Chrome policies. These policies override user preferences and cannot be changed through Chrome's settings UI.

Detect Policy Blocks

Open `chrome://policy` in Chrome. This page shows all active policies affecting your browser. Look for these extension-related policies:

- `ExtensionInstallBlocklist` -- Extensions explicitly blocked by policy
- `ExtensionInstallAllowlist` -- Only these extensions are allowed
- `ExtensionSettings` -- Granular per-extension policy controls
- `ExtensionManifestV2Availability` -- Controls whether MV2 extensions can run

If you see policies listed here that you did not set, your IT department, antivirus software, or a browser hijacker has installed them.

Remove Unwanted Policies (Personal Computers Only)

On macOS:

```bash
List all Chrome policies
defaults read com.google.Chrome

Remove a specific policy
defaults delete com.google.Chrome ExtensionInstallBlocklist

Remove all Chrome policies
defaults delete com.google.Chrome
```

On Windows:

```
Open Registry Editor (regedit)
Navigate to: HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Google\Chrome
Delete unwanted policy keys
Also check: HKEY_CURRENT_USER\SOFTWARE\Policies\Google\Chrome
```

On Linux:

```bash
Chrome policies are stored in:
/etc/opt/chrome/policies/managed/
/etc/opt/chrome/policies/recommended/
Remove or edit the JSON files in these directories
sudo ls /etc/opt/chrome/policies/managed/
```

After removing policies, restart Chrome and check `chrome://policy` again to verify they are gone.

Enterprise Environments

If your computer is managed by an organization, you typically cannot remove Chrome policies yourself. Contact your IT administrator and request that the specific extension you need be added to the allowlist. Provide the extension's Chrome Web Store URL and explain the business need.

Reinstall vs. Repair Decision Tree

When an individual extension breaks, you need to decide between repairing it in place or doing a clean reinstall.

Repair in place when:
- The extension has complex configuration or settings you do not want to lose
- The extension stores local data (like notes or bookmarks) that is not synced
- The error is a permissions issue or a conflict with another extension

Clean reinstall when:
- The extension shows "This extension may have been corrupted"
- The extension files have been modified by antivirus or cleanup software
- Repairing does not resolve the issue

Repair Steps

1. Go to `chrome://extensions`
2. Enable "Developer mode"
3. Find the broken extension
4. Click "Repair" if the button is visible (Chrome will re-download and verify the extension)
5. If no Repair button exists, click "Details" and check if the extension has pending updates

Clean Reinstall Steps

1. Go to `chrome://extensions`
2. Remove the broken extension
3. Clear extension remnants:

```bash
macOS: Remove leftover extension data
find ~/Library/Application\ Support/Google/Chrome/Default/Extensions/ -name "EXTENSION_ID" -type d -exec rm -rf {} +

Replace EXTENSION_ID with the actual extension ID from chrome://extensions
```

4. Restart Chrome
5. Reinstall from the Chrome Web Store

Preserving Extension Data During Reinstall

Some extensions store data in Chrome's local storage. Before removing the extension:

1. Go to `chrome://extensions` and find the extension ID
2. Open the extension's background page (if accessible) and export any data
3. Alternatively, back up the extension's data directory:

```bash
macOS: Back up extension data before reinstall
cp -r ~/Library/Application\ Support/Google/Chrome/Default/Local\ Extension\ Settings/EXTENSION_ID ~/Desktop/extension-backup/
```

After reinstalling, restore the backed-up data directory.

Developer Mode Debugging

When standard fixes do not resolve the issue, Developer mode provides detailed error information that pinpoints the exact cause.

Enable Developer Mode

1. Go to `chrome://extensions`
2. Toggle "Developer mode" in the top-right
3. Each extension card now shows additional information: ID, version, manifest version, and an "Errors" button if errors exist

Read Extension Errors

Click the "Errors" button on the broken extension. Chrome displays a log of runtime errors with:
- Error message and stack trace
- Source file and line number
- Timestamp of when the error occurred

Common error patterns and their fixes:

| Error Message | Cause | Fix |
|---------------|-------|-----|
| `Uncaught TypeError: chrome.webRequest is undefined` | MV2 API used in MV3 | Update extension or find MV3 alternative |
| `Service worker registration failed` | Corrupt service worker cache | Clear extension state (see Fix 1 above) |
| `Permissions not granted` | Missing permissions after update | Remove and reinstall extension |
| `net::ERR_BLOCKED_BY_CLIENT` | Another extension blocking requests | Disable other extensions to find conflict |

Inspect Extension Service Worker

For MV3 extensions, the service worker is the background process:

1. On the extension card, click the "service worker" link
2. This opens Chrome DevTools for the extension
3. Check the Console tab for errors
4. Check the Network tab for failed requests
5. Check the Application tab for storage issues

Load an Extension Unpacked (Advanced)

If an extension's Chrome Web Store version is broken but the developer has published a fix:

1. Download the extension source from the developer's GitHub repository
2. Go to `chrome://extensions` and enable Developer mode
3. Click "Load unpacked"
4. Select the extension's directory
5. The extension loads directly from the local files, bypassing Chrome Web Store

This approach is useful for testing beta versions or patches before they reach the Chrome Web Store. Documentation on loading unpacked extensions is available at [developer.chrome.com](https://developer.chrome.com/docs/extensions/get-started/tutorial/hello-world#load-unpacked).

Chrome 134 Specific Changes

Chrome 134 introduced several changes that directly affect extension behavior. Understanding these changes helps distinguish between bugs and intentional platform changes.

MV2 Deprecation Phase 3

Chrome 134 is in Phase 3 of the MV2 deprecation timeline. In this phase:
- MV2 extensions are disabled by default for new installations
- Existing MV2 extensions may be disabled during Chrome updates
- Enterprise policy can still override the disable (`ExtensionManifestV2Availability` set to 2)
- The Chrome Web Store no longer accepts new MV2 extension submissions

Source: [Chrome MV2 deprecation timeline](https://developer.chrome.com/docs/extensions/develop/migrate/mv2-deprecation-timeline)

Side Panel API Changes

Chrome 134 modified how extensions interact with the Side Panel API. Extensions that used `chrome.sidePanel` may need to update their permissions in the manifest. If a side panel extension stopped working, check if the developer has released an update.

Service Worker Lifetime Changes

Chrome 134 extended the service worker idle timeout from 30 seconds to 5 minutes for extensions that register active alarms or maintain open ports. This should fix extensions that previously lost state due to premature service worker termination.

However, extensions that rely on the previous 30-second timeout for cleanup operations may behave differently. If an extension's memory usage has increased since updating to Chrome 134, this lifetime change may be the cause.

Content Security Policy Enforcement

Chrome 134 enforces stricter Content Security Policy (CSP) for extension pages. Extensions that loaded external fonts, images, or scripts in their popup or options pages may break. The fix is on the developer side -- they need to bundle these resources locally or update their CSP declarations.

FAQ

Why did all my Chrome extensions stop working after an update?

Chrome updates can disable extensions for several reasons: MV2 deprecation (extensions using the old Manifest V2 platform are being phased out), profile corruption during the update process, or policy changes. Go to `chrome://extensions` to check each extension's status. If they show an MV2 deprecation warning, search for MV3 alternatives on the Chrome Web Store. If no warning appears, try the profile repair steps in this guide. Source: [Chrome Extensions developer documentation](https://developer.chrome.com/docs/extensions/)

How do I fix Chrome extensions that are grayed out?

Grayed-out extensions are typically blocked by Chrome policies. Open `chrome://policy` to check for active policies. On personal computers, you can remove unwanted policies through the system registry (Windows), defaults command (macOS), or policy files (Linux). On managed enterprise computers, contact your IT administrator to request the extension be allowlisted. Source: [Chrome Enterprise policy list](https://chromeenterprise.google/policies/)

Is uBlock Origin still working in Chrome 2026?

The original uBlock Origin (MV2) is being disabled in Chrome 134 as part of the MV2 deprecation. The developer released uBlock Origin Lite, an MV3-compatible version, which works in Chrome 134 but has fewer filter capabilities due to the `declarativeNetRequest` API limitations. For maximum ad blocking in Chrome, use uBlock Origin Lite or switch to AdGuard's MV3 extension. Source: [Chrome Web Store](https://chromewebstore.google.com/)

Can I force enable a disabled Chrome extension?

Yes, temporarily. On personal computers, you can set the `ExtensionManifestV2Availability` Chrome policy to value 2, which re-enables MV2 extensions. However, Google will eventually remove this override. A more permanent solution is to find an MV3-compatible replacement or switch to a browser that still supports MV2 (Firefox does not have the same deprecation timeline).

How do I check if an extension is causing Chrome to crash?

Open Chrome's Task Manager (Shift+Esc on Windows/Linux, Window > Task Manager on macOS). Sort by Memory or CPU usage. Extensions with runaway memory or CPU consumption are likely causing stability issues. You can also check `chrome://crashes` for crash reports that reference specific extension IDs in the crash signature. Disable suspected extensions one at a time and test stability between each change. Source: [Chromium crash reports documentation](https://www.chromium.org/developers/crash-reports/)
