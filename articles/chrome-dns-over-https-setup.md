---
layout: default
title: "Chrome DNS Over HTTPS Setup Guide"
description: "Learn how to enable DNS over HTTPS (DoH) in Chrome for enhanced privacy and security. Step-by-step guide covering secure DNS, provider selection, and custom DNS configuration."
date: 2026-01-15
categories: [privacy, security, chrome]
tags: [chrome, dns-over-https, doh, privacy, security, browser]
author: theluckystrike
---

# Chrome DNS Over HTTPS Setup Guide

In an era where online privacy is increasingly important, understanding and configuring **DNS over HTTPS (DoH)** in Chrome is one of the most effective steps you can take to protect your web browsing activity. This comprehensive guide will walk you through everything you need to know about setting up DoH in Google Chrome, from understanding what it does to selecting the right provider for your needs.

## What is DNS Over HTTPS?

**DNS over HTTPS** is a protocol that encrypts your DNS queries using the same HTTPS protocol that secures websites. When you type a website address into your browser, your computer needs to translate that human-readable address (like google.com) into a numerical IP address that computers use to identify servers. This translation process is called DNS lookup, and traditionally, these queries were sent in plain text over the internet.

The problem with plain text DNS is that anyone who can intercept your internet traffic—such as your Internet Service Provider (ISP), Wi-Fi operators, or potentially malicious actors on the same network—can see which websites you are visiting. This creates significant privacy concerns because your browsing history can be logged, analyzed, and potentially sold to advertisers or handed over to authorities without your knowledge or consent.

**DNS over HTTPS** solves this problem by encrypting these queries. When you enable DoH, your browser sends DNS requests as encrypted HTTPS traffic, making it virtually impossible for anyone to intercept and read them. This encryption uses the same security standards that protect your sensitive data when you visit banking websites or online stores.

## Why Should You Enable DNS Over HTTPS in Chrome?

The benefits of enabling **DNS over HTTPS** extend beyond basic privacy. Understanding these benefits can help you appreciate why this configuration is worth the few minutes it takes to set up.

### Enhanced Privacy Protection

The primary benefit of DoH is improved privacy. Without DoH, your ISP can see every website you visit because they handle your DNS requests. This data can be used to build detailed profiles of your browsing habits, which may be shared with advertisers or other third parties. Some ISPs have been known to collect and sell browsing data as part of their business models. With DoH enabled, your ISP can still see that you are using Chrome and accessing the internet, but they cannot see which specific websites you are visiting because the DNS queries are encrypted.

### Protection Against DNS Spoofing

DNS over HTTPS also provides protection against DNS spoofing attacks, also known as DNS cache poisoning. In these attacks, a malicious actor redirects your DNS queries to fake websites designed to steal your personal information, such as login credentials or financial data. Because DoH uses cryptographic verification and encrypted connections, it is much more difficult for attackers to intercept and manipulate your DNS queries.

### Improved Security on Public Wi-Fi

When using public Wi-Fi networks at cafes, airports, or hotels, you are sharing the network with strangers. Without DoH, network operators or anyone else on the same network could potentially monitor your DNS queries and see your browsing activity. DoH encrypts this information, ensuring that even if someone is monitoring the network, they cannot see which websites you are accessing.

### Faster Connection Times

While the primary motivation for DoH is privacy and security, some users report faster connection times when using DoH. This can happen because some DNS providers operate globally distributed networks that can respond to queries more quickly than traditional ISP DNS servers, particularly for frequently visited websites that are cached on their networks.

## How Chrome Handles DNS Over HTTPS

Google Chrome includes built-in support for DNS over HTTPS, making it relatively simple to enable and configure. Chrome's implementation of DoH is designed to be user-friendly while providing robust privacy and security benefits.

When you enable DoH in Chrome, the browser automatically checks if your current DNS provider supports DoH and attempts to use it if available. Chrome maintains a list of major DNS providers that support DoH, including Google DNS, Cloudflare, and others. If your DNS provider is on this list, Chrome will automatically use DoH without requiring any additional configuration.

