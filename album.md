---
layout: page
title: ALBUM
#permalink: /album/
---

{% for image in site.static_files %}
    {% if image.path contains 'imgs/album' %}
<img src="{{ image.path }}" alt="image" />
    {% endif %}
{% endfor %}

