---
layout: default
title: "Chrome Translate Not Working? Here's How to Fix It"
description: "Fix Chrome's built-in translation feature when it stops working. Troubleshoot missing translate bar, incorrect translations, and language detection issues."
date: 2025-03-14
categories: [troubleshooting, features]
tags: [chrome-translate, translation-fix, language-settings, google-translate]
author: theluckystrike
---

# Chrome Translate Not Working? Here's How to Fix It

Chrome's built-in translation is one of those features you don't think about until it stops working. You visit a page in another language and... nothing happens. No translation bar, no prompt, just a page you can't read. Here's how to fix it.

## Check If Translation Is Enabled

The most common reason Chrome doesn't offer to translate is that the feature is turned off. Go to Settings, then Languages. Make sure "Offer to translate pages that aren't in a language you read" is turned on.

If it was already on, try toggling it off, waiting a few seconds, and toggling it back on. Sometimes this resets the feature.

## Check Your Language Settings

Chrome needs to know which languages you read to know when to offer translation. In Settings, then Languages, make sure your primary language is listed.

Click "Add languages" and add any languages you read fluently. Chrome won't offer to translate pages in languages on your list since it assumes you can read them.

If Chrome isn't translating a specific language, check that you haven't accidentally added it to your languages list or told Chrome to "never translate" that language.

## You Might Have Clicked "Never Translate"

When Chrome offers to translate a page, one of the options is "Never translate [language]." If you clicked this at some point, Chrome will silently ignore all pages in that language.

To fix this, go to Settings, Languages, and look for a list of languages you've told Chrome not to translate. Remove the language you want translated. The phrasing varies by Chrome version — look for something like "Don't offer to translate" or a list of blocked languages.

## You Might Have Blocked a Specific Site

Similarly, Chrome offers a "Never translate this site" option. If you clicked this for a particular website, Chrome won't translate any page on that domain.

Go to Settings, Languages, and look for a list of sites you've blocked from translation. Remove the site you want translated.

## Manually Trigger Translation

If the automatic translation prompt doesn't appear, you can manually trigger it. Right-click anywhere on the page and look for "Translate to [your language]" in the context menu.

Alternatively, click the translate icon in the address bar (it looks like a small page with a language symbol). If you don't see this icon, the page might already be in your language or Chrome might not have detected a foreign language.

## The Page Language Might Be Mislabeled

Sometimes a website's HTML declares one language but the actual content is in another language. Chrome relies on the declared language to trigger translation, so if a page says it's in English but the content is in French, Chrome might not offer to translate.

In this case, right-click and use "Translate to [language]" from the context menu. This forces translation regardless of the declared language.

## Clear Cache and Restart

Like many Chrome features, translation can get stuck. Try:
1. Clear your browsing data (cached images and files)
2. Close Chrome completely
3. Reopen Chrome and try visiting the foreign-language page again

## Check for Extension Conflicts

Some extensions interfere with Chrome's built-in translation. Ad blockers, privacy extensions, and script blockers can sometimes prevent the translation service from working.

Try disabling your extensions temporarily and check if translation works. If it does, re-enable extensions one by one to identify the culprit.

## Chrome's Translation vs Google Translate

Chrome's built-in translation uses Google Translate's engine. If you're having persistent issues with Chrome's built-in feature, you can use Google Translate directly as a workaround:

Visit translate.google.com and paste the URL of the page you want translated. Google Translate will render the entire page in your language.

There's also a Google Translate extension available in the Chrome Web Store that adds translation capabilities with a different interface than the built-in feature.

## When Translation Quality Is Poor

If translation is working but the quality is bad, it might be because:
- The page uses unusual formatting that confuses the translation engine
- The content uses specialized jargon or slang
- The page has a mix of languages

For important content, consider using a professional translation service or the desktop version of Google Translate, which sometimes gives better results for complex text.

## On Chromebooks

Chromebooks use the same Chrome translation feature. All the fixes above apply. Additionally, Chromebooks have a system-level translation feature in ChromeOS settings that can help if Chrome's translation isn't sufficient.

---

*Part of [Chrome Tips](https://theluckystrike.github.io/chrome-tips/) by theluckystrike. More browser guides at [zovo.one](https://zovo.one).*
