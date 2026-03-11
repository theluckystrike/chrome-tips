---
layout: default
title: "Chrome Payment Request API Guide"
<<<<<<< HEAD
description: "Learn how to implement Chrome Payment Request API for seamless digital wallet payments, Google Pay integration, shipping options, and multiple payment methods on your website."
date: 2026-01-20
categories: [chrome, payment, web-development, api]
tags: [payment-request-api, google-pay, digital-wallet, ecommerce, chrome-api]
=======
description: "Learn how to use Chrome Payment Request API for digital wallets, Google Pay integration, shipping options, and payment methods. A complete developer guide for web payments."
date: 2026-03-11
categories: [chrome, development, payments, api]
tags: [payment-request-api, digital-wallet, google-pay, online-payments, checkout, web-development]
>>>>>>> consumer/a7-chrome-payment-request-api
author: theluckystrike
---

# Chrome Payment Request API Guide

<<<<<<< HEAD
The Chrome Payment Request API represents one of the most significant advancements in modern web commerce. This powerful browser API enables websites to accept payments through a native, secure interface that connects directly to the user's preferred payment methods, including digital wallets like Google Pay, Apple Pay, and various card payments. For e-commerce businesses and web developers, understanding how to implement this API can dramatically improve checkout conversion rates while providing a smoother, more trustworthy payment experience for customers.
=======
The Chrome Payment Request API represents one of the most significant advancements in web payment technology over the past decade. This comprehensive guide will walk you through everything you need to know about implementing and using this powerful API, from basic concepts to advanced integration techniques. Whether you are a web developer looking to streamline checkout processes or a curious user wanting to understand how modern online payments work, this guide has you covered.
>>>>>>> consumer/a7-chrome-payment-request-api

## Understanding the Payment Request API

<<<<<<< HEAD
The Payment Request API is a browser-native standard that allows web developers to integrate a standardized payment checkout flow directly into their websites. Rather than building custom checkout forms from scratch, developers can now leverage a system-level payment UI that browsers like Chrome provide. This approach offers several compelling advantages that have made it increasingly popular among e-commerce platforms.

First and foremost, the Payment Request API dramatically reduces the amount of code developers need to write and maintain. Instead of creating complex forms that collect payment details, validating those details, securely transmitting them to payment processors, and handling various error states, developers can make a single API call that handles all of these complexities. The browser manages the entire interaction, from displaying the payment sheet to collecting user credentials and returning the payment data in a standardized format.

Security is another major benefit that cannot be overstated. When users enter their payment information through the Payment Request API, that data never touches your servers directly. Instead, the browser handles all sensitive information and passes only tokenized payment data to your backend. This significantly reduces your compliance burden since you never handle raw credit card numbers, and it gives users confidence that their financial information is protected by the browser's security infrastructure.

The user experience improvements are perhaps the most immediately visible benefit. The Payment Request API enables what is commonly called a "two-click" checkout, where users can complete a purchase with just two clicks after their payment information is stored in the browser. This is dramatically faster than traditional checkout flows that can require filling out multiple form fields, creating accounts, and navigating through various checkout steps. Faster checkouts mean fewer abandoned carts and higher conversion rates for merchants.

## Digital Wallets and the Payment Request Ecosystem

Digital wallets have fundamentally transformed how consumers make online purchases, and the Payment Request API was designed with this transformation in mind. When you implement this API, you are essentially creating a bridge between your website and the digital wallet ecosystem that users have come to expect.

The most prominent digital wallet in the Chrome ecosystem is Google Pay. Originally launched as Android Pay and later merged with Google Wallet, Google Pay has become the default payment method for millions of Chrome users. When users have Google Pay set up on their Chrome browser or Android device, the Payment Request API automatically detects this and presents Google Pay as a primary payment option in the payment sheet. This seamless integration means users do not need to manually enter card details every time they make a purchase.

Beyond Google Pay, the Payment Request API supports a variety of other digital payment methods. Users can store multiple credit cards, debit cards, and even loyalty program information in their browser's payment locker. When they initiate a purchase on your site, they can select from any of their stored payment methods, giving them flexibility while keeping the checkout process simple and fast.

The beauty of this ecosystem is that it continues to grow as more payment providers and banks adopt the Payment Request standard. This means that as new digital wallet services launch or existing ones expand their offerings, your website can automatically support these new methods without requiring code changes. The standardization inherent in the Payment Request API creates a future-proof payment infrastructure for your business.

