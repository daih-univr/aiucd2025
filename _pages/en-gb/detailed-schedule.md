---
page_id: detailed-schedule
layout: page
title: Detailed schedule
permalink: /detailed-schedule/
nav: false
---

<nav aria-label="Program Navigation">
  <ul>
  {% for day in site.data.program %}
    <li><a href="#{{ day.day.en | slugify }}">{{ day.day.en }}</a></li>
  {% endfor %}
  </ul>
</nav>

<a href="/assets/img/programme-overview.png" data-lightbox="programme-overview.png" data-title="Programme Overview">
  <img src="/assets/img/programme-overview.png" alt="Thumbnail of the Programme Overview" class="gallery-thumbnail">
</a>

{% for day in site.data.program %}
  <br/>
  <hr/>
  <h2 id="{{ day.day.en | slugify }}">{{ day.day.en }}</h2>  
{% for session in day.sessions %}
  <h4>{{ session.time }}: {{ session.type.en }}</h4>


{% if session.type.en != "Keynote" and session.type.en != "Oral Presentations" and session.type.en != "Poster Madness" and session.type.en != "Social dinner"%}
  Room: {{ session.room }}<br/>
{% endif %}

{% if session.type.en == "Keynote" %}
  Room: {{ session.room }} - <em>Chair: {{ session.chair }}</em><br/>
  <strong>{{ session.title }}</strong> – {{ session.speaker }}
{% endif %}


{% if session.type.en == "Oral Presentations" %}
{% for psession in session.psessions %}
<strong>Session {{ psession.title }}</strong> - Room: {{ psession.room }} - <em>Chair: {{ psession.chair }}</em>
  <ul>
  {% for paper in psession.papers %}
    <li>{{ paper.time }}: <a href="{{ paper.pdf }}">{{ paper.title }}</a> ({{ paper.authors }}) </li>
  {% endfor %}
  </ul>
{% endfor %}
{% endif %}


{% if session.type.en == "Poster Madness" %}
  Room: {{ session.room }} - <em>Chair: {{ session.chair }}</em><br/>
  <ul>
  {% for paper in session.papers %}
    <li>{{ paper.time }}: <a href="{{ paper.pdf }}">{{ paper.title }}</a> ({{ paper.authors }}) </li>
  {% endfor %}
  </ul>
{% endif %}


{% endfor %}
{% endfor %}