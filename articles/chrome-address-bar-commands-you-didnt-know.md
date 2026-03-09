---
layout: post
title: "Chrome Address Bar Commands You Didnt Know"
description: "Discover hidden Chrome address bar commands that can speed up your browsing and boost productivity instantly."
---

Chrome address bar commands you didnt know about can genuinely change how you use your browser. Most people treat the address bar as just a place to type website URLs, but the omnibox (Chrome's official name for it) is a multi-function tool. Here are commands that actually work, with specifics on what each one does.

## Site-Specific Search with Tab-to-Search

Type the name of a site you have visited before — say `amazon.com` — then press Tab. The omnibox changes to say "Search Amazon.com" and you can type your query directly. Chrome auto-registers sites that use OpenSearch, so this works on YouTube, Wikipedia, GitHub, Stack Overflow, Reddit, and thousands of other sites without any setup.

You can also create custom search shortcuts manually. Go to `chrome://settings/searchEngines`, click "Add," and set a keyword. For example:
- **Keyword:** `gh` / **URL:** `https://github.com/search?q=%s` — typing `gh react hooks` searches GitHub directly
- **Keyword:** `yt` / **URL:** `https://www.youtube.com/results?search_query=%s` — `yt lofi beats` goes straight to YouTube results
- **Keyword:** `mdn` / **URL:** `https://developer.mozilla.org/en-US/search?q=%s` — `mdn flexbox` searches MDN Web Docs

The `%s` placeholder gets replaced with whatever you type after the keyword.

## Math and Unit Conversions

Type calculations directly and Chrome shows the answer in the suggestion dropdown before you even press Enter:
- `sqrt(144)` → 12
- `15% of 230` → 34.5
- `2^10` → 1024

Unit conversions work the same way:
- `5 miles in km` → 8.04672 km
- `72 fahrenheit in celsius` → 22.22 °C
- `150 usd in eur` → shows current exchange rate (requires internet)
- `3 cups in ml` → 709.765 ml

These calculations run through Google's search engine, so you need an internet connection for conversions with live rates.

## Chrome Internal Pages (chrome:// URLs)

These are the actually useful `chrome://` pages — every one listed here is real and works:

| Command | What It Opens |
|---------|--------------|
| `chrome://settings` | Main settings page |
| `chrome://extensions` | Manage installed extensions |
| `chrome://history` | Browsing history with search |
| `chrome://downloads` | Downloaded files list |
| `chrome://bookmarks` | Bookmark manager |
| `chrome://flags` | Experimental features (350+ toggles) |
| `chrome://settings/performance` | Memory Saver and Energy Saver controls |
| `chrome://settings/passwords` | Saved passwords and passkeys |
| `chrome://settings/searchEngines` | Custom search shortcuts (see above) |
| `chrome://inspect` | Debug connected devices and service workers |
| `chrome://net-internals` | Network diagnostics — DNS cache, sockets, HSTS |
| `chrome://gpu` | GPU hardware info and feature status |
| `chrome://crashes` | Recent crash reports |
| `chrome://discards` | Tab lifecycle states — which tabs are frozen or discarded |
| `chrome://system` | Full system info dump (Chrome OS and some desktop builds) |
| `chrome://about` | Complete list of all chrome:// pages |

To see every available internal page, type `chrome://about` — it lists all of them, typically 60-80 depending on your Chrome version and OS.

## Quick Tab Search with @tabs

Type `@tabs` followed by a space in the address bar, then start typing the name of an open tab. Chrome filters your open tabs and lets you switch to a match directly. This is far faster than scanning a crowded tab bar when you have 30+ tabs open.

Similarly:
- `@bookmarks` + space + query → searches your bookmarks
- `@history` + space + query → searches your browsing history

These "@" shortcuts were introduced in Chrome 108 and work in all current versions.

## Address Bar as a Quick Launcher

Type action phrases directly and Chrome suggests matching settings:
- `clear browsing data` → jumps to the clear data dialog
- `manage passwords` → opens password settings
- `change language` → opens language settings
- `update chrome` → opens the About page to check for updates

Chrome matches against ~150 common actions. These are not hardcoded commands — Chrome fuzzy-matches your input against its settings pages.

## Navigate Faster with Keyboard Shortcuts

These work while the address bar is focused:
- **Ctrl+L / Cmd+L** — select the address bar and highlight the current URL
- **Ctrl+Enter** — adds `www.` and `.com` to what you typed (type `github`, press Ctrl+Enter, navigates to `www.github.com`)
- **Alt+Enter** — opens your typed URL in a new tab instead of the current one
- **Shift+Delete** — removes a highlighted autocomplete suggestion permanently
- **Down arrow** — move through suggestions, then Enter to select

## Making These Commands Stick

Start with the ones that match tasks you do repeatedly. If you search GitHub 10 times a day, the custom `gh` keyword pays for itself in a week. If you have 40 tabs open, `@tabs` is immediately useful.

The internal `chrome://` pages are worth bookmarking if you troubleshoot often. `chrome://flags`, `chrome://net-internals`, and `chrome://discards` are the three most useful for power users.

Tips from the team behind Tab Suspender Pro and the Zovo extension suite at zovo.one
