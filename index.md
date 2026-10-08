---
layout: default
title: Research
---

<div class="hero">
  <div class="hero__text">
    {% if site.university != "" %}<div class="hero__eyebrow">{{ site.department }} · {{ site.university }}</div>{% endif %}
    <h1 class="hero__title">Algorithms and Data Science for (Microbial) Genomics</h1>
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
<b>We build computational methods to make sense
    of large-scale biological sequence data</b>, such as trillions of DNA or amino acids characters. To do this, we use a pragmatic combination of techniques spanning <b>classical algorithm design to modern data science methods</b>. 
  </p>

  <p>
    Our tools and software are routinely used by biologists to search, compare, and reconstruct hundreds of terabytes of genomic data for biological discovery. We take pride in computational methodology being driven by real biological applications, usually in the fascinating field of microbiome and "metaomics" research. See below for specific areas of research we are interested in. 
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
        <h3>Terabyte-scale algorithms for disentangling microbial genomics data</h3>
        <p>To analyze and compare terabytes of redundant, noisy sequencing data, we design highly efficient algorithms and turn them into high-performance tools. 
    We leverage ideas from string algorithms (e.g., edit distance computation / dynamic programming) and combine them with a probabilistic flavor (e.g., sketching-based techniques and statistical inference).  </p>
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
        <h3>Long-read metagenome assembly: reconstructing genomes from substrings</h3>
        <p> We work on the exciting field of metagenome assembly, where we use highly efficient graph algorithms to reconstruct microbial genomes from the sequencing of entire microbiomes, such as our gut. In some environments, more than 90% of genomes can be completely novel; thus, our algorithms are frequently used to discover genomes of completely novel species. </p>
      </div>
    </div>
    <div class="research-item">
      <div class="research-icon">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.6" stroke-linecap="round" stroke-linejoin="round">
          <path d="M12 3v7M12 10c-4 0-6 2-6 5v6M12 10c4 0 6 2 6 5v6M6 21v-4M18 21v-4"/>
        </svg>
      </div>
      <div>
        <h3>Microbiome genome evolution and horizontal gene transfer</h3>
        <p> In a microbiome, trillions of microbes interact and evolve, often driven by horizontal gene transfer, where DNA jumps between organisms. This is mediated by mobile genetic elements (MGEs) that confer important adaptive traits such as pathogenicity or antibiotic resistance. We are building computational tools to illuminate these events and broadly characterize MGEs such as prophages, plasmids, and transposons in human and environmental microbiomes.  </p>
      </div>
    </div>
  </div>
</div>

<div class="section">
  <h2 class="section__heading">Recent Publications</h2>
  {% assign recent = site.data.publications | slice: 0, 3 %}
  {% include pub-list.html pubs=recent %}
  <a class="view-all" href="{{ '/publications/' | relative_url }}">View all publications &rarr;</a>
</div>
