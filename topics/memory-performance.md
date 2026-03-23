---
layout: default
title: "Memory & Performance Guides"
description: "All memory and performance articles on Chrome Tips Guide"
permalink: /topics/memory-performance/
---

# Memory & Performance Guides

Guides for reducing Chrome memory usage, speeding up page loads, and getting better performance on any hardware.

{% assign topic_pages = site.pages | where_exp: "page", "page.path contains 'articles/'" | sort: "title" %}
{% for page in topic_pages %}{% if page.title and page.categories contains 'performance' %}
- [{{ page.title }}]({{ page.url }})
{% endif %}{% endfor %}
