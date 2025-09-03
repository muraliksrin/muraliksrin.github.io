---
layout: archive
title: "Courses"
permalink: /courses/
author_profile: true
---

{% include base_path %}

{% for course in site.courses reversed %}
  {% include archive-single.html %}
{% endfor %}
