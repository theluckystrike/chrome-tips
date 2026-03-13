---
layout: default
title: "Chrome Translate Not Working? Here's How to Fix It"
description: "Fix Chrome's built-in translation when it stops working. Covers missing translate bar, incorrect translations, extension conflicts, and language detection issues."
date: 2026-03-14
last_modified_at: 2026-03-14
permalink: /chrome-translate-not-working-fix/
categories: [troubleshooting, language-tools]
tags: [chrome-translate, translation-fix, language-settings, google-translate]
author: Michael Lip
target_keyword: "chrome translate not working fix"
target_extension: "belikenative"
word_count: 1280
reading_time: 6
canonical_url: "https://zovo.one/chrome-translate-not-working-fix/"
---

# Chrome Translate Not Working? Here's How to Fix It

If Chrome translate is not working, start by checking Settings, then Languages, and confirming that "Offer to translate pages that aren't in a language you read" is toggled on. That single setting controls whether Chrome ever shows the translation bar. If it is off, no translation prompt will appear regardless of the page language. Most Chrome translation failures trace back to one of six causes: the feature is disabled in settings, a language is whitelisted by accident, a specific site is blocked, an extension conflict is preventing the translation API from loading, JavaScript is disabled for that site, or Chrome's translation cache is corrupted.

Work through the steps below in order and you will resolve the issue in most cases.

Last tested: March 2026, Chrome latest stable.

## Why Chrome Translate Stops Working

Chrome's translation system depends on multiple services working together. When any one of them fails, the translation bar disappears without explanation. The most common causes:

- Translation is turned off in language settings
- You previously clicked "Never translate this language" and forgot
- You previously clicked "Never translate this site" on a specific domain
- An extension (ad blocker, VPN, or another translation tool) is interfering with the translation API
- JavaScript is disabled for the page, which breaks translation scripts
- Chrome's translation cache has corrupted entries from a crash or update
- The page's HTML declares an incorrect language code, so Chrome does not recognize it as foreign

## Step-by-Step Fix Instructions

### Step 1: Verify Translation Is Enabled

Go to Settings, then Languages. Find the setting labeled "Offer to translate pages that aren't in a language you read" and confirm it is toggled on. If it was already on, toggle it off, wait five seconds, and toggle it back. This sometimes resets the translation service without requiring a full restart.

### Step 2: Check Your Language List

Chrome will not offer to translate content in languages you have listed as languages you read, because it assumes you can read them. In Settings, then Languages, review the list of added languages. Remove any languages that you do not actually read fluently. If you see an unexpected language like Catalan or Welsh that you added by accident, removing it should restore translation offers for pages in that language.

### Step 3: Check the "Never Translate" Lists

Chrome maintains two blocked lists: one for languages and one for specific sites. When you dismiss a translation offer and click "Never translate [language]" or "Never translate this site," those entries persist until you manually remove them.

To clear language-level blocks: go to Settings, then Languages, then look for a section showing languages you have told Chrome not to translate. Remove the blocked languages.

To clear site-level blocks: go to Settings, then Privacy and Security, then Site Settings, then Additional Content Settings, then Automatic Translation. Remove entries for sites where you want translation re-enabled.

### Step 4: Manually Trigger Translation

If the automatic bar does not appear, right-click any text on the page and look for "Translate to [your language]" in the context menu. Alternatively, click the translate icon in the address bar if one appears. This forces a translation attempt regardless of Chrome's automatic detection.

If the context menu option does not appear at all, it typically means the translation feature is disabled or blocked by an extension.

### Step 5: Test in Incognito Mode

Press Ctrl+Shift+N (Windows/Linux) or Cmd+Shift+N (Mac) to open an incognito window. Chrome extensions are disabled in incognito by default. Visit the foreign-language page and check whether translation works there.

If translation works in incognito but not in regular browsing, an extension is causing the conflict. Return to your regular window and go to Settings, then Extensions. Disable extensions one at a time, checking translation after each, until you identify the problem. Common culprits are ad blockers set to aggressive mode, VPN extensions that modify network requests, and other translation extensions that conflict with Chrome's built-in service.

