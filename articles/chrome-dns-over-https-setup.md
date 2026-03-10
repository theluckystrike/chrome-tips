---
layout: post
title: "Chrome DNS Over HTTPS Setup Guide"
<<<<<<< HEAD
description: "Learn how to set up DNS Over HTTPS (DoH) in Chrome for enhanced privacy and security. Complete guide covering secure DNS providers, custom DNS configuration, and privacy benefits."
date: 2026-03-10
categories: [security, privacy, chrome-tips]
tags: [dns-over-https, chrome-security, privacy, secure-dns, doh, encrypted-dns]
=======
description: "Learn how to enable and configure DNS Over HTTPS (DoH) in Chrome for enhanced privacy, security, and faster browsing. Complete setup guide with provider recommendations."
date: 2026-01-15
categories: [privacy, security, chrome]
tags: [dns-over-https, chrome-privacy, secure-dns, doh, browser-security]
>>>>>>> consumer/a4-chrome-dns-over-https-setup
author: theluckystrike
---

# Chrome DNS Over HTTPS Setup Guide

<<<<<<< HEAD
In an era where online privacy is increasingly under threat, understanding and implementing DNS Over HTTPS (DoH) has become essential for anyone who wants to browse the web more securely. Chrome, as the world's most popular web browser, offers built-in support for DoH, allowing you to encrypt your DNS queries and protect your browsing activity from prying eyes. This comprehensive guide will walk you through everything you need to know about setting up DNS Over HTTPS in Chrome, from understanding what it is and why it matters to selecting the right provider and configuring custom DNS settings.
=======
In an era where online privacy is increasingly under threat, understanding and implementing DNS Over HTTPS (DoH) in your browser is one of the most effective steps you can take to protect your browsing activity. This comprehensive guide will walk you through everything you need to know about DNS Over HTTPS, why it matters, how to set it up in Chrome, and how to choose the right provider for your needs.
>>>>>>> consumer/a4-chrome-dns-over-https-setup

## Understanding DNS and Its Privacy Implications

To appreciate the value of DNS Over HTTPS, it helps to understand what DNS does and why traditional DNS queries are problematic from a privacy standpoint.

Every time you type a website address into your browser, such as example.com, your computer needs to translate that human-readable name into a numerical IP address that servers can use to locate the website. This translation process is handled by the Domain Name System, or DNS. Your computer contacts a DNS server, asks "What is the IP address for example.com?", and receives an answer that allows your browser to connect to the correct server.

The problem with traditional DNS is that these queries are sent in plain text. This means anyone who can intercept your network traffic, such as your Internet Service Provider (ISP), network administrators, or potentially malicious actors on the same network, can see which websites you are attempting to visit. They cannot necessarily see what you do on those websites, but they can build a comprehensive profile of your browsing habits simply by watching your DNS queries.

DNS queries can also be logged, stored, and analyzed by your ISP or other entities. In many jurisdictions, ISPs are required or encouraged to retain this data, creating a detailed record of your online activity that can be subpoenaed, sold to third parties, or exploited in data breaches. This represents a significant privacy concern for anyone who wants to keep their browsing history confidential.

<<<<<<< HEAD
To fully appreciate the value of DNS Over HTTPS, it helps to understand how traditional DNS works what problems DoH solves. In a traditional DNS query, your computer sends a request to your ISP's DNS server (or whichever DNS server you've configured) using UDP or TCP port 53. This request is sent in plain text, meaning anyone along the network path can read it. Your ISP can see every domain you visit, and so can anyone else who might be monitoring your network traffic.

This lack of privacy has significant implications. Your ISP knows exactly which websites you visit, which can be used to build profiles of your browsing habits for advertising purposes or, in some jurisdictions, to comply with government data retention laws. Network administrators at work or school can see which sites you're accessing, and hackers on public WiFi networks can potentially intercept your DNS queries to learn about your browsing behavior.
=======
Beyond privacy, traditional DNS queries are also vulnerable to manipulation. Malicious actors can intercept DNS queries and return false IP addresses, redirecting you to phishing websites or malware-laden servers. This technique, known as DNS spoofing or cache poisoning, can compromise your security even if you are otherwise careful about the websites you visit.

## What Is DNS Over HTTPS and How Does It Work
>>>>>>> consumer/a4-chrome-dns-over-https-setup

