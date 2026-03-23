---
layout: default
title: "Chrome Flags & Settings Guides"
description: "All Chrome flags and settings articles on Chrome Tips Guide"
permalink: /topics/flags-settings/
---

# Chrome Flags & Settings Guides

Experimental flags, hidden settings, and configuration tweaks to customize Chrome behavior.

{% assign topic_pages = site.pages | where_exp: "p", "p.path contains 'articles/'" | where_exp: "p", "p.title != nil" | sort: "title" %}
{% for p in topic_pages %}{% if p.categories contains 'chrome-flags' or p.title contains 'Flag' or p.title contains 'Settings' %}
- [{{ p.title }}]({{ p.url }})
{% endif %}{% endfor %}
