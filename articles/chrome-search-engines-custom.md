---
layout: post
title: "Chrome Custom Search Engines Guide"
<<<<<<< HEAD
description: "Master Chrome custom search engines with our comprehensive guide. Learn how to add search engines, create keyword shortcuts, set up site search, and configure your default search engine for maximum productivity."
date: 2026-03-11
categories: [features, productivity, customization]
tags: [search-engines, chrome-settings, shortcuts, productivity, browser-tips, chrome-tips]
=======
description: "Master Chrome custom search engines with this comprehensive guide. Learn how to add search engines, create keyword shortcuts, set up site-specific search, and change your default search engine for faster browsing."
date: 2026-03-11
categories: [features, customization, productivity]
tags: [search-engines, chrome-settings, shortcuts, productivity, browser-tips]
>>>>>>> consumer/a68-chrome-search-engines-custom
author: theluckystrike
---

# Chrome Custom Search Engines Guide

<<<<<<< HEAD
Chrome custom search engines are one of the most powerful yet underutilized features in Google's popular browser. If you find yourself repeatedly visiting the same websites to search for information, you're missing out on a significant productivity boost. This comprehensive guide will walk you through everything you need to know about customizing your search experience in Chrome, from basic setup to advanced techniques that will transform how you browse the web.

## Understanding Chrome Custom Search Engines

Before diving into the practical aspects, it's important to understand what custom search engines actually are and why they matter. Chrome's address bar, also known as the omnibox, isn't just for entering website URLs. It's a powerful search tool that can directly access search functions on virtually any website you frequent.

When you type a query into Chrome's address bar, by default it uses your chosen search engine to find results across the entire web. However, you can configure shortcuts that tell Chrome to use a specific website's search function instead. For example, instead of going to YouTube and then searching for a video, you can type "yt chrome tips" directly in the address bar and land straight on the results page.

The beauty of custom search engines lies in their flexibility. You can create shortcuts for virtually any website that has a search function, from major platforms like YouTube, Wikipedia, and Amazon to niche tools like your company's internal wiki, a project management tool, or a documentation site you reference regularly. This eliminates the need to navigate through multiple pages just to perform a simple search, saving you valuable time throughout your workday.

Chrome automatically learns about search engines as you browse. When you visit a website and use its search function, Chrome takes note and can suggest adding that search engine to your collection. However, you can also manually add or modify search engines for complete control over your setup.

## How to Add Search Engines in Chrome

Adding a custom search engine in Chrome is a straightforward process that can be accomplished in several ways. The easiest method is to let Chrome discover search engines as you browse, but manual addition gives you more precise control.

### Automatic Detection Method

Chrome is quite good at detecting when you're using a website's search function. When you visit a site and use its search box, Chrome sometimes displays a small popup asking if you'd like to add that site's search engine. This popup typically appears near the address bar and includes the name of the website and a suggested shortcut.

To use this method effectively, simply visit websites you frequently search on and use their built-in search functionality. Keep an eye out for the "Add search engine" popup that may appear. If it doesn't appear, don't worry—you can add search engines manually with just a few clicks.

When Chrome does offer to add a search engine, you'll see fields for the name (how it appears in your settings), the shortcut (what you type in the address bar to trigger it), and the URL template. You can accept the defaults or customize them to your preference. For instance, if Chrome suggests "youtube" as the shortcut but you'd prefer "yt" for faster typing, you can modify it before clicking Add.

### Manual Addition Method

For complete control over your custom search engines, you can add them manually through Chrome's settings. This method is particularly useful when Chrome doesn't automatically detect a website's search function or when you want to create more precise shortcuts.

To begin, click the three-dot menu in Chrome's top-right corner and select Settings. In the settings page, click Search engine in the left sidebar, then click Manage search engines and site search. You'll see a list of all your search engines, including defaults like Google, Bing, and any you've added yourself.

To add a new search engine, scroll to the Site search section and click the Add button. You'll need to fill in three fields:

The first field is the name of the search engine. This is purely for your reference and can be anything that helps you identify the search engine in your settings. For example, you might enter "Wikipedia" or "My Company's Wiki."

The second field is the shortcut keyword. This is what you'll type in the address bar to trigger the search. Choose something short and memorable—ideally one or two characters that won't conflict with other commands. Many users use abbreviations like "yt" for YouTube, "am" for Amazon, or "gh" for GitHub.

