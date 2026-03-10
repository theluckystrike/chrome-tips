---
layout: default
title: "Chrome DNS Over HTTPS Setup Guide — Secure Your Browser DNS Queries"
description: "Learn how to set up DNS Over HTTPS (DoH) in Chrome for enhanced privacy and security. This guide covers secure DNS configuration, provider selection, custom DNS servers, and privacy benefits for Chrome users."
date: 2026-03-11
categories: [privacy, security, chrome-settings]
tags: [dns-over-https, chrome-dns, doh, privacy, secure-dns, chrome-security, browser-privacy]
author: theluckystrike
---

# Chrome DNS Over HTTPS Setup Guide — Secure Your Browser DNS Queries

Every time you type a website address into Chrome, your browser needs to translate that human-readable domain name into a numerical IP address that computers can understand. This translation process happens through the Domain Name System, or DNS. By default, these DNS queries are sent in plain text, meaning anyone watching your network traffic can see which websites you are trying to visit. Setting up DNS Over HTTPS (DoH) in Chrome encrypts these queries, protecting your browsing privacy and adding an extra layer of security to your web experience.

In this comprehensive guide, I will walk you through what DNS Over HTTPS is, why it matters, how to configure it in Chrome, how to select the right DNS provider, and how to set up custom DNS servers if you want even more control over your browsing experience.

## What Is DNS Over HTTPS and Why Should You Care

DNS Over HTTPS is a protocol that encrypts your DNS queries using the same HTTPS protocol that secures websites. When you visit a website normally, your computer sends an unencrypted request to your internet service provider's DNS server, asking something like "what is the IP address for example.com?" This request travels across the network in plain text, which means your ISP, potential hackers on the same network, or anyone else monitoring traffic can see exactly which domains you are attempting to access.

DoH wraps these DNS requests in HTTPS encryption, the same security layer that protects your credit card information when you shop online. When you enable DoH in Chrome, your browser encrypts each DNS query before sending it, and the DNS response comes back through the same encrypted channel. This prevents network observers from seeing your DNS queries, significantly improving your privacy.

Beyond privacy, DoH also offers security benefits. Traditional DNS queries are vulnerable to man-in-the-middle attacks, where an attacker could intercept your request and redirect you to a malicious website. Because DoH uses HTTPS encryption with certificate verification, your browser can confirm that the DNS response actually came from the legitimate DNS server and has not been tampered with.

Chrome was one of the first major browsers to implement DoH support, making it accessible to millions of users. The feature is built directly into Chrome's settings, so you do not need to install any extensions or additional software to use it.

## How to Enable DNS Over HTTPS in Chrome

Enabling DoH in Chrome is straightforward and takes only a few moments. Follow these steps to secure your DNS queries.

First, open Chrome on your computer and click the three-dot menu icon in the upper right corner of the window. From the dropdown menu, select "Settings." You can also access Settings by typing chrome://settings in the address bar and pressing Enter.

In the Settings page, scroll down to the "Privacy and security" section and click on it. Look for the option labeled "Security" and click on that as well. On the Security page, you will find a toggle called "Use secure DNS" with the description "With Secure DNS providers, browsing is more private by preventing eavesdropping and tampering."

Toggle the switch to turn on this feature. When enabled, Chrome will automatically use DoH for all your DNS queries. By default, Chrome will use your existing DNS provider if it supports DoH, or it will fall back to a Google-provided DoH service if your current provider does not support the protocol.

For more control over which DNS provider Chrome uses, click the "With" dropdown menu below the toggle. Here you can select from several popular DoH providers or choose "Custom" to enter your own DNS server addresses. I will explain the different provider options in the next section.

Once you have made your selection, close the Settings tab. Your DNS queries are now encrypted through HTTPS, providing immediate privacy and security benefits for all your browsing activity.

## Selecting the Right DNS Over HTTPS Provider

Choosing the right DoH provider is an important decision that affects your privacy, speed, and overall browsing experience. There are several reputable providers to choose from, each with different philosophies, logging policies, and performance characteristics.