Chrome also includes a fallback mechanism. If DoH fails for any reason (such as network connectivity issues), Chrome will automatically revert to traditional DNS queries, ensuring that you can still access the internet even if there are temporary problems with your DoH configuration.

## Step-by-Step Guide to Enabling DNS Over HTTPS in Chrome

Setting up DNS over HTTPS in Chrome is a straightforward process that can be completed in just a few minutes. Follow these steps to enable this important privacy feature:

### Step 1: Open Chrome Settings

Launch Google Chrome on your computer and click on the three-dot menu icon in the upper-right corner of the browser window. From the dropdown menu, select "Settings" to open the Chrome settings page.

### Step 2: Navigate to Privacy and Security

In the settings page, scroll down until you find the "Privacy and security" section in the left sidebar. Click on this option to expand the privacy settings menu.

### Step 3: Select Security Settings

Within the "Privacy and security" section, look for and click on "Security." This will take you to the security settings page where you can configure various security options including DNS over HTTPS.

### Step 4: Enable DNS Over HTTPS

On the security settings page, scroll down until you find the "Use secure DNS" option. This setting is typically located in the "Advanced" section at the bottom of the page. Click on the toggle switch to enable this feature.

When you enable secure DNS, Chrome will display two options: "With current service provider" and "With Google" or other providers depending on your location and Chrome version. The "With current service provider" option attempts to use DoH with whatever DNS provider you are currently using, provided they support it. The "With Google" option explicitly configures Chrome to use Google's DNS service.

### Step 5: Choose Your Preferred Provider

Select the provider that best meets your needs. For most users, the default "With current service provider" option works well because it automatically selects a DoH-capable provider. However, if you want to explicitly choose a specific provider for reasons we will discuss later in this guide, you can select it from the available options.

## Selecting a DNS Over HTTPS Provider

While Chrome's default behavior is to automatically select a DoH provider, you may want to explicitly choose a specific provider based on your priorities. Here are the most popular DNS over HTTPS providers and their characteristics:

### Google DNS

**Google Public DNS** is one of the most widely used DNS services, and it supports DNS over HTTPS. Google's DNS service is known for its reliability and speed, with a global network of servers that typically provide fast response times. If you already use Google services and trust Google with your DNS data, this is a solid choice. Google has a strong track record of security and has implemented DoH support with strong encryption.

### Cloudflare

**Cloudflare DNS** (also known as 1.1.1.1) has become extremely popular for privacy-conscious users. Cloudflare has a strong commitment to user privacy and does not log IP addresses or sell user data to advertisers. They also offer a WARP service that provides additional privacy features. Cloudflare's DNS service is known for its speed, often providing some of the fastest DNS response times globally.

### Quad9

**Quad9** is a security-focused DNS provider that blocks malicious domains at the DNS level. If your priority is protection against malware and phishing attacks, Quad9 is an excellent choice. Quad9 does not collect personally identifiable information and is operated as a non-profit organization, making it a good option for users who prioritize both security and privacy.

### OpenDNS

**OpenDNS**, owned by Cisco, is another established DNS provider that supports DoH. OpenDNS offers both free and paid tiers, with the paid versions providing additional security features such as content filtering and threat intelligence. This provider is a good choice if you want DNS-based content filtering in addition to encrypted queries.

## Configuring Custom DNS Over HTTPS Providers

If you want to use a DNS provider that is not listed in Chrome's default options, you can configure a custom DoH provider. This requires a bit more technical knowledge but allows you to use virtually any DNS provider that supports DoH.

To configure a custom DNS provider, you will need to know the DoH endpoint URL for your chosen provider. Most DNS providers that support DoH publish their endpoint URLs on their websites. Once you have this URL, you can configure Chrome to use it by enabling DoH and then selecting the option to add a custom provider.

To find this option, go to Chrome's security settings as described earlier. After enabling secure DNS, look for an option to add a custom provider or enter a custom DoH URL. Enter the provider's DoH endpoint URL and save your settings.

