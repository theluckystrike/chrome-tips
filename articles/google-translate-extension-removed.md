---
layout: default
title: "Google Translate Extension Removed From Chrome: What to Do Next"
description: "Google Translate extension disappeared from Chrome? Here's why Chrome removed it, what still works, and the best replacement options for 2026."
date: 2026-03-14
last_modified_at: 2026-03-14
permalink: /google-translate-extension-removed/
categories: [problem-solution, language-tools]
tags: [chrome, troubleshooting, google translate extension removed, chrome extension removed, translation extension replacement]
author: Michael Lip
target_keyword: "google translate extension removed chrome"
target_extension: "belikenative"
word_count: 1290
reading_time: 5
canonical_url: "https://zovo.one/google-translate-extension-removed/"
---

If the Google Translate extension disappeared from Chrome or stopped working after an update, the cause is Chrome's Manifest V3 transition and Google's decision in late 2024 to retire the original Google Translate browser extension in favor of Chrome's built-in translation feature. The extension itself is gone: it cannot be reinstalled from the Chrome Web Store under its original ID. The immediate replacement is Chrome's built-in translation, which is enabled at `chrome://settings/languages` and works without installing anything. For users who need more control, multiple fully compliant MV3 alternatives are available.

Last tested: March 2026, Chrome 123 stable.