## Implementing Google Pay Through the Payment Request API

Integrating Google Pay through the Payment Request API requires understanding both the browser-side implementation and the backend processing flow. The process begins with checking whether the Payment Request API is supported in the user's browser and whether Google Pay is available as a payment method.

The first step in implementation is to create a PaymentRequest object in JavaScript. This object defines what payment methods you accept and what information you need from the user. For Google Pay integration, you will include the standard payment method identifiers that Google Pay recognizes. You also specify whether you need shipping information, which brings us to another powerful feature of the API.

```javascript
const supportedInstruments = [
  {
    supportedMethods: 'https://google.com/pay',
    data: {
      environment: 'TEST',
      apiVersion: 2,
      apiVersionMinor: 0,
      merchantInfo: {
        merchantName: 'Your Merchant Name',
        merchantId: 'your-merchant-id'
      },
      transactionInfo: {
        currencyCode: 'USD',
        totalPriceStatus: 'FINAL',
        totalPrice: '100.00'
      }
    }
  },
  {
    supportedMethods: 'basic-card',
    data: {
      supportedNetworks: ['visa', 'mastercard', 'amex']
    }
  }
];

const details = {
  displayItems: [
    {
      label: 'Product Name',
      amount: { currency: 'USD', value: '100.00' }
    }
  ],
  total: {
    label: 'Total',
    amount: { currency: 'USD', value: '100.00' }
  }
};

const paymentRequest = new PaymentRequest(supportedInstruments, details);
```

This code creates a payment request that supports both Google Pay and basic card payments. The Google Pay configuration includes your merchant credentials, which you obtain through the Google Pay developer console, and specifies the transaction details. The basic-card configuration defines which card networks you accept.

Once you have created the PaymentRequest object, you show the payment sheet by calling the show() method. This is where the magic happens from a user experience perspective. The browser displays a native payment sheet that shows the user their available payment options, including any Google Pay accounts they have configured. The user selects their preferred method and completes any required authentication, and the browser returns the payment data to your JavaScript code.

## Handling Shipping Information and Options

One of the most valuable features of the Payment Request API is its built-in support for collecting shipping information. For e-commerce businesses that sell physical goods, shipping address collection has traditionally been a separate friction point in the checkout process. The Payment Request API streamlines this by integrating shipping information collection directly into the payment flow.

When creating your PaymentRequest object, you can specify that you need shipping information by including shipping options in the details object. You can define different shipping methods with associated costs, such as standard shipping, express shipping, or international shipping. The API handles presenting these options to the user and collecting their preferred shipping address.

The shipping address collection works seamlessly with Google Pay integration. When users have a Google Pay account with a saved address, the Payment Request API can use that address as a default or allow the user to select from multiple saved addresses. This means customers who already have their information stored can complete both payment and shipping in just a few clicks.

Implementing shipping address collection requires handling several events that the PaymentRequest object emits. The most important is the shippingaddresschange event, which fires when the user selects or changes their shipping address. In your event handler, you can validate the address, calculate appropriate shipping costs based on the destination, and update the payment details to reflect the new total including shipping.

```javascript
paymentRequest.addEventListener('shippingaddresschange', (event) => {
  const address = event.shippingAddress;
  
  // Validate address and calculate shipping
  const shippingCost = calculateShipping(address);
  
  // Update payment details with new total
  event.updateWith({
    total: {
      label: 'Total',
      amount: { currency: 'USD', value: (100 + shippingCost).toFixed(2) }
    },
    shippingOptions: [
      {
        id: 'standard',
        label: 'Standard Shipping',
        amount: { currency: 'USD', value: shippingCost.toFixed(2) }
      }
    ]
  });
});
```

This dynamic updating allows you to provide accurate shipping costs based on the specific address the customer provides, which is essential for businesses that ship internationally or have complex shipping rate structures.
=======
The Payment Request API is a browser-native feature that enables websites to collect payment information from users through a standardized, secure interface built directly into Chrome. Rather than requiring users to manually enter credit card numbers, billing addresses, and shipping details on every purchase, this API allows Chrome to retrieve previously saved information and present it in a consistent, user-friendly dialog.

