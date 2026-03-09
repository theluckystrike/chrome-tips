---
layout: post
title: "How to Fix Chrome ERR_NAME_NOT_RESOLVED Error"
description: "Struggling with the ERR_NAME_NOT_RESOLVED error in Chrome? Learn what causes it and how to fix it with simple solutions."
---

If you are trying to open a website in Google Chrome and you see a message that says ERR_NAME_NOT_RESOLVED, you are not alone. This error is one of the most common issues Chrome users encounter, and it can be frustrating when you just want to browse the web. The good news is that this error is usually easy to fix once you understand what is causing it. Let me walk you through what the error means, why it happens, and how you can get back to browsing in just a few minutes.

## What ERR_NAME_NOT_RESOLVED Actually Means

When you type a website address into Chrome, your browser needs to find the actual location of that website on the internet. It does this by asking a DNS server, which is like a phone book for the web. The DNS server takes the website name you typed and translates it into a numerical address that computers can understand.

The ERR_NAME_NOT_RESOLVED error occurs when Chrome cannot complete this translation. In other words, your browser asked the DNS server for the address of a website, and the DNS server replied that it has no idea what website you are talking about. This is why the error message says the name cannot be resolved.

Think of it like calling directory assistance and asking for a phone number for a business that does not exist. They simply cannot help you because the information you are looking for is not in their database.

## Why This Error Happens

There are several reasons why you might see this error, and understanding the cause can help you choose the right fix.

The most common reason is a typo in the website address. If you accidentally typed "googel.com" instead of "google.com," the DNS server will not be able to find the website because that address simply does not exist. This is the easiest cause to fix, so always double-check the spelling of the website address first.

Another common cause is a problem with your internet connection. If your connection is unstable or if there is an issue with your ISP is DNS servers, Chrome might not be able to reach the directory it needs to look up website addresses. This can happen even if other apps on your computer seem to work fine, because different apps might use different DNS servers.

Sometimes the issue is with the website itself rather than your connection. If the website owner let their domain name expire or did not configure their DNS settings correctly, visitors will see this error. In this case, there is nothing you can do on your end except wait for the website owner to fix the problem.

Firewall or antivirus settings can also sometimes block Chrome is ability to connect to DNS servers, leading to this error. This is less common but worth considering if you have recently changed your security software or added new rules.

Finally, if you have recently changed your DNS settings or installed new software that modifies your network configuration, you might accidentally be using DNS servers that are not working properly.

## Simple Steps to Fix the Error

Now let is get to the practical part. Here are the most effective ways to resolve the ERR_NAME_NOT_RESOLVED error, starting with the simplest solutions.

First, check for typos in the website address. This sounds obvious, but it is the most frequent cause of this error. Look carefully at every letter in the URL and make sure there are no extra or missing characters. Also make sure you included the correct prefix, whether it is http or https.

Second, try reloading the page. Sometimes the error is temporary and simply refreshing the page can resolve it. You can do this by clicking the circular arrow icon next to the address bar or by pressing the F5 key on your keyboard.

Third, clear your browser cache and cookies. Over time, cached data can become corrupted and cause issues with how Chrome resolves website addresses. To do this, click the three dots in the upper right corner of Chrome, select Settings, then click Privacy and security, and choose Clear browsing data. SelectCached images and files and Cookies and other site data, then click Clear data.

Fourth, try using a different DNS server. Your computer is probably set to use DNS servers provided by your ISP, but these can sometimes be slow or unavailable. You can change your DNS settings to use public DNS servers like Google is (8.8.8.8 and 8.8.4.4) or Cloudflare is (1.1.1.1). To do this on Windows, go to Control Panel, Network and Internet, Network and Sharing Center, Change adapter settings, right-click your connection, select Properties, double-click Internet Protocol Version 4, and enter the DNS server addresses. On Mac, go to System Preferences, Network, select your connection, click Advanced, go to the DNS tab, and add the new server addresses.

Fifth, check your firewall and antivirus settings. If you have recently added new security software or changed its settings, it might be blocking Chrome is ability to connect to DNS servers. Try temporarily disabling your firewall or antivirus to see if that resolves the issue. Remember to re-enable them after testing.

Sixth, try flushing your DNS cache. Your computer stores a local cache of recently resolved website addresses, and sometimes this cache can become outdated or corrupted. To flush the DNS cache on Windows, open Command Prompt as administrator and type ipconfig /flushdns. On Mac, open Terminal and type sudo killall -HUP mDNSResponder.

## A Helpful Tool to Consider

If you find that you frequently encounter connection issues or slow browsing speeds, you might want to consider using a browser extension designed to optimize your browsing experience. Tab Suspender Pro is one option that can help manage your open tabs more efficiently, which can reduce the load on your browser and potentially help avoid some connection-related issues. It automatically suspends tabs you have not used recently, freeing up memory and network resources for the tabs you are currently using. This can be particularly helpful if you tend to keep many tabs open at once.

## When All Else Fails

If you have tried all these steps and you still see the ERR_NAME_NOT_RESOLVED error, there are a few more things to consider. The website itself might be down or experiencing problems. You can check if a website is down for everyone by using a service like downforeveryoneorjustme.com.

You might also want to try a different browser to see if the issue is specific to Chrome. Sometimes browser settings or extensions can cause problems that do not occur in other browsers.

If the issue persists across multiple websites and you have tried everything else, it is possible there is a problem with your internet service provider or your network equipment. Contacting your ISP might be necessary at this point.

Most of the time, the ERR_NAME_NOT_RESOLVED error is nothing serious. It is usually just a simple typo, a temporary DNS issue, or a minor configuration problem that you can resolve in a few minutes. Now that you know what causes it and how to fix it, you can get back to browsing the web without frustration.

Tips from the team behind Tab Suspender Pro and the Zovo extension suite at zovo.one
