---
layout: post
title: "Chrome Address Bar Shortcuts You Should Know"
description: "Keyboard shortcuts for Chrome's address bar that save real time: tab search, custom keywords, quick navigation, and lesser-known tricks."
---

Chrome address bar shortcuts you should know — not a generic list of Ctrl+C and Ctrl+V, but the specific omnibox behaviors that save measurable time if you type URLs and search queries frequently.

## The Shortcuts That Matter Most

### Ctrl+L / Cmd+L — Jump to Address Bar
Instantly selects the address bar and highlights the current URL. This is faster than clicking the address bar with your mouse. Works from anywhere in Chrome, including when a text field on a page has focus (unlike Tab, which would move between form fields).

### Ctrl+Enter — Auto-Complete .com
Type a word like `github` and press Ctrl+Enter. Chrome wraps it into `www.github.com` and navigates there. This saves typing the scheme and TLD for .com sites. Unfortunately, it only works for .com — there is no equivalent for .org, .io, or other TLDs.

### Alt+Enter — Open in New Tab
Type a URL or search query, then press Alt+Enter (Option+Enter on Mac) to open it in a new tab instead of navigating the current tab. This is useful when you want to keep your current page open while opening something new.

### Shift+Delete — Remove Autocomplete Suggestion
When the dropdown shows a suggestion you do not want (an embarrassing URL, a typo you visited once), arrow down to highlight it and press Shift+Delete (Shift+Fn+Delete on Mac). The suggestion is permanently removed from your history.

### Up/Down Arrows — Navigate Suggestions
Arrow keys move through autocomplete suggestions. Press Enter to navigate to the highlighted suggestion, or Alt+Enter to open it in a new tab.

### Ctrl+Backspace — Delete Word
Deletes the word to the left of the cursor in the address bar. Faster than holding Backspace to erase character by character. On Mac, use Option+Delete.

## Tab-to-Search: The Most Underused Feature

When you type a site's domain that Chrome recognizes (one you have visited before that supports OpenSearch), Chrome shows "Press Tab to search [site]." Press Tab, and the omnibox becomes a search box for that specific site.

This works out of the box for: YouTube, Wikipedia, GitHub, Amazon, Stack Overflow, Reddit, and hundreds of other sites.

**Example workflow:** You want to search GitHub for "react hooks tutorial."
1. Type `github.com` in the address bar
2. Press Tab when you see "Search GitHub"
3. Type `react hooks tutorial`
4. Press Enter — you land directly on GitHub search results

No need to navigate to github.com first, find the search bar, and type your query. Saves 3-5 seconds per search, which adds up if you do this 20 times a day.

## Custom Keywords for Any Search

Go to `chrome://settings/searchEngines` and click **Add** under "Site search." Create shortcuts for any URL that has a search function:

| Keyword | Name | URL |
|---------|------|-----|
| `npm` | npm search | `https://www.npmjs.com/search?q=%s` |
| `so` | Stack Overflow | `https://stackoverflow.com/search?q=%s` |
| `maps` | Google Maps | `https://www.google.com/maps/search/%s` |
| `tr` | Google Translate | `https://translate.google.com/?sl=auto&tl=en&text=%s` |
| `caniuse` | Can I Use | `https://caniuse.com/?search=%s` |
| `mdn` | MDN Web Docs | `https://developer.mozilla.org/en-US/search?q=%s` |
| `jira` | Your Jira | `https://yourcompany.atlassian.net/browse/%s` |

After adding these, type `npm lodash` and press Enter — you go directly to npm search results for "lodash." Type `tr bonjour` — Google Translate opens with "bonjour" ready to translate.

The `%s` in the URL gets replaced with whatever you type after the keyword.

## @-Shortcuts for Searching Chrome Itself

Chrome 108 introduced built-in @ shortcuts:

- **`@tabs`** + space + query — search your open tabs by title or URL. Results show "Switch to this tab" actions
- **`@bookmarks`** + space + query — search bookmarks by title or URL
- **`@history`** + space + query — search browsing history

Type `@tabs meeting` to find that Google Meet tab buried among 40 open tabs. Faster than scanning the tab bar or using Ctrl+Tab repeatedly.

## Clipboard URL Detection

If you copy a URL to your clipboard and then click the address bar, Chrome shows a "Paste and go" suggestion at the top of the dropdown. Click it or press Enter to navigate directly — saves the separate paste + Enter step.

Similarly, if you copy non-URL text, Chrome shows "Paste and search" to run it as a search query immediately.

## Address Bar for Quick Actions

Type natural language phrases and Chrome matches them to settings pages:

- `clear cache` → suggests "Clear browsing data"
- `manage extensions` → suggests "Extensions" settings page
- `change password` → suggests "Password Manager"
- `update` → suggests "About Chrome" (which triggers an update check)

Chrome fuzzy-matches against its settings pages, so you do not need the exact wording — just close enough.

## Putting It All Together

The highest-impact shortcuts for most users are:
1. **Ctrl+L** to jump to the address bar without mousing
2. **Tab-to-search** for sites you search frequently
3. **Custom keywords** for 3-5 sites you use daily
4. **@tabs** when you have too many tabs to scan visually
5. **Shift+Delete** to clean up embarrassing or incorrect suggestions

Each one shaves seconds off tasks you perform many times a day. Over a week, that is minutes. Over a year, hours.

---

Tips from the team behind Tab Suspender Pro and the Zovo extension suite at zovo.one