The third field is the URL with query parameter. This is the most critical part because it tells Chrome how to construct the search URL. Most websites use a format like "https://www.example.com/search?q=%s" where "%s" represents your search query. When you type a search, Chrome replaces "%s" with your actual query.

Finding the correct URL format can require some investigation. One reliable method is to perform a search on the target website normally, then examine the resulting URL in your address bar. Look for the pattern that contains your search terms and replace those terms with "%s" to create the proper format.

## Mastering Keyword Shortcuts

Keyword shortcuts are the heart of the custom search engine experience. They transform a multi-step process into a lightning-fast address bar command. Understanding how to create and use these shortcuts effectively can dramatically improve your browsing efficiency.

### Creating Effective Shortcuts

When creating shortcuts, think about what will be fastest for you to type. Shorter is generally better, but you need something you'll remember. Some users prefer one or two characters for their most-used sites: "g" for Google, "y" for YouTube, "w" for Wikipedia. Others prefer slightly longer shortcuts that are more descriptive: "yt" for YouTube, "doc" for documentation.

Avoid using shortcuts that conflict with each other or with Chrome's built-in commands. For instance, don't use "g" if you've set up a custom search for a site that also starts with "g" and you want to distinguish between them.

It's also worth considering your workflow. If you frequently search multiple related sites, you might create shortcuts that follow a logical pattern. For example, you might use "shop" for Amazon, "comp" for comparison shopping, and "rev" for review sites. This organization makes it easier to remember your shortcuts.

### Using Shortcuts in the Address Bar

Once you've set up your shortcuts, using them is intuitive. Simply type the shortcut in the address bar, followed by a space, then type your search query. Press Enter, and Chrome will take you directly to the search results on that site.

For example, if you've set up "wiki" as your Wikipedia shortcut, you would type "wiki chrome custom search engines" to search Wikipedia for that topic. Chrome recognizes the shortcut and automatically routes your query to the appropriate search engine.

Chrome is smart about distinguishing between shortcuts and regular searches. If you type something that doesn't match any of your shortcuts, Chrome treats it as a regular search using your default search engine. This means you don't need to remember which shortcuts you've set up—you can just start typing, and Chrome will do the right thing.

One useful feature is that Chrome shows your matching shortcuts in the address bar dropdown as you type. This serves as a helpful reminder of which shortcuts are available and allows you to select one with your arrow keys if desired.

## Setting Up Site Search for Specific Websites

Site search is a powerful application of custom search engines that lets you quickly find content on specific websites. While this is similar to what we've already covered, it's worth exploring in more depth because it can be incredibly valuable for certain use cases.

### Documentation and Technical Sites

If you work in software development, technical writing, or any field that requires frequently referencing documentation, setting up site search for documentation sites is essential. Rather than navigating to the documentation site and using its search function, you can jump directly to the relevant results with a quick address bar command.

Common examples include searching programming language documentation (MDN for JavaScript, Python docs, React docs), searching Stack Overflow for programming questions, or searching your company's internal documentation. For developers who reference these resources dozens of times daily, the time savings are substantial.

When setting up documentation searches, pay attention to the URL format. Many documentation sites use query parameters that might not be obvious. For instance, a site might use "/search?q=" or "/search?query=" or something entirely different. Test your search engine thoroughly after setting it up to ensure it works correctly.

### Research and Reference Sites

Researchers, students, and anyone who frequently looks up information on specific websites can benefit from site search shortcuts. Consider setting up searches for academic databases, news sites, reference encyclopedias, or any website you regularly use to find specific information.

A particularly useful application is setting up searches for your own bookmarks. If you use a bookmarking service or have a personal knowledge base, you can often create a search shortcut that searches across your saved items. This transforms your browser into a powerful personal research assistant.

### E-commerce and Shopping

Online shoppers can benefit from custom search engines for price comparisons, product searches, and deal hunting. Setting up shortcuts for major retailers allows you to quickly check prices across different stores without navigating through multiple homepages.
=======
Chrome custom search engines are one of the most powerful yet underutilized features available in Google's browser. While most users simply type their queries into Google and call it a day, Chrome offers a sophisticated system that allows you to create personalized search shortcuts for virtually any website. This comprehensive guide will walk you through everything you need to know about Chrome custom search engines, from basic setup to advanced techniques that can dramatically improve your browsing efficiency.

