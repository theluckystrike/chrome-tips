---
layout: default
title: "Privacy & Security Guides"
description: "All privacy and security articles on Chrome Tips Guide"
permalink: /topics/privacy-security/
---

# Privacy & Security Guides

Settings, extensions, and configurations for locking down Chrome and protecting your data.

{% assign topic_pages = site.pages | where_exp: "p", "p.path contains 'articles/'" | where_exp: "p", "p.title != nil" | sort: "title" %}
{% for p in topic_pages %}{% if p.categories contains 'privacy' or p.categories contains 'security' %}
- [{{ p.title }}]({{ p.url }})
{% endif %}{% endfor %}
