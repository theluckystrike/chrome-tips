---
layout: post
title: How to Migrate Chrome Data to a New Computer
description: Moving to a new computer? Learn how to transfer your Chrome bookmarks,
  passwords, history, and settings seamlessly. Keep your browsing experience intact.
date: 2026-03-12
categories:
- chrome
- data-migration
- sync
- backup
tags:
- chrome-sync
- data-transfer
- browser-migration
- bookmarks
- passwords
author: theluckystrike
last_modified_at: '2026-03-12'
permalink: how-to-migrate-chrome-data-to-new-computer
---
# How to Migrate Chrome Data to a New Computer

Getting a new computer is exciting, but the thought of losing your carefully curated Chrome bookmarks, saved passwords, and browsing history can be stressful. The good news is that Google Chrome makes it remarkably easy to transfer all your data to a new machine using its built-in sync feature. Whether you're moving from Windows to Mac, upgrading to a new PC, or switching between operating systems, your Chrome data can follow you seamlessly.

In this guide, I'll walk you through the best methods to migrate your Chrome data to a new computer, ensuring you don't lose any of your important bookmarks, passwords, or settings.

## Method 1: Using Chrome Sync (The Easiest Way)

Chrome Sync is Google's built-in solution for keeping your data synchronized across devices. This is the recommended approach because it handles everything automatically.

### Setting Up Chrome Sync on Your New Computer

**Step 1:** Download and install Chrome on your new computer if you haven't already.

**Step 2:** Launch Chrome and sign in with the same Google account you used on your old computer. Click the profile icon in the top-right corner, then click "Turn on sync."

**Step 3:** You'll be prompted to confirm your Google account credentials. Enter your email and password.

**Step 4:** Once signed in, Chrome will automatically begin syncing your data. This includes:
- Bookmarks
- Browsing history
- Saved passwords
- Autofill data
- Extensions
- Settings and preferences
- Open tabs (if enabled)

**Step 5:** Wait a few minutes for the sync to complete. The time depends on how much data you have.

### What Gets Synced?

When you enable Chrome Sync, the following data types are transferred:

| Data Type | What's Included |
|-----------|------------------|
| Bookmarks | All folders and saved links |
| History | Browsing history and download history |
| Passwords | Saved login credentials |
| Autofill | Addresses, credit cards, and other form data |
| Extensions | Your installed extensions |
| Settings | Theme, homepage, and browser preferences |
| Tabs | Open tabs (if sync is enabled) |

### Managing What Gets Synced

If you don't want everything synced, you can customize which data types are transferred:

**Step 1:** Click your profile icon and select "Manage your Google Account"

**Step 2:** Navigate to the "Data & privacy" tab

**Step 3:** Under "History settings," click "Chrome history"

**Step 4:** Review and adjust what gets synced. You can pause sync for specific data types.

## Method 2: Manual Export and Import

If you prefer more control or don't want to use sync for privacy reasons, you can manually export and import your Chrome data.

### Exporting Your Data

**Step 1:** On your old computer, open Chrome and click the three dots in the top-right corner

**Step 2:** Select "Bookmarks" → "Bookmark manager"

**Step 3:** Click the three-dot menu in the manager and select "Export bookmarks"

**Step 4:** Choose a location to save the HTML file and give it a descriptive name

**Step 5:** For passwords, you'll need to use a different approach. Chrome doesn't directly export passwords, but you can:
- Use a password manager to export
- Access chrome://settings/passwords and manually note them
- Use a third-party tool (be cautious with these)

### Importing Your Data

**Step 1:** On your new computer, open Chrome

**Step 2:** Go to the three-dot menu → "Bookmarks" → "Bookmark manager"

**Step 3:** Click the three-dot menu and select "Import bookmarks"

**Step 4:** Choose the HTML file you exported from your old computer

**Step 5:** Your bookmarks will appear in a new folder called "Imported"

### Exporting Chrome Settings

For settings and other data, you can use Chrome's built-in export feature:

**Step 1:** Go to chrome://settings/importAndExport

**Step 2:** Click "Export to file" to save your settings, autofill data, and search engines

