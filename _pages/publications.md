---
layout: single
title: "Publications"
permalink: /publications/
author_profile: true
---

{% include base_path %}

## Journals
{% assign pubs = site.publications | where: "type", "journal" %}
{% assign groups = pubs | sort: "date" | reverse | group_by_exp: "p", "p.date | date: '%Y'" %}
{% for g in groups %}
### {{ g.name }}
<ul class="pub-list">
  {% for p in g.items %}
    {% if p.url %}
      {% assign link = p.url %}
    {% elsif p.doi %}
      {% assign link = "https://doi.org/" | append: p.doi %}
    {% else %}
      {% assign link = p.url | default: p.permalink | relative_url %}
    {% endif %}
    <li>
      <a href="{{ link }}">{{ p.title }}</a><br>
      <span class="pub-authors">{{ p.authors }}</span><br>
      <span class="pub-venue">{{ p.venue }}</span>
    </li>
  {% endfor %}
</ul>
{% endfor %}

## Conferences & Workshops
{% assign pubs = site.publications | where: "type", "conference" %}
{% assign groups = pubs | sort: "date" | reverse | group_by_exp: "p", "p.date | date: '%Y'" %}
{% for g in groups %}
### {{ g.name }}
<ul class="pub-list">
  {% for p in g.items %}
    {% if p.url %}
      {% assign link = p.url %}
    {% elsif p.doi %}
      {% assign link = "https://doi.org/" | append: p.doi %}
    {% else %}
      {% assign link = p.url | default: p.permalink | relative_url %}
    {% endif %}
    <li>
      <a href="{{ link }}">{{ p.title }}</a><br>
      <span class="pub-authors">{{ p.authors }}</span><br>
      <span class="pub-venue">{{ p.venue }}</span>
    </li>
  {% endfor %}
</ul>
{% endfor %}

## Book Chapters
{% assign pubs = site.publications | where: "type", "book" %}
{% assign groups = pubs | sort: "date" | reverse | group_by_exp: "p", "p.date | date: '%Y'" %}
{% for g in groups %}
### {{ g.name }}
<ul class="pub-list">
  {% for p in g.items %}
    {% if p.url %}
      {% assign link = p.url %}
    {% elsif p.doi %}
      {% assign link = "https://doi.org/" | append: p.doi %}
    {% else %}
      {% assign link = p.url | default: p.permalink | relative_url %}
    {% endif %}
    <li>
      <a href="{{ link }}">{{ p.title }}</a><br>
      <span class="pub-authors">{{ p.authors }}</span><br>
      <span class="pub-venue">{{ p.venue }}</span>
    </li>
  {% endfor %}
</ul>
{% endfor %}
