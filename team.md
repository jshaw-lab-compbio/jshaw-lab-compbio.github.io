---
layout: default
title: Team
---

<h1 class="page-title">Team</h1>
<p class="page-lede">The people behind the lab's research.</p>

{% assign pi = site.data.team | where: "role", "pi" | first %}
{% if pi %}
<div class="pi-block">
  {% if pi.photo %}
  <img class="pi-block__photo" src="{{ pi.photo | relative_url }}" alt="{{ pi.name }}">
  {% endif %}
  <div class="pi-block__info">
    <div class="team-card__role">{{ pi.title }}</div>
    <h2 style="margin-bottom: 0.3em;">{{ pi.name }}</h2>
    <p class="team-card__bio">{{ pi.bio }}</p>
    {% if pi.links or pi.cv %}
    <div class="pub-links">
      {% if pi.cv %}<a href="{% if pi.cv contains '://' %}{{ pi.cv }}{% else %}{{ pi.cv | relative_url }}{% endif %}" target="_blank" rel="noopener">CV</a>{% endif %}
      {% for link in pi.links %}
      <a href="{{ link.url }}" target="_blank" rel="noopener">{{ link.label }}</a>
      {% endfor %}
    </div>
    {% endif %}
  </div>
</div>
{% endif %}

{% assign members = site.data.team | where_exp: "m", "m.role != 'pi'" %}
{% if members.size > 0 %}
<div class="section">
  <h2 class="section__heading">Lab Members</h2>
  <div class="team-grid">
    {% for member in members %}
    <div>
      {% if member.photo %}
      <img class="team-card__photo" src="{{ member.photo | relative_url }}" alt="{{ member.name }}">
      {% else %}
      <div class="team-card__photo"></div>
      {% endif %}
      <div class="team-card__name">{{ member.name }}</div>
      <div class="team-card__role">{{ member.title }}</div>
      <p class="team-card__bio">{{ member.bio }}</p>
      {% if member.cv %}
      <div class="pub-links"><a href="{% if member.cv contains '://' %}{{ member.cv }}{% else %}{{ member.cv | relative_url }}{% endif %}" target="_blank" rel="noopener">CV</a></div>
      {% endif %}
    </div>
    {% endfor %}
  </div>
</div>
{% endif %}

<div class="section">
  <h2 class="section__heading">Join Us</h2>
  <p>We're growing — see the <a href="{{ '/join/' | relative_url }}">How to Join</a> page for how to get in touch.</p>
</div>
