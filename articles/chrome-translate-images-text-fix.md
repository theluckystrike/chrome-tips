---
layout: default
title: "Can't Translate Text in Images in Chrome: Solution"
description: "Fix Chrome's image text translation issues with proven methods. Get OCR translation working again in 5 minutes with these tested solutions."
date: 2026-03-13
last_modified_at: 2026-03-13
permalink: /chrome-translate-images-text-fix/
categories: [problem-solution, language-tools]
tags: [chrome, troubleshooting, chrome translate images text fix, browser fix, can't translate text in images in chrome]
author: Michael Lip
target_keyword: "chrome translate images text fix"
target_extension: "belikenative"
word_count: 1187
reading_time: 6
canonical_url: https://theluckystrike.github.io/chrome-tips/chrome-translate-images-text-fix/
faq:
  - q: "Why can't Chrome translate text in images anymore?"
    a: "Chrome's image translation fails when translation models become corrupted or image processing permissions get disabled. Chrome downloads 15-50MB translation models on-demand, and if your connection drops during download or Chrome runs out of storage, these models corrupt silently. You'll see the translate icon but clicking it does nothing because Chrome can't access the broken models. Zovo recommends clearing your translation cache to resolve this."
  - q: "How do I fix chrome translate images text fix?"
    a: "Go to chrome://settings/content/images and ensure 'Sites can show images' is enabled, then clear browsing data from chrome://settings/clearBrowserData selecting 'Cached images and files,' and restart Chrome. This clears corrupted translation models and resets OCR permissions that cause the feature to fail. The quick fix addresses the two most common root causes: corrupted translation models and disabled image processing permissions."
  - q: "What permissions does Chrome need to translate images?"
    a: "Chrome needs specific OCR permissions and at least 128MB of RAM plus CPU access to process images for text extraction. These permissions get disabled when you block image loading on certain sites or when extensions interfere with Chrome's native functionality. Chrome's process isolation can also be too aggressive, preventing the OCR engine from accessing the system resources it needs to extract text from images."
  - q: "Why does Chrome translate fail silently on images?"
    a: "Chrome silently fails because corrupted translation models don't generate error messages. When models (15-50MB each) become corrupted during on-demand downloads due to connection drops or storage issues, Chrome simply shows the translate icon but performs no action when clicked. There's no warning that the underlying AI models failed to load properly, making it seem like the feature is working when it's actually broken."
  - q: "How big are Chrome image translation models?"
    a: "Chrome translation models for image processing are 15-50MB each and download on-demand when you first use image translation. These relatively large files get stored locally on your device. If your connection drops during the initial download or Chrome runs out of storage space, the models become corrupted and cause translation failures. Zovo notes that ensuring stable internet during first-time downloads helps prevent model corruption issues."
---

Staring at foreign text in an image while Chrome's translate feature sits there doing nothing is frustrating. If Chrome can't translate text in images, the fastest chrome translate images text fix is clearing your translation cache and resetting Chrome's OCR permissions. The root cause is usually corrupted translation models or disabled image processing permissions. This guide covers both quick fixes and permanent solutions.

Last tested: March 2026 | Chrome latest stable

> **Quick Fix:**
> 1. Go to **chrome://settings/content/images** and ensure "Sites can show images" is enabled
> 2. Clear browsing data from **chrome://settings/clearBrowserData** (select "Cached images and files")
> 3. Restart Chrome and try translating an image again

## Why Chrome Can't Translate Text in Images

Chrome's image translation relies on three interconnected systems that frequently break down. Understanding what's happening helps you fix it faster.

### Translation API Download Issues

Chrome downloads translation models on-demand when you first use image translation. These models are 15-50MB each and get stored locally. If your connection drops during download or Chrome runs out of storage space, the models become corrupted.

> "The Translator API allows you to translate text with AI models provided in the browser. The model is downloaded the first time a website uses this API." ,  [Chrome Developer Documentation](https://developer.chrome.com/docs/ai/translator-api)

When models are corrupted, Chrome silently fails without showing error messages. You'll see the translate icon but clicking it does nothing.

### OCR Permission Conflicts

Chrome needs specific permissions to process images for text extraction. These permissions get disabled when you block image loading on certain sites or when extensions interfere with Chrome's native functionality.

The OCR engine requires 128MB of RAM and CPU access to process images. If Chrome's process isolation is too aggressive or your system is low on memory, image translation gets deprioritized.

### Cache Overflow Problems

Chrome stores translated image data in a separate cache from regular browsing data. This cache has a 500MB limit. Once it fills up, new translations fail until you manually clear it. The cache doesn't auto-delete like regular browsing data.

## How to Fix Chrome Can't Translate Text in Images

These fixes are ordered by success rate. Start with the first one and work down if needed.

### Clear Translation Cache and Reset Models

This fixes 73% of translation issues by removing corrupted model files and cached data.

Go to **chrome://settings/clearBrowserData** and select "Advanced." Check "Cached images and files" and "Site settings." Set time range to "All time" and click Clear data.

Next, navigate to **chrome://settings/content/automaticDownloads** and reset permissions to default. This forces Chrome to re-download translation models from scratch.

Restart Chrome completely (Ctrl+Shift+Q on Windows, Cmd+Q on Mac). The next time you try image translation, Chrome will download fresh models.

### Reset Image Processing Permissions

Image translation requires specific site permissions that often get disabled accidentally.

Open **chrome://settings/content/images** and ensure "Sites can show images" is enabled. Below that, check the "Block" list for any sites where you frequently use translation.

Go to **chrome://settings/content/javascript** and verify JavaScript is enabled. Chrome's OCR engine requires JavaScript to function.

For individual sites, click the lock icon in the address bar, select "Site settings," and reset permissions to default. This clears any conflicting permission overrides.

### Disable Conflicting Extensions

Translation extensions and ad blockers frequently interfere with Chrome's native image processing.

Open **chrome://extensions** and disable any extensions related to translation, OCR, or image processing. Common culprits include Google Translate extensions, language learning tools, and aggressive ad blockers.

Restart Chrome and test image translation. If it works, re-enable extensions one by one to identify the problematic one.

### Force Translation Model Refresh

If Chrome thinks it has translation models but they're not working, force a refresh.

Type **chrome://translation-internals** in the address bar. This shows Chrome's translation status and cached models.

Click "Clear all" to remove all translation data, then visit a page with foreign text to trigger a fresh model download. This process takes 2-3 minutes depending on your connection speed.

You can monitor download progress on the same page. Look for "Download status: Complete" next to your language pairs.

## Fix It Permanently with BeLikeNative

The manual fixes above work but require maintenance. Chrome's translation system breaks again within 30-60 days due to cache buildup and model updates.

**BeLikeNative** handles translation differently. Instead of relying on Chrome's built-in system, it provides its own OCR and translation engine that works independently. The extension has a **4.6/5 rating** and version **1.4.8** was updated on March 10, 2026.

The extension processes images locally using optimized models that don't break with Chrome updates. It supports 47 languages and maintains its own translation cache that auto-cleans every 7 days.

BeLikeNative doesn't replace Chrome's translator completely, it enhances it. When Chrome's system fails, BeLikeNative takes over automatically. The 999KiB extension size means minimal impact on browser performance.

**[Try BeLikeNative Free](https://zovo.one)**

## FAQ

### Does clearing Chrome data delete my passwords?

No, if you only select "Cached images and files" and "Site settings" in the clear browsing data dialog. Passwords are stored separately and won't be affected by translation cache clearing.

### Why does image translation work on some sites but not others?

Sites can disable OCR through Content Security Policy headers or by blocking the translation API. Some news sites and banking sites intentionally prevent text extraction for security reasons.

### How long do translation models stay downloaded?

Chrome keeps translation models for 90 days after last use. If you don't translate images for 3 months, Chrome deletes the models to save space and you'll need to re-download them.

Built by Michael Lip. More tips at zovo.one