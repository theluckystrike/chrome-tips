---
layout: default
title: "Chrome Translate Bar Not Showing: How to Fix It"
description: "Chrome translate bar not showing up? Fix the missing translation popup in under 5 minutes with these proven steps. Covers all Chrome versions through 2026."
date: 2026-03-14
last_modified_at: 2026-03-14
permalink: /chrome-translate-bar-not-showing/
categories: [problem-solution, language-tools]
tags: [chrome, troubleshooting, chrome translate bar not showing, browser fix, translate bar missing]
author: Michael Lip
target_keyword: "chrome translate bar not showing"
target_extension: "belikenative"
word_count: 1210
reading_time: 5
canonical_url: "https://zovo.one/chrome-translate-bar-not-showing/"
---

Chrome's translate bar disappears when the browser's language detection setting gets turned off, either by a Chrome update, a profile sync conflict, or an extension that overwrites the translation trigger. The fix takes about two minutes: open `chrome://settings/languages`, confirm the "Use Google Translate" toggle is on, restart Chrome, then visit any foreign-language page. That single change restores the bar for most users.

Last tested: March 2026, Chrome 123 stable.

> **Quick fix:** Navigate to `chrome://settings/languages`, scroll to "Google Translate" and enable the toggle. Close Chrome completely (not just the tab) and reopen it. Visit a French, Spanish, or German page to confirm the bar appears.

## Why the Translate Bar Disappears

### Translation Service Registration Breaks During Updates

Chrome registers its translation service through an internal startup routine. Major version updates (Chrome ships roughly every four weeks) sometimes reset this registration when the browser migrates profile data to a new directory structure. The registration queries 47 active language pairs and opens an HTTPS connection to Google's translation servers. If that connection handshake fails on first launch, Chrome marks the service as unavailable and stops offering translation prompts for the rest of that session.