DNS Over HTTPS represents a fundamental improvement over traditional DNS by encrypting your DNS queries and sending them over the secure HTTPS protocol. Instead of sending plain text queries to a DNS server, your browser encapsulates the query within an encrypted HTTPS connection, making it essentially impossible for anyone on your network or between you and the DNS server to observe which websites you are requesting.

When you enable DNS Over HTTPS in Chrome, the browser performs DNS resolution differently than it would otherwise. Rather than relying on your operating system's default DNS settings, Chrome directly contacts a DoH-compatible DNS server using HTTPS. This server processes your request and returns the encrypted response, all within the protected HTTPS tunnel.

The encryption provided by DoH solves both of the main problems with traditional DNS. First, it prevents eavesdroppers from seeing which domains you are resolving, protecting your privacy. Second, because the entire query and response are protected by HTTPS encryption and authentication, it becomes extremely difficult for attackers to intercept and tamper with your DNS queries.

It is worth noting that DNS Over HTTPS is distinct from DNSSEC, which adds cryptographic signatures to DNS responses to verify their authenticity but does not encrypt them. DoH provides both authentication and encryption, making it a more comprehensive solution for privacy and security.

<<<<<<< HEAD
Once you're in the Settings page, you'll need to find the security settings. The easiest way to do this is to use the search box at the top of the Settings page. Type "DNS" or "Secure DNS" into the search box, and Chrome will show you relevant settings. You can also navigate manually by clicking on "Privacy and security" in the left sidebar, then clicking on "Security."

Within the security settings, look for a section called "Advanced" or scroll down until you find the "Use secure DNS" option. This is the setting that controls DNS Over HTTPS in Chrome. Click on it to open the DNS configuration options.

You'll see several options for how Chrome handles DNS queries. The default setting is usually "With your current service provider," which means Chrome will use whatever DNS server your computer or network is configured to use. This typically doesn't provide any privacy or security benefits beyond what your ISP already offers.
=======
## The Privacy Benefits of Enabling DNS Over HTTPS in Chrome

Enabling DNS Over HTTPS in Chrome offers several significant privacy benefits that make it worth considering for any privacy-conscious user.

The most immediate benefit is that your ISP or network provider can no longer see which websites you are visiting based on DNS queries. While they may still be able to see that you are connecting to certain IP addresses, correlating those IP addresses with domain names becomes much more difficult without access to the DNS query data. This is particularly valuable for users who want to minimize the data footprint they leave with their ISP.

Network administrators, whether at work, school, or public WiFi hotspots, similarly lose the ability to monitor your browsing activity through DNS queries. This can be especially important in environments where network monitoring is extensive or where certain websites may be blocked based on domain names.

DNS Over HTTPS also protects against certain types of web tracking. Some tracking systems rely on observing DNS queries to build profiles of user behavior. By encrypting your DNS queries, you make it much harder for these trackers to follow you across the web.

For users concerned about government surveillance or data retention mandates, DoH adds an important layer of protection. While it does not make you invisible online, it significantly raises the bar for anyone trying to monitor your browsing habits through DNS analysis.

## The Security Benefits of DNS Over HTTPS

Beyond privacy, DNS Over HTTPS provides important security improvements that protect you from various online threats.

DNS spoofing attacks become much more difficult when DoH is enabled. Because the query and response are transmitted over an authenticated HTTPS connection, attackers cannot easily inject false DNS records into your traffic. The cryptographic protections of HTTPS ensure that you are receiving legitimate responses from the DNS server you configured.

This protection is particularly valuable when using public WiFi networks, which are often targeted by attackers looking to intercept user traffic. On an unsecured public network, traditional DNS queries are trivially easy to intercept and manipulate. With DoH enabled, even if an attacker manages to intercept your network traffic, they cannot read or modify your DNS queries.

DNS Over HTTPS also protects against man-in-the-middle attacks that rely on DNS manipulation. Phishing websites often use DNS spoofing to direct users to fake versions of legitimate sites. DoH makes these attacks significantly harder to execute reliably.

Many DoH providers also implement additional security measures, such as filtering known malicious domains or providing threat intelligence feeds. By choosing a DoH provider that offers these features, you can get enhanced protection beyond what traditional DNS provides.
>>>>>>> consumer/a4-chrome-dns-over-https-setup

