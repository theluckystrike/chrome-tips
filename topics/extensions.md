---
layout: default
title: "Extensions Guides"
description: "All Chrome extension articles on Chrome Tips Guide"
permalink: /topics/extensions/
---

# Extensions Guides

Reviews, comparisons, and setup guides for Chrome extensions across productivity, privacy, and development.

{% assign topic_pages = site.pages | where_exp: "p", "p.path contains 'articles/'" | where_exp: "p", "p.title != nil" | sort: "title" %}
{% for p in topic_pages %}{% if p.categories contains 'extensions' %}
- [{{ p.title }}]({{ p.url }})
{% endif %}{% endfor %}
