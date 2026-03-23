---
layout: default
title: "Privacy & Security Guides"
description: "All privacy and security articles on Chrome Tips Guide"
permalink: /topics/privacy-security/
---

# Privacy & Security Guides

Settings, extensions, and configurations for locking down Chrome and protecting your data.

{% assign topic_pages = site.pages | where_exp: "page", "page.path contains 'articles/'" | sort: "title" %}
{% for page in topic_pages %}{% if page.title and page.categories contains 'privacy' or page.categories contains 'security' %}
- [{{ page.title }}]({{ page.url }})
{% endif %}{% endfor %}
