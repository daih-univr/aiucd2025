---
layout: page
title: Keynote Speakers
permalink: /keynotes/
horizontal: false
---


<!-- pages/keynotes.md -->
<div class="keynotes">

<!-- Display keynotes without categories -->

{% assign sorted_keynotes = site.keynotes | sort: "importance" %}

<!-- Generate cards for each keynote -->

{% if page.horizontal %}
    <div class="container">
    <div class="row row-cols-2">
    {% for keynote in sorted_keynotes %}
        {% include keynotes_horizontal.liquid %}
    {% endfor %}
    </div>
    </div>
{% else %}
    <div class="grid">
    {% for keynote in sorted_keynotes %}
        {% include keynotes.liquid %}
    {% endfor %}
    </div>
{% endif %}
</div>