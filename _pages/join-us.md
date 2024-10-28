---
title: "Join us!"
layout: page
sitemap: false
permalink: /join-us/
---

Interested in working at our lab?

## Master of Applied Research

Interested in doing a master's degree at our lab, focusing on cutting-edge speech research?
The [Master of Applied Research (M-APR)](https://www.th-nuernberg.de/einrichtungen-gesamt/in-institute/institut-fuer-leistungselektronische-systeme-elsys/studium/forschungsmaster/) is a research-focused degree program.
At its core are two consecutive research projects (10 ECTS each) followed by a research thesis (30 ECTS).


## Research Thesis

Interested in doing a Bachelor's or Master's thesis at our lab?
We currently offer the following topics:

<ul>
{% for page in site.pages %}
  {% if page.dir == '/open-theses/' %}
    <li><a href="{{ page.url }}">{{ page.title }}</a></li>
  {% endif %}
{% endfor %}
</ul>