This technology emerged from a collaborative effort among major browser vendors, including Google, Apple, and Microsoft, through the W3C Web Payments Working Group. The goal was simple yet ambitious: create a universal standard that would make online payments faster, more secure, and more consistent across the entire web. Before this API existed, each e-commerce website implemented its own checkout forms, leading to a fragmented and often frustrating user experience.

When a website implements the Payment Request API, users benefit from a dramatically simplified checkout process. Instead of typing their card number, expiration date, security code, name, address, and contact information for every purchase, they can complete transactions with just a few clicks or taps. The browser handles all the heavy lifting, presenting saved payment methods and addresses in a clean, familiar interface that looks the same regardless of which website the user is shopping on.

The API works by establishing a communication channel between the merchant's website and the browser's payment handling capabilities. When a user initiates a purchase, the website creates a PaymentRequest object containing details about the transaction, including the total amount, currency, and accepted payment methods. The browser then takes over, displaying a native dialog where users can select their preferred payment method and shipping address. Once the user confirms, the browser returns the necessary payment credentials to the merchant for processing.

## Digital Wallets and Payment Methods

One of the most powerful aspects of the Payment Request API is its ability to work seamlessly with digital wallets. Digital wallets have revolutionized how people make online purchases, allowing users to store multiple payment methods in a single, secure location. Chrome's implementation supports various digital wallet solutions, with Google Pay being the most prominent integration for Chrome users.

Google Pay serves as the primary digital wallet service for Chrome, enabling users to store credit cards, debit cards, and loyalty cards in their Google Account. When a user makes a purchase on a website supporting the Payment Request API, they can select their Google Pay card directly from the payment dialog. The system automatically retrieves the saved card details, including the card brand, last four digits, and expiration date, allowing users to quickly identify and select the correct payment method.

Beyond credit and debit cards, the Payment Request API supports multiple payment methods through a flexible extensibility model. Merchants can specify which payment methods they accept, and the API will only display relevant options to users. This might include specific card networks like Visa, Mastercard, or American Express, or it could encompass alternative payment methods like bank transfers or buy-now-pay-later services.

The API also supports what is known as "cardized" payments, where the actual card credentials are never transmitted to the merchant. Instead, the browser provides a payment token that represents the user's payment method. This token can only be used for the specific transaction initiated through the Payment Request API, adding a significant layer of security. Even if a malicious actor were to intercept the token, they could not use it for any other purchases.

For merchants looking to implement the Payment Request API, the supportedMethods array in the PaymentRequest object determines which payment options appear in the dialog. This array can include standard card networks using the "card" basic card method, or it can specify payment apps that the user has installed. The flexibility allows businesses to support traditional card payments while also preparing for emerging payment technologies.

## Google Pay Integration

Google Pay integration with the Payment Request API provides one of the smoothest checkout experiences available on the web today. For users who have set up Google Pay in their Chrome browser, the entire checkout process can be completed in seconds without typing any information. This frictionless experience has proven incredibly popular, with millions of transactions processed through this method daily.

Setting up Google Pay in Chrome is straightforward. Users need to sign in to Chrome with their Google Account and enable sync for payment methods. Once this is done, any credit or debit cards added to their Google Pay account become available for use in the Payment Request API dialog. Chrome automatically syncs this information across devices, so users can enjoy the same streamlined checkout experience on their desktop, laptop, or mobile device.

The integration goes beyond just card storage. Google Pay also maintains users' shipping addresses, making it possible to complete both payment and delivery information in a single step. When a merchant requests shipping information through the Payment Request API, Chrome presents the user's saved addresses alongside their payment methods. This eliminates another major source of friction in the online checkout process, as users no longer need to type their address for each new purchase.

From a technical standpoint, Google Pay integration requires merchants to register their website with Google and obtain a merchant ID. This registration process helps ensure that only legitimate businesses can collect payment information through the API. Once registered, merchants can specify Google Pay as a supported payment method in their PaymentRequest configuration, and Chrome will present the Google Pay option when users visit the site.

The security model behind Google Pay and the Payment Request API is particularly worth understanding. When users pay with Google Pay through this API, their actual card numbers are never shared with the merchant. Instead, Google generates a unique, single-use token that represents the payment authorization. This token is transmitted to the payment processor, who then communicates with the relevant card network to complete the transaction. This approach provides the convenience of digital wallet storage while maintaining the security benefits of tokenization.