> "The Translator API allows you to translate text with AI models provided in the browser. The model is downloaded the first time a website uses this API."
> [Translation with built-in AI, Chrome Translator API](https://developer.chrome.com/docs/ai/translator-api)

### Language Detection Sees the Page as Matching Your Locale

Chrome scans the first 1,500 characters of visible text to determine page language. If a page mixes two languages, or if the site sets an incorrect `lang` attribute in its HTML (for example, `lang="en"` on a Spanish page), Chrome concludes the content already matches your preferred language and skips the translation offer. This is especially common on international news aggregators that pull content from multiple regional sources into a single page.

### Extensions Overwrite the Translation Trigger

DOM-modifying extensions, including grammar checkers, reading-mode tools, and other translation extensions, sometimes inject content before Chrome's language-detection pass completes. When extension code rewrites the page body or changes text nodes during the DOMContentLoaded window, Chrome's language scanner may analyze the injected placeholder text instead of the original content, resulting in no translation bar.

## Step-by-Step Fixes

### Fix 1: Re-enable the Translation Toggle

1. Type `chrome://settings/languages` in the address bar and press Enter.
2. Under the "Google Translate" section, confirm "Use Google Translate" is toggled on (blue).
3. If it is already on, toggle it off, wait 10 seconds, then toggle it back on.
4. Completely close Chrome from the taskbar or Dock. Do not just close the window.
5. Reopen Chrome and navigate to any foreign-language page such as `bbc.com/russian` or `lemonde.fr`.

The 10-second wait ensures Chrome flushes its language-model cache before reinitializing. Skipping it can cause the browser to reload the same corrupted state.

### Fix 2: Clear Cached Translation Data

1. Press `Ctrl+Shift+Delete` on Windows or `Cmd+Shift+Delete` on Mac.
2. Select the "Advanced" tab in the Clear browsing data dialog.
3. Set time range to "Last 7 days" (not All time, to avoid removing account data).
4. Check "Cached images and files" and "Site settings."
5. Click "Clear data" and wait for the process to complete.
6. Restart Chrome and test on a foreign-language page.

This removes stale language-detection results that Chrome stores per domain. Sites you have previously told Chrome "never translate" keep that setting in site data, so clearing it gives those domains a fresh evaluation.

### Fix 3: Remove Sites From the "Never Translate" List

1. Go to `chrome://settings/languages`.
2. Scroll to the section listing languages and click the three-dot menu next to any language.
3. Select "Languages you've chosen not to translate pages in" or look under "Sites that will never be translated."
4. Remove any entries that should receive the translation bar.

A common accident: clicking the translate bar's "Never translate this site" option when you meant to dismiss it. The site then never shows the bar again until you remove it from this list.

### Fix 4: Test in an Incognito Window to Isolate Extension Conflicts

1. Press `Ctrl+Shift+N` (Windows) or `Cmd+Shift+N` (Mac) to open an incognito window.
2. Visit the foreign-language page that isn't showing the bar.
3. If the bar appears in incognito but not normal mode, an extension is the cause.
4. Return to `chrome://extensions/` and disable extensions one at a time, testing after each.

Focus first on extensions that touch page content: reading-mode tools (Mercury Reader, Readability), other translation extensions (Immersive Translate, Google Translate extension), and grammar checkers (Grammarly, LanguageTool). Re-enable each after confirming it is not the culprit.

> "Most Discussed Translation Extensions for Chrome. Pros and Cons."
> [Adsterra Chrome Translation Extension Analysis](https://adsterra.com/blog/chrome-translate-extension/)

### Fix 5: Reset Chrome's Language Preferences Entirely

If none of the above steps work, the Chrome profile's language data may be corrupted. Go to `chrome://settings/languages`, remove all preferred languages except your primary one, then re-add them in order of preference. This forces Chrome to rebuild its language-detection priority list from scratch without touching any other profile data.

## Quick Fix Summary

| Problem | Fix | Time Required |
|---|---|---|
| Toggle disabled | Re-enable in settings | 1 minute |
| Stale cache | Clear site data | 3 minutes |
| Site in "never translate" list | Remove from list | 2 minutes |
| Extension conflict | Test incognito, disable culprit | 5 minutes |
| Corrupted language list | Remove and re-add languages | 3 minutes |

## When to Try an Alternative Solution

If Chrome's bar still refuses to appear after all five fixes, the issue likely lives in a Chrome profile flag that requires a full profile reset to clear. Rather than losing bookmarks and history, a dedicated translation extension gives you a reliable fallback that operates independently of Chrome's built-in system.

BeLikeNative maintains its own language-detection engine and translation popup that do not depend on Chrome's translation registration routine. Version 1.4.8 (released March 2026) added an updated detection layer that catches mixed-language pages Chrome misses, along with improved conflict resolution when multiple extensions are active. The extension weighs 999 KiB, carries a 4.6/5 rating, and works entirely through Chrome's extension API without touching the browser's core translation service, which means it does not conflict with Chrome's bar if you later get that working too.

**[Try BeLikeNative Free at zovo.one](https://zovo.one)**

## FAQ

### Why does Chrome translate bar not show on some pages but work on others?

Chrome runs language detection per domain and caches the result. If it correctly identifies English on a site you visit often, it stores that result and skips detection on future visits. Pages that mix languages or use incorrect `lang` attributes in HTML can produce false positives, telling Chrome the page matches your locale when it does not.

### Can I force the translate bar to always show?

Not through Chrome's built-in settings. The bar only appears when Chrome detects foreign content. You can right-click any page and select "Translate to English" from the context menu, which triggers translation manually without waiting for the bar.

### Does the fix work on Chrome for Android and iOS?

On Android, the translate bar setting is under Chrome Menu > Settings > Languages > Translate. On iOS, tap the address bar, then the three-dot menu, and look for "Translate." The same toggle logic applies, but the menu paths differ from desktop.

### Will clearing site settings remove my saved passwords?

No. Clearing "Site settings" removes per-domain permissions (camera, microphone, translation preferences) but does not touch passwords, bookmarks, or browsing history. Those live in separate storage that the site-settings clear does not reach.

---

Built by Michael Lip — More tips at [zovo.one](https://zovo.one)
