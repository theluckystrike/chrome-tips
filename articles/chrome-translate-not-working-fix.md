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

Sometimes, the issue isn't with Chrome itself but with the extensions you have installed. Certain ad blockers, script blockers, or even privacy-focused extensions can inadvertently interfere with Chrome's built-in translation service. These extensions might block the scripts required for the translation bar to appear or prevent the browser from communicating with Google's translation servers.

To troubleshoot this, try opening the problematic page in an Incognito window (Ctrl+Shift+N or Cmd+Shift+N). By default, extensions are disabled in Incognito mode. If translation works there, you know one of your extensions is the culprit. You can then go back to your main window, disable all extensions, and re-enable them one by one to identify which one is causing the conflict.

While some extensions can cause issues, others are designed to help your browser run more efficiently. For instance, if you frequently have many tabs open while researching across different languages, your browser's performance might degrade, potentially affecting features like translation. Using a tool like **Tab Suspender Pro** can help. It automatically suspends inactive tabs, freeing up system resources and ensuring that your active tabs—including the ones you're trying to translate—have the memory and CPU power they need to function correctly. This can lead to a smoother, more reliable translation experience.

## The Role of JavaScript

Chrome's translation feature relies heavily on JavaScript. If you have disabled JavaScript for a specific site or globally in your Chrome settings, the translation feature will not work. To check this, go to Settings, then Privacy and Security, then Site Settings. Look under the "Content" section for JavaScript and ensure it is set to "Sites can use Javascript." Also, check the "Customized behaviors" section to see if the site you're trying to translate is on the "Not allowed to use Javascript" list.

## Update Chrome to the Latest Version

Google frequently pushes updates to Chrome that include bug fixes for built-in features like translation. If you're running an outdated version of the browser, you might be experiencing a bug that has already been resolved in a newer release. To check for updates, click the three-dot menu in the top-right corner, go to Help, and select "About Google Chrome." Chrome will automatically check for and install any available updates. Restart the browser once the update is complete and see if the translation feature is back to normal.

## Reset Chrome Settings

If none of the above steps work, you might need to reset your Chrome settings to their original defaults. This can resolve deeper configuration issues that might be preventing translation from working. Note that this will reset your startup page, new tab page, search engine, and pinned tabs. It will also disable all extensions and clear temporary data like cookies. Your bookmarks, history, and saved passwords will not be deleted.

To reset Chrome, go to Settings, then "Reset settings" in the left-hand sidebar, and click "Restore settings to their original defaults." Confirm the action and then check if the translation feature is working again.

## Conclusion

Chrome's translation feature is incredibly useful for navigating the multilingual web. When it fails, it's usually due to a simple setting or a minor conflict. By systematically checking your language settings, site-specific permissions, and extension interactions, you can almost always get it working again quickly. Remember that keeping your browser optimized with tools like **Tab Suspender Pro** can also contribute to a more stable environment for all of Chrome's built-in features.

Tips from the team behind Tab Suspender Pro and the Zovo extension suite at zovo.one
