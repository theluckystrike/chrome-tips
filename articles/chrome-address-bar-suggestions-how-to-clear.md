---
layout: post
title: "Chrome Address Bar Suggestions How to Clear"
description: "Learn how to clear address bar suggestions in Chrome, including trending searches, history matches, and site suggestions."
date: 2026-03-09
categories: [privacy]
tags: [address-bar, chrome-settings, suggestions, privacy]
author: theluckystrike
---

# Chrome Address Bar Suggestions How to Clear

Chrome's address bar shows up to 8 suggestions in the dropdown as you type. These come from different sources, and each type requires a different approach to clear. Here is a breakdown by suggestion type and how to remove each one.

## Understanding the Suggestion Types

Chrome labels its suggestions with small icons and text to tell you where each one comes from:

| Icon/Label | Source | How to remove |
|------------|--------|---------------|
| Clock icon | Your browsing history | Shift+Delete on the highlighted item, or clear history |
| Star icon | Your bookmarks | Delete the bookmark at `chrome://bookmarks` |
| Tab icon with "Switch to tab" | An open tab | Close that tab |
| Magnifying glass | Google search prediction | Cannot delete — disable search suggestions to hide |
| Globe icon | URL suggestion from Google Trends | Cannot delete — disable search suggestions to hide |

Knowing which type you are looking at tells you exactly how to get rid of it.

## Remove Individual History Suggestions

Highlight the suggestion using arrow keys and press **Shift+Delete** (Windows/Linux) or **Shift+Fn+Delete** (Mac). This only works on history-based suggestions (clock icon). You cannot delete search predictions, bookmark suggestions, or tab matches this way.

## Clear All History-Based Suggestions

Press **Ctrl+Shift+Delete** (Cmd+Shift+Delete on Mac) to open the Clear Browsing Data dialog. Check **Browsing history**, set the time range, and click **Clear data**.

For more targeted clearing, use the Advanced tab in the same dialog. You can separately control:
- **Browsing history** — removes URL suggestions from visited sites
- **Download history** — removes downloaded file entries from `chrome://downloads`
- **Cookies and other site data** — removes login sessions and site preferences
- **Cached images and files** — frees disk space but does not affect suggestions

Only "Browsing history" directly affects address bar suggestions.

## Disable Google Search Predictions

The magnifying glass and globe suggestions come from Google's servers in real time. To stop them:

1. Go to **Settings > Sync and Google services**
2. Turn off **Autocomplete searches and URLs**

This removes all server-side suggestions. Your address bar will only show matches from local history and bookmarks. It also stops Chrome from sending partial queries to Google as you type — a meaningful privacy improvement, since Google otherwise receives every keystroke in the address bar before you press Enter.

## Manage Bookmark Suggestions

Bookmark suggestions (star icon) cannot be removed with Shift+Delete. You have two options:

1. Delete the bookmark: go to `chrome://bookmarks`, search for it, right-click > Delete
2. Move the bookmark to a folder — Chrome still suggests bookmarks from folders, but you can use this to reorganize rather than delete

If you have hundreds of old bookmarks generating unwanted suggestions, consider exporting your bookmarks (three dots menu in bookmark manager > Export bookmarks), editing the HTML file to remove unwanted entries, then re-importing.

## Stop "Switch to Tab" Suggestions

When Chrome detects that a URL you are typing matches an open tab, it shows a "Switch to this tab" suggestion. This cannot be disabled through settings — it is hardcoded behavior. The only way to prevent it is to close the tab.

If you use tab groups, collapsed groups still generate "Switch to tab" suggestions for their contained tabs.

## Trending Searches on New Tab Page

The New Tab page (`chrome://new-tab-page`) shows trending search suggestions below the search bar. These are not the same as address bar suggestions but look similar. To hide them:

1. Click "Customize Chrome" (pencil icon) at the bottom right of the New Tab page
2. Under "Cards," toggle off "Trending searches"

This only affects the New Tab page, not the address bar dropdown.

## Nuclear Option: Guest Mode

If you need to browse without any suggestions at all — no history, no bookmarks, no synced data — open a Guest window from the profile menu. Guest mode is more isolated than Incognito: it has no access to your profile data at all, so the address bar starts completely empty with zero suggestions.

---

Tips from the team behind Tab Suspender Pro and the Zovo extension suite at zovo.one