Whether you are a developer who constantly searches documentation, a researcher who frequently visits academic databases, or simply someone who shops online and wants faster access to favorite stores, custom search engines can save you countless clicks and precious seconds every day. The beauty of this feature lies in its simplicity—you create a shortcut once, and then use it forever.

## Understanding Chrome Custom Search Engines

Before diving into the setup process, it is helpful to understand what custom search engines actually are and how they work within Chrome. At their core, custom search engines are URL templates that allow you to search specific websites directly from Chrome's address bar. Instead of first navigating to a website and then using its internal search function, you can type a short keyword and let Chrome do the heavy lifting.

When you add a custom search engine to Chrome, you are essentially teaching the browser a new trick. You provide three key pieces of information: a name for the search engine (for your reference), a shortcut keyword that triggers the search, and the search URL with a placeholder for your query. Chrome then uses this information to construct the proper URL whenever you use the shortcut.

The search URL format typically includes `%s` as a placeholder where your search query will be inserted. For example, if you add Wikipedia as a custom search engine, the URL would look something like `https://en.wikipedia.org/wiki/%s`. When you type `w your search term` in the address bar, Chrome replaces `%s` with your actual search term and takes you directly to the Wikipedia results page.

Chrome comes with several built-in search engines already configured, including Google, Bing, Yahoo, and DuckDuckGo. These are the options you see when you click on the search engine icon in the address bar. However, you are not limited to these options—you can add as many custom search engines as you need for different websites and purposes.

## How to Add Custom Search Engines in Chrome

Adding a custom search engine in Chrome is a straightforward process that can be accomplished in several ways. The most common method involves visiting a website and using Chrome's automatic detection feature, but you can also manually add search engines through Chrome's settings. Both approaches have their advantages, and understanding both gives you maximum flexibility.

### Adding Search Engines Automatically

The easiest way to add a custom search engine is to let Chrome detect it while you are browsing. This method works on websites that have a search box and works best when Chrome can figure out the search URL pattern on its own.

First, navigate to the website where you want to create a search shortcut. For instance, if you want to add Amazon for quick product searches, go to amazon.com. Locate the search box on the website—it is usually near the top of the page and typically says "Search" or displays a magnifying glass icon.

Right-click on this search box to open the context menu. You should see an option that says "Add to search engines" or "Add to Search Engines" near the bottom of the menu. Click on this option, and a small dialog will appear with three fields already populated.

The first field is the name of the search engine, which Chrome usually fills in with the website's name. You can keep this or change it to something more descriptive. The second field is the shortcut keyword—this is what you will type in the address bar to trigger the search. Chrome typically suggests a short abbreviation, but you can choose anything that is easy to remember. The third field shows the search URL, which Chrome automatically generates based on the website's search functionality.

Once you are satisfied with the information in these fields, click "Add" to save the custom search engine. It will now be available whenever you use the address bar.

### Adding Search Engines Manually

Sometimes automatic detection does not work, especially on websites with complex search functionality or unusual URL structures. In these cases, you can manually add a custom search engine through Chrome's settings page.

To access this, click on the three-dot menu in the top-right corner of Chrome and select "Settings" from the dropdown. In the settings page, click on "Search engine" in the left sidebar, or scroll down to the "Search engine" section. You will see a button or link labeled "Manage search engines and site search."

On the page that opens, you will see three sections: "Search engines," "Site search," and "Inactive." The main area shows your active search engines, including any custom ones you have added. At the very bottom of the "Search engines" list, you should see a button to "Add" a new search engine.

Click this button, and a form will appear with three fields: "Search engine," "Keyword," and "URL with %s in place of query." Fill in each field carefully. The search engine name is for your reference and can be anything you like. The keyword should be short and memorable—something you will type in the address bar to trigger the search. The URL field is the most critical: you need to find the actual search URL for the website you want to add.

Finding the correct search URL sometimes requires a bit of investigation. Visit the website, perform a test search, and look at the URL in your address bar. Look for the pattern—most search URLs follow a format like `https://www.example.com/search?q=` or `https://www.example.com/search?query=`. Replace your actual search term with `%s` to create the URL you need.

For example, if searching for "test" on a website produces the URL `https://www.example.com/search?q=test`, your custom URL would be `https://www.example.com/search?q=%s`. Once you have entered all three fields correctly, click "Add" to save your custom search engine.

