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

  <p class="p-tagline">Learning Beyond Spurious Correlations</p>

  <p>
    I am <strong>Yibo Zhou (周亦博)</strong>, a Ph.D. graduate in
    Artificial Intelligence from
    <a class="p-academic-link"
       href="https://www.buaa.edu.cn/"
       target="_blank" rel="noopener noreferrer">Beihang University</a>
    (June 2026).
  </p>

  <p class="p-advisor">
    My doctoral advisor was
    <a class="p-academic-link"
       href="https://teacher.buaa.edu.cn/huhaimiao/en/index/28756/list/index.htm"
       target="_blank" rel="noopener noreferrer">Prof. Hai-Miao Hu</a>.
  </p>

  <p>
    My research connects <strong>identifiability and computational limits</strong>,
    <strong>shortcut-resistant evaluation</strong>, and
    <strong>balanced representation learning</strong>.
    I study when models can recover task-relevant structure rather than
    rely on misleading statistical regularities.
  </p>

  <p>
    Across these directions, I examine
    <strong>what data can identify</strong>,
    <strong>what algorithms can recover</strong>, and
    <strong>what evaluations can verify</strong>,
    with applications to trustworthy computer vision,
    out-of-distribution detection, and pedestrian attribute recognition.
  </p>

  <p class="p-links">
    <a href="mailto:ybzhou@buaa.edu.cn">Email</a>
    <a href="https://scholar.google.com/citations?user=Ch18_eIAAAAJ"
       target="_blank" rel="noopener noreferrer">Google Scholar</a>
    <a href="https://orcid.org/0000-0001-7964-7517"
       target="_blank" rel="noopener noreferrer">ORCID</a>
    <a href="https://github.com/SDret"
       target="_blank" rel="noopener noreferrer">GitHub</a>
  </p>
</section>

<section id="news">
  <h1>News</h1>

  {% assign honors = site.data.news | where: "kind", "honor" %}
  <div class="n-awards">
    {% for item in honors %}
    <article class="n-award">
      <div class="n-award-top">
        <span class="n-star" aria-hidden="true">★</span>
        <span class="n-date">{{ item.date }}</span>
      </div>
      <h3>{{ item.title }}</h3>
      <p>{{ item.text }}</p>
    </article>
    {% endfor %}
  </div>

  {% assign updates = site.data.news | where: "kind", "paper" %}
  <ul class="n-timeline" role="list">
    {% for item in updates limit:3 %}
    <li>
      <span class="n-date">{{ item.date }}</span>
      <div>
        <span class="n-tag">{{ item.tag }}</span>
        <p><strong>{{ item.title }}</strong> — {{ item.text }}</p>
        <div class="n-links">
          {% if item.url %}
          <a href="{{ item.url | escape }}"
             target="_blank" rel="noopener noreferrer">Paper ↗</a>
          {% endif %}
          {% if item.code %}
          <a href="{{ item.code | escape }}"
             target="_blank" rel="noopener noreferrer">Code ↗</a>
          {% endif %}
        </div>
      </div>
    </li>
    {% endfor %}
  </ul>

  {% if updates.size > 3 %}
  <details class="n-history">
    <summary>Earlier publication updates</summary>
    <ul class="n-timeline" role="list">
      {% for item in updates offset:3 %}
      <li>
        <span class="n-date">{{ item.date }}</span>
        <div>
          <span class="n-tag">{{ item.tag }}</span>
          <p><strong>{{ item.title }}</strong> — {{ item.text }}</p>
          <div class="n-links">
            {% if item.url %}
            <a href="{{ item.url | escape }}"
               target="_blank" rel="noopener noreferrer">Paper ↗</a>
            {% endif %}
            {% if item.code %}
            <a href="{{ item.code | escape }}"
               target="_blank" rel="noopener noreferrer">Code ↗</a>
            {% endif %}
          </div>
        </div>
      </li>
      {% endfor %}
    </ul>
  </details>
  {% endif %}
</section>

