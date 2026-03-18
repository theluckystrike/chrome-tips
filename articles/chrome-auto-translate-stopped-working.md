---
layout: default
title: "Chrome Auto-Translate Stopped Working: How to Fix"
description: "Chrome auto-translate stopped working? Get your translation feature back with these proven fixes for 2026. Covers cache corruption, settings, and extension conflicts."
date: 2026-03-14
last_modified_at: 2026-03-14
permalink: /chrome-auto-translate-stopped-working/
categories: [troubleshooting, language-tools]
tags: [chrome, troubleshooting, chrome auto translate stopped working, browser fix, auto-translate]
author: Michael Lip
target_keyword: "chrome auto translate stopped working"
target_extension: "belikenative"
word_count: 1280
reading_time: 6
canonical_url: "https://zovo.one/chrome-auto-translate-stopped-working/"
---

# Chrome Auto-Translate Stopped Working: How to Fix

When Chrome auto-translate stops working, the fastest fix is toggling the translation setting off and back on, then clearing cookies and site data from the last 24 hours. Go to Settings, then Advanced, then Languages, turn off "Offer to translate pages that aren't in a language you read," wait ten seconds, then turn it back on. Follow that with a cache clear and a full Chrome restart. This sequence resolves the majority of auto-translate failures because most problems stem from corrupted language detection files or stale cached API responses rather than missing permissions or deep configuration errors.

If the toggle fix does not work, there are three other causes that cover almost every remaining case: a conflicting extension is blocking the translation API, a corporate firewall is blocking translate.googleapis.com, or Chrome's translation exception lists have grown to include sites or languages you actually want translated.

Last tested: March 2026, Chrome latest stable.

## Why Chrome Auto-Translate Stopped Working

### Language Detection File Corruption

Chrome stores local language detection data in your profile directory. These files identify when a page is in a language other than your primary reading language, which is what triggers the automatic translation offer. When Chrome crashes during a language model update, or when disk space runs low during a cache write, these files can contain invalid entries.

Corrupted detection files cause Chrome to treat foreign-language pages as if they are in your primary language. The translation bar never appears because Chrome believes no translation is needed. Clearing the cache removes the corrupted files and forces Chrome to rebuild them cleanly.

### Translation API Connection Failures

Chrome's auto-translate feature connects to Google's translation servers at translate.googleapis.com. This connection can fail due to network interruptions, VPN configuration changes, corporate firewall rules, or DNS issues. Chrome times out translation requests after a few seconds of no response, and repeated failures can cause Chrome to temporarily disable auto-translate for specific domains.

Corporate networks frequently block translation API endpoints as part of outbound data policies. The failure appears identical to a settings issue, which is why testing in incognito mode and checking network conditions is part of the diagnostic process.

### Site and Language Exception Lists

Chrome maintains lists of languages and websites where you have previously declined translation offers. When you click "Never translate this language" or "Never translate this site," Chrome adds those entries and respects them permanently until you remove them. Over time, these lists grow through accidental clicks or changed preferences.

If auto-translate recently stopped working on specific sites or in specific languages, checking these exception lists is usually the fastest path to a fix.

## How to Fix Chrome Auto-Translate Stopped Working

### Fix 1: Reset Chrome Language Settings

Go to Settings, then Advanced, then Languages. Toggle the "Offer to translate pages that aren't in a language you read" setting off. Wait ten seconds. Toggle it back on.

While in the language settings, review the list of languages you have added. Remove any languages you do not actually read, since Chrome will not offer translation for content in those languages. If you see an unexpected language entry, deleting it restores normal translation behavior for content in that language.

Click the "Manage languages" or language settings link and review the exception lists. Remove any entries for languages or sites where you want auto-translate re-enabled.

### Fix 2: Clear Translation Cache and Cookies

Go to Settings, then Privacy and Security, then Clear Browsing Data. Select the Advanced tab. Choose "Last 7 days" as the time range. Check "Cookies and other site data" and "Cached images and files." Leave browsing history, passwords, and autofill data unchecked since these do not affect translation.

Click Clear Data, then close Chrome entirely using Ctrl+Shift+Q on Windows or Cmd+Q on Mac. Reopen Chrome and visit a foreign-language page to test. A full restart ensures Chrome reinitializes its translation service connections with the fresh cache files.

### Fix 3: Identify and Disable Conflicting Extensions

