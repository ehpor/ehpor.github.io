---
layout: page
permalink: /publications/
title: publications
description: publications by categories in reversed chronological order.
nav: true
nav_order: 5
---

{% assign years = (1950..2050) %}

<div class="publications">

<h2>major contribution</h2>

{% for y in years reversed %}
  {% capture count %}
  {% bibliography_count -q @*[year={{y}} && author ~= Por && major_contribution = true]* %}
  {% endcapture %}
  {% assign count = count | plus: 0 %}
  {% if count > 0 %}
    <h2 class="year">{{y}}</h2>
  {% bibliography -q @*[year={{y}} && author ~= Por && major_contribution = true]* %}
  {% endif %}
{% endfor %}

<h2>minor contribution</h2>

{% for y in years reversed %}
  {% capture count %}
  {% bibliography_count -q @*[year={{y}} && author ~= Por && major_contribution !~ true]* %}
  {% endcapture %}
  {% assign count = count | plus: 0 %}
  {% if count > 0 %}
    <h2 class="year">{{y}}</h2>
  {% bibliography -q @*[year={{y}} && author ~= Por && major_contribution !~ true]* %}
  {% endif %}
{% endfor %}

</div>
