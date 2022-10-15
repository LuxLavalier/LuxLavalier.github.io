---
layout: page
title: Update
---

The [Pixelblaze](https://electromage.com) controller inside your Lux Lavalier can receive updates via the internet.

For example, in the v3.30 update exciting new features were added that allow for much more dynamic patterns: Perlin noise & color palettes!

To update your Lux Lavalier:

1. Make sure it's [connected to a wi-fi network](/setup/wifi.md) with internet access.
1. Go to the [settings page](/setup/settings.md).
1. Scroll down to the bottom of the page and click the `Check for Update` button.
1. If an update is not found, you're already on the latest version.
1. If an update is found, click the `Perform Update and Restart` button.
1. Once the update is complete, your Lux Lavalier will restart.
1. After the update & restart, if you are not be able to reconnect to the page, 
   press and hold the button on the back for 5 seconds.
   The status LED on the back will flash twice.
   You may need to refresh the page.

Congratulations, your Lux Lavalier is now updated!

Now you can add patterns that use the new features:

1. Click the <i class="bi bi-cloud-download"></i> (download) button for each pattern below.
1. In your Lux Lavalier's page, click the `Edit` tab at the top.
1. Click the `Open file` button and open one of the files you downloaded.
1. Once the pattern loads, click the `Save New` button.
1. Repeat the steps above for any other patterns you want to add.

These patterns have all been tested and work great on Lux Lavalier:

{% for pattern in site.data.patterns %}

{% if pattern.download %}

<a id="{{ pattern.name }}" href="#{{ pattern.name }}">{{ pattern.title }}</a> <a href="/assets/patterns/{{ pattern.download }}"><i class="bi bi-cloud-download"></i></a>

<div class="ratio ratio-1x1">
  <video poster="//i.imgur.com/{{ pattern.imgurId }}.png" preload="auto" autoplay="autoplay" muted="muted" loop="loop" loading="lazy">
    <source src="//i.imgur.com/{{ pattern.imgurId }}.mp4" type="video/mp4">
  </video>
</div>

{% unless forloop.last %}

---

{% endunless -%}

{% endif %}

{% endfor %}

You can also find even more Pixelblaze patterns at [electromage.com/patterns](https://electromage.com/patterns)

Please note that the patterns on electromage.com are meant generally for any Pixelblaze, and may
not be designed to work or look great on your Lux Lavalier.
