---
layout: post
title: "Chrome ERR_TOO_MANY_REDIRECTS Cookie Fix"
description: "Getting ERR_TOO_MANY_REDIRECTS in Chrome? This cookie-related error is common and fixable. Learn the simple steps to get browsing again."
date: 2026-01-15
categories: [troubleshooting, connectivity]
tags: [chrome-error, too-many-redirects, cookie-fix, browser-problem]
author: theluckystrike
---

# Chrome ERR_TOO_MANY_REDIRECTS Cookie Fix

You are browsing along in Chrome, click a link or try to log into a website, and suddenly your screen fills with an error that says ERR_TOO_MANY_REDIRECTS. This is a frustrating issue that can leave you stuck, unable to reach the page you want. The good news is that this error is very often caused by problems with cookies, and there are several straightforward fixes you can try. In this guide, I will explain what causes the ERR_TOO_MANY_REDIRECTS error, why cookies play a role, and exactly what you can do to resolve it.

## What ERR_TOO_MANY_REDIRECTS Actually Means

When Chrome displays the ERR_TOO_MANY_REDIRECTS error, it is telling you that the browser got stuck in an endless loop of page forwards. Websites sometimes redirect you from one page to another automatically. This is normal behavior when you log in, for example, where you might be redirected from a login page to your dashboard. However, when something goes wrong, Chrome can get trapped in a cycle where page A redirects to page B, which redirects back to page A, which redirects to page B again, and so on. After Chrome detects this loop, it stops and shows you the error to prevent your browser from getting stuck forever.

The most common cause of this redirect loop is corrupted or conflicting cookie data. Cookies are small pieces of information that websites store on your browser to remember you, keep you logged in, and track your session. When these cookies become outdated, duplicated, or conflict with each other, they can trick a website into repeatedly redirecting you. This is why clearing your cookies is often the fastest fix for this error.

Other possible causes include browser cache issues, problems with website servers, browser extension interference, or incorrect date and time settings on your computer. However, cookie problems are by far the most frequent culprit.

## Start by Clearing Site Cookies

The first and most effective fix for ERR_TOO_MANY_REDIRECTS is to clear the cookies for the specific website causing the problem. Here is how to do it.

Open Chrome and click the lock icon or information icon in the address bar next to the website URL. This icon is usually located to the left of the web address. Click on it, and you will see a dropdown menu that shows information about the site. Look for an option that says Cookies or Site Data. Click on it, and you will see a list of cookies that Chrome is storing for that website.

Click the option to clear all cookies and site data for that site. This will remove any corrupted or conflicting cookies that might be causing the redirect loop. After clearing the cookies, close the tab where you were seeing the error and try opening the website again in a new tab.

If you cannot access the website at all to clear its cookies through this method, you can also clear all cookies in Chrome. Go to the three dots in the top right corner, click on Settings, then Privacy and Security, and look for the option to clear browsing data. Make sure Cookies and other site data is selected, choose a time range like All Time, and click Clear Data.

## Clear Your Browser Cache

While you are clearing cookies, it is also a good idea to clear your browser cache. The cache stores copies of website files like images and scripts to help pages load faster. Sometimes this cached data can become outdated or corrupted, contributing to redirect issues.

To clear your cache, go to the same clear browsing data section in Chrome settings. This time, select Cached images and files in addition to cookies. Clearing both together gives you the best chance of fixing the redirect error. After clearing, restart Chrome and try visiting the website again.

## Try Incognito Mode

If clearing cookies and cache does not work, the next step is to test whether the problem is caused by one of your Chrome extensions. Chrome extensions can sometimes interfere with how websites handle redirects and cookies.

Open a new incognito window by clicking the three dots in the top right corner and selecting New Incognito Window. In incognito mode, Chrome does not load your extensions by default. Try visiting the same website in the incognito window and see if the error persists.

If the website works fine in incognito mode, then one of your extensions is likely causing the problem. To identify which extension is the culprit, go back to your normal Chrome window and click the puzzle piece icon next to the address bar. This shows all your installed extensions. Try disabling them one by one, testing the website after each disable. When the website starts working, you have found the problematic extension.

## Check Your Date and Time Settings

It might seem surprising, but incorrect date and time settings on your computer can cause ERR_TOO_MANY_REDIRECTS errors. Websites use cookies with built-in expiration dates, and if your computer thinks it is a different time than what the cookie expects, the cookie might behave unexpectedly, causing redirect loops.

Check that your computer's date and time are set correctly. On Windows, right-click on the time in the bottom right corner and select Adjust date and time. Make sure Set time automatically is turned on. On Mac, go to System Settings, click on Date and Time, and ensure the date and time are correct or set to adjust automatically.

## Try a Different Browser

If you have tried all the steps above and the error persists, it is worth testing whether the problem is specific to Chrome or something more general. Try opening the same website in a different browser like Firefox, Safari, or Microsoft Edge.

If the website works in another browser, the issue is likely with your Chrome profile or settings. You might consider resetting Chrome to its default settings, which can be found in Chrome settings under Privacy and Security. This will clear all your extensions, cookies, and settings, giving you a fresh start.

If the website does not work in any browser, the problem is likely on the website's end. The website might be experiencing technical difficulties, and there is not much you can do except wait and try again later.

## Prevent Future Redirect Issues

Once you have fixed the ERR_TOO_MANY_REDIRECTS error, you can take some steps to prevent it from happening again in the future.

Regularly clearing your cookies and cache helps prevent corrupted data from building up. You can set Chrome to automatically clear certain data when you close the browser, though this might be inconvenient if you want to stay logged into sites.

If you frequently keep many tabs open, browser extensions that manage tabs efficiently can help reduce the likelihood of running into redirect issues. One useful tool is Tab Suspender Pro, which automatically suspends tabs you have not used recently. This can help keep your browser running smoothly and reduce the chances of encountering redirect errors caused by resource conflicts. The extension works by putting inactive tabs to sleep so they do not consume resources, and when you return to them, they reload normally.

Keeping your browser and extensions updated also helps, since developers frequently release updates that fix bugs and improve compatibility with websites.

## Wrapping Up

The ERR_TOO_MANY_REDIRECTS error in Chrome is almost always related to cookie problems, and clearing cookies and cache is usually all it takes to fix it. Start with the simple steps, try incognito mode to test for extension issues, and check your computer is date and time settings if needed.

Most of the time, one of these methods will get you back to browsing normally. If the problem keeps happening on the same website, clearing that site is cookies and cache should solve it. For ongoing issues across many websites, consider resetting Chrome or trying a different browser to narrow down whether the problem is with your browser or something else.

---

Built by theluckystrike — More tips at [zovo.one](https://zovo.one)
