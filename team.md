---
layout: default
title: Jim & Team
---

<h1 class="page-title">Jim &amp; Team</h1>
<p class="page-lede">The people behind the lab's research.</p>

{% assign pi = site.data.team | where: "role", "pi" | first %}
{% if pi %}
<div class="section">
  <h2 class="section__heading">Assistant Professor</h2>
  {% include person-card.html person=pi %}
</div>
{% endif %}

{% assign members = site.data.team | where_exp: "m", "m.role != 'pi'" %}
<div class="section">
  <h2 class="section__heading">Lab Members</h2>
  {% for member in members %}
    {% include person-card.html person=member %}
  {% endfor %}
  {% if members.size > 0 %}
  <p>We're growing — see the <a href="{{ '/join/' | relative_url }}">How to Join</a> page for how to get in touch.</p>
  {% else %}
  <p>Our first students and postdocs will join in Fall 2027. This could be you! See the <a href="{{ '/join/' | relative_url }}">How to Join</a> page.</p>
  {% endif %}
</div>
