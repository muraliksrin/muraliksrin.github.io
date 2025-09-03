---
layout: single
title: "Projects Awarded"
permalink: /projects/
author_profile: true
---

{% include base_path %}

{%- assign pi = site.projects | where: "role", "PI" | sort: "start" | reverse -%}
{%- assign copi = site.projects | where: "role", "Co-PI" | sort: "start" | reverse -%}

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
    <!-- PI block first -->
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

    <!-- Co-PI block after PI -->
    {% for p in copi %}
    <tr>
      <td>{{ forloop.index }}</td>
      <td><a href="{{ p.url | relative_url }}">{{ p.title }}</a></td>
      <td>{{ p.sponsor }}</td>
      <td>{{ p.amount }}</td>
      <td>{{ p.role }}</td>
      <td>{{ p.start | date: "%b %Y" }} – {{ p.end | date: "%b %Y" }}</td>
    </tr>
    {% endfor %}
  </tbody>
</table>
