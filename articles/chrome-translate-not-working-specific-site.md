---
layout: default
title: "Chrome Translate Not Working on a Specific Website: Fix Guide"
description: "Chrome won't translate one particular site? This guide explains why site-specific translation fails and how to fix it with step-by-step instructions."
date: 2026-03-14
last_modified_at: 2026-03-14
permalink: /chrome-translate-not-working-specific-site/
categories: [problem-solution, language-tools]
tags: [chrome, troubleshooting, chrome translate not working specific site, site translation fix, browser translation]
author: Michael Lip
target_keyword: "chrome translate not working specific site"
target_extension: "belikenative"
word_count: 1235
reading_time: 5
canonical_url: "https://zovo.one/chrome-translate-not-working-specific-site/"
---

When Chrome translates most websites correctly but refuses to translate one specific site, the cause is almost always a cached "never translate" preference or a site-level block stored in Chrome's profile data. The fix: go to `chrome://settings/languages`, scroll to the "Sites that will never be translated" section, find the domain, and remove it. After removing it, hard-refresh the page with `Ctrl+Shift+R` (Windows) or `Cmd+Shift+R` (Mac) and the translate bar should reappear within three seconds.

Last tested: March 2026, Chrome 123 stable.

> **Quick fix:** Navigate to `chrome://settings/languages`, look under any language for sites blocked from translation, remove the problem domain, then hard-refresh the page.

## Why Chrome Translate Stops Working on One Specific Site

### Accidentally Blocked the Site From Translation

Chrome's translate bar has a dropdown with a "Never translate this site" option. It sits next to "Never translate [language]" and users frequently tap the wrong one, especially on mobile. Once a domain is added to the "never translate" list, Chrome skips translation offers on every page of that domain, indefinitely and silently. Nothing in the browser UI indicates a site is on this list unless you visit the language settings screen.