## Shipping Options and Address Handling

Physical goods purchased online require shipping, and the Payment Request API includes robust support for collecting shipping information. The API allows merchants to request shipping addresses from users and even provides options for calculating shipping costs based on the selected address. This creates a complete checkout solution that handles both payment and delivery in one unified interface.

When configuring the Payment Request API for shipping, merchants can specify different shipping options that vary in cost and delivery time. Standard shipping might be cheaper but slower, while express shipping costs more but delivers faster. The API displays these options in the payment dialog, allowing users to choose their preferred delivery method based on the price and estimated arrival time.

The API also supports real-time shipping calculation. When a user selects a shipping address, the merchant's website can receive a notification and calculate appropriate shipping costs for that specific location. This is particularly useful for merchants who ship internationally, as shipping costs can vary significantly based on destination. The payment dialog updates dynamically to show the calculated shipping cost alongside the item total.
>>>>>>> consumer/a7-chrome-payment-request-api

Address collection through the Payment Request API benefits from Chrome's autofill capabilities. Users who have saved addresses in their Google Account or Chrome's autofill settings can select from these saved addresses directly in the payment dialog. This means users no longer need to type their full address from memory or search for a piece of paper with their shipping information. The address appears in the dialog pre-filled and ready to confirm.

<<<<<<< HEAD
The Payment Request API is designed to be flexible, supporting multiple payment methods within a single payment request. This flexibility is crucial for maximizing conversion because it allows you to accept the widest possible range of payment options without complicating your checkout flow.

The basic-card payment method is the most universally supported option. When you include basic-card in your supported methods, users can pay with any credit or debit card that matches the networks you specify. The browser handles collecting the card number, expiration date, and cardholder name, and it performs basic validation before returning the data to your code.

Beyond basic-card and Google Pay, other payment method identifiers can be added to support services like Apple Pay, Microsoft Pay, or regional payment services. Each payment method has its own configuration requirements and may require separate agreements with the payment service providers. However, the advantage is that you can include all supported methods in a single PaymentRequest object, giving users a choice without requiring multiple checkout implementations.

When implementing multiple payment methods, it is important to understand how the API handles method-specific data. Different payment methods return different data structures. Google Pay returns encrypted payment tokens that your backend must decrypt and process through Google's payment network. Basic-card returns the raw card details that you would then process through your payment processor. Your code needs to handle these different response formats appropriately.

Error handling is another important consideration. Users may encounter errors when their payment is declined, when there are network issues, or when their selected payment method cannot be processed for some reason. The PaymentRequest API provides mechanisms for displaying error messages to users and allowing them to try again or select a different payment method.

## Best Practices for Payment Request Implementation

Successfully implementing the Payment Request API requires attention to several best practices that ensure a smooth experience for users while maintaining security and reliability. One of the most important practices is to always have a fallback payment method available. While the Payment Request API is supported in most modern browsers, some users may be on older browsers or have disabled the API for privacy reasons. Your site should still function for these users with an alternative checkout method.

Performance optimization is crucial when implementing the Payment Request API. The API should initialize quickly, so avoid making slow network requests before creating the PaymentRequest object. If you need to fetch dynamic pricing or shipping options, do this asynchronously and update the payment details after the initial request is created, rather than delaying the entire checkout experience.

Testing your implementation thoroughly across different scenarios is essential. This includes testing with different payment methods, testing with various shipping addresses to verify shipping calculations work correctly, testing error conditions to ensure users receive helpful messages, and testing on different devices and browsers to ensure consistent behavior.

Security should be a top priority in your implementation. Remember that the Payment Request API only handles the front-end portion of payment collection. You still need secure backend processing for handling payment credentials, storing transaction records, and communicating with payment processors. Follow PCI compliance guidelines and never log or store sensitive payment information on your servers.

## Enhancing the Checkout Experience with Tab Suspender Pro

While the Payment Request API significantly improves the payment experience on your website, overall browser performance can still impact how smoothly users navigate through your checkout process. Users who keep many browser tabs open may experience slower performance, which can cause frustration during the critical final steps of completing a purchase.

One tool that can help manage browser performance is Tab Suspender Pro. This Chrome extension automatically suspends tabs that have been inactive for a configurable period, freeing up memory and CPU resources. For users who tend to keep numerous tabs open while shopping, Tab Suspender Pro can help ensure that their browser remains responsive during the checkout process.

