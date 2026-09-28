---
layout: default
title: Software
---

<h1 class="page-title">Software</h1>
<p class="page-lede">Open-source tools developed by the lab.</p>

<div class="software-list">
  {% for tool in site.data.software %}
  <div class="software-item" style="--tool-color: {{ tool.color | default: site.accent_color }};">
    <div class="software-item__header">
      <span class="software-item__name">
        <span class="software-item__dot"></span>{{ tool.name }}
      </span>
      {% if tool.links %}
      <span class="software-item__links">
        {% for link in tool.links %}
        <a href="{{ link.url }}" target="_blank" rel="noopener">{{ link.label }}</a>
        {% endfor %}
      </span>
      {% endif %}
    </div>
    <div class="software-item__tagline">{{ tool.tagline }}</div>
    <p class="software-item__desc">{{ tool.description }}</p>
    {% if tool.publication %}
    <a class="software-item__pub" href="{{ tool.publication.url }}" target="_blank" rel="noopener">
      {{ tool.publication.venue }}, {{ tool.publication.year }}
    </a>
    {% endif %}
  </div>
  {% endfor %}
</div>
