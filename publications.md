---
layout: default
title: Publications
---

<h1 class="page-title">Publications</h1>
<p class="page-lede">Jim's <a href="https://scholar.google.com/citations?user={{ site.google_scholar }}" target="_blank" rel="noopener">Google Scholar</a> profile also lists a complete set of publications and preprints. In computational biology, conferences (e.g., RECOMB) have associated journals (e.g., Genome Research). An asterisk (*) indicates co-lead authors.</p>

{% assign selected = site.data.publications | where: "selected", true %}
{% if selected.size > 0 %}
<div class="section" style="margin-top: 0;">
  <h2 class="section__heading">Selected works</h2>
  {% include pub-list.html pubs=selected %}
</div>
{% endif %}

<div class="section">
  <h2 class="section__heading">All publications</h2>
  {% include pub-list.html pubs=site.data.publications %}
</div>
