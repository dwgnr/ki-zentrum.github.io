---
title: "Research"
layout: page
sitemap: false
permalink: /research/
---

## Current

{% for p in site.data.projects_current %}
<div class="card mb-3">
  <div class="row g-0">
    <div class="col-md-4 d-flex">
      <img src="{{p.image}}" class="img-fluid rounded-start h-100 object-fit-cover">
  	</div>
   	<div class="col-md-8">
      <div class="card-body">
        <h3 class="card-title">{{p.name}} ({% if p.end %}{{p.start}} &mdash; {{p.end}}{% else %}since {{p.start}}{% endif %})</h3>
        <p class="card-text">{{p.description}}</p>
        <p><small><a href="{{p.url}}">Learn more...</a></small></p>
      </div>
    </div>
  </div>
</div>
{% endfor %}


## Past

{% for p in site.data.projects_past %}
<div class="card mb-3">
  <div class="row g-0">
    <div class="col-md-4 d-flex">
      <img src="{{p.image}}" class="img-fluid rounded-start h-100 object-fit-cover">
    </div>
    <div class="col-md-8">
      <div class="card-body">
        <h3 class="card-title">{{p.name}} ({% if p.end %}{{p.start}} &mdash; {{p.end}}{% else %}since {{p.start}}{% endif %})</h3>
        <p class="card-text">{{p.description}}</p>
        <p><small><a href="{{p.url}}">Learn more...</a></small></p>
      </div>
    </div>
  </div>
</div>
{% endfor %}


