---
layout: default
title: Publications
---

<h1 class="page-title">Publications</h1>
<p class="page-lede">See also our <a href="https://scholar.google.com/citations?user={{ site.google_scholar }}" target="_blank" rel="noopener">Google Scholar</a> profile.</p>

<ul class="pub-list">
  {% for pub in site.data.publications %}
  <li>
    <span class="pub-year">{{ pub.year }}</span>
    <div class="pub-body">
      <div class="pub-title">{{ pub.title }}</div>
      <div class="pub-meta">{{ pub.authors }} — <em>{{ pub.venue }}</em></div>
      {% if pub.links %}
      <div class="pub-links">
        {% for link in pub.links %}
        <a href="{{ link.url }}" target="_blank" rel="noopener">{{ link.label }}</a>
        {% endfor %}
      </div>
      {% endif %}
    </div>
  </li>
  {% endfor %}
</ul>
