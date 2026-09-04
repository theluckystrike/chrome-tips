---
layout: default
title: "Telegram Web in Chrome: Shortcuts, Notifications, and Pinning Tips"
description: "Keyboard shortcuts, notification settings, and tab tricks that make Telegram Web faster in Chrome. Save a minute a day with these small fixes."
date: '2026-09-04'
last_modified_at: '2026-09-04'
permalink: /telegram-web-chrome-shortcuts-notifications-pinning/
categories:
- how-to
- productivity
tags:
- telegram
- chrome-shortcuts
- notifications
- tab-management
author: theluckystrike
---

# Telegram Web in Chrome: the shortcuts, notification and pinning tips that save a minute a day

If you use Telegram in a browser tab all day, small friction adds up. You hunt for the chat you want. You miss a message because Chrome never asked to notify you. You close the tab by accident and lose your place. None of this is necessary. A few Chrome and Telegram Web habits fix all of it, and each one takes less than a minute to set up.

## Keyboard shortcuts that actually save time

Telegram Web supports real keyboard shortcuts, not just mouse clicks. Learn these four and you will stop reaching for the trackpad.

**Ctrl+K (Cmd+K on Mac) opens search.** This is the fastest way to jump to any chat, channel, or message. Type a few letters of a contact's name and press Enter. You skip the scroll through your chat list entirely.

**Ctrl+Up / Ctrl+Down (or Alt+Up / Alt+Down) switches between chats.** Instead of clicking down a long list, hold Ctrl (or Alt, depending on your Telegram Web version) and tap the arrow keys to move to the next or previous chat in your list. This is the single biggest time saver if you check several chats in a row.

**Esc closes the current view.** Use it to back out of search, a media viewer, or a settings panel without touching the mouse.

**Ctrl+P pins the current chat's browser tab (via Chrome, not Telegram).** More on this below, but it is worth knowing this shortcut exists in Chrome itself and works on any tab, including your Telegram Web tab.

These shortcuts work whether you are on web.telegram.org's classic layout or the newer "K" version. If one combination does not respond, try the other modifier key (Ctrl vs Alt), since Telegram has changed this between versions.

## Pin the Telegram Web tab in Chrome

A pinned tab shrinks down to just its icon, sits at the far left of your tab bar, and stays put even when you open new tabs or restart Chrome. This means you always know where Telegram is, and you never close it by accident (pinned tabs skip the normal close button; you have to right-click and choose "Unpin" or "Close tab" on purpose).

To pin it: right-click the Telegram Web tab and choose **Pin tab**. That's it. Chrome remembers this the next time you open the browser, as long as you don't clear your session data.

## Turn on desktop notifications properly

Telegram Web asks for notification permission the first time you open it, but a lot of people click "Block" by accident or forget they did. Here is how to check and fix it directly:

1. Open a new tab and go to `chrome://settings/content/notifications`.
2. Look under "Not allowed to send notifications" for `web.telegram.org`. If it's there, remove it.
3. Look under "Allowed to send notifications." If `web.telegram.org` is missing, click **Add** and type it in.
4. Reload your Telegram Web tab.

You can also click the lock or tune icon in the address bar while on web.telegram.org and set notifications to "Allow" directly from there, which is faster if you are already on the page.

One more thing worth checking: Telegram Web has its own in-app notification settings (under Settings > Notifications) that control which chats can notify you at all. Chrome's permission is the master switch; Telegram's settings are the fine-tuning underneath it.

## Install it as a Chrome app

Chrome can install Telegram Web as its own app, separate from your regular browsing tabs. Click the three-dot menu in Chrome, then **Cast, save, and share** (or **More tools** on older versions), then **Install Telegram Web**. This gives you a standalone window with its own icon in your dock or taskbar, its own Chrome profile-independent notifications, and no tab bar or address bar competing for space. It behaves like a real app and it's the closest thing to a native Telegram client without leaving Chrome.

## Use Chrome profiles for multiple Telegram accounts

If you run more than one Telegram account, for example a personal one and a work one, Chrome profiles keep them cleanly separated. Each Chrome profile has its own cookies and login session, so you can be logged into a different Telegram account in each one, with separate pinned tabs and separate notification settings. Switch between them from the profile icon in Chrome's top-right corner instead of logging in and out of the same tab.

## Bots you can use without adding them

Telegram bots have quietly gotten more useful in group chats. Two changes matter here, and they are easy to miss unless you use them.

The first is inline mode, which has been around for a while. Type a bot's username followed by a query, anywhere, in any chat, and the bot answers right there without you ever adding it to that chat. [SplitTabsBot](https://tg.zovo.one/bots/split/) is a good example. It's a group expense ledger: add expenses, see balances, and get a minimal settlement plan, with CSV export when you need the numbers elsewhere. You don't need to add it to a group to try it. Type `@SplitTabsBot 120 pizza @anna @ben` in any chat and it posts the computed split immediately.

The second is newer: Telegram's Bot API 10.0 added Guest Mode, which lets a bot answer when it's @-mentioned in a group it was never added to. This is different from inline mode. Inline mode works by typing the bot's username plus a query, in any chat. Guest Mode works by @-mentioning the bot directly inside a group, and the bot can reply to that mention even though it isn't a member of the group. Our [guide to Telegram's guest mode](https://tg.zovo.one/guides/telegram-guest-mode-without-adding-bot/) walks through the difference in more detail.

[WhisperLockBot](https://tg.zovo.one/bots/whisper/) shows off the inline side of this well. It creates a locked message that only one named person can open, and it posts that message inline into any chat, even one the bot has never joined. Type `@WhisperLockBot @friend your secret text` and it drops a locked card into the chat that only your friend can open.

Neither of these bots needs an install, an admin to add them, or a permissions request. That is the whole point: you get the feature exactly when you need it, without changing anything about the group chat you are already in.
