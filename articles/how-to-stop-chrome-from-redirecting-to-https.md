---
layout: post
title: "How to Stop Chrome from Redirecting to HTTPS"
description: "Chrome automatically redirects you to HTTPS? Learn why this happens and how to disable HTTPS redirect in Chrome settings."
date: 2026-01-15
categories: [privacy, security, settings]
tags: [chrome-https, https-redirect, browser-settings, chrome-security]
author: theluckystrike
---

If you type a website address into Chrome and find yourself automatically redirected to a secure version, you might be wondering how to stop Chrome from redirecting to HTTPS. This behavior is built into Chrome for security reasons, but there are situations where you might need more control over when these redirects happen.

Chrome redirects to HTTPS because of a feature called HTTPS-First Mode or because websites enforce secure connections. While this is generally a good thing for your security, it can cause problems in certain situations. Perhaps you are testing a website that does not have an SSL certificate yet, or you need to access an older site that only works over HTTP. Whatever your reason, there are several ways to gain more control over this behavior.

## Understanding Why Chrome Redirects to HTTPS

Chrome started pushing HTTPS as the default because secure connections protect your data from being intercepted by third parties. When you visit a site over HTTPS, the connection is encrypted, making it much harder for anyone to eavesdrop on what you are doing online. This is especially important when handling sensitive information like passwords, credit card numbers, or personal messages.

Google, the company behind Chrome, has been encouraging website owners to switch to HTTPS for years. They even give websites with HTTPS a slight ranking boost in search results. Chrome also shows a warning icon in the address bar when you visit sites that do not use HTTPS, which can be alarming even when you are just browsing safe content.

The automatic redirect happens through a few different mechanisms. Chrome may upgrade HTTP requests to HTTPS automatically, or websites themselves may include redirects that send visitors to their secure versions. Some of this behavior can be controlled through Chrome settings, while other redirects come from the websites themselves.

## Adjusting Chrome Security Settings

The most direct way to change how Chrome handles secure connections is through its security settings. Open Chrome and click on the three dots in the upper right corner, then select Settings. From there, click on Privacy and security, then scroll down to the Security section.

You will find an option called "Always use secure connections" or similar wording depending on your Chrome version. This setting controls whether Chrome automatically upgrades requests to HTTPS. Turning this off will prevent Chrome from automatically redirecting HTTP URLs to their secure counterparts.

Keep in mind that disabling this feature means your connections will not be encrypted on sites that do not enforce HTTPS. This is fine for testing purposes or accessing specific sites, but for everyday browsing, keeping HTTPS enabled is safer. You can always use the HTTP version of a site manually by typing it directly into the address bar.

## Using a Separate Profile for Testing

If you need to frequently access sites that do not have HTTPS, consider creating a separate Chrome profile for this purpose. Chrome profiles let you have different settings, bookmarks, and extensions for different uses. You can set up one profile with HTTPS redirects enabled for normal browsing and another profile with reduced security for testing or accessing older sites.

To create a new profile, click on your profile icon in the upper right of Chrome, then select Add. Give your new profile a name, and you can customize its settings independently from your main profile. This approach keeps your everyday browsing secure while giving you the flexibility to work with sites that have not made the switch to HTTPS yet.

## Trying Extensions for More Control

Browser extensions offer another way to manage how Chrome handles HTTPS redirects. Some extensions let you set custom rules for which sites should use HTTP and which should use HTTPS. This gives you fine-grained control without having to change global settings.

One useful extension to consider is Tab Suspender Pro. While this extension is primarily designed to automatically suspend tabs that you have not used recently, it also gives you additional control over how tabs behave. It can help manage your browser resources more effectively and provides options that let you decide how Chrome handles different types of content. It is not the only solution available, but it offers a practical way to customize your browsing experience.

When looking for extensions that control HTTPS behavior, read reviews carefully and make sure the extension comes from a trusted developer. Some extensions claim to manage redirects but may actually be collecting your browsing data.

## Dealing with Specific Website Redirects

Sometimes the redirect does not come from Chrome itself but from the website you are visiting. Many websites automatically redirect all visitors to their HTTPS version because they have configured their servers to do this. In these cases, there is not much you can do through Chrome settings to stop the redirect.

If you need to access the HTTP version of such a site, you might try using an older browser or contacting the website administrator to request access to their HTTP version. Some sites offer special URLs or parameters that let you bypass the redirect, though this is becoming increasingly rare as HTTPS adoption grows.

You can also try accessing the site through a web archive service if the content is available there. This will not let you interact with the live site, but it may let you view older content that was captured when the site was accessible over HTTP.

## When You Might Want to Disable HTTPS Redirects

There are legitimate reasons for wanting to stop Chrome from redirecting to HTTPS. Web developers often need to test sites that are still being built and do not yet have SSL certificates configured. Students learning about web development may need to practice with local servers that only work over HTTP. IT professionals sometimes need to access internal company resources that have not been set up with HTTPS.

In these cases, temporarily disabling the HTTPS redirect feature is perfectly reasonable. Just remember to turn it back on when you are done. Browsing over HTTPS is genuinely safer, and most of the time you want that protection enabled.

For development and testing work, many developers use local testing environments that they can access through special URLs like localhost or 127.0.0.1. These addresses typically bypass the HTTPS redirect because they are considered local and do not require the same security as public websites.

## The Trade-offs to Consider

Turning off HTTPS redirects does come with risks. Any information you send over HTTP can potentially be intercepted by someone else on your network. This includes passwords, personal information, and any data you enter into forms. If you are on a public WiFi network, this risk is even greater.

Before disabling HTTPS redirects, think about whether you really need to. If it is just about convenience or curiosity, it is probably not worth the risk. But if you have a specific need like testing a website you are developing, then the temporary risk is acceptable as long as you are careful about what you do while the setting is changed.

Some websites are beginning to drop support for HTTP entirely. This is part of a broader movement to make the web more secure. As time goes on, you may find fewer and fewer situations where you actually need to access HTTP versions of sites.

## Staying Safe While Having Control

The good news is that Chrome gives you enough control to handle most situations without compromising your overall security. By understanding how HTTPS redirects work and knowing where to find the relevant settings, you can make informed decisions about when to allow automatic redirects and when to disable them.

Remember that you can always type an HTTP address directly into the address bar even with HTTPS-first mode enabled. Chrome will try to upgrade it, but you can often override this by being explicit about what you want. Some browsers and tools also let you create exceptions for specific sites.

Taking a moment to understand these settings gives you more flexibility while keeping your everyday browsing secure. The web is moving toward HTTPS by default, and for good reason, but that does not mean you should be locked out of older content when you genuinely need access.

Tips from the team behind Tab Suspender Pro and the Zovo extension suite at zovo.one.
