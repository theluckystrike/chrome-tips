---
layout: default
title: "Chrome Flags & Settings Guides"
description: "All Chrome flags and settings articles on Chrome Tips Guide"
permalink: /topics/flags-settings/
---

# Chrome Flags & Settings Guides

Experimental flags, hidden settings, and configuration tweaks to customize Chrome behavior.

{% assign topic_pages = site.pages | where_exp: "page", "page.path contains 'articles/'" | sort: "title" %}
{% for page in topic_pages %}{% if page.title and page.categories contains 'chrome-flags' or page.title contains 'Flag' or page.title contains 'Settings' %}
- [{{ page.title }}]({{ page.url }})
{% endif %}{% endfor %}
