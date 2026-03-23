---
layout: default
title: "Extensions Guides"
description: "All Chrome extension articles on Chrome Tips Guide"
permalink: /topics/extensions/
---

# Extensions Guides

Reviews, comparisons, and setup guides for Chrome extensions across productivity, privacy, and development.

{% assign topic_pages = site.pages | where_exp: "page", "page.path contains 'articles/'" | sort: "title" %}
{% for page in topic_pages %}{% if page.title and page.categories contains 'extensions' %}
- [{{ page.title }}]({{ page.url }})
{% endif %}{% endfor %}
