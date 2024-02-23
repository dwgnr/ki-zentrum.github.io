---
title: "KIZ: Team"
layout: team
excerpt: "KIZ: Team members"
sitemap: false
permalink: /team/
---

# Group Members


## Research Staff

{% for member in site.data.staff_scientific %}
<div class="card mb-3" style="max-width: 540px;">
  <div class="row g-0">
    <div class="col-md-4">
      <img src="/images/team/{{ member.photo }}" class="img-fluid rounded-start" alt="...">
    </div>
    <div class="col-md-8">
      <div class="card-body">
        <h5 class="card-title">{{ member.name }}</h5>
        <p class="card-text">{{ member.info }}</p>
        {% if member.subject %}
        <p class="card-text"><i class="fa-solid fa-graduation-cap"></i> {{ member.subject }}</p>
        {% endif %}
        {% if member.project %}
        <p class="card-text"><i class="fa-solid fa-screwdriver-wrench"></i>
          {% for p in member.project %}
          <a href="/research/{{ member.project }}/">{{ p }}</a>{% if forloop.last == false %}, {% endif %}
          {% endfor %}
        </p>
        {% endif %}
        <p class="card-text"><small class="text-body-secondary"><i class="fa-solid fa-envelope"></i> {{ member.email }} </small></p>
      </div>
    </div>
  </div>
</div>
{% endfor %}


## Administrative Support

{% for member in site.data.staff_admin %}
<div class="card mb-3" style="max-width: 540px;">
  <div class="row g-0">
    <div class="col-md-4">
      <img src="/images/team/{{ member.photo }}" class="img-fluid rounded-start" alt="...">
    </div>
    <div class="col-md-8">
      <div class="card-body">
        <h5 class="card-title">{{ member.name }}</h5>
        <p class="card-text">{{ member.info }}</p>
        <p class="card-text"><small class="text-body-secondary"><i class="fa-solid fa-envelope"></i> {{ member.email }}</small></p>
      </div>
    </div>
  </div>
</div>
{% endfor %}


## Alumni

{% for member in site.data.alumni %}
<div class="card mb-3" style="max-width: 540px;">
  <div class="row g-0">
    <div class="col-md-4">
      <img src="/images/team/{{ member.photo }}" class="img-fluid rounded-start" alt="...">
    </div>
    <div class="col-md-8">
      <div class="card-body">
        <h5 class="card-title">{{ member.name }}</h5>
        <p class="card-text">{{ member.info }}</p>
        <p class="card-text"><small class="text-body-secondary"><i class="fa-solid fa-envelope"></i> {{ member.email }}</small></p>
      </div>
    </div>
  </div>
</div>
{% endfor %}