**Google DNS** is the default option in Chrome and offers reliable, fast performance worldwide. Google operates one of the largest DNS networks on the planet, which typically means low latency and high availability. However, Google is an advertising company that collects significant amounts of data, so while your DNS queries themselves are encrypted, Google still sees which domains you request. If your primary concern is network-level surveillance rather than the DNS provider itself, Google DNS is a solid choice.

**Cloudflare** is another excellent DoH provider, particularly known for its strong commitment to privacy. Cloudflare's 1.1.1.1 service promises not to sell user data and deletes DNS logs within 24 hours. The company has positioned itself as a privacy-focused alternative to Google, making it popular among users who want both speed and privacy. Cloudflare also offers a version specifically designed for families that blocks malware and adult content.

**Quad9** is a security-focused DNS provider that blocks domains known to be malicious, protecting users from phishing attempts and malware. Quad9 does not log IP addresses, making it an excellent choice for users who prioritize security and privacy equally. The service is operated by a nonprofit foundation, which means it is not driven by advertising revenue.

**AdGuard DNS** offers DNS-level ad blocking in addition to privacy protection. If you want to block ads across your entire browsing experience without installing an ad-blocking extension, AdGuard's DoH service can filter out advertising and tracking domains at the DNS level. This can speed up page loads by preventing ads from loading in the first place.

When selecting a provider, consider what matters most to you. Speed and reliability might be your priority, in which case Google or Cloudflare are excellent choices. If privacy is your primary concern, Quad9 or Cloudflare are strong options. If you want ad blocking built into your DNS, AdGuard provides that additional functionality.

## Setting Up Custom DNS Servers in Chrome

While the preset DoH providers offer excellent options for most users, some users may want to set up custom DNS servers for specific reasons. Perhaps you run your own DNS server at home, or you want to use a specialized DNS service not listed in Chrome's presets. Chrome allows you to configure custom DoH servers with your own addresses.

To set up custom DNS servers, return to the Security settings page where you found the "Use secure DNS" option. After enabling the feature, click the dropdown menu and select "Custom." Two new fields will appear where you can enter DNS server addresses.

In the first field, enter the DoH template for your primary DNS server. This is usually a URL that follows the format https://dns.example.com/dns-query, where "dns.example.com" is replaced with your actual DNS provider's domain. Some DNS providers use different formats, so check with your provider's documentation for the correct DoH endpoint.

For example, if you wanted to use Cloudflare's DoH service manually, you would enter https://cloudflare-dns.com/dns-query in the first field. Similarly, Google DNS uses https://dns.google/dns-query, and Quad9 uses https://dns.quad9.net/dns-query.

In the second field, you can optionally enter a backup DNS server that Chrome will use if the primary server is unavailable. This provides redundancy and ensures you maintain DoH protection even if your primary DNS provider experiences issues.

When entering custom DNS addresses, make sure you are using a legitimate DoH service. Entering incorrect addresses could break your DNS functionality, causing websites to fail to load. Double-check the URLs from your DNS provider's official documentation before saving.

One important note: Chrome's DoH implementation requires the DNS server to support DNS-over-HTTPS in a standard format. Not all DNS servers offer this capability, so verify that your chosen provider supports DoH before attempting to configure it in Chrome.

## Understanding the Privacy Benefits of DNS Over HTTPS

Enabling DoH in Chrome provides several meaningful privacy improvements that protect your browsing activity from various observers.

The most immediate benefit is protection from network-level surveillance. Without DoH, anyone on your local network, your internet service provider, or any entity that can intercept your network traffic can see every domain you visit. This is particularly concerning on public Wi-Fi networks, where malicious actors could potentially monitor all DNS queries. DoH encrypts these queries, making them invisible to network observers.

DoH also protects against DNS spoofing attacks, where an attacker could intercept your DNS query and return a fake IP address, redirecting you to a malicious website that looks legitimate. The HTTPS encryption and certificate verification in DoH make it much harder for attackers to tamper with DNS responses.

It is important to understand what DoH does and does not protect. DoH encrypts the translation of domain names to IP addresses, but it does not hide the IP addresses you connect to. Once your browser knows the IP address for a website, subsequent connections to that IP address are not encrypted by DoH alone. Websites you visit can still see your IP address, and your ISP can see which IP addresses you connect to, even if they cannot see which specific domains correspond to those addresses.

