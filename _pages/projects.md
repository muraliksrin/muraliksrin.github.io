---
layout: single
title: "Projects Awarded"
permalink: /projects/
author_profile: true
---

{% include base_path %}

{%- assign all = site.projects -%}
{%- if all == nil -%}
  {%- assign all = "" | split: "|" -%} {# creates an empty array #}
{%- endif -%}

{%- assign pi   = all | where: "role", "PI"     | sort: "start" | reverse -%}
{%- assign copi = all | where: "role", "Co-PI"  | sort: "start" | reverse -%}

<table class="projects-table">
  <thead>
    <tr>
      <th style="width:3rem;">No</th>
      <th>Title of Project</th>
      <th>Sponsoring Organization</th>
      <th>Amount of Grant</th>
      <th>Role</th>
      <th>Duration</th>
    </tr>
  </thead>
  <tbody>
    {# PI block first #}
    {% for p in pi %}
    <tr>
      <td>{{ forloop.index }}</td>
      <td><a href="{{ p.url | relative_url }}">{{ p.title }}</a></td>
      <td>{{ p.sponsor }}</td>
      <td>{{ p.amount }}</td>
      <td>{{ p.role }}</td>
      <td>{{ p.start | date: "%b %Y" }} – {{ p.end | date: "%b %Y" }}</td>
    </tr>
    {% endfor %}

    {# Co-PI block #}
    {% for p in copi %}
    <tr>
