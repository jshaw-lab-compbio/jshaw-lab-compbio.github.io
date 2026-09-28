---
layout: default
title: Research
---

<div class="hero">
  <div class="hero__text">
    <div class="hero__eyebrow">{{ site.department }} · {{ site.university }}</div>
    <h1 class="hero__title">Algorithms and Data Science for Microbial Genomics</h1>
    <p class="hero__lede">{{ site.description }}</p>
  </div>

  {% if site.hero_image and site.hero_image != "" %}
  <div class="hero__media">
    <img src="{{ site.hero_image | relative_url }}" alt="{{ site.hero_image_caption | default: site.title }}">
    {% if site.hero_image_caption and site.hero_image_caption != "" %}
    <p class="hero__caption">{{ site.hero_image_caption }}</p>
    {% endif %}
  </div>
  {% endif %}
</div>

<div class="section">
  <h2 class="section__heading">Research Overview</h2>
  <p>
    We build computational methods and open-source software for making sense
    of large-scale microbial and metagenomic sequencing data. Modern
    sequencing produces datasets — from long-read metagenomes to massive
    microbial reference databases — that outpace the algorithms designed to
    analyze them. Our lab works at the intersection of algorithm design,
    statistics, and applied genomics to close that gap.
  </p>
  <p>
    A second, related thread of our work asks evolutionary questions about
    microbial genomes and microbiome communities: how strains diverge, how
    genomes assemble and recombine within a community, and what these
    dynamics reveal about the underlying biology.
  </p>
</div>

<div class="section">
  <h2 class="section__heading">Research Areas</h2>
  <div class="research-list">
    <div class="research-item">
      <div class="research-icon">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.6" stroke-linecap="round" stroke-linejoin="round">
          <path d="M4 19V9M10 19V5M16 19v-7M22 19v-3"/>
        </svg>
      </div>
      <div>
        <h3>Ultrafast genome comparison</h3>
        <p>Sketch-based and probabilistic methods for computing genome and
        metagenome similarity at the scale of hundreds of thousands of
        references.</p>
      </div>
    </div>
    <div class="research-item">
      <div class="research-icon">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.6" stroke-linecap="round" stroke-linejoin="round">
          <circle cx="7" cy="7" r="3"/><circle cx="17" cy="7" r="2"/>
          <circle cx="8" cy="17" r="2.5"/><circle cx="17" cy="16" r="3"/>
          <path d="M9.5 8.8 L15.5 15.2 M8.5 9.8 L7.6 14.7"/>
        </svg>
      </div>
      <div>
        <h3>Long-read metagenome assembly</h3>
        <p>Assembly and profiling methods tailored to long-read sequencing of
        complex, multi-strain microbial communities.</p>
      </div>
    </div>
    <div class="research-item">
      <div class="research-icon">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.6" stroke-linecap="round" stroke-linejoin="round">
          <path d="M12 3v7M12 10c-4 0-6 2-6 5v6M12 10c4 0 6 2 6 5v6M6 21v-4M18 21v-4"/>
        </svg>
      </div>
      <div>
        <h3>Microbiome genome evolution</h3>
        <p>Analytical approaches for understanding how microbial strains and
        genomes evolve within and across host-associated communities.</p>
      </div>
    </div>
  </div>
</div>

<div class="section">
  <h2 class="section__heading">Recent Publications</h2>
  <ul class="pub-list">
    {% for pub in site.data.publications limit:3 %}
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
  <a class="view-all" href="{{ '/publications/' | relative_url }}">View all publications &rarr;</a>
</div>