When users have a smooth, fast browsing experience, they are more likely to complete their purchases without frustration. While Tab Suspender Pro is not directly related to payment processing, it represents the kind of tool-conscious users employ to maintain browser performance, and it can indirectly support higher conversion rates by preventing browser slowdowns that might cause users to abandon their carts.
=======
For merchants, handling shipping information through the API provides several advantages. First, the address format is standardized, reducing errors in shipping label creation. Second, the API can validate addresses in real-time, alerting users if their address appears incomplete or invalid before they complete their purchase. Third, merchants can restrict shipping to certain regions or countries by specifying allowed shipping areas in their API configuration.

The shipping address functionality also supports multiple address types. Users can save separate addresses for billing and shipping in their Google Account, and the Payment Request API allows merchants to request either or both. This is essential for users who want to ship gifts directly to recipients or who have different addresses for business and personal deliveries.

## Advanced Implementation Considerations

Implementing the Payment Request API effectively requires attention to several technical details. The API provides extensive configuration options that allow merchants to tailor the checkout experience to their specific needs while maintaining a smooth user experience. Understanding these options helps developers create payment flows that work seamlessly across different devices and user scenarios.

The PaymentRequest constructor takes two main arguments: a PaymentDetailsInit object that describes the transaction, and an array of PaymentMethodData objects that specify supported payment methods. The details object includes the total amount, display items, and optionally, shipping options and modifiers. The methods array defines which payment options the merchant accepts, whether they are standard card networks or specific payment apps.

Error handling is a crucial aspect of implementation. The Payment Request API can fail in various scenarios, from users declining the payment request to network issues during processing. The API uses a combination of promise resolution and rejection to handle these scenarios. Developers must implement appropriate error handling to provide useful feedback to users when payments cannot be completed.

The API also supports merchant validation, a security measure that confirms the identity of websites requesting payment information. This validation uses the Web Payments HTTP API and helps prevent phishing attacks where malicious sites attempt to collect payment credentials. Chrome performs this validation automatically when the Payment Request API is invoked, providing an additional layer of security for users.

Performance optimization is another important consideration. The Payment Request API is designed to be fast, but its effectiveness depends on how quickly merchants can respond to browser events. Implementing efficient server-side processing and minimizing latency in payment handler code ensures that users experience the quick, responsive checkout that the API is designed to provide.

## Browser Support and Compatibility

While the Payment Request API was originally designed for Chrome, it has since been adopted by other browsers, creating a more universal standard for web payments. However, browser support varies, and developers need to understand how to provide fallback experiences for users whose browsers do not support the API.

Chrome was the first browser to implement the Payment Request API, and it remains the most widely used browser for this feature. All modern versions of Chrome on desktop and mobile platforms support the API, making it a reliable choice for merchants targeting Chrome users. The API is also supported in Edge, Safari, and Opera, providing varying levels of implementation across these browsers.

For browsers that do not support the Payment Request API, merchants should implement traditional checkout forms as a fallback. The best approach involves using feature detection to determine whether the API is available and conditionally loading the appropriate checkout experience. This ensures that all users can complete purchases regardless of their browser choice.

Mobile browsers present unique considerations for Payment Request API implementation. On mobile devices, the API often triggers a native payment sheet that takes over the screen, providing a particularly smooth user experience on smartphones and tablets. This mobile-first approach aligns with the growing trend of mobile commerce, where an increasing percentage of online purchases occur on handheld devices.

The Payment Request API also works with progressive web applications (PWAs), enabling developers to create installable web apps with native-like payment capabilities. This combination allows businesses to offer app-like experiences on the web while maintaining the security and convenience of browser-native payments.

## Security and Privacy Benefits

The Payment Request API was designed with security as a foundational principle. By keeping payment credentials in the browser rather than transmitting them directly to merchants, the API significantly reduces the risk of payment information being compromised. This approach addresses many of the security concerns that have plagued online commerce since its inception.

Tokenization forms the core of the API's security model. When users pay through the Payment Request API, their actual card numbers are replaced with unique tokens that can only be used for a single transaction. These tokens are meaningless to anyone who might intercept them, as they cannot be reused or reverse-engineered to reveal the original card details. This same tokenization technology is used by mobile payment systems like Apple Pay and Google Pay in physical stores.