It is important to note that not all DNS providers support DoH, and not all DoH implementations are equally secure. When selecting a custom provider, ensure they use modern encryption standards and have a good reputation for privacy and security.

## Understanding the Limitations of DNS Over HTTPS

While DNS over HTTPS significantly improves your privacy and security, it is important to understand its limitations to maintain realistic expectations about what it can and cannot protect.

### What DoH Does Not Hide

When you enable DoH, your ISP can still see the IP addresses of the servers you connect to. While they cannot see which specific websites you are visiting through DNS queries, they can see the IP addresses of those websites in your network traffic. Additionally, the DNS provider you use (such as Google or Cloudflare) will still see your DNS queries, so you are essentially transferring trust from your ISP to your DNS provider.

### HTTPS Still Reveals Some Information

Even with DoH enabled, the websites you visit can still see some information about your browsing. The domain name you are visiting is often visible in the Server Name Indication (SNI) field during the TLS handshake, which is necessary for servers to present the correct SSL certificate. While technologies like Encrypted Client Hello (ECH) are being developed to address this, they are not yet universally adopted.

### DoH Does Not Make You Completely Anonymous

DNS over HTTPS is an important privacy tool, but it is just one piece of the privacy puzzle. For truly anonymous browsing, you would need to use additional tools such as the Tor network, which provides stronger anonymity guarantees but at the cost of potentially slower browsing speeds.

## Combining DoH with Other Privacy Tools

For comprehensive browser privacy and security, consider combining DNS over HTTPS with other tools and practices. Using a privacy-focused browser extension can help block tracking scripts and advertisements. Similarly, using a VPN in conjunction with DoH can provide additional layers of privacy and security.

**Tab Suspender Pro** can complement your privacy setup by helping you manage your browser tabs more efficiently. While Tab Suspender Pro is primarily designed to save memory and improve browser performance by automatically suspending inactive tabs, it also provides a clearer view of your active browsing session. This can help you maintain awareness of which sites are open and potentially collecting data, supporting your overall privacy-conscious browsing habits.

## Troubleshooting DNS Over HTTPS Issues

After enabling DoH, you may occasionally encounter issues with website connectivity or loading. Here are some common problems and their solutions:

### Some Websites Not Loading

If certain websites stop loading after enabling DoH, try temporarily disabling DoH to see if the issue resolves. If the website loads without DoH, the problem may be with your DNS provider. Try switching to a different provider or reverting to "With current service provider" to allow Chrome to automatically select an appropriate provider.

### Slow Connection Speeds

If you notice slower browsing speeds after enabling DoH, try switching to a different DNS provider. Some providers have faster response times depending on your geographic location. You can use online tools to test DNS response times for different providers from your location.

### Corporate Network Issues

If you are using Chrome on a work computer connected to a corporate network, your IT department may have policies that conflict with DoH. Some organizations use their own DNS servers for content filtering or security monitoring, and enabling DoH may bypass these controls. If you encounter issues on a work network, consult with your IT department before enabling DoH.

## Maintaining Your DNS Privacy

Enabling DNS over HTTPS is not a one-time configuration that you can forget about. To maintain optimal privacy and security, periodically review your DNS settings and stay informed about developments in DNS privacy technology.

Keep your browser updated to ensure you have the latest security features and bug fixes. New DNS providers may become available, and Chrome's implementation of DoH may improve over time. Additionally, keep an eye on news about DNS providers' privacy policies, as these can change.

## Final Thoughts

Setting up DNS over HTTPS in Chrome is one of the most impactful steps you can take to improve your online privacy and security. With just a few minutes of configuration, you can significantly reduce the amount of data that can be collected about your browsing activity. Whether you choose Google's DNS, Cloudflare's 1.1.1.1, or another provider, enabling DoH puts you in greater control of your digital privacy.

Remember that DoH is just one layer of a comprehensive privacy strategy. By combining it with other privacy tools and practices, you can enjoy a more private and secure browsing experience. Take the time to explore Chrome's other privacy settings and consider what additional measures make sense for your specific needs and threat model.

Built by theluckystrike — More tips at [zovo.one](https://zovo.one)