## Mastering Keyword Shortcuts

The real power of custom search engines comes from their keyword shortcuts. These short codes allow you to trigger searches directly from the address bar without having to visit the website first. Understanding how to create effective shortcuts and use them efficiently can transform your browsing experience.

### Creating Effective Shortcuts

When choosing a shortcut keyword, think about what will be easy to type and remember. Short keywords are better because they require less typing, but they should also be unique enough that Chrome can easily recognize them as search commands rather than regular text.

Common approaches include using the first letter or two of the website name, using an abbreviation, or choosing something that has meaning to you personally. For example, you might use "w" for Wikipedia, "am" for Amazon, "yt" for YouTube, or "gh" for GitHub. The key is consistency—pick a pattern and stick with it across all your custom search engines.

Avoid using keywords that conflict with existing shortcuts or that might accidentally trigger when you are typing regular website addresses. If you accidentally trigger a search engine shortcut, you can press Escape to cancel and continue typing your URL normally.

### Using Shortcuts in Practice

To use a custom search engine shortcut, click on the address bar or press Ctrl+L (or Cmd+L on Mac) to focus it. Type your keyword followed by a space, then type your search query. As soon as you type the space, Chrome recognizes that you are initiating a search and will show the custom search engine as a suggestion.

For example, if you have set up Wikipedia with the shortcut "w," you would type "w python programming" to search Wikipedia for Python programming. Press Enter, and Chrome will take you directly to the Wikipedia results page for that search.

This method works with any custom search engine you have added. The workflow becomes incredibly fast once you have set up your most frequently visited sites. Instead of navigating through multiple pages to find what you are looking for, you go straight from the address bar to the results.

You can also combine shortcuts with Chrome's other features for even greater efficiency. For instance, you can open search results in a new tab by pressing Ctrl+Enter (or Cmd+Enter on Mac) instead of just Enter. This opens the results in a new tab while keeping your current page open.

## Site Search and Site-Specific Searches

Beyond creating custom search engines for external websites, Chrome also offers powerful site search functionality that allows you to restrict searches to specific domains. This is incredibly useful when you are looking for information on a particular website or when you want to narrow down search results to a trusted source.

### Using the Site: Operator

The simplest way to perform a site-specific search is to use the `site:` operator directly in your search query. This works with any search engine, including your default Google search. Simply type "site:example.com your search terms" in the address bar to see results only from that specific domain.

For instance, searching "site:github.com chrome extension" will show you only results from github.com that mention Chrome extensions. This is particularly valuable when you know the information you need is on a specific website but would be difficult to find using the site's own search function.

You can combine the site operator with any other search operators or modifiers to create very precise searches. This technique is especially popular among researchers, developers, and anyone who frequently searches within specific domains.

### Setting Up Site Search Shortcuts

If you frequently search within certain websites, you can create custom search engines specifically for site searches. This combines the convenience of custom shortcuts with the power of site-restricted searches.

To set this up, create a custom search engine where the URL includes the site operator. For example, if you want to quickly search within GitHub, you could create a search engine with the URL `https://github.com/search?q=%s&type=code`. When you use this shortcut, all your searches will automatically be performed within GitHub.

Alternatively, you can use Google's site search by setting up a URL like `https://www.google.com/search?q=site:%s+YOURKEYWORD`, though this requires adjusting the query format slightly. Many users find it easier to create separate search engines for each site they frequently search within.
>>>>>>> consumer/a68-chrome-search-engines-custom

For example, you might set up "am" for Amazon, "eb" for eBay, "wmt" for Walmart, and "trg" for Target. When you need to check if a product is available or compare prices, simply type your shortcut and product name to go straight to the search results.

<<<<<<< HEAD
Some shoppers take this further by setting up search engines for deal aggregation sites, price history trackers, or coupon finders. This creates a comprehensive shopping research workflow entirely within the address bar.

## Configuring Your Default Search Engine

While custom search engines are powerful, your default search engine is what Chrome uses for regular address bar queries. Understanding how to configure and optimize your default search engine is crucial for a smooth overall experience.

### Changing Your Default Search Engine

Chrome allows you to set any of your search engines as the default. This is useful if you prefer a different search provider than the one Chrome shipped with, or if you've found that you use a particular custom search more than general web search.