Extensions that modify network requests are the most common source of translation conflicts. Ad blockers, VPN extensions, privacy tools, and other translation extensions can interfere with Chrome's API calls to Google's translation servers.

Open an incognito window with Ctrl+Shift+N (Windows) or Cmd+Shift+N (Mac) and visit a foreign-language page. Extensions are disabled in incognito by default. If auto-translate works in incognito but not in regular mode, an extension is the culprit.

Return to regular Chrome and go to Settings, then Extensions. Disable extensions one at a time, testing translation after each. Common problem extensions include uBlock Origin with aggressive filter lists, Privacy Badger, and any other translation extension that may be competing with Chrome's built-in service.

### Fix 4: Check Network and Firewall Settings

If you are on a corporate network, behind a VPN, or using parental control software, those systems may be blocking translate.googleapis.com. Open Chrome's Developer Tools with F12, go to the Console tab, and visit a foreign-language page. Look for error messages mentioning translate.googleapis.com, CORS errors, or net::ERR_BLOCKED_BY_ADMINISTRATOR.

If you see blocked requests, the fix requires adjusting your firewall or VPN settings, or testing on a different network. If translation works on your personal mobile hotspot but not on your corporate network, the network configuration is the cause.

### Fix 5: Update Chrome and Restart

Auto-translate bugs introduced in Chrome updates are often fixed in subsequent releases. Click the three-dot menu, then Help, then About Google Chrome. Install any pending updates, then restart the browser. Test auto-translate on a foreign-language page after restart.

## Quick Fix Summary

| Symptom | Most Likely Cause | Fix |
|---------|-------------------|-----|
| Auto-translate bar never appears on any page | Feature disabled in settings | Toggle off and on in Settings, Languages |
| Stopped working on specific languages | "Never translate" exception set | Clear language exceptions in Settings, Languages |
| Stopped working on specific sites | "Never translate this site" exception | Clear site exceptions in Site Settings, Automatic Translation |
| Works in incognito but not regular mode | Extension conflict | Disable extensions one by one to find the culprit |
| Error messages in Developer Tools Console | Network or firewall blocking translation API | Check VPN, firewall, or corporate network settings |
| Stopped after a Chrome update | Translation cache corruption | Clear cache, update Chrome, restart |

## When to Try Alternative Solutions

If Chrome's auto-translate remains unreliable after working through these steps, the underlying problem may be environmental rather than fixable through settings alone. Corporate network restrictions, managed device policies, or persistent extension conflicts can make Chrome's built-in translation consistently unreliable.

BeLikeNative provides translation that does not depend on Chrome's internal auto-detect system. The extension uses its own language detection and translation API connections, so it works even when Chrome's native translation service is blocked or broken. Rather than waiting for a page to trigger auto-translate, you select any text and request translation on demand.

> "The tested 6 best Chrome translation extensions in 2025 showed that third-party extensions with their own API infrastructure outperform Chrome's built-in translation in enterprise and restricted network environments."
>
> Source: [The Tested 6 Best Chrome Translation Extensions in 2025](https://www.swifdoo.com/blog/chrome-translation-extension), swifdoo.com

BeLikeNative also adds features beyond translation, including paraphrasing and writing assistance, which makes it a useful permanent addition rather than just a workaround.

**[Try BeLikeNative Free at zovo.one](https://zovo.one)**

## FAQ

**Does clearing Chrome data delete my bookmarks?**

No. Clearing "Cookies and other site data" and "Cached images and files" preserves your bookmarks, passwords, and browsing history. These are stored separately from translation-related cache files and are not affected by the clearing process.

**Why does translation work on some sites but not others?**

Individual websites can disable Chrome's translation using HTML meta tags or HTTP response headers. Banking sites, government portals, and secure applications commonly block translation. The "This page can't be translated" message appears when this restriction is in place.

**Can I force translation on blocked websites?**

Chrome's built-in translation respects site-level blocking for security reasons. Third-party extensions like BeLikeNative can translate content on blocked sites by using separate translation APIs that operate independently of Chrome's restriction system.

**Which translation extension has the fewest conflicts with other Chrome extensions?**

BeLikeNative is designed to coexist with ad blockers and privacy extensions. It requests only the permissions needed for text processing and does not interact with Chrome's built-in translation service, which eliminates the conflict that commonly occurs between Chrome's native translate and other installed translation extensions.

---

Built by Michael Lip — More tips at zovo.one
