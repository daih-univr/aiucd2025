---
id: sponsors
layout: page
title: Sponsors
permalink: /sponsors/
nav: true
nav_order: 5
dropdown: false   
---
{% assign sponsors = site.data.sponsors.sponsors %}

{% if sponsors %}
{% for category_item in sponsors %}
    {% assign category = category_item[0] %}
    {% assign category_data = category_item[1] %}
<h3>{{ category_data.en }}</h3>
<hr/>
    
<div class="container">
    <div class="row mb-5">
    {% for sponsor in category_data.list %}
        <div class="col-12 col-md-6 col-lg-4 text-left mb-4">
            <div class="card sponsor-card">
                <div class="card-body d-flex justify-content-center align-items-center">
                {% assign logo = sponsor.logo | prepend: '/assets/img/sponsors/' %}
                <a href="{{ sponsor.url }}" target="_blank" >
                    <img src="{{ logo }}" alt="{{ sponsor.name }}" class="img-fluid sponsor-logo">
                </a>
                </div>
<!--                 <div class="card-footer">
                <a href="{{ sponsor.url }}" target="_blank" class="text-decoration-none">
                    {{ sponsor.name }}
                </a>
                </div> -->
            </div>
        </div>
    {% endfor %}    
    </div>
</div>

{% endfor %}
{% if site.data.sponsors.thanks %}
<p>{{ site.data.sponsors.thanks.en }}</p>
{% endif %}
{% else %}
<p>No sponsors found.</p>
{% endif %}