---
page_id: detailed-schedule
layout: page
title: Programma dettagliato
permalink: /detailed-schedule/
nav: false
---


<nav aria-label="Program Navigation">
  <ul>
  {% for day in site.data.program %}
    <li><a href="#{{ day.day.it | slugify }}">{{ day.day.it }}</a></li>
  {% endfor %}
  </ul>
</nav>

<a href="/assets/img/programme-overview.png" data-lightbox="programme-overview.png" data-title="Overview del Programma">
  <img src="/assets/img/programme-overview.png" alt="Miniatura dell'Overview del Programma" class="gallery-thumbnail">
</a>

{% for day in site.data.program %}
  <br/>
  <hr/>
  <h2 id="{{ day.day.it | slugify }}">{{ day.day.it }}</h2>  
{% for session in day.sessions %}
  <h4>{{ session.time }}: {{ session.type.it }}</h4>


{% if session.type.en != "Keynote" and session.type.en != "Oral Presentations" and session.type.en != "Poster Madness" and session.type.en != "Social dinner" %}
  Aula: {{ session.room }}<br/>
{% endif %}

{% if session.type.en == "Keynote" %}
  Aula: {{ session.room }} - <em>Chair: {{ session.chair }}</em><br/>
  <strong>{{ session.title }}</strong> – {{ session.speaker }}
{% endif %}


{% if session.type.en == "Oral Presentations" %}
{% for psession in session.psessions %}
<strong>Sessione {{ psession.title }}</strong> - Aula: {{ psession.room }} - <em>Chair: {{ psession.chair }}</em>
  <ul>
  {% for paper in psession.papers %}
    <li>{{ paper.time }}: <a href="{{ paper.pdf }}">{{ paper.title }}</a> ({{ paper.authors }}) </li>
  {% endfor %}
  </ul>
{% endfor %}
{% endif %}


{% if session.type.en == "Poster Madness" %}
  Aula: {{ session.room }} - <em>Chair: {{ session.chair }}</em><br/>
  <ul>
  {% for paper in session.papers %}
    <li>{{ paper.time }}: <a href="{{ paper.pdf }}">{{ paper.title }}</a> ({{ paper.authors }}) </li>
  {% endfor %}
  </ul>
{% endif %}


{% endfor %}
{% endfor %}