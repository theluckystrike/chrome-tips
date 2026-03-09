---
layout: post
title: "Chrome DNS Over HTTPS How to Enable"
description: "Learn how to enable DNS over HTTPS in Chrome to improve your privacy and security while browsing. Simple steps anyone can follow."
date: 2026-03-09
categories: [privacy, security, network]
tags: [dns-over-https, chrome-privacy, secure-browsing, https-dns, browser-security]
author: theluckystrike
---

# Chrome DNS Over HTTPS How to Enable

If you have ever searched for "chrome dns over https how to enable," you probably want to make your browsing more private and secure. Many people are concerned about their internet service providers being able to see every website they visit. DNS over HTTPS, sometimes called DoH, is a technology that helps keep your browsing more private by encrypting the requests your browser makes to find websites.

When you type a website address into Chrome, your browser needs to figure out where that website is located on the internet. This process is called DNS lookup, and it normally happens in plain text. That means anyone who can see your internet traffic, including your internet service provider, can see which websites you are visiting. Enabling DNS over HTTPS encrypts these lookups so that only you and the DNS server know which websites you are trying to visit.

## Why DNS Over HTTPS Matters

Your internet service provider can see the websites you visit when you use regular DNS. They know because every time your computer looks up a website address, it sends a request to a DNS server in plain text. This request contains the website name you are trying to visit. Your ISP can log these requests and build a record of your browsing habits.

There are other reasons why you might want to enable DNS over HTTPS in Chrome. Sometimes DNS servers run by your ISP can be slow, which makes websites take longer to load. Using a secure DNS service like Cloudflare or Google DNS can sometimes make your browsing faster. Additionally, DNS over HTTPS can protect you from certain types of attacks where someone tries to redirect you to fake websites.

Another benefit is that DNS over HTTPS can prevent your ISP from blocking certain websites. Since your ISP cannot see which websites you are requesting, they cannot easily block specific sites based on DNS lookups. This is particularly useful for people who live in countries with internet restrictions or who want to access content that their ISP might block.

## What You Need Before You Start

Before you enable DNS over HTTPS in Chrome, there are a few things you should know. First, you need to make sure Chrome is updated to the latest version. Google regularly updates Chrome with new features and security improvements, and DNS over HTTPS requires a relatively recent version of the browser.

Second, you should understand that DNS over HTTPS only encrypts the part of your browsing where your browser looks up website addresses. The rest of your connection to websites is still visible unless those websites also use HTTPS. Fortunately, most popular websites now use HTTPS by default, so most of your browsing activity is already encrypted.

Finally, keep in mind that enabling DNS over HTTPS means you are trusting the DNS service you choose with your browsing data. Google DNS and Cloudflare DNS are popular choices because they have strong privacy policies, but you should pick a provider that you feel comfortable trusting with this information.

## How to Enable DNS Over HTTPS in Chrome

Enabling DNS over HTTPS in Chrome is straightforward and does not require any technical knowledge. Here are the steps to follow.

First, open Chrome on your computer. Click on the three dots in the upper right corner of the browser window. This opens a menu with various options. Look for the option that says "Settings" and click on it.

In the Settings page, you will see a search box at the top. Type "security" into this search box. Chrome will show you several security-related settings. Look for a section called "Security" or "Privacy and security" depending on your Chrome version.

Within the security settings, you should find an option that says "Use secure DNS" or "DNS over HTTPS." The exact wording might vary slightly depending on your Chrome version. Click on this option to open the DNS settings.

You will see a few choices for how to handle DNS lookups. The first option is probably "With your current service provider," which means Chrome will use whatever DNS server your computer is configured to use. This is the default setting and does not provide the privacy benefits of DNS over HTTPS.

Look for an option that says "With Cloudflare," "With Google," or "With a custom provider." Any of these options will enable DNS over HTTPS. If you see "With Cloudflare (1.1.1.1)" or a similar option, this is a good choice because Cloudflare has a strong commitment to privacy and does not sell user data.

Select the option that enables DNS over HTTPS. Chrome might show you a warning about using a custom DNS provider, but this is normal and you can proceed. Once you select the option, Chrome will immediately start using DNS over HTTPS for all your browsing.

## Choosing a DNS Provider

If you want to customize your DNS provider, you can usually find more options in Chrome's advanced settings. Look for a way to enter a custom DNS provider URL. This might be under "Custom" or "Enter custom provider" in the DNS settings.

Google DNS is a popular choice for DNS over HTTPS. You can find the addresses for Google's DNS service online. Cloudflare is another excellent choice, particularly if privacy is your main concern. Both services are fast, reliable, and have strong privacy policies.

Some people prefer to use their own DNS provider based on specific needs. For example, you might choose a DNS provider that blocks ads or malicious websites. Chrome does not provide these features natively, but you can find DNS providers that offer them.

When choosing a DNS provider, consider what matters most to you. If you want the simplest experience, stick with Cloudflare or Google. If you want specific features like ad blocking at the DNS level, look for a provider that offers those features.

## Verifying DNS Over HTTPS Is Working

After you enable DNS over HTTPS, you might want to confirm that it is actually working. There are several websites that can test whether your browser is using DNS over HTTPS.

Visit a website that offers DNS testing services. These sites can tell you if your browser is making secure DNS queries. If everything is working correctly, the test will show that you are using DNS over HTTPS.

You can also check Chrome's settings to confirm that DNS over HTTPS is enabled. Go back to the security settings where you turned it on and verify that the option you selected is still active. Sometimes browser updates can reset settings, so it is worth checking occasionally.

If the test shows that DNS over HTTPS is not working, try restarting Chrome. Close all Chrome windows completely and then reopen the browser. This ensures that the new settings take full effect.

## What to Do If You Encounter Problems

Sometimes enabling DNS over HTTPS can cause issues with certain websites or network configurations. If you find that some websites are not loading after enabling this feature, you might need to try a different DNS provider.

Try switching from Cloudflare to Google DNS or vice versa. One provider might work better with your network than the other. You can do this by going back to the DNS settings in Chrome and selecting a different provider.

If problems persist, you can temporarily disable DNS over HTTPS by going back to the settings and selecting the option to use your current service provider. This uses the standard DNS lookup method and should restore access to websites that were not working.

Some corporate networks and school networks block DNS over HTTPS or have specific requirements for DNS lookups. If you are on such a network, you might not be able to use DNS over HTTPS while connected to that network. You can enable it again when you are on a different network.

## Other Ways to Protect Your Privacy

Enabling DNS over HTTPS is a great step toward more private browsing, but there are other things you can do as well. Consider using a privacy-focused search engine that does not track your searches. You can also install extensions that block tracking scripts and ads.

If you are looking for ways to improve your Chrome experience overall, consider trying extensions like Tab Suspender Pro. This extension helps you manage open tabs more efficiently, which can improve browser performance and reduce memory usage. It is one of many tools available that can make your browsing experience better.

Remember that DNS over HTTPS is just one piece of the privacy puzzle. Your internet service provider can still see which IP addresses you connect to, and websites can still track you through cookies and other methods. However, encrypting your DNS lookups is an important step that makes it harder for anyone to monitor your browsing activity.

---

Tips from the team behind Tab Suspender Pro and the Zovo extension suite at zovo.one