To enable DNS Over HTTPS, select one of the other options. Chrome offers two main categories: using a provider like Cloudflare or Google, or setting up a custom provider. The easiest option is to select "With Cloudflare" or "With Google" from the dropdown menu. Both of these providers offer free DNS Over HTTPS services with strong privacy policies.

<<<<<<< HEAD
## Selecting the Right DNS Provider

Choosing the right DNS provider is an important decision that affects your privacy, security, and potentially your browsing speed. Let's examine the most popular options available for use with Chrome's DNS Over HTTPS feature.

Cloudflare is often recommended as the best choice for most users. Their 1.1.1.1 DNS service is known for being extremely fast, with response times often under 10 milliseconds. Cloudflare has a strong commitment to privacy and was one of the first major companies to offer free DoH. They explicitly state that they don't sell user data and that they don't log IP addresses for more than 24 hours. Their service also includes optional malware blocking through the 1.1.1.1 with WARP app, though this requires additional setup.

Google's Public DNS is another popular option, particularly for users who already trust Google with their data. Google's DNS service is extremely reliable and fast, benefiting from Google's massive infrastructure. However, some privacy-conscious users may be uncomfortable with Google collecting even more data about their browsing habits. Google states that they don't correlate DNS data with personal information, but the company's primary business model revolves around data collection.

Quad9 is an excellent choice for users who prioritize security and privacy. This service blocks connections to known malicious domains, providing protection against malware and phishing attacks. Quad9 is a non-profit organization that doesn't log personally identifiable information, making it a favorite among privacy advocates. The service is free and supported by various security organizations around the world.

For users who want even more privacy, there's also the option of running your own DNS server or using specialized privacy-focused providers. However, these options typically require more technical knowledge to set up properly.

## Setting Up Custom DNS Providers

While the built-in options for Cloudflare, Google, and Quad9 are sufficient for most users, Chrome also allows you to configure custom DNS providers. This is useful if you have a specific DNS service you prefer or if you want to use a private DNS server you've set up yourself.

To configure a custom DNS provider, go back to the DNS settings in Chrome as described earlier. Instead of selecting one of the preset providers, look for an option that says "Custom" or "With a custom provider." You'll need to enter the DNS over HTTPS URL for your chosen provider.

Finding the right URL is usually straightforward. Most DNS providers that support DoH publish their URLs on their websites. For example, Cloudflare's DoH endpoint is https://1.1.1.1/dns-query, while Google's is https://dns.google/dns-query. You'll need to enter the complete URL in the field provided.

Custom DNS can be particularly useful in enterprise environments where organizations want to maintain DNS logging for compliance purposes while still encrypting the connections. It can also be useful for users who want to use specialized DNS services like Pi-hole with DoH capabilities, though this requires additional configuration.

When setting up custom DNS, make sure you trust the provider you're connecting to. Since all your DNS queries will be routed through this provider, you're placing a significant amount of trust in them. Research the provider's privacy policy and reputation before entrusting them with your DNS queries.

## Privacy Benefits of DNS Over HTTPS

The primary reason most users enable DNS Over HTTPS is for the privacy benefits it provides. Let's explore in detail how DoH protects your privacy and why it matters for your online security.

When you browse the internet without DoH, your DNS queries are sent in plain text. This means your ISP can see every website you visit, creating a detailed record of your browsing habits. They know exactly which domains you access, when you access them, and how often you visit certain sites. This information can be used for various purposes, from targeted advertising to complying with government data requests.

By encrypting your DNS queries with DoH, you prevent your ISP from seeing which websites you're visiting. While they can still see that you're making HTTPS connections, they can't determine what those connections are for or which specific domains you're accessing. This significantly reduces the amount of data your ISP can collect about your browsing habits.

Public WiFi networks pose particular privacy risks because they're often unsecured. Anyone connected to the same network can potentially intercept your traffic and see your DNS queries. DoH protects you from this by encrypting your queries, making it impossible for other users on the same network to see what websites you're visiting.

It's important to understand that DoH doesn't make you completely anonymous online. While it hides your DNS queries, other aspects of your browsing can still be tracked. Websites you visit can still see your IP address, and if you're logged into your Google account while browsing, Google can still track your activity. Additionally, if you use Chrome and are signed in, Google may still collect some data about your browsing. For maximum privacy, consider using additional tools like VPNs or privacy-focused browsers alongside DoH.

## Security Benefits Beyond Privacy

