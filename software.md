---
layout: default
title: Software
---

<h1 class="page-title">Software</h1>
Our lab has written widely used software in microbial genomics such as [skani (Nature Methods, 2023)](https://www.nature.com/articles/s41592-023-02018-3), [sylph (Nature Biotechnology, 2024)](https://www.nature.com/articles/s41587-024-02412-y), and [myloasm (Nature Biotechnology, 2026)](https://www.nature.com/articles/s41587-026-03053-z). 

Below is a complete list of software written directly by lab members or supervised by our lab.

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
        <a href="{{ link.url }}" target="_blank" rel="noopener">{{ link.label }}</a>{% if link.url contains "https://github.com/" %}<span class="gh-stars" data-repo="{{ link.url | remove: 'https://github.com/' }}" hidden></span>{% endif %}
        {% endfor %}
      </span>
      {% endif %}
    </div>
    <div class="software-item__tagline">{{ tool.tagline }}</div>
    {% if tool.description %}<p class="software-item__desc">{{ tool.description }}</p>{% endif %}
    {% if tool.publication %}
    <a class="software-item__pub" href="{{ tool.publication.url }}" target="_blank" rel="noopener">
      {{ tool.publication.venue }}, {{ tool.publication.year }}
    </a>
    {% endif %}
  </div>
  {% endfor %}
</div>

<script>
// Fills in GitHub star counts in the visitor's browser, then sorts the list by
// stars (most first). Counts are cached in localStorage for an hour to stay
// under the unauthenticated GitHub API limit. If anything fails, the badge stays
// hidden and the order from _data/software.yml is kept.
(function () {
  var TTL = 60 * 60 * 1000;
  var list = document.querySelector('.software-list');

  function stars(repo) {
    var key = 'gh-stars:' + repo;
    try {
      var c = JSON.parse(localStorage.getItem(key) || 'null');
      if (c && Date.now() - c.t < TTL) return Promise.resolve(c.n);
    } catch (e) {}
    return fetch('https://api.github.com/repos/' + repo)
      .then(function (r) { return r.ok ? r.json() : Promise.reject(); })
      .then(function (d) {
        if (typeof d.stargazers_count !== 'number') return null;
        try { localStorage.setItem(key, JSON.stringify({ n: d.stargazers_count, t: Date.now() })); } catch (e) {}
        return d.stargazers_count;
      })
      .catch(function () { return null; });
  }

  var jobs = Array.prototype.map.call(document.querySelectorAll('.gh-stars'), function (el) {
    return stars(el.dataset.repo).then(function (n) {
      if (n === null) return;
      el.textContent = '\u2605 ' + n.toLocaleString();
      el.hidden = false;
      var item = el.closest('.software-item');
      item.dataset.stars = Math.max(n, +item.dataset.stars || 0);
    });
  });

  Promise.all(jobs).then(function () {
    var items = Array.prototype.slice.call(list.children);
    items.forEach(function (it, i) { it.dataset.order = i; });
    items.sort(function (a, b) {
      var d = (+b.dataset.stars || -1) - (+a.dataset.stars || -1);
      return d || a.dataset.order - b.dataset.order;
    });
    items.forEach(function (it) { list.appendChild(it); });
  });
})();
</script>
