---
layout: post
title: "Chrome Address Autofill How to Manage"
description: "Learn how to manage Chrome address autofill: add, edit, delete saved addresses, fix common problems, and control sync across devices."
date: 2025-03-09
categories: [tips, privacy]
tags: [chrome-address-autofill, chrome-autofill, address-management, chrome-tips]
author: theluckystrike
---

# Chrome Address Autofill How to Manage

Chrome saves physical addresses you enter into web forms and offers to fill them in automatically on future sites. It stores name, company, street address, city, state, ZIP, country, phone number, and email — and syncs them across devices if you are signed into a Google account. Here is how to control all of it.

## Where to Find Your Saved Addresses

Go to **Settings > Autofill and passwords > Addresses and more** (or type `chrome://settings/addresses` in the address bar). This page lists every address Chrome has saved, with a preview showing the name and first line of each address.

If you are signed into Google, you will also see a link to **Google Account addresses** — these are stored server-side and may include addresses from Google Pay, Google Maps, and other Google services. Chrome's local addresses and Google Account addresses are separate stores that both feed into autofill suggestions.

## Add a New Address

Click the **Add** button on the addresses page. Fill in the fields:
- Full name
- Company (optional)
- Street address (supports line 1 and line 2 for apartment/suite numbers)
- City
- State/Province
- ZIP/Postal code
- Country
- Phone number
- Email address

Click **Save**. The address is now available for autofill on any site. If sync is enabled, it appears on your other devices within a few minutes.

**Tip:** Chrome does not support address labels (like "Home" or "Work") in the autofill UI. If you have multiple addresses, the only way to distinguish them is by the content itself. Put a distinctive company name or the city in a prominent field to tell them apart at a glance.

## Edit an Existing Address

Click the three-dot menu (or pencil icon) next to the address you want to update. Edit any field and click **Save**. Common reasons to edit:
- You moved and your street address changed
- A ZIP code was entered incorrectly (autofill will suggest the wrong address for forms that match on ZIP)
- Your phone number changed

Edits sync across devices if you have sync enabled.

## Delete an Address

Click the three-dot menu next to the address and select **Remove**. The address is removed from Chrome immediately. If sync is enabled, it is also removed from your other devices.

If you want to keep the address in your Google Account but remove it from Chrome locally, turn off address sync: **Settings > Sync and Google services > Manage what you sync > uncheck Addresses and more**.

## Fix "Autofill Not Working" Issues

**Autofill toggle is off.** Go to **Settings > Autofill and passwords > Addresses and more** and make sure "Save and fill addresses" is toggled on. This gets accidentally turned off by extensions and settings resets.

**The website uses non-standard form fields.** Chrome matches form fields by their HTML `name`, `id`, and `autocomplete` attributes. If a site uses custom JavaScript input fields or unconventional attribute names, Chrome cannot detect them as address fields. This is a website problem, not a Chrome problem — you will need to type manually on that site.

**An extension is interfering.** Password managers (1Password, Bitwarden, LastPass) and form-filling extensions often conflict with Chrome's built-in autofill. They intercept form fields before Chrome can. To test: open `chrome://extensions`, disable your password manager, reload the page, and try autofill again. If it works, you need to choose between Chrome autofill and your extension's autofill — running both causes unpredictable behavior.

**Autofill suggests the wrong address.** Chrome picks the most recently used address by default. You cannot explicitly set a "default" address, but you can delete the wrong one so only the correct one remains as a suggestion.

**Autofill fills fields incorrectly (e.g., puts city in the state field).** This happens when websites use ambiguous field names. Chrome does its best to match, but gets it wrong on roughly 5-10% of sites. No fix on your end — report the issue to the website.

## Security Considerations

Chrome stores autofill addresses **unencrypted** in your browser profile (in a SQLite database at `~/Library/Application Support/Google/Chrome/Default/Web Data` on macOS, or `%LOCALAPPDATA%\Google\Chrome\User Data\Default\Web Data` on Windows). Anyone with access to your computer can read your saved addresses.

Mitigations:
- Use **separate Chrome profiles** if you share a computer — each profile has its own autofill data
- Lock your computer when stepping away (Win+L on Windows, Ctrl+Cmd+Q on Mac)
- If you are on a shared or public computer, **never save addresses** — use Incognito mode instead

Unlike passwords, Chrome does not require re-authentication to view saved addresses. There is no PIN or biometric prompt before displaying your address data in Settings.

---

Tips from the team behind Tab Suspender Pro and the Zovo extension suite at zovo.one