DNS Over HTTPS provides significant security benefits that go beyond just privacy. Understanding these benefits can help you appreciate why this technology is considered an important advancement in internet security.

One of the most important security benefits is protection against DNS spoofing attacks. In these attacks, a malicious actor on your network attempts to redirect you to fake websites by providing incorrect DNS responses. For example, you might type in your bank's website address, but the attack could redirect you to a lookalike site designed to steal your login credentials. Because DoH uses encrypted connections, it's much harder for attackers to intercept and modify your DNS responses.

DoH also provides protection against man-in-the-middle attacks, where someone intercepts your communication with a website to eavesdrop or modify the content. The encryption used in DoH makes it much more difficult for attackers to insert themselves between you and the DNS server you're using.

Many DNS providers that offer DoH also include additional security features. For example, some providers block known malicious domains, helping protect you from malware and phishing attempts. This is particularly useful for users who don't have other security software installed, as it provides an additional layer of defense against web-based threats.

## Common Questions and Troubleshooting

Even though setting up DNS Over HTTPS in Chrome is straightforward, you might encounter some questions or issues. Here are answers to common questions and troubleshooting tips.

One common question is whether DoH will slow down your browsing. In practice, the encryption overhead is minimal and most users don't notice any difference in speed. In fact, because many DoH providers have fast servers and optimized infrastructure, you might actually experience faster page loads compared to your ISP's DNS servers.

If you encounter issues with DoH, the first step is to verify that it's actually enabled. Some networks, particularly corporate or school networks, may have policies that interfere with DoH. If DoH isn't working, you might see slower page loads or DNS error messages.

Another issue can occur if your chosen DNS provider is temporarily unavailable. If this happens, Chrome should automatically fall back to using your system's default DNS settings, so you shouldn't lose internet connectivity entirely. However, your privacy protection will be reduced until the DoH service is available again.

If you're experiencing issues, try switching to a different DNS provider to see if that resolves the problem. Cloudflare's 1.1.1.1 is generally the most reliable option, but having a backup provider configured can help ensure continuous service.

## Additional Privacy Measures to Consider

While DNS Over HTTPS is an important step toward better privacy, it's just one piece of the puzzle. For comprehensive online privacy, consider implementing additional measures alongside DoH.

Using a reputable VPN service can significantly enhance your privacy by encrypting all your internet traffic, not just DNS queries. A good VPN also hides your IP address from the websites you visit, making it much harder to track your online activities. However, it's important to choose a VPN provider that doesn't log your activity, as you're essentially moving your trust from your ISP to the VPN provider.

