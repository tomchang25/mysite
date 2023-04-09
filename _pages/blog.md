---
layout: archive-taxonomies
title: Blog
permalink: /blog/
author_profile: true
---

{% assign posts = site.posts %}
{% assign date_format = site.minimal_mistakes.date_format | default: "%b %-d, %Y" %}

{% include group-by-array collection=posts field="date" %}
{% for group in group_names %}
{% capture y %}{{ group | first | date: '%Y' }}{% endcapture %}
{% capture m %}{{ group | first | date: '%m' }}{% endcapture %}
{% capture mon %}{{ group | first | date: '%b' }}{% endcapture %}

  <h2 id="{{ y }}-{{ m }}" class="archive__subtitle">{{ mon }}, {{ y }}</h2>

{% for post in group.items %}
{% include archive-single.html %}
{% endfor %}
{% endfor %}
