---
layout: default
title: "Chrome Tips"
description: "Practical Chrome browser tips for speed, memory, and productivity"
---

# Chrome Tips

Practical guides to make Chrome faster, use less memory, and work better for you.

{% for page in site.pages %}
{% if page.path contains 'articles/' %}
- [{{ page.title }}]({{ page.url | relative_url }})
{% endif %}
{% endfor %}
