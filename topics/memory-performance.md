---
layout: default
title: "Memory & Performance Guides"
description: "All memory and performance articles on Chrome Tips Guide"
permalink: /topics/memory-performance/
---

# Memory & Performance Guides

Guides for reducing Chrome memory usage, speeding up page loads, and getting better performance on any hardware.

{% assign topic_pages = site.pages | where_exp: "p", "p.path contains 'articles/'" | where_exp: "p", "p.title != nil" | sort: "title" %}
{% for p in topic_pages %}{% if p.categories contains 'performance' %}
- [{{ p.title }}]({{ p.url }})
{% endif %}{% endfor %}