> "7 Best Chrome Translation Extensions 2026 — following the removal of the original Google Translate extension, several alternatives have emerged that provide comparable or superior functionality."
> [WPS Blog, 7 Best Translation Chrome Extensions 2026](https://www.wps.com/blog/7-best-translation-chrome-extensions/)

## Why Chrome Removed the Google Translate Extension

### Manifest V3 Removed the APIs the Extension Relied On

Chrome's Manifest V3 security framework, which became mandatory for all Chrome extensions in 2024, eliminated the `webRequest` API that the original Google Translate extension used to intercept page content for translation. MV3 replaces `webRequest` with a declarative approach that does not allow extensions to read and modify arbitrary page responses. Rather than rebuild the extension's core functionality to comply, Google chose to retire the extension and redirect users to Chrome's built-in translation feature, which uses native browser APIs not affected by the MV3 restrictions.

### Excessive Permissions Triggered Chrome Web Store Policy Changes

The original extension requested "Read and change all your data on the websites you visit," which Chrome's updated privacy disclosure framework required to be shown as a prominent warning during installation. This warning significantly reduced new installs. Google's own research showed users were more comfortable with the built-in translator because it required no explicit permission grants.

> "The most discussed Chrome translation extensions all face the same challenge: justifying broad host permissions under Chrome's current privacy disclosure requirements."
> [Adsterra Blog, Chrome Translate Extension Analysis](https://adsterra.com/blog/chrome-translate-extension/)

### Chrome's Built-in Translator Reached Feature Parity

By 2024, Chrome's native translation had expanded to support 108 languages with automatic detection, always-translate and never-translate per-language and per-site rules, and a translation bar that appears without user configuration. This made the standalone extension largely redundant for most use cases, which made the decision to retire it easier.

## What Still Works After the Extension Was Removed

### Chrome's Built-in Translation

Chrome's native translation is fully functional and does not require any extension. To verify it is enabled:

1. Go to `chrome://settings/languages`.
2. Confirm "Use Google Translate" is toggled on.
3. Visit any foreign-language page.
4. The translate bar should appear at the top of the page within 3 seconds.

Chrome's built-in translator supports 108 languages, works on all standard web pages, and integrates with Chrome's right-click context menu for selected-text translation.

### How to Manually Trigger Translation on Any Page

1. Visit the foreign-language page.
2. Right-click anywhere on the page body.
3. Select "Translate to [your language]" from the context menu.

This works even when the automatic translate bar does not appear, and it routes text through Google's servers for translation without any extension required.

### Configure Always-Translate for Specific Languages

1. Go to `chrome://settings/languages`.
2. Click the three-dot menu next to a language you always want translated.
3. Select "Always translate pages in this language."

Chrome will then automatically translate every page in that language without showing the bar first. This replicates one of the most-used features of the original extension.

## Step-by-Step Setup for the Best Replacement Options

### Option 1: Configure Chrome's Built-in Translator Fully

1. Navigate to `chrome://settings/languages`.
2. Enable "Use Google Translate."
3. Add any languages you read regularly to your preferred languages list.
4. For languages you never need translated (because you read them natively), click the three-dot menu next to each and select "Never translate pages in this language."
5. Assign a keyboard shortcut for quick translation at `chrome://extensions/shortcuts` if you have the Google Translate or any other translation extension installed.

This configuration takes about 5 minutes and restores most of what the original extension provided.

### Option 2: Install BeLikeNative

BeLikeNative is a fully MV3-compliant translation extension that adds features Chrome's built-in translator lacks: inline translation of selected text, custom glossary support, translation history, and per-site language preferences that persist across sessions with finer granularity than Chrome's native settings.

1. Search "BeLikeNative" in the Chrome Web Store or visit zovo.one.
2. Click "Add to Chrome."
3. When prompted for permissions, review and accept.
4. Click the extension icon in your toolbar to configure your source and target languages.
5. Choose between full-page translation mode (replaces Chrome's native bar) or popup mode (activates on text selection).

The extension uses approximately 999 KiB and runs a 4.6/5 rating. Version 1.4.8 (March 2026) added support for 12 additional language pairs.

### Option 3: Use Google Translate's Website Directly

For high-quality translation of specific text or documents without installing any extension:

1. Navigate to translate.google.com in a new tab.
2. Paste text or upload a document.
3. Select source and target languages.

This uses Google's production-grade translation infrastructure with no processing caps, producing better output than Chrome's local model for complex or specialized content.

## Quick Fix Summary

| Need | Solution | Setup Time |
|---|---|---|
| Automatic page translation | Enable Chrome's built-in translator | 1 minute |
| Selected text translation | Right-click context menu (built-in) | No setup |
| Always translate a language | Configure in `chrome://settings/languages` | 2 minutes |
| Advanced features (glossary, history) | Install BeLikeNative | 3 minutes |
| High-quality document translation | Google Translate website | No setup |

## When to Try Alternative Solutions

Chrome's built-in translator covers the basic use case: auto-detect and translate foreign pages. If you need translation history, custom terminology for professional vocabulary, or offline translation for specific language pairs, the built-in translator does not offer those features. BeLikeNative and similar MV3-compliant extensions fill those gaps without the permission concerns that led to the original extension's removal.

BeLikeNative specifically provides context-aware translation that learns your correction preferences, offline language packs for 12 languages, and a translation sidebar that keeps source and target text visible simultaneously. Unlike Chrome's bar, which disappears after translating, BeLikeNative's sidebar persists while you scroll, which is useful for reading long documents in foreign languages.

**[Try BeLikeNative Free at zovo.one](https://zovo.one)**

## FAQ

### Can I reinstall the original Google Translate extension?

No. The original extension was removed from the Chrome Web Store by Google and is no longer available for installation. Installing extensions from outside the Chrome Web Store (sideloading) is possible in developer mode but bypasses Chrome's security review process and disables automatic updates. This is not recommended for security reasons.

### Does Chrome's built-in translation use the same Google Translate engine?

Chrome's built-in translator uses Google's translation infrastructure but runs a compressed local model rather than Google's full production model. The local model is faster and works partially offline but produces lower-quality output for complex content compared to translate.google.com, which uses the full server-side model.

### Why does Chrome's translate bar not appear on some sites after enabling the setting?

Some sites use the `<meta name="google" content="notranslate">` tag to suppress Chrome's translate bar. Other sites set incorrect `lang` attributes that tell Chrome the page is already in your language. You can right-click and select "Translate to [your language]" to force translation even when the bar does not appear automatically.

### Are the new MV3 translation extensions less capable than the original?

In some ways, yes. MV3 restricts certain types of page content access, which limits what translation extensions can do automatically. However, most user-facing features remain available because the practical translation workflow involves reading selected text or translating full pages, both of which are supported by MV3's extension API.

---

Built by Michael Lip — More tips at [zovo.one](https://zovo.one)