### Step 6: Check JavaScript Settings

Chrome's translation feature relies on JavaScript. If JavaScript is disabled for a site or globally, translation will not work. Go to Settings, then Privacy and Security, then Site Settings, then JavaScript. Confirm it is set to "Sites can use JavaScript." Also check the "Not allowed" list to see if the site you are trying to translate has been explicitly blocked from running JavaScript.

### Step 7: Clear the Translation Cache

Cached translation data can become corrupted after a Chrome update or crash. Go to Settings, then Privacy and Security, then Clear Browsing Data. Select the Advanced tab. Choose "Last 7 days" as the time range and check "Cookies and other site data" and "Cached images and files." Click Clear Data, then restart Chrome completely.

### Step 8: Update Chrome

Chrome translation bugs are fixed regularly in browser updates. Click the three-dot menu, then Help, then About Google Chrome. Chrome will check for and install any available updates. Restart the browser after updating and test translation again.

### Step 9: Reset Chrome Settings

If nothing else works, reset Chrome to its original defaults. Go to Settings, then Reset Settings, then Restore settings to their original defaults. This disables all extensions and clears temporary data but preserves bookmarks, history, and saved passwords. After resetting, test translation before re-enabling extensions.

## Quick Fix Summary

| Problem | Fix |
|---------|-----|
| No translation bar appears | Check Settings, Languages, enable "Offer to translate" |
| Chrome never translates one language | Check and clear the "Never translate language" list |
| Chrome never translates one site | Check and clear the "Never translate site" list in Site Settings |
| Translation works in incognito but not regular mode | Disable extensions one by one to find the conflict |
| No "Translate to" option in right-click menu | Translation feature may be fully disabled; reset settings |
| Translation worked before but stopped after update | Clear browsing data and update Chrome |

## Why This Happens

Chrome's built-in translation system routes requests through Google's translate.googleapis.com infrastructure. When this connection is interrupted by a firewall, corporate network policy, or extension that blocks external API calls, translation fails silently. Chrome does not display a visible error, it simply does not offer to translate.

Corporate networks are a common culprit. Many enterprise firewall configurations block Google API endpoints to control outbound data flow. If Chrome translate stopped working after you joined a new network or connected to a VPN, network-level blocking is the likely cause.

## When to Try Alternative Solutions

If Chrome's built-in translate consistently fails in your environment, a third-party extension like BeLikeNative provides translation that does not depend on Chrome's internal translation service. BeLikeNative uses its own API connections and language detection, which means it works in environments where Chrome's native translation is blocked.

BeLikeNative also adds features Chrome's native translation lacks, including text selection translation for any portion of a page, paraphrasing suggestions, and writing assistance.

**[Try BeLikeNative Free at zovo.one](https://zovo.one)**

## FAQ

**Why doesn't Chrome translate work in incognito mode?**

Chrome's built-in translate works in incognito by default, since it is a native browser feature rather than an extension. However, third-party translation extensions are disabled in incognito unless you explicitly enable them for that mode. If Chrome's native translate is also failing in incognito, check that the "Offer to translate" setting is enabled.

**Why does translation work on some sites but not others?**

Individual websites can disable Chrome's translation using HTML meta tags or HTTP headers. Secure platforms including banking sites, government portals, and medical applications frequently block translation. You will usually see a "This page can't be translated" message when this is the case.

**Can I force Chrome to translate a page in a specific language?**

Yes. Right-click the page, select "Translate to [your language]," and in the translate bar that appears, click the source language dropdown to manually select the correct source language. This overrides Chrome's automatic detection.

**Should I disable some extensions to fix Chrome translate?**

If translation works in incognito but not in regular mode, yes. Disable extensions one at a time and test after each to isolate the conflict. Ad blockers using aggressive filter lists and extensions that modify network requests are the most frequent sources of translation conflicts.

---

Built by Michael Lip — More tips at zovo.one