The Chrome Web Store offers various extensions that can enhance your privacy. Consider using extensions like uBlock Origin to block ads and trackers, or privacy-focused extensions that block social media tracking. For users who want to manage their tabs more efficiently while maintaining privacy, [Tab Suspender Pro](https://chrome.google.com/webstore/detail/tab-suspender-pro/fkdfhfhmdjdhaickjhlbgaimmmnjknbc) is an excellent extension that automatically suspends inactive tabs to save memory while keeping your browsing data local to your device.

Regularly clearing your browser's cache and cookies can also help maintain privacy, as these can contain tracking data that reveals your browsing habits. Chrome provides easy options to clear this data, and you can configure it to automatically clear data when you close the browser.

## Conclusion

Setting up DNS Over HTTPS in Chrome is one of the simplest yet most effective steps you can take to improve your online privacy and security. By encrypting your DNS queries, you prevent ISPs, network administrators, and potential attackers from seeing which websites you visit. This is a fundamental improvement to how your browser communicates with the internet, and it's available right in Chrome's settings with no additional software required.

Whether you choose Cloudflare for its speed and privacy commitment, Google for its reliability, Quad9 for its security features, or a custom provider for specific needs, enabling DoH is a worthwhile investment in your online privacy. The setup process takes just a few minutes, and the benefits of encrypted DNS queries far outweigh any potential drawbacks.

Remember that DoH is just one layer of your overall online security posture. For comprehensive protection, consider combining it with other privacy tools and practices. With DNS Over HTTPS enabled, you're taking an important step toward a more private and secure browsing experience.
=======
Choosing the right DoH provider is an important decision that affects your privacy, security, and potentially your browsing experience. Several factors should guide your choice.

### Major DNS Over HTTPS Providers

There are numerous DoH providers available, each with different characteristics, privacy policies, and feature sets. Here are some of the most popular options.

**Cloudflare** offers one of the most well-known DoH services, with the addresses 1.1.1.1 and 1.0.0.1. Cloudflare has a strong privacy commitment and has implemented a no-logging policy for their DNS service. They also offer a malware-blocking option that filters requests to known malicious domains. Their service is known for being extremely fast, often faster than traditional DNS.

**Google Public DNS** is another major option, with addresses 8.8.8.8 and 8.8.4.4. Google's DNS service is highly reliable and fast, benefiting from Google's extensive infrastructure. However, some privacy-conscious users may be uncomfortable sending their DNS queries to Google, given the company's data collection practices elsewhere.

**Quad9** is a security-focused DoH provider that blocks connections to known malicious domains. They do not log IP addresses and have a strong commitment to privacy and security. Their focus on blocking malware makes them a good choice for users prioritizing security.

**NextDNS** offers customizable DNS services with various filtering options. They have both free and paid tiers, allowing you to choose the level of service and privacy protection that suits your needs. Their service includes blocking trackers, ads, and malicious domains.

**AdGuard DNS** provides DNS resolution with built-in ad and tracker blocking. They offer both a standard service and a family-oriented service that includes additional filtering for inappropriate content.

### Factors to Consider When Choosing

When selecting a DoH provider, consider the following factors.

**Privacy Policy**: Review the provider's privacy policy to understand what data they collect and how they handle it. Look for providers that explicitly state they do not log IP addresses or DNS query data, or that delete such data promptly.

**Security Features**: Some providers offer additional security features such as malware blocking, phishing protection, or threat intelligence integration. These features can provide valuable additional protection beyond basic DNS resolution.

**Speed and Reliability**: The speed of your DNS resolution can affect your overall browsing experience. Major providers like Cloudflare and Google typically offer excellent performance, but you may want to test several options to find the fastest for your location.

**Logging Practices**: Even providers that claim not to log may retain some data for operational purposes. Understanding exactly what is logged and for how long is important for making an informed choice.

**Transparency and Open Source**: Some providers make their DNS software open source or publish transparency reports about requests they receive. These practices can increase trust in the provider's commitments.

For most users, Cloudflare or Quad9 offer an excellent balance of privacy, security, and performance. Cloudflare's 1.1.1.1 service is particularly popular due to its speed and strong privacy commitments, while Quad9's security-focused approach appeals to users prioritizing malware protection.

## How to Enable DNS Over HTTPS in Chrome

Enabling DNS Over HTTPS in Chrome is straightforward. Follow these steps to configure your browser.

First, open Chrome and click the three-dot menu in the upper right corner of the window. From the dropdown menu, select "Settings" to open the Chrome settings page.

In the settings page, click on "Privacy and security" in the left sidebar. This will expand a menu of privacy-related options.

Scroll down to the "Security" section and click on it. Look for the option labeled "Use Secure DNS" with a description about how this setting enables DNS Over HTTPS.

Click on the "Use Secure DNS" option to open the DNS configuration dropdown. Here you will see several options.

The first option, "With your current service provider," will attempt to use DoH with your existing DNS provider if they support it. This is the default setting in some regions and provides a quick way to enable DoH without changing providers.

The second option, "Choose a service provider," allows you to select from a list of popular DoH providers. Clicking on this option reveals a dropdown where you can select providers like Cloudflare, Google, Quad9, or others.

To manually configure a specific provider not listed, select "Custom" and enter the DoH URL of your chosen provider. This gives you flexibility to use any DoH-compatible service.

For most users, selecting Cloudflare or Google from the provider list is the simplest approach. Both offer excellent performance and reliability. If you prefer a security-focused provider, select Quad9.

After selecting your provider, Chrome will immediately begin using DNS Over HTTPS for all DNS resolutions. You do not need to restart the browser for the change to take effect.

To verify that DoH is working, you can visit a website like 1.1.1.1/help or dnsleaktest.com, which can confirm that your DNS queries are being handled by your chosen DoH provider.

## Configuring Custom DNS Providers in Chrome

While Chrome includes several popular DoH providers in its settings, you may want to use a provider that is not on the default list. This could be a specialized provider with unique features, a private DNS server you run yourself, or a regional provider with better performance in your area.

To add a custom provider, select the "Custom" option in the "Choose a service provider" dropdown. A text field will appear where you can enter the DoH template URL for your provider.

The DoH URL format typically looks something like "https://dns.example.com/dns-query" or "https://dns.example.com/resolve". You will need to obtain the correct URL from your provider's documentation.

When entering a custom provider URL, ensure that the URL uses HTTPS. Chrome will not accept HTTP URLs for DoH, as the encryption would be defeated.

After entering your custom URL, Chrome will immediately begin using it for DNS resolution. Test that everything is working by visiting a DNS testing website.

Custom providers can be useful in enterprise environments where organizations run their own DNS infrastructure with DoH support, or for users who want maximum control over their DNS configuration.

## Troubleshooting DNS Over HTTPS Issues

While DNS Over HTTPS typically works without issues, you may occasionally encounter problems. Here are some common issues and their solutions.

If you find that certain websites are not loading after enabling DoH, try switching to a different DoH provider. Some providers may block certain domains or have temporary issues with specific DNS records.

If you cannot access any websites after enabling DoH, check that your internet connection is working and that you can reach other services. You can temporarily disable DoH to determine if the issue is related to your DNS configuration.

Some corporate networks may block DoH connections or may require DoH to be configured with specific servers to work within their infrastructure. If you are on a work or school network, check with your IT department for the appropriate DoH configuration.

Browser extensions that modify DNS settings may conflict with Chrome's DoH configuration. If you use extensions that handle DNS or proxy settings, try disabling them to see if that resolves the issue.

## Enhancing Your Privacy Setup with Related Tools

While DNS Over HTTPS is a powerful privacy tool, it is most effective as part of a comprehensive approach to browser security and privacy.

**Tab Suspender Pro** is a Chrome extension that can complement your privacy setup by automatically managing open tabs. By suspending tabs you are not actively using, it reduces memory usage and can improve browser performance. The extension also provides visibility into which tabs are consuming resources, helping you maintain better control over your browsing environment. When combined with DNS Over HTTPS, you create a more private and efficient browsing experience.

Using a privacy-focused search engine alongside DoH can further enhance your privacy. Search engines like DuckDuckGo, Startpage, or Brave Search do not track your searches, complementing the protection DoH provides for DNS queries.

Keeping your browser updated ensures that you have the latest security patches and privacy features. Chrome regularly updates its DoH implementation and may add new providers or features over time.

## Understanding the Limitations of DNS Over HTTPS

While DNS Over HTTPS significantly improves your privacy and security, it is important to understand what it does and does not protect.

DoH encrypts your DNS queries, but it does not hide the IP address of the server you are connecting to from your ISP or network observers. They can still see which IP addresses you connect to, even if they cannot determine the domain names. For full IP address masking, you would need to use a VPN or Tor in addition to DoH.

Websites you visit can still potentially track you through cookies, browser fingerprinting, and other techniques. DoH only protects the DNS resolution step of your browsing.

Your DoH provider still sees your DNS queries, although reputable providers have strict privacy policies. Choosing a provider you trust is important because they will have access to this data.

DoH does not protect against all forms of DNS-based attacks. While it prevents most man-in-the-middle attacks, sophisticated attackers with access to your machine or the DNS provider itself could still potentially manipulate DNS responses.

## Final Thoughts

Enabling DNS Over HTTPS in Chrome is one of the most impactful steps you can take to improve your online privacy and security. By encrypting your DNS queries, you prevent ISPs, network administrators, and other observers from seeing which websites you visit. The protection against DNS spoofing adds an important security layer, particularly when using public networks.

The setup process takes only a few minutes, and the benefits are immediate and significant. Whether you choose Cloudflare for its speed, Quad9 for its security focus, or another provider that meets your specific needs, you will be taking a meaningful step toward a more private browsing experience.

Remember that DNS Over HTTPS is just one component of a comprehensive privacy strategy. Combining it with other privacy tools and practices, such as using privacy-focused extensions like Tab Suspender Pro to manage your tabs, using encrypted messaging apps, and being thoughtful about the information you share online, creates defense in depth that protects your digital life.

Take a few minutes today to enable DNS Over HTTPS in Chrome. Your browsing activity will be more private, your connections more secure, and you will have taken an important stand for your digital rights in an increasingly connected world.

Built by theluckystrike — More tips at [zovo.one](https://zovo.one)
>>>>>>> consumer/a4-chrome-dns-over-https-setup
