---
layout: default
permalink: /
title: ""
excerpt: "Yibo Zhou — Learning Beyond Spurious Correlations"
author_profile: true
---

<div id="portfolio">

<section id="about-me">
  <h1>About Me</h1>

  <p class="p-tagline">
    Learning Beyond Spurious Correlations
  </p>

  <p>
    I am <strong>Yibo Zhou (周亦博)</strong>.
    I received my Ph.D. in Artificial Intelligence from
    <strong>Beihang University</strong> in June 2026.
  </p>

  <p class="p-advisor">
    During my Ph.D., I was advised by
    <strong>Prof. Hai-Miao Hu</strong>.
  </p>

  <p>
    My research asks when learning systems can distinguish
    task-relevant structure from misleading statistical regularities.
    I connect <strong>identifiability and computational limits</strong>,
    <strong>shortcut-resistant evaluation</strong>, and
    <strong>balanced representation learning</strong>.
  </p>

  <p>
    Across these directions, I study
    <strong>what data can identify</strong>,
    <strong>what algorithms can recover</strong>, and
    <strong>what evaluations can verify</strong>,
    with applications to out-of-distribution detection and
    pedestrian attribute recognition.
  </p>
</section>

<section id="arxiv-updates">
  <h1>arXiv Papers · Auto-updated</h1>

  <p>
    This list is automatically loaded from my arXiv author profile.
    <a
      href="https://arxiv.org/a/0000-0001-7964-7517"
      target="_blank"
      rel="noopener">
      View all papers on arXiv
    </a>
  </p>

  <div id="arxivfeed">
    Loading the arXiv publication list...
  </div>
</section>

<script>
  var arxiv_authorid = "0000-0001-7964-7517";
  var arxiv_format = "arxiv";
  var arxiv_max_entries = 10;
  var arxiv_includeTitle = 0;
  var arxiv_includeSummary = 0;
  var arxiv_includeComments = 0;
  var arxiv_includeSubjects = 0;
  var arxiv_includeJournalRef = 1;
  var arxiv_includeDOI = 1;
</script>

<script src="https://arxiv.org/js/myarticles.js"></script>

<section id="publications">
  <h1>Selected Publications</h1>

  <p class="p-muted">
    Complete author lists are available on the linked paper pages.
    Click a figure to enlarge it.
  </p>

  <div id="p-filters" class="p-filters" hidden>
    <input
      id="p-search"
      type="search"
      placeholder="Search papers..."
      aria-label="Search papers">

    <select id="p-topic" aria-label="Filter by research direction">
      <option value="">All topics</option>
      <option value="theory">Identifiability &amp; computation</option>
      <option value="evaluation">Evaluation &amp; OOD</option>
      <option value="representation">Representation &amp; balancing</option>
    </select>

    <select id="p-year" aria-label="Filter by year">
      <option value="">All years</option>
      {% assign years = site.data.papers | map: "year" | uniq | sort | reverse %}
      {% for year in years %}
      <option value="{{ year }}">{{ year }}</option>
      {% endfor %}
    </select>

    <span id="p-count" class="p-muted" aria-live="polite"></span>
  </div>

  {% for paper in site.data.papers %}
  <article
    class="paper-box p-card"
    data-year="{{ paper.year }}"
    data-topic="{{ paper.topic }}">

    <div class="paper-box-image">
      <div>
        <div class="badge">{{ paper.venue }}</div>

        <button
          type="button"
          class="p-zoom"
          aria-label="Enlarge figure: {{ paper.title | escape }}">

          <img
            src="{{ '/images/' | append: paper.image | relative_url }}"
            alt="{{ paper.title | escape }}"
            loading="lazy">
        </button>
      </div>
    </div>

    <div class="paper-box-text">
      <h3>
        <a
          href="{{ paper.url | escape }}"
          target="_blank"
          rel="noopener">{{ paper.title }}</a>
      </h3>

      <p>
        <strong>Yibo Zhou</strong>

        <span class="p-role">
          {% if paper.sole %}
            Sole author
          {% elsif paper.role == "corresponding" %}
            Corresponding author
          {% else %}
            First author
          {% endif %}
        </span>
      </p>

      <p class="p-muted">
        {{ paper.venue }} · {{ paper.status }}

        {% if paper.honor %}
        <span class="p-honor">{{ paper.honor }}</span>
        {% endif %}
      </p>

      <p class="p-takeaway">
        {{ paper.takeaway }}
      </p>

      <p class="p-links">
        <a
          href="{{ paper.url | escape }}"
          target="_blank"
          rel="noopener">Paper</a>

        {% if paper.code %}
        <a
          href="{{ paper.code | escape }}"
          target="_blank"
          rel="noopener">Code</a>
        {% endif %}
      </p>

      <details>
        <summary>Research summary</summary>
        <p>{{ paper.summary }}</p>
      </details>
    </div>
  </article>
  {% endfor %}
</section>

<section id="patent">
  <h1>Patent Application</h1>

  <p>
    <a
      href="https://patents.google.com/patent/CN117115851A/en"
      target="_blank"
      rel="noopener"><strong>CN 117115851 A</strong></a>
    — A Pedestrian Attribute Recognition Method for Complex
    Surveillance Scenarios.
  </p>
</section>

<section id="education">
  <h1>Education</h1>

  <ul>
    <li>
      <strong>Beihang University</strong><br>
      Ph.D. in Artificial Intelligence<br>
      September 2022 – June 2026
    </li>

    <li>
      <strong>University of California San Diego</strong><br>
      M.S. in Electrical Engineering<br>
      August 2017 – May 2019
    </li>

    <li>
      <strong>Lanzhou University</strong><br>
      B.S. in Materials Physics<br>
      August 2013 – June 2017
    </li>
  </ul>
</section>

<section id="experience">
  <h1>Professional Experience</h1>

  <p>
    <strong>OPPO Guangdong Mobile Telecommunications Corp., Ltd.</strong><br>
    Artificial Intelligence Algorithm Engineer<br>
    101 Laboratory · Imaging Algorithm Development Department<br>
    July 2019 – March 2021 · Shenzhen, China
  </p>
</section>

</div>

{% include portfolio-tools.html %}
