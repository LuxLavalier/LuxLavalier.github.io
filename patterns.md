---
layout: page
title: Patterns
---

<!-- {% assign sorted_patterns = site.data.patterns | sort: "title" %} -->

{% for pattern in site.data.patterns %}

<a id="{{ pattern.name }}" href="#{{ pattern.name }}">{{ pattern.title }}</a>

<div class="ratio ratio-1x1">
  <video poster="//i.imgur.com/{{ pattern.imgurId }}.png" preload="auto" autoplay="autoplay" muted="muted" loop="loop" loading="lazy">
    <source src="//i.imgur.com/{{ pattern.imgurId }}.mp4" type="video/mp4">
  </video>
</div>

{% unless forloop.last %}

---

{% endunless -%}

{% endfor %}
