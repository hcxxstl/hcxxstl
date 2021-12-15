---
layout: page
title: ALBUM
#permalink: /album/
---

{% for image in site.static_files %}
    {% if image.path contains 'imgs/album' %}
        {% if image.path contains 'FRA' %}
<img src="{{ image.path }}" alt="image" />
<center>FRANCE</center>
        {% endif %}
        {% if image.path contains 'GBP' %}
<img src="{{ image.path }}" alt="image" />
<center>UNITED KINGDOM</center>
        {% endif %}
        {% if image.path contains 'NLD' %}
<img src="{{ image.path }}" alt="image" />
<center>NETHERLANDS</center>
        {% endif %}
    {% endif %}
{% endfor %}

