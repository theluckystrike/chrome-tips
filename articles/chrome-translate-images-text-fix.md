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
  - q: "How do I fix Chrome not translating text in images?"
    a: "The fastest chrome translate images text fix involves clearing your translation cache and resetting Chrome's OCR permissions. Go to chrome://settings/content/images and ensure \"Sites can show images\" is enabled, then clear cached images and files from chrome://settings/clearBrowserData, and restart Chrome. This resolves issues caused by corrupted translation models or disabled image processing permissions. For additional help, check Zovo's guide on browser troubleshooting."
  - q: "Why does Chrome fail to translate text in images?"
    a: "Chrome fails to translate image text primarily because translation models become corrupted during incomplete downloads or when storage runs out. The translation API downloads models ranging from 15-50MB when you first use image translation, and interrupted downloads cause silent failures. Additionally, OCR permission conflicts prevent text extraction—the OCR engine requires 128MB of RAM and CPU access to process images."
  - q: "What causes the chrome translate images text fix to not work?"
    a: "The chrome translate images text fix fails to work when translation models remain corrupted or OCR permissions stay disabled. Chrome's image translation relies on three interconnected systems that frequently break down: the Translation API, image loading permissions, and OCR processing. If your connection dropped during the initial 15-50MB model download or Chrome ran out of storage space, the models become permanently corrupted without showing error messages."
  - q: "Does Chrome need special permissions to translate images?"
    a: "Yes, Chrome needs specific OCR permissions to process images for text extraction, and these frequently get disabled. The OCR engine requires 128MB of RAM and CPU access to function properly. These permissions get blocked when you restrict image loading on certain sites or when extensions interfere with Chrome's native functionality. Chrome's process isolation can also be too aggressive, preventing the OCR engine from accessing necessary system resources."
  - q: "How do I reset Chrome OCR permissions for image translation?"
    a: "Reset Chrome OCR permissions by visiting chrome://settings/content/images and confirming \"Sites can show images\" is enabled—this controls the OCR functionality. Clear your browsing data to remove corrupted translation models, then restart Chrome completely. If the issue persists, you may need to reset all Chrome settings, as the problem often stems from disabled image processing permissions that simple cache clearing cannot restore."
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