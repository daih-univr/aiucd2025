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

{% include figure.liquid loading="eager" path="/assets/img/programme-overview.png" class="img-fluid rounded z-depth-1" zoomable=true alt="Programme Overview" max-width="300px" %}

Map of the conference venue:

{% include figure.liquid loading="eager" path="assets/img/marked-map.jpeg" class="img-fluid rounded z-depth-1" zoomable=true alt="detailed information about the conference buildings and rooms" max-width="300px" %}


{% for day in site.data.program %}
  <br/>
  <hr/>
  <h2 id="{{ day.day.en | slugify }}">{{ day.day.en }}</h2>  
{% for session in day.sessions %}
  <h4>{{ session.time }}: {{ session.type.en }}</h4>


{% if session.type.en != "Keynote" and session.type.en != "Oral Presentations" and session.type.en != "Poster Madness" and session.type.en != "Social dinner" and session.type.en != "AIUCD2025 Sponsors Event" and session.type.en != "Opening Ceremony" %}
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

{% if session.type.en == "AIUCD2025 Sponsors Event" %}
  Room: {{ session.room }} - <em>Chair: {{ session.chair }}</em><br/>
  {{ session.speaker }} - {{ session.title }} 
{% endif %}

{% if session.type.en == "Opening Ceremony" %}
  Room: {{ session.room }} - <em>Chair: {{ session.chair }}</em><br/>
  <ul>
  {% for greeting in session.greetings %}
    <li>{{ greeting.en }}</li>
  {% endfor %}
  </ul>
{% endif %}


{% endfor %}
{% endfor %}