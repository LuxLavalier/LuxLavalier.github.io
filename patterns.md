---
layout: page
title: Patterns
---

Lux Lavalier comes with a wide variety of patterns built-in, as shown below.
By default, it will automatically play a playlist of pre-selected patterns.
The sequencer can be configured via the web interface over wi-fi in the following ways:

---

##### Pattern sequencer options:

* <b><u>Off</u></b>: Continuously play your selected favorite pattern. You can manually move to the next pattern by clicking the button on the back.
* <b><u>Shuffle All</u></b>: randomly shuffle between all patterns after playing each one for an adjustable duration.
* <b><u>Playlist</u></b>: patterns can be arranged into a playlist with customizable order and duration for each pattern.

---

The Pixelblaze controller inside your Lux Lavalier makes it easy for you to write your own patterns! In fact, you can view and edit the code for every pattern included with it.

##### Next step: [Writing your own patterns](/code)

---

##### Patterns:

<!-- Lux Lavalier has {{ site.data.patterns | size }} different patterns so far: -->

<!-- uncomment to sort patterns alphabetically, as opposed to the order they appear in the patterns.yml data file -->
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