For comprehensive privacy protection, consider combining DoH with other tools like a VPN, which encrypts all your traffic and masks your IP address. However, DoH is an excellent first step that significantly improves privacy with minimal inconvenience.

## Performance Considerations and Common Questions

One common concern about DoH is whether it slows down browsing due to the encryption overhead. In practice, the performance impact is minimal for most users. The HTTPS encryption adds only a small amount of data to each DNS query, and the speed benefits of using a well-optimized DNS provider often outweigh any minor overhead.

Some users worry that DoH might interfere with their organization's network policies. If your workplace uses DNS-based filtering to block certain websites, enabling DoH might bypass those controls. Chrome's DoH settings respect system DNS settings on managed devices, so if your computer is part of a managed network, your organization might have configured how DoH works. If you encounter issues accessing network resources after enabling DoH, check with your IT department.

Another question involves whether using DoH means you are no longer using your ISP's DNS servers. When you enable DoH in Chrome, your DNS queries still go through your ISP's network, but they are encrypted. Your ISP can see that you are making HTTPS connections to a DoH provider, but they cannot see which domains you are requesting. Some privacy-conscious users combine DoH with a VPN for additional protection.

For users concerned about tab management and memory usage, it is worth noting that Chrome includes additional privacy and performance features alongside DoH. For example, the browser's tab grouping and Memory Saver features help manage resource usage. If you find that Chrome is consuming too much memory, you might also explore extensions like **Tab Suspender Pro** to automatically suspend inactive tabs, further reducing browser resource consumption while maintaining your privacy setup.

## Verifying That DNS Over HTTPS Is Working

After enabling DoH in Chrome, you may want to verify that your DNS queries are actually being encrypted. Several online tools can help you check this.

One option is to visit a website like "dnsleaktest.com" or "dohtest.neustar.biz" that can analyze your DNS configuration. These tests examine various aspects of your DNS queries to determine which provider you are using and whether your queries are properly protected.

You can also check Chrome's behavior directly. When DoH is enabled and working, Chrome handles all DNS resolution through HTTPS. You can verify this by visiting chrome://dns in your address bar, which shows Chrome's DNS cache and can provide information about how names are being resolved.

If you find that DoH is not working as expected, first check that the feature is still enabled in Settings. Some software updates or browser restarts might occasionally reset settings. Also verify that you have selected a valid DoH provider, particularly if using custom DNS settings.

## Additional Chrome Privacy Settings to Consider

While you are configuring DNS Over HTTPS, Chrome offers several other privacy settings worth exploring. In the Privacy and security section of Settings, you can enable or disable various tracking features, manage cookies, and control how Chrome handles your data.

"Cookies and site data" lets you decide whether to allow all cookies, block third-party cookies, or block all cookies. Third-party cookies are commonly used for cross-site tracking, so blocking them improves privacy.

"Privacy Sandbox" settings control whether Chrome uses privacy-preserving APIs that limit tracking while still allowing some personalization. Reviewing these settings lets you balance functionality with privacy.

"Safe Browsing" is Chrome's built-in protection against malicious websites and downloads. Keeping this enabled provides valuable security warnings when you attempt to visit known phishing or malware sites.

Combining DoH with these additional privacy settings creates a more comprehensive privacy posture for your browsing. Each setting addresses different aspects of online privacy, and together they provide meaningful protection against various tracking and surveillance methods.

## Conclusion

Enabling DNS Over HTTPS in Chrome is one of the simplest yet most effective steps you can take to improve your online privacy and security. The feature is built directly into Chrome, requires no additional software, and can be enabled in just a few clicks.

By encrypting your DNS queries, you protect your browsing activity from network observers, gain protection against DNS-based attacks, and take control of who can see which websites you visit. With multiple DoH providers available, you can choose the one that best fits your priorities, whether that is speed, privacy, security, or additional features like ad blocking.

Take a few minutes today to enable DoH in Chrome. Your browsing history will thank you.
