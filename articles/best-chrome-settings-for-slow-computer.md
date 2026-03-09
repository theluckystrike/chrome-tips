---
layout: default
title: "Best Chrome Settings for a Slow Computer"
description: "Optimize Chrome settings for better performance on slow or older computers. Every setting explained with clear instructions."
date: 2025-02-19
categories: [performance, settings]
tags: [chrome-settings, slow-computer, performance-optimization, browser-speed]
author: theluckystrike
---

# Best Chrome Settings for a Slow Computer

If your computer is on the slower side, Chrome's default settings aren't doing you any favors. The good news is there are several built-in settings you can adjust to make Chrome more comfortable on modest hardware. No technical expertise needed — just follow along.

## Memory Saver: Your Most Important Setting

This is the single most impactful setting for slow computers. Go to Settings, then Performance, and turn on Memory Saver.

What it does: When you haven't looked at a tab for a while, Chrome frees up the memory it was using. When you click back to that tab, it reloads. This means Chrome is only actively using resources for the tabs you're currently working in.

You can add exceptions for sites you always want to stay active — things like messaging apps or music streaming — but keep the exception list short.

## Preloading: Turn It Off

Go to Settings, then Performance (or Privacy and Security, then Preload Pages, depending on your Chrome version). Set page preloading to "No preloading."

By default, Chrome tries to be clever by loading pages before you click on them, predicting where you'll go next. On a fast computer with plenty of RAM, this feels seamless. On a slow computer, it means Chrome is using precious resources to load pages you might never visit.

## Startup Settings: Start Fresh

Go to Settings, then On Startup. Choose "Open the New Tab page" instead of "Continue where you left off."

Restoring your previous session means Chrome immediately loads every tab you had open last time. If you had 15 tabs open when you last closed Chrome, all 15 start loading at once when you open it again. That's a recipe for a frozen computer for the first few minutes.

Start fresh and open only what you need.

## Hardware Acceleration: Test Both Ways

Go to Settings, then System, and look for "Use hardware acceleration when available."

This is one where you need to experiment. On some older computers, hardware acceleration helps because it offloads work to the GPU. On others, especially those with very old or weak GPUs, it causes stuttering and higher CPU usage.

Try it both ways. Use Chrome for a day with it on, then a day with it off, and go with whatever feels better.

## Background Apps: Turn Them Off

In Settings, then System, disable "Continue running background apps when Google Chrome is closed."

When this is on, Chrome keeps running in the background even after you close the browser window. On a slow computer, you want Chrome to actually stop when you close it so those resources are available for other things.

## Site Permissions: Block What You Don't Need

Go to Settings, then Privacy and Security, then Site Settings. Here you can control what websites are allowed to do. For a slow computer, consider these changes:

**Notifications**: Set to "Don't allow sites to send notifications." Those notification pop-ups and the processes behind them use resources.

**Location**: Set to "Don't allow sites to see your location" unless you specifically need it. Location services run background processes.

**Motion sensors, USB devices, Serial ports, Bluetooth**: Block all of these unless you have a specific need. Most people don't use any of them through Chrome.

**Automatic downloads**: Set to "Don't allow." This prevents sites from downloading multiple files automatically.

## Search Engine Suggestions: Consider Disabling

Go to Settings, then Search Engine, then Manage Search Engines and Site Search. Also check Settings, then You and Google, then Sync and Google Services.

Look for "Autocomplete searches and URLs" and consider turning it off. Every keystroke in the address bar triggers a network request to generate suggestions. On a slow connection or slow computer, this adds up.

## Fonts and Encoding: Keep Defaults

Some guides suggest changing font settings, but this rarely makes a meaningful difference. Keep the defaults here — the performance impact is negligible.

## Chrome Flags for Slow Computers

Type `chrome://flags` into your address bar. These are experimental settings, so only change what's suggested here:

**Smooth Scrolling**: Search for it and set to Disabled if scrolling feels laggy. This removes the smooth scroll animation, making it feel more responsive.

**Heavy Ad Intervention**: Search for it and set to Enabled. This automatically blocks ads that use excessive CPU or network resources.

**Back-Forward Cache**: Make sure this is Enabled (it usually is by default). This caches pages so the back button is instant instead of triggering a full reload.

Don't change other flags unless you know what they do. Some can actually make performance worse.

## Content Settings in Practice

Block auto-playing video: Go to Settings, Privacy and Security, Site Settings, then Additional Content Settings, and look for Sound or Autoplay. Setting this to block prevents videos from auto-playing, which saves significant resources on slow hardware.

Block JavaScript on specific sites: If there are sites you only visit for text content, you can block JavaScript on them individually through Site Settings. This makes those sites load much faster, though some features won't work.

## The Settings That Don't Matter

Some things people recommend that don't actually make a meaningful difference on slow computers:

- Changing the default font (negligible impact)
- Adjusting the page zoom level (no performance impact)
- Changing the download location (doesn't affect browsing speed)
- Enabling dark mode (it's nice, but doesn't improve performance)

Focus your energy on the settings that actually move the needle: Memory Saver, preloading, startup behavior, and background apps.

## Use a Tab Suspender Extension

If you have already turned on Memory Saver and still notice slowdowns, a dedicated tab suspender can help. Tab Suspender Pro automatically detects idle tabs and suspends them on a shorter timer than Chrome's built-in Memory Saver, which means memory gets freed sooner. On a slow computer where every bit of RAM counts, the difference is noticeable. The extension is lightweight and adds almost nothing to Chrome's footprint, so it works well even on machines with limited resources.

## After Changing Settings

Once you've adjusted everything, close Chrome completely and reopen it. Some settings only take full effect after a restart. Then give it a few minutes of normal use to see the difference.

The combination of Memory Saver plus disabled preloading plus fresh startup is typically where people notice the biggest improvement. Adding Tab Suspender Pro on top of that gives your slow computer even more breathing room.

---

*Part of [Chrome Tips](https://theluckystrike.github.io/chrome-tips/) by theluckystrike. More browser guides at [zovo.one](https://zovo.one).*