> "Chrome stores translation preferences per origin, meaning a single click on 'Never translate this site' blocks the entire domain from receiving translation offers."
> [5 Best Ways to Fix Google Chrome Translate Not Working, Guiding Tech](https://www.guidingtech.com/fix-google-chrome-translate-not-working/)

### The Site Sends a Blocking Meta Tag

Some websites inject a `<meta name="google" content="notranslate">` tag into their HTML. Chrome respects this tag and suppresses the translation bar entirely. This is common on platforms that have their own multilingual system (international e-commerce sites, some news networks, language-learning platforms) and do not want browser translation interfering with their own content delivery. You cannot override this through Chrome settings because the block is coming from the website, not from your profile.

### Incorrect Language Reported in HTML Headers

If a site's HTML `lang` attribute matches your primary Chrome language, Chrome concludes no translation is needed. For example, a Spanish-language site that incorrectly declares `<html lang="en">` looks like English to Chrome's detection system, so no offer to translate appears. Chrome caches this language determination per domain, so even correcting the site would not clear the cached result without user action.

### Cached Language Detection Is Stale

Chrome stores language detection results for visited domains. If Chrome previously visited the site when it was in a different language (during a testing period or before a site redesign), the cached language code persists in the browser profile. Chrome serves the cached result on subsequent visits rather than re-scanning the page content.

## Step-by-Step Fixes

### Fix 1: Remove the Site From the "Never Translate" List

1. Go to `chrome://settings/languages`.
2. Click the dropdown arrow next to any language in your list to reveal the "Sites that will never be translated" subsection.
3. Check all languages for the domain name you are having trouble with.
4. Click the X next to the domain entry to remove it.
5. Return to the site and press `Ctrl+Shift+R` (Windows) or `Cmd+Shift+R` (Mac) for a hard refresh.

If the site does not appear in language settings at all, proceed to Fix 2.

### Fix 2: Clear Site-Specific Data for the Domain

1. Go to `chrome://settings/content/all` in the address bar.
2. Search for the website's domain name in the search box.
3. Click on the domain entry that appears.
4. Click "Clear data" at the top of that page.
5. Navigate back to the site and refresh.

This removes all cached language detection results and site-level preferences for that domain. Chrome will treat the site as if you are visiting it for the first time, scanning the content fresh and offering translation if the language differs from your preference.

### Fix 3: Trigger Translation Manually Through the Context Menu

Even if the translate bar does not appear automatically, you can often force translation:

1. Visit the site in question.
2. Right-click anywhere on the page.
3. Select "Translate to [your language]" from the context menu.

If this option is absent from the context menu, the site is sending a `notranslate` meta tag that Chrome is respecting. Manual context-menu translation is also blocked by that tag.

### Fix 4: Override a Site's notranslate Meta Tag

When a site actively blocks Chrome translation with a meta tag, the only Chrome-native option is to view the page source and copy the text to translate.google.com manually. However, a more practical approach is using the DevTools console:

1. Press `F12` to open DevTools.
2. Select the Console tab.
3. Paste and run this code: `document.querySelector('meta[name="google"]')?.remove()`
4. After running it, right-click the page and select "Translate to [your language]."

This removes the blocking meta tag from the live DOM for your current page session. It does not persist after a refresh, but it confirms whether a meta tag was causing the block.

> "Translate Not Working in Chrome: 5 Quick Ways to Fix."
> [Windows Report Chrome Translation Guide](https://windowsreport.com/translate-not-working-in-chrome/)

### Fix 5: Test Translation in Incognito Mode

1. Press `Ctrl+Shift+N` (Windows) or `Cmd+Shift+N` (Mac).
2. Navigate to the problem site in incognito.
3. Wait for the page to load fully.

If translation works in incognito but not in normal mode, the issue lives in your browser profile data, and clearing site data through Fix 2 will resolve it. If translation also fails in incognito, the problem is on the website's side (notranslate tag or incorrect lang attribute), and a dedicated extension is the practical solution.

## Quick Fix Summary

| Cause | Where to Look | Fix |
|---|---|---|
| Accidentally added to "never translate" list | `chrome://settings/languages` | Remove domain from list |
| Stale cached language detection | Site data in Chrome settings | Clear site data for domain |
| Website sends notranslate tag | DevTools Elements panel | Remove meta tag via console or use extension |
| Incorrect HTML lang attribute | Cannot fix from Chrome | Use extension or Google Translate directly |
| Extension conflict | Incognito test | Disable conflicting extension |

## When to Try Alternative Solutions

If the site uses a `notranslate` meta tag or an incorrect lang attribute, Chrome's built-in translation will always fail for that domain regardless of settings changes. A dedicated translation extension bypasses these server-side signals because it applies its own translation layer rather than using Chrome's native translation trigger.

BeLikeNative does not respect `notranslate` meta tags the way Chrome's built-in translator does. The extension applies its own detection and translation layer, which is particularly useful for sites that block Chrome's native translation with good reason from their side but where you still need to read the content. Version 1.4.8 added improved handling for sites with mixed-language content and better support for websites that use client-side-rendered text that Chrome's language detector misses. Rating: 4.6/5. Size: 999 KiB.

**[Try BeLikeNative Free at zovo.one](https://zovo.one)**

## FAQ

### Can a website legally block Chrome from translating its content?

Yes. Websites control their own content and can use the `<meta name="google" content="notranslate">` tag to request that Chrome not offer translation. This is a legitimate technical mechanism, not a restriction on users. Chrome respects it by default, though extensions can override it.

### Why does Chrome remember "never translate" settings indefinitely?

Chrome stores language and translation preferences per domain in the user profile without an expiration date. This is by design: if you told Chrome you read Japanese and do not want pages translated, it assumes that preference is permanent. The only way to clear it is to explicitly remove the entry from settings or clear all site data.

### My site's language changed after a redesign. How do I make Chrome re-detect it?

Go to `chrome://settings/content/all`, find your domain, and clear its data. Chrome will re-scan the language on your next visit. If Chrome's detection is still wrong due to an incorrect HTML lang attribute, right-click and manually trigger translation.

### Does this fix work the same way on Chrome for Android?

On Android, find the same "never translate" list under Chrome Menu > Settings > Languages. The site-data clearing option is under Chrome Menu > Settings > Site Settings > All Sites. The manual right-click translate option works through a long-press on the page on Android.

---

Built by Michael Lip — More tips at [zovo.one](https://zovo.one)
