---
layout: single
title: "Projects Awarded"
permalink: /projects/
author_profile: true
---

{% include base_path %}

{% assign all = site.projects %}
{% if all %}
  {% assign pi   = all  | where: "role", "PI"    | sort: "start" | reverse %}
  {% assign copi = all  | where: "role", "Co-PI" | sort: "start" | reverse %}
{% else %}
  {% assign pi   = "" | split: "|" %}
  {% assign copi = "" | split: "|" %}
{% endif %}

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
    {% assign n = 0 %}

    {%- comment -%} PI block {%- endcomment -%}
    {% for p in pi %}
      {% assign n = n | plus: 1 %}
      <tr>
        <td>{{ n }}</td>
        <td><a href="{{ p.url | relative_url }}">{{ p.title }}</a></td>
        <td>{{ p.sponsor }}</td>
        <td>{{ p.amount }}</td>
        <td>{{ p.role }}</td>
        <td>{{ p.start | date: "%b %Y" }} – {{ p.end | date: "%b %Y" }}</td>
      </tr>
    {% endfor %}

    {%- comment -%} Co-PI block {%- endcomment -%}
    {% for p in copi %}
      {% assign n = n | plus: 1 %}
      <tr>
        <td>{{ n }}</td>
        <td><a href="{{ p.url | relative_url }}">{{ p.title }}</a></td>
        <td>{{ p.sponsor }}</td>
        <td>{{ p.amount }}</td>
        <td>{{ p.role }}</td>
        <td>{{ p.start | date: "%b %Y" }} – {{ p.end | date: "%b %Y" }}</td>
      </tr>
    {% endfor %}
  </tbody>
</table>
