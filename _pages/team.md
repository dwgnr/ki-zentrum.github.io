---
title: "KIZ: Team"
layout: gridlay
excerpt: "KIZ: Team members"
sitemap: false
permalink: /team/
---

# Group Members

Jump to [staff](#staff), [administrative support](#administrative-support), [students](#master-and-bachelor-students), [alumni](#alumni).

## Research Staff
{% assign number_printed = 0 %}
{% for member in site.data.staff_scientific %}

{% assign even_odd = number_printed | modulo: 2 %}

{% if even_odd == 0 %}
<div class="row">
{% endif %}

<div class="col-sm-6 clearfix">
  <img src="{{ site.url }}{{ site.baseurl }}/images/team/{{ member.photo }}" class="img-responsive" width="25%" style="float: left" />
  <h4>{{ member.name }}</h4>
  <i>{{ member.info }} <br>email: <{{ member.email }}></i>
  
  {% if member.education %}
  <ul style="overflow: hidden">
  {% for edu in member.education %}
    <li> {{ edu }} </li>
  {% endfor %}
  </ul>
  {% endif %}
</div>

{% assign number_printed = number_printed | plus: 1 %}

{% if even_odd == 1 %}
</div>
{% endif %}

{% endfor %}

{% assign even_odd = number_printed | modulo: 2 %}
{% if even_odd == 1 %}
</div>
{% endif %}

## Administrative Support

{% assign number_printed = 0 %}
{% for member in site.data.staff_admin %}

{% assign even_odd = number_printed | modulo: 2 %}

{% if even_odd == 0 %}
<div class="row">
{% endif %}

<div class="col-sm-6 clearfix">
  <img src="{{ site.url }}{{ site.baseurl }}/images/team/{{ member.photo }}" class="img-responsive" width="25%" style="float: left" />
  <h4>{{ member.name }}</h4>
  <i>{{ member.info }} <br>email: <{{ member.email }}></i>
  
  {% if member.education %}
  <ul style="overflow: hidden">
  {% for edu in member.education %}
    <li> {{ edu }} </li>
  {% endfor %}
  </ul>
  {% endif %}
</div>

{% assign number_printed = number_printed | plus: 1 %}

{% if even_odd == 1 %}
</div>
{% endif %}

{% endfor %}

{% assign even_odd = number_printed | modulo: 2 %}
{% if even_odd == 1 %}
</div>
{% endif %}


## Students
{% assign number_printed = 0 %}
{% for member in site.data.students %}

{% assign even_odd = number_printed | modulo: 2 %}

{% if even_odd == 0 %}
<div class="row">
{% endif %}

<div class="col-sm-6 clearfix">
  <h4>{{ member.name }}</h4>
  <i>{{ member.info }}</i>
  <p>{{ member.topic }}</p>
</div>

{% assign number_printed = number_printed | plus: 1 %}

{% if even_odd == 1 %}
</div>
{% endif %}

{% endfor %}

{% assign even_odd = number_printed | modulo: 2 %}
{% if even_odd == 1 %}
</div>
{% endif %}



## Alumni

{% assign number_printed = 0 %}
{% for member in site.data.alumni %}

{% assign even_odd = number_printed | modulo: 2 %}

{% if even_odd == 0 %}
<div class="row">
{% endif %}

<div class="col-sm-6 clearfix">
  <img src="{{ site.url }}{{ site.baseurl }}/images/team/{{ member.photo }}" class="img-responsive" width="25%" style="float: left" />
  <h4>{{ member.name }}</h4>
  <i>{{ member.duration }} <br> Role: {{ member.info }} <br> Now at: {{ member.now}} </i>
</div>

{% assign number_printed = number_printed | plus: 1 %}

{% if even_odd == 1 %}
</div>
{% endif %}

{% endfor %}

{% assign even_odd = number_printed | modulo: 2 %}
{% if even_odd == 1 %}
</div>
{% endif %}