<section id="publications">
  <h1>Selected Publications</h1>

  <p class="p-muted">
    Complete author lists are available on the linked paper pages.
    Click a figure to enlarge it.
  </p>

  <div id="p-filters" class="p-filters" hidden>
    <input id="p-search" type="search"
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

  {% assign ordered_papers = site.data.papers | sort: "display_order", "last" %}
  {% for paper in ordered_papers %}
  <article class="paper-box p-card"
           data-year="{{ paper.year }}"
           data-topic="{{ paper.topic }}"
           data-role="{{ paper.role }}"
           data-title="{{ paper.title | escape }}">

    <div class="paper-box-image">
      <div>
        <div class="badge">{{ paper.venue }}</div>
        <button type="button" class="p-zoom"
                aria-label="Enlarge figure: {{ paper.title | escape }}">
          <img src="{{ '/images/' | append: paper.image | relative_url }}"
               alt="{{ paper.title | escape }}"
               loading="lazy">
        </button>
      </div>
    </div>

    <div class="paper-box-text">
      <h3>
        <a href="{{ paper.url | escape }}"
           target="_blank" rel="noopener noreferrer">{{ paper.title }}</a>
      </h3>

      <p>
        <strong>Yibo Zhou</strong>
        <span class="p-role">
          {% if paper.sole %}
            Sole author
          {% elsif paper.role == "corresponding" %}
            Corresponding author
          {% elsif paper.role == "first" %}
            First author
          {% else %}
            Author
          {% endif %}
        </span>
      </p>

      <p class="p-muted">
        {{ paper.venue }} · {{ paper.status }}
        {% if paper.honor %}
        <span class="p-honor">{{ paper.honor }}</span>
        {% endif %}
      </p>

      <p class="p-takeaway">{{ paper.takeaway }}</p>

      <p class="p-links">
        <a href="{{ paper.url | escape }}"
           target="_blank" rel="noopener noreferrer">Paper ↗</a>
        {% if paper.code %}
        <a href="{{ paper.code | escape }}"
           target="_blank" rel="noopener noreferrer">Code ↗</a>
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
    <a href="https://patents.google.com/patent/CN117115851A/en"
       target="_blank" rel="noopener noreferrer"><strong>CN 117115851 A</strong></a>
    — A Pedestrian Attribute Recognition Method for Complex Surveillance Scenarios.
  </p>
</section>

<section id="education">
  <h1>Education</h1>

  <div class="p-education">
    <div>
      <strong>
        <a class="p-academic-link" href="https://www.buaa.edu.cn/"
           target="_blank" rel="noopener noreferrer">Beihang University</a>
      </strong>
      <p>Ph.D. in Artificial Intelligence</p>
      <p class="p-muted">September 2022 – June 2026</p>
    </div>

    <div>
      <strong>
        <a class="p-academic-link" href="https://www.ucsd.edu/"
           target="_blank" rel="noopener noreferrer">University of California San Diego</a>
      </strong>
      <p>M.S. in Electrical Engineering</p>
      <p class="p-muted">August 2017 – May 2019</p>
    </div>

    <div>
      <strong>
        <a class="p-academic-link" href="https://www.lzu.edu.cn/"
           target="_blank" rel="noopener noreferrer">Lanzhou University</a>
      </strong>
      <p>B.S. in Materials Physics</p>
      <p class="p-muted">August 2013 – June 2017</p>
    </div>
  </div>
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

<section id="publication-list">
  <h1>publication list</h1>

  <p class="p-muted">
    Automatically synchronized from my arXiv author profile.
    Journal-only publications may not appear in this list.
    <a href="https://arxiv.org/a/0000-0001-7964-7517"
       target="_blank" rel="noopener noreferrer">View on arXiv ↗</a>
  </p>

  <div id="arxivfeed">
    Loading publications from arXiv…
  </div>
</section>

</div>

<script>
  var arxiv_authorid = "0000-0001-7964-7517";
  var arxiv_format = "arxiv";
  var arxiv_max_entries = 0;
  var arxiv_includeTitle = 0;
  var arxiv_includeSummary = 0;
  var arxiv_includeComments = 0;
  var arxiv_includeSubjects = 0;
  var arxiv_includeJournalRef = 1;
  var arxiv_includeDOI = 1;
</script>
<script src="https://arxiv.org/js/myarticles.js"></script>

{% include portfolio-tools.html %}
{% include portfolio-polish.html %}
