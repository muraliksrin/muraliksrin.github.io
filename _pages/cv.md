---
layout: single
title: "CV"
permalink: /cv/
author_profile: true
classes: cv-page
---

<!-- Summary pulled from _config.yml (fill fields there) -->
**{{ site.author.name | default: site.title }}** · {{ site.author.employer | default: "" }}  
{{ site.author.location | default: "" }} · {{ site.author.email | default: "" }}

## Education
- **Ph.D.**, Indian Institute of Technology Madras — 2020
- **M.Tech., Communication Engineering**, Indian Institute of Technology Madras — 2020
- **B.E., Electronics and Communication Engineering**, College of Engineering Guindy (Anna University, Chennai) — 2012

## Experience
- **Assistant Professor**, Indian Institute of Technology (BHU), Varanasi — *Dec 2023–Present*
- **Postdoctoral Researcher**, Chalmers University of Technology, Gothenburg — *Dec 2021–2023*  
  Communication Systems Group (Supervisor: Henk Wymeersch)
- **Postdoctoral Researcher**, ETIS (CY Cergy Paris University / ENSEA / CNRS) — *Nov 2020–2021*  
  (Supervisor: Arsenia Chorti)
- **Software Engineer**, Alcatel-Lucent India Ltd. (now Nokia Siemens) — *Jun 2012–Jun 2014*

## Skills
- (Edit this section in `/cv/` page)  
  Signal Processing · Wireless Comm. · Optical Systems · ML for PHY · Python/Matlab

## Publications — Journals
{% assign jpubs = site.publications | where: "type", "journal" | sort: "date" | reverse %}
{% assign jgroups = jpubs | group_by_exp: "p", "p.date | date: '%Y'" %}
{% for g in jgroups %}
### {{ g.name }}
{% for p in g.items %}
- {{ p.authors }}. “{{ p.title }}”. _{{ p.venue }}_, {{ p.date | date: "%Y" }}.
{% endfor %}
{% endfor %}

## Publications — Conferences & Workshops
{% assign cpubs = site.publications | where: "type", "conference" | sort: "date" | reverse %}
{% assign cgroups = cpubs | group_by_exp: "p", "p.date | date: '%Y'" %}
{% for g in cgroups %}
### {{ g.name }}
{% for p in g.items %}
- {{ p.authors }}. “{{ p.title }}”. _{{ p.venue }}_, {{ p.date | date: "%Y" }}.
{% endfor %}
{% endfor %}

## Publications — Book Chapters
{% assign bpubs = site.publications | where: "type", "book" | sort: "date" | reverse %}
{% assign bgroups = bpubs | group_by_exp: "p", "p.date | date: '%Y'" %}
{% for g in bgroups %}
### {{ g.name }}
{% for p in g.items %}
- {{ p.authors }}. “{{ p.title }}”. _{{ p.venue }}_, {{ p.date | date: "%Y" }}.
{% endfor %}
{% endfor %}

## Projects
### PI
{% assign pi = site.projects | where: "role", "PI" | sort: "start" | reverse %}
{% for p in pi %}
- **{{ p.title }}** — {{ p.sponsor }}; {{ p.amount }}; {{ p.start | date: "%b %Y" }}–{{ p.end | date: "%b %Y" }}
{% endfor %}

### Co‑PI
{% assign copi = site.projects | where: "role", "Co-PI" | sort: "start" | reverse %}
{% for p in copi %}
- **{{ p.title }}** — {{ p.sponsor }}; {{ p.amount }}; {{ p.start | date: "%b %Y" }}–{{ p.end | date: "%b %Y" }}
{% endfor %}

## Teaching
{% assign offerings = site.teaching %}
{% assign years = offerings | map: "year" | uniq | sort | reverse %}
{% assign term_order = "odd,even" | split: "," %}
<table class="cv-table">
  <thead>
    <tr><th>Year</th><th>Term</th><th>Course(s)</th></tr>
  </thead>
  <tbody>
{% for y in years %}
  {% for t in term_order %}
    {% assign rows = offerings | where: "year", y | where: "term", t %}
    {% if rows.size > 0 %}
    <tr>
      <td>{{ y }}</td>
      <td>{{ t | capitalize }}</td>
      <td>
        {% for offer in rows %}
          {% assign course = site.courses | where: "code", offer.code | first %}
          {% if course %}
            {{ offer.code }}: {{ course.title | replace_first: offer.code | strip }}
          {% else %}
            {{ offer.code }}
          {% endif %}
          {% unless forloop.last %}; {% endunless %}
        {% endfor %}
      </td>
    </tr>
    {% endif %}
  {% endfor %}
{% endfor %}
  </tbody>
</table>

## Talks
{% assign talks = site.talks | sort: "date" | reverse %}
{% for t in talks %}
- {{ t.date | date: "%b %Y" }} — {{ t.title }}{% if t.venue %}, {{ t.venue }}{% endif %}{% if t.location %}, {{ t.location }}{% endif %}
{% endfor %}