**Step 3:** On your new computer, use "Import from file" to restore this data

## Method 3: Transferring Profile Folder (Advanced)

For a complete transfer including all data, you can manually copy Chrome's profile folder. This is more technical but transfers absolutely everything.

### Finding Your Chrome Profile Folder

The location varies by operating system:

**Windows:**
```
C:\Users\[YourUsername]\AppData\Local\Google\Chrome\User Data\Default
```

**Mac:**
```
~/Library/Application Support/Google/Chrome/Default
```

**Linux:**
```
~/.config/google-chrome/Default
```

### Transferring the Profile

**Step 1:** Close Chrome completely on both computers

**Step 2:** On your old computer, navigate to the profile folder

**Step 3:** Copy the entire "Default" folder (or the specific profile folder if you use multiple profiles)

**Step 4:** Transfer this folder to your new computer using an external drive or cloud storage

**Step 5:** On your new computer, navigate to the Chrome profile location

**Step 6:** Paste the folder and replace the existing Default folder

**Step 7:** Launch Chrome—you should see all your data

### Important Warnings

- This method can cause issues if Chrome versions differ significantly between computers
- Always back up the existing Default folder before replacing it
- This transfers all data including cookies, which may log you out of websites

## Transferring Specific Data Types

### Bookmarks Only

The quickest way to transfer just bookmarks is through the export/import method mentioned above. Chrome creates a standard HTML file that can be imported into any browser.

### Passwords

Chrome's passwords are encrypted and tied to your Google account when sync is enabled. Without sync, you have a few options:

1. **Use Chrome Sync (recommended):** Passwords sync automatically
2. **Manual export:** Visit chrome://settings/passwords and export
3. **Password manager:** If you use a password manager like Bitwarden or 1Password, export from there

### Extensions

When you sign in with Chrome Sync, extensions should automatically install on your new computer. If not:

**Step 1:** Go to chrome://extensions

**Step 2:** Enable "Developer mode" in the top-left corner

**Step 3:** Your extensions will show an "Enable" option—click it for each

### History and Autofill

These are automatically synced when you enable Chrome Sync. If not using sync, you can export via chrome://settings/importAndExport.

## Troubleshooting Common Issues

### Sync Not Working

If your data isn't syncing to your new computer:

1. **Check your internet connection**
2. **Verify you're signed into the same Google account**
3. **Go to chrome://sync and check for any error messages**
4. **Try clicking "Sync now" button**
5. **Ensure sync isn't paused in your Google account settings**

### Bookmarks Missing After Transfer

If your bookmarks didn't transfer properly:

1. Check if they're in the "Imported" folder
2. Try the export/import method again
3. Check if Chrome Sync is enabled
4. Look for bookmarks in other profile folders

### Passwords Not Transferring

Chrome encrypts passwords and links them to your Google account when sync is enabled. Without sync, you'll need to either:

1. Enable sync to transfer passwords
2. Manually export passwords before switching
3. Use a dedicated password manager

### Extensions Not Installing

If extensions won't transfer:

1. Make sure sync is enabled
2. Go to each extension's page in Chrome Web Store and reinstall
3. Check chrome://extensions for any errors

## Best Practices for Data Migration

1. **Enable sync before switching:** This is the easiest method
2. **Export bookmarks as backup:** Even with sync, keep a backup HTML file
3. **Update Chrome on both computers:** Using the same version reduces compatibility issues
4. **Check your sync settings:** Ensure all desired data types are enabled
5. **Wait for sync to complete:** Don't close Chrome until syncing finishes

## Conclusion

Migrating your Chrome data to a new computer doesn't have to be a headache. With Chrome Sync, you can transfer all your bookmarks, passwords, history, and settings with just a few clicks. For those who prefer more control, manual export and import methods work well too.

The key is to make sure you're signed into the same Google account on both computers and that sync is enabled. Within minutes, your new computer will feel just like your old one—complete with all your bookmarks, passwords, and browsing history.

Remember to keep a manual backup of your bookmarks even when using sync, and you'll never have to worry about losing your Chrome data again.