To change your default search engine, go to Settings > Search engine. You'll see a dropdown menu labeled "Search engine used in the address bar." Select your preferred engine from the list, which includes all the search engines you've added plus the defaults.

Keep in mind that your default search engine handles queries that don't match any of your shortcuts. If you type something that Chrome doesn't recognize as a URL or shortcut, it passes the query to your default search engine. Choose one that you trust with your search data and that provides results you're happy with.

### Managing Multiple Search Engines

As you add more custom search engines, you'll want to keep them organized. Chrome doesn't have built-in folders or tags for search engines, but you can impose your own organization through naming conventions.

Some users prefix their shortcuts with categories: "dev-github" for developer-related GitHub searches, "shop-amazon" for shopping searches, and so on. This makes it easier to scan the list and find what you're looking for.

Periodically review your search engines and remove ones you no longer use. A cluttered list makes it harder to find the shortcuts you actually need and can slow down Chrome's address bar suggestions.

## Advanced Tips and Troubleshooting

Even experienced Chrome users sometimes encounter issues with custom search engines or don't know about advanced features that could further improve their experience.

### Importing and Exporting Search Engine Settings

If you use multiple computers or want to share your search engine setup with colleagues, you'll be pleased to know that Chrome stores your search engine configuration in your user profile. While there's no direct import/export feature in Chrome's settings, you can manually back up your settings or use extensions that provide this functionality.

To manually find your search engine settings, look in your Chrome user data directory for files related to preferences or search engines. However, be cautious when editing these files directly as mistakes can cause issues.

Several extensions in the Chrome Web Store can help you manage backup and restore functions for your search engines and other settings. This is particularly useful for IT departments managing multiple users or power users who want to maintain consistent setups across their devices.

### Troubleshooting Common Issues

Custom search engines can sometimes stop working, usually due to changes on the target website. If a previously working search engine suddenly fails, the website likely updated its search URL format. You'll need to find the new format and update your search engine settings accordingly.

To diagnose issues, try performing a manual search on the target website and comparing the URL to what you have configured. Look for differences in query parameters or URL structure. Update your search engine to match the new format, replacing your test search term with "%s."

Another common issue is forgetting your shortcuts. If you have many search engines configured, you might forget which shortcuts you've created. Chrome's address bar suggestions can help remind you, but you can also view all your search engines and their shortcuts in Settings > Search engine > Manage search engines.

### Performance Considerations

Custom search engines have minimal impact on Chrome's performance. The main consideration is the number of shortcuts you're actively using. Having dozens or hundreds of custom search engines won't significantly slow down Chrome, but a well-curated list of your most-used searches provides the best balance between capability and simplicity.

If you notice any performance issues, make sure they aren't caused by something else first. Extensions, too many open tabs, and browser clutter are more likely culprits than search engine configuration.

## Enhancing Your Setup with Tab Suspender Pro

While custom search engines streamline how you find information, managing the tabs you open from those searches is another aspect of browser efficiency. Tab Suspender Pro is an extension that automatically suspends inactive tabs to save memory and reduce CPU usage, complementing your search engine setup perfectly.

When you use custom search engines extensively, you might find yourself opening many tabs throughout the day. Tab Suspender Pro helps manage this by putting tabs you aren't actively viewing to sleep, preserving system resources while keeping everything accessible. The extension is particularly useful for power users who maintain dozens of open tabs from research sessions or multiple search results.

The combination of efficient search shortcuts and smart tab management creates a remarkably productive browsing environment. Your custom search engines help you find information quickly, while Tab Suspender Pro ensures that finding information doesn't come at the cost of system performance.

## Conclusion

Chrome custom search engines represent one of the browser's most powerful productivity features. By taking the time to set up shortcuts for the websites you frequently search, you can dramatically reduce the number of clicks and navigation steps required to find information. Whether you're a developer searching documentation, a researcher browsing academic papers, or a shopper comparing prices, custom search engines can streamline your workflow.

Remember to start with your most-used sites, choose memorable shortcuts, and periodically review and clean up your configuration. With a well-organized set of custom search engines, Chrome's address bar becomes a command center for all your web searching needs, making your browsing faster and more efficient than ever before.

=======
Your default search engine is the one Chrome uses when you type regular queries in the address bar without a shortcut keyword. Chrome typically sets Google as the default, but you can change this to any search engine you prefer. Understanding how to manage your default search engine is an important part of customizing your Chrome experience.

