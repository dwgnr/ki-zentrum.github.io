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
<div class="card mb-3 w-100">
  <div class="row g-0">
    <div class="col-md-3">
      <img src="/images/team/{{ member.photo }}" class="img-fluid rounded-start w-100 h-100 object-fit-cover" alt="...">
    </div>
    <div class="col-md-9">
      <div class="card-body">
        <h5 class="card-title">
          {{ member.name }}
          {% if member.twitter %}
          <a href="https://twitter.com/{{member.twitter}}"><i class="fa-brands fa-twitter"></i></a>
          {% endif %}
          {% if member.gscholar %}
          <a href="https://scholar.google.de/citations?user={{member.gscholar}}"><i class="fa-brands fa-google-scholar"></i></a>
          {% endif %}
          {% if member.orcid %}
          <a href="https://orcid.org/{{member.orcid}}"><i class="fa-brands fa-orcid"></i></a>
          {% endif %}
          {% if member.arxiv %}
          <a href="https://arxiv.org/a/{{member.arxiv}}.html"><img src="/images/arxiv-logo.svg" style="display: inline-block; height: 1em;"></a>
          {% endif %}
        </h5>
        <p class="card-text">{{ member.info }}</p>
        {% if member.subject %}
        <p class="card-text"><i class="fa-solid fa-graduation-cap"></i> {{ member.subject }}</p>
        {% endif %}
        {% if member.project %}
        <p class="card-text"><i class="fa-solid fa-screwdriver-wrench"></i>
          {% for p in member.project %}
          <a href="/research/{{ p }}/">{{ p }}</a>{% if forloop.last == false %}, {% endif %}
          {% endfor %}
        </p>
        {% endif %}
        <p class="card-text">
          <small class="text-body-secondary"><i class="fa-solid fa-envelope"></i> {{ member.email }}
          {% if member.pgp %}
            <br/><i class="fa-solid fa-key"></i> <a href="https://keys.openpgp.org/vks/v1/by-fingerprint/{{member.pgp}}" target="_blank">{{ member.pgp }}</a>
          {% endif %}
          </small>
        </p>
      </div>
    </div>
  </div>
</div>
{% endfor %}


## Administrative Support

{% for member in site.data.staff_admin %}
<div class="card mb-3 w-100">
  <div class="row g-0">
    <div class="col-md-3">
      <img src="/images/team/{{ member.photo }}" class="img-fluid rounded-start w-100 h-100 object-fit-cover" alt="...">
    </div>
    <div class="col-md-9">
      <div class="card-body">
        <h5 class="card-title">{{ member.name }}</h5>
        <p class="card-text">
          {{ member.info }}
          {% if member.twitter %}
          <a href="https://twitter.com/{{member.twitter}}"><i class="fa-brands fa-twitter"></i></a>
          {% endif %}
        </p>
        <p class="card-text">
          <small class="text-body-secondary"><i class="fa-solid fa-envelope"></i> {{ member.email }}
          {% if member.pgp %}
            <br/><i class="fa-solid fa-key"></i> <a href="https://keys.openpgp.org/vks/v1/by-fingerprint/{{member.pgp}}" target="_blank">{{ member.pgp }}</a>
          {% endif %}
          </small>
        </p>
      </div>
    </div>
  </div>
</div>
{% endfor %}


## Alumni

{% for member in site.data.alumni %}
<div class="card mb-3 w-100">
  <div class="row g-0">
    <div class="col-md-3">
      <img src="/images/team/{{ member.photo }}" class="img-fluid rounded-start w-100 h-100 object-fit-cover" alt="...">
    </div>
    <div class="col-md-9">
      <div class="card-body">
        <h5 class="card-title">
          {{ member.name }}
          {% if member.twitter %}
          <a href="https://twitter.com/{{member.twitter}}"><i class="fa-brands fa-twitter"></i></a>
          {% endif %}
          {% if member.gscholar %}
          <a href="https://scholar.google.de/citations?user={{member.gscholar}}"><i class="fa-brands fa-google-scholar"></i></a>
          {% endif %}
          {% if member.orcid %}
          <a href="https://orcid.org/{{member.orcid}}"><i class="fa-brands fa-orcid"></i></a>
          {% endif %}
          {% if member.arxiv %}
          <a href="https://arxiv.org/a/{{member.arxiv}}.html"><img src="/images/arxiv-logo.svg" style="display: inline-block; height: 1em;"></a>
          {% endif %}
        </h5>
        <p class="card-text">{{ member.info }}</p>
        <p class="card-text">
          <small class="text-body-secondary"><i class="fa-solid fa-envelope"></i> {{ member.email }}
          {% if member.pgp %}
            <br/><i class="fa-solid fa-key"></i> <a href="https://keys.openpgp.org/vks/v1/by-fingerprint/{{member.pgp}}" target="_blank">{{ member.pgp }}</a>
          {% endif %}
          </small>
        </p>
      </div>
    </div>
  </div>
</div>
{% endfor %}