From a privacy perspective, the API gives users more control over their payment information. Users can manage their saved payment methods through Chrome settings, adding, removing, or editing cards as needed. They can also view which websites have access to their payment information and revoke that access if desired. This transparency helps users make informed decisions about how their payment data is used and shared.

The API also supports two-factor authentication through the browser's existing security infrastructure. When users configure 2FA on their Google Account, this protection extends to Payment Request API transactions. Users may need to verify their identity through two-factor authentication before completing high-value purchases, adding another layer of security to the payment process.

Chrome's Enhanced Safe Browsing protection further enhances security for Payment Request API transactions. When this feature is enabled, Chrome proactively checks websites against Google databases of known threats, warning users about potentially malicious sites before they can attempt to collect payment information. This real-time protection helps prevent phishing attacks that target payment credentials.

## Performance Optimization Tips

While the Payment Request API is inherently fast, several optimization strategies can further improve the checkout experience. One of the most important factors is ensuring that payment handler code executes quickly, as users perceive any delay during checkout as a friction point that might discourage completion.

Minimizing the number of payment methods displayed can speed up the decision-making process for users. Rather than overwhelming users with dozens of options, merchants should focus on their most commonly used payment methods. This streamlined approach reduces cognitive load and helps users make decisions faster, ultimately improving conversion rates.

Pre-fetching payment information when possible can also improve perceived performance. Some implementations load saved payment methods in the background while users are still browsing, ensuring that the PaymentRequest object is ready to display immediately when users click the checkout button. This technique eliminates the brief delay that might occur if payment information needs to be retrieved at the moment of purchase.

Managing browser resources becomes particularly important when users have many tabs open. Chrome's tab management system can sometimes compete with payment processing for system resources, leading to sluggish performance during checkout. Users experiencing this issue can benefit from extensions like Tab Suspender Pro, which automatically pauses inactive tabs to free up memory and processing power for active tasks like completing purchases.

Tab Suspender Pro is particularly valuable during the checkout process because it identifies tabs that have been idle for a configurable period and suspends their activity. This frees up CPU cycles and memory that can be redirected to the checkout flow, ensuring that payment requests and other interactive elements respond quickly. When users need to return to a suspended tab, they can simply click on it and it reloads instantly, preserving their place without the performance penalty of keeping all tabs active simultaneously.

## The Future of Web Payments

The Payment Request API continues to evolve, with new features and capabilities being added regularly. The W3C Web Payments Working Group maintains the specification, incorporating feedback from merchants, browser vendors, and users to improve the standard over time. Future versions may include additional payment methods, enhanced security features, and more sophisticated fraud detection capabilities.

The success of the Payment Request API has inspired similar approaches in other areas of web commerce. Concepts pioneered in this API, such as browser-mediated data exchange and tokenization, are now being applied to other sensitive information types. This suggests that the Payment Request API may be just the beginning of a broader shift toward browser-mediated data sharing across the web.
>>>>>>> consumer/a7-chrome-payment-request-api

For merchants, staying current with Payment Request API developments makes good business sense. As more users become accustomed to the streamlined checkout experience, businesses that do not offer this option may find themselves at a competitive disadvantage. Implementing the API now positions merchants to take advantage of future improvements as they become available.

<<<<<<< HEAD
The Chrome Payment Request API offers a powerful, standardized approach to accepting payments on the web. By supporting digital wallets like Google Pay, enabling seamless shipping information collection, and accommodating multiple payment methods, this API provides the foundation for modern, conversion-optimized checkout experiences.

Implementing the Payment Request API requires attention to both the technical integration and the user experience aspects of payment processing. Following best practices around fallback methods, performance optimization, thorough testing, and security will help ensure your implementation serves both your business and your customers well.

As digital payments continue to evolve, the Payment Request API provides a future-proof foundation that will automatically benefit from new payment methods and improvements to the browser payment ecosystem. Investing in this implementation today will pay dividends in improved conversion rates and customer satisfaction for years to come.
=======
The payment landscape continues to shift toward digital and mobile-first experiences. The Payment Request API positions Chrome and supporting browsers at the forefront of this transformation, offering users and merchants alike a glimpse of what online checkout can become when designed from the ground up for the modern web.

---
>>>>>>> consumer/a7-chrome-payment-request-api

Built by theluckystrike — More tips at [zovo.one](https://zovo.one)