### Changing Your Default Search Engine

To change your default search engine, navigate to Chrome's settings as described earlier and go to the "Search engine" section. You will see a dropdown or list showing your available search engines, with your current default marked as such.

Click on the search engine you want to use as your default, and Chrome will immediately make the change. The next time you type a query in the address bar without using a shortcut, Chrome will use your chosen default search engine.

You can also reorder your search engines to change how they appear in suggestions. Chrome shows search engine suggestions as you type, and the order in the settings page determines which ones appear first.

### When Your Default Search Engine Changes

Sometimes you might notice that your default search engine has changed without your intervention. This can happen if you have installed certain software or browser extensions that modify your browser settings, or if you have accidentally clicked on something during installation that changed your preferences.

If your default search engine keeps changing, it is worth checking your installed extensions and any recently installed software on your computer. Malicious extensions or unwanted software sometimes hijack browser settings as part of their monetization strategy.

To prevent unwanted changes, you can also access Chrome's search engine settings and lock your preferred search engine in place, if that option is available in your version. Additionally, reviewing your installed extensions periodically helps ensure nothing is modifying your browser settings without your knowledge.

## Advanced Tips and Best Practices

Now that you understand the basics of Chrome custom search engines, let us explore some advanced tips and best practices that can help you get the most out of this feature.

### Organizing Multiple Search Engines

As you add more custom search engines, keeping them organized becomes increasingly important. While Chrome does not offer folders or tags for search engines, you can use naming conventions to create logical groupings. For example, prefix all work-related search engines with "work-" or all shopping-related ones with "shop-."

Periodically review your list of custom search engines and remove any that you no longer use. This keeps your list manageable and ensures Chrome's suggestions remain relevant. To remove a search engine, go to the "Manage search engines" page, find the one you want to delete, and click on the three-dot menu next to it, then select "Delete."

### Backing Up Your Search Engines

If you use many custom search engines and plan to switch computers or reinstall Chrome, you will want to back up your search engine configuration. While Chrome does not offer a direct export feature for search engines, you can use extensions that provide this functionality.

Alternatively, you can manually note down your custom search engines, including their names, keywords, and URLs. This takes a bit of time to set up but ensures you can quickly recreate your setup if needed.

### Combining with Tab Management

Custom search engines work beautifully alongside tab management tools like Tab Suspender Pro. While search engines help you find information quickly, Tab Suspender Pro helps you manage the tabs you open during your research sessions. By automatically suspending inactive tabs, Tab Suspender Pro keeps your browser running smoothly even when you have dozens of tabs open from various searches.

The workflow becomes incredibly efficient: use custom search engines to find what you need, open interesting results in new tabs, and let Tab Suspender Pro handle memory management while you continue your research. This combination of fast searching and smart tab management represents Chrome at its most productive.

### Troubleshooting Common Issues

Even with a feature as well-designed as custom search engines, you may occasionally encounter problems. Understanding common issues and their solutions helps you resolve them quickly.

One frequent issue is a search engine that suddenly stops working. This usually happens when the website changes its search URL structure. When this occurs, you need to update the URL in your custom search engine settings. Visit the website, perform a test search, and check the new URL format.

Another common problem is forgetting your shortcut keywords. If you cannot remember a keyword, go to the manage search engines page and look through your list. Consider keeping a written record of your most-used shortcuts to avoid this problem in the future.

Some websites block automated searches or require additional parameters. If a search engine is not working, try manually constructing a search URL and testing it. You may need to experiment with different URL formats to find one that works reliably.

## Conclusion

Chrome custom search engines represent a powerful feature that can dramatically improve your browsing efficiency. By taking the time to set up shortcuts for your most-used websites, you transform Chrome's address bar into a powerful command center for all your searching needs.

The initial investment of a few minutes to add your favorite sites pays dividends in saved time and clicks over the long run. Whether you are searching for products, documentation, research papers, or anything else, custom search engines make the process faster and more intuitive.

Remember to periodically review and update your search engines as your needs change, and do not be afraid to experiment with new shortcuts. With practice, you will develop a personalized system that makes browsing feel effortless and efficient.

>>>>>>> consumer/a68-chrome-search-engines-custom
---

Built by theluckystrike — More tips at [zovo.one](https://zovo.one)
