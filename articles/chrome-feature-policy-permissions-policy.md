---
layout: post
title: Chrome Feature Policy vs Permissions Policy Understanding the Difference
description: Learn the key differences between Chrome Feature Policy and Permissions
  Policy.
date: '2026-03-11'
last_modified_at: '2026-03-12'
permalink: chrome-feature-policy-permissions-policy
categories:
- security
- web-development
- headers
tags:
- chrome
- feature-policy
- permissions-policy
- http-headers
- security
- web-development
author: theluckystrike
---
# Chrome Feature Policy vs Permissions Policy: Understanding the Difference

If you have been working with web security headers, you may have encountered both the Feature-Policy and Permissions-Policy headers. These two headers are closely related, and understanding their relationship is essential for properly securing your web applications. This article will clarify what each header does, how they differ, and how to use them effectively in Chrome and other modern browsers.

## What Is Feature Policy?

The **Feature-Policy** header was the original HTTP header introduced to give website owners control over which browser features and APIs their sites could use. It allowed developers to enable or disable specific capabilities such as geolocation, camera access, microphone access, and more directly from the server side.

When the Feature-Policy header was first introduced, it served as a powerful security mechanism. Website owners could explicitly declare which features their pages required, and the browser would enforce those restrictions automatically. This approach provided an additional layer of protection beyond what JavaScript-based controls could offer.

The syntax for Feature-Policy was straightforward. You would specify a feature name followed by a list of allowed origins. For example, to allow camera access only from your own domain, you would include a header like `Feature-Policy: camera 'self'`. This meant that attempts to access the camera from any other origin would be blocked.

However, as the web platform evolved, the Web Incubator Community Group decided to rename this header to better reflect its purpose. The new name more accurately described what the header actually did, which was controlling permissions rather than just enabling features.

## What Is Permissions Policy?

The **Permissions-Policy** header is essentially the successor to Feature-Policy. It provides the same functionality but with a new name that more clearly indicates its purpose. The header controls which browser features and APIs can be used on your website, giving you fine-grained control over permissions at the HTTP level.

The Permissions-Policy header works by allowing website owners to specify which origins can access specific features. When a feature is disabled or restricted, any attempt to use that feature from an unauthorized origin will be blocked by the browser. This happens before the JavaScript code even executes, providing a robust security layer.

The header supports dozens of features including geolocation, camera, microphone, fullscreen mode, payment requests, USB device access, clipboard operations, and many more. Each feature can be individually configured with different origin restrictions, giving you precise control over your site's capabilities.

## Key Differences Between Feature-Policy and Permissions-Policy

The primary difference between Feature-Policy and Permissions-Policy is the name. Functionally, they are identical. Permissions-Policy was chosen as the new name because it better describes what the header actually controls. The header does not simply enable or disable features; it controls the permissions that websites have to use those features.

Another difference is browser support evolution. When Feature-Policy was introduced, browser support was limited. Today, Permissions-Policy enjoys broad support across Chrome, Edge, Firefox, and Safari. The older Feature-Policy header is still recognized by some browsers for backward compatibility, but it is considered deprecated.

The documentation and community resources have also shifted toward Permissions-Policy. When looking for information about controlling browser features via HTTP headers, you should search for Permissions-Policy to find the most up-to-date information and examples.

## Why Should You Use These Headers?

There are several compelling reasons to implement either Feature-Policy or Permissions-Policy on your website. First, these headers significantly enhance security by limiting what your site can do. If your application does not need camera or microphone access, blocking those features ensures that no malicious script can exploit them, even if it manages to run on your page.

Second, these headers protect user privacy. Users are increasingly concerned about how websites access their personal information. By explicitly disabling features you do not need, you demonstrate a commitment to privacy and give users confidence that their data is not being accessed unnecessarily.

Third, these headers provide defense in depth. Even if a vulnerability is discovered in one of your scripts, the policy headers can prevent that script from accessing certain APIs, limiting the potential damage. This layered approach to security is considered a best practice in web development.

## Implementing Permissions Policy in Chrome

Implementing the Permissions-Policy header is straightforward and depends on your web server configuration. Here is the basic syntax:

```
Permissions-Policy: geolocation=(), camera=(), microphone=()
```

This example disables geolocation, camera, and microphone access entirely. The empty parentheses indicate that no origins are allowed to use these features. To allow features only from your own domain, you would use:

```
Permissions-Policy: geolocation=(self), camera=(self), microphone=(self)
```

For Apache servers, add the header in your .htaccess file:

```apache
Header set Permissions-Policy "geolocation=(), camera=(), microphone=()"
```

For Nginx, add it to your server block:

```nginx
add_header Permissions-Policy "geolocation=(), camera=(), microphone=()";
```

If you use platforms like Netlify or Vercel, you can configure custom headers in your deployment configuration file.

## Testing Your Implementation

After implementing the Permissions-Policy header, you should verify that it works correctly. In Chrome, open Developer Tools and navigate to the Application tab. Look for the Permissions-Policy section, which displays all the features and their current status for the page.

You can also use online tools like securityheaders.com to check your site's headers and ensure the Permissions-Policy header is properly configured. These tools provide detailed reports on your security header implementation.

Another testing approach is to attempt using a feature you have disabled. For instance, if you blocked the geolocation API, try calling `navigator.geolocation.getCurrentPosition()` in the console. If properly blocked, the browser will prevent the call from executing.

## A Practical Tip

If you want to optimize your Chrome experience and reduce browser resource consumption, consider using **Tab Suspender Pro** to automatically suspend tabs you are not actively using. This can significantly reduce memory usage and improve performance, especially when you have many tabs open. Combined with proper use of Permissions-Policy headers on your websites, you can create a more secure and efficient browsing environment.

## Final Thoughts

Understanding the relationship between Feature-Policy and Permissions-Policy is important for modern web development. While Feature-Policy was the original name, Permissions-Policy is now the standard that you should use. By implementing these headers, you take control of which browser features your website can access, enhancing security and protecting user privacy. Take time to review what features your site actually needs, and disable everything else.

## Related Articles
- [Chrome Permissions Policy Header Explained](/chrome-tips/chrome-permissions-policy-header-explained/)
- [Chrome Document Policy: The New Security Feature You Need to Know](/chrome-tips/chrome-document-policy-new-security-feature/)
- [Chrome Content Security Policy Explained: A Complete Guide](/chrome-tips/chrome-content-security-policy-explained/)

Built by theluckystrike — More tips at [zovo.one](https://zovo.one)

---

## Related Articles
* [Chrome Permissions Policy Header Explained](/articles/chrome-permissions-policy-header-explained/)
* [Chrome Biometric Authentication for the Web](/articles/chrome-biometric-authentication-web/)
* [Chrome Site Isolation: What It Is and Why It Matters for Your Security](/articles/chrome-site-isolation-security-feature/)
