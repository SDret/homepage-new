---
layout: default
permalink: /
title: ""
excerpt: "Yibo Zhou — Learning Beyond Spurious Correlations"
author_profile: true
portfolio_pdf: ""
---

<div id="portfolio">

<section id="about-me">
  <h1>About Me</h1>

  <p>I am <strong>Yibo Zhou (周亦博)</strong>. I received my Ph.D. in Artificial Intelligence from <strong>Beihang University</strong> in June 2026.</p>

  <p>My research asks when learning systems can distinguish task-relevant structure from misleading statistical regularities. I connect <strong>identifiability and computational limits</strong>, <strong>shortcut-resistant evaluation</strong>, and <strong>balanced representation learning</strong>.</p>

  <p>Across these directions, I study <strong>what data can identify</strong>, <strong>what algorithms can recover</strong>, and <strong>what evaluations can verify</strong>, with applications to out-of-distribution detection and pedestrian attribute recognition.</p>

  <p class="p-links">
    <a href="mailto:ybzhou@buaa.edu.cn">Email</a>
    <a href="https://scholar.google.com/citations?user=Ch18_eIAAAAJ" target="_blank" rel="noopener">Google Scholar</a>
    <a href="https://orcid.org/0000-0001-7964-7517" target="_blank" rel="noopener">ORCID</a>
    {% if page.portfolio_pdf and page.portfolio_pdf != "" %}
    <a href="{{ page.portfolio_pdf | relative_url }}" target="_blank" rel="noopener">Research Portfolio PDF</a>
    {% endif %}
  </p>

  <p class="p-news"><strong>2026:</strong> Three papers accepted to NeurIPS 2026, covering label-only auditing, source calibration, and counterfactual pairing.</p>
</section>

<section id="research">
  <h1>Research at a Glance</h1>

  <div class="p-stats">
    <div><strong>{{ site.data.papers | size }}</strong><span>Published / accepted papers</span></div>
    <div><strong>{{ site.data.papers | where: "role", "first" | size }}</strong><span>First-author papers</span></div>
    <div><strong>{{ site.data.papers | where: "role", "corresponding" | size }}</strong><span>Corresponding-author papers</span></div>
    <div><strong>{{ site.data.papers | where: "sole", true | size }}</strong><span>Sole-author paper</span></div>
    <div><strong id="p-total">—</strong><span>Scholar total citations</span></div>
    <div><strong id="p-first-cites">—</strong><span>Citations to first-author papers</span></div>
    <div><strong id="p-hindex">—</strong><span>Scholar h-index</span></div>
    <div><strong id="p-i10">—</strong><span>Scholar i10-index</span></div>
  </div>

  <p id="p-citation-note" class="p-muted" aria-live="polite">Citation data will load from the latest successful update.</p>

  <p class="p-muted">The sole-author paper is included in the first-author count. None of the seven first-author papers has shared first authorship. CCF categories follow the classification in effect at acceptance; IJCAI 2023 is counted as CCF A on that basis.</p>

  <div class="p-areas">
    <div><h3>Ⅰ. Identifiability &amp; Computation</h3><p>What makes reliable learning identifiable and computationally tractable?</p></div>
    <div><h3>Ⅱ. Shortcut-resistant Evaluation</h3><p>Does an evaluation test the intended signal, or can the components fool the test?</p></div>
    <div><h3>Ⅲ. Balanced Representations</h3><p>How should representations and training distributions be corrected under co-occurrence and imbalance?</p></div>
  </div>
</section>

<section id="publications">
  <h1>Selected Publications</h1>
  <p class="p-muted">Author roles are shown below. Complete author lists are available on the linked paper pages. Click a figure to enlarge it.</p>

  <div id="p-filters" class="p-filters" hidden>
    <input id="p-search" type="search" placeholder="Search papers..." aria-label="Search papers">
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
    <span id="p-count" class="p-muted"></span>
  </div>

  {% for paper in site.data.papers %}
  <article class="paper-box p-card"
    data-title="{{ paper.title | escape }}"
    data-scholar-title="{{ paper.scholar_title | default: paper.title | escape }}"
    data-year="{{ paper.year }}"
    data-topic="{{ paper.topic }}"
    data-role="{{ paper.role }}">

    <div class="paper-box-image"><div>
      <div class="badge">{{ paper.venue }}</div>
      <button type="button" class="p-zoom" aria-label="Enlarge figure: {{ paper.title | escape }}">
        <img src="{{ '/images/' | append: paper.image | relative_url }}" alt="{{ paper.title | escape }}" loading="lazy">
      </button>
    </div></div>

    <div class="paper-box-text">
      <h3><a href="{{ paper.url | escape }}" target="_blank" rel="noopener">{{ paper.title }}</a></h3>

      <p><strong>Yibo Zhou</strong> ·
        {% if paper.sole %}Sole author
        {% elsif paper.role == "corresponding" %}Corresponding author
        {% else %}First author{% endif %}
      </p>

      <p class="p-muted">{{ paper.venue }} · {{ paper.status }}
        {% if paper.honor %}<span class="p-honor">{{ paper.honor }}</span>{% endif %}
      </p>

      <p>{{ paper.takeaway }}</p>

      <p class="p-links">
        <a href="{{ paper.url | escape }}" target="_blank" rel="noopener">Paper</a>
        {% if paper.code %}<a href="{{ paper.code | escape }}" target="_blank" rel="noopener">Code</a>{% endif %}
        <span class="p-cite">Citations: —</span>
      </p>

      <details>
        <summary>Research summary</summary>
        <p>{{ paper.summary }}</p>
      </details>
    </div>
  </article>
  {% endfor %}
</section>

<section id="demo">
  <h1>Interactive Research Demo</h1>
  <h3>Can component shortcuts change a pairing cycle?</h3>
  <p>This toy example adds relational signal <strong>r</strong> to the valid diagonal pairs. Image biases are <strong>a, −a</strong>, and caption biases are <strong>b, −b</strong>. Move the sliders: component biases change individual scores, but cancel in the cycle contrast.</p>

  <div class="p-demo">
    <label>Image bias a <input id="p-a" type="range" min="-5" max="5" step="0.5" value="2"></label>
    <label>Caption bias b <input id="p-b" type="range" min="-5" max="5" step="0.5" value="3"></label>
    <label>Relational signal r <input id="p-r" type="range" min="0" max="3" step="0.5" value="1"></label>

    <table>
      <thead><tr><th></th><th>Caption C₁</th><th>Caption C₂</th></tr></thead>
      <tbody>
        <tr><th>Image I₁</th><td class="p-valid">+ <span id="p-s11"></span></td><td>− <span id="p-s12"></span></td></tr>
        <tr><th>Image I₂</th><td>− <span id="p-s21"></span></td><td class="p-valid">+ <span id="p-s22"></span></td></tr>
      </tbody>
    </table>

    <p><strong>Δ = s₁₁ + s₂₂ − s₁₂ − s₂₁ = 2r = <span id="p-delta"></span></strong></p>
    <p class="p-muted">Scores: s₁₁=r+a+b; s₁₂=a−b; s₂₁=−a+b; s₂₂=r−a−b. The signs outside each table entry indicate its coefficient in the contrast. This is an algebraic illustration, not an experimental result.</p>
  </div>
</section>

<section id="patent">
  <h1>Patent Application</h1>
  <p><a href="https://patents.google.com/patent/CN117115851A/en" target="_blank" rel="noopener"><strong>CN 117115851 A</strong></a> — A Pedestrian Attribute Recognition Method for Complex Surveillance Scenarios.</p>
</section>

<section id="education">
  <h1>Education</h1>
  <ul>
    <li><strong>Beihang University</strong> — Ph.D. in Artificial Intelligence, September 2022 – June 2026.</li>
    <li><strong>University of California San Diego</strong> — M.S. in Electrical Engineering, August 2017 – May 2019.</li>
    <li><strong>Lanzhou University</strong> — B.S. in Materials Physics, August 2013 – June 2017.</li>
  </ul>
</section>

<section id="experience">
  <h1>Professional Experience</h1>
  <p><strong>OPPO Guangdong Mobile Telecommunications Corp., Ltd.</strong><br>
  Artificial Intelligence Algorithm Engineer<br>
  101 Laboratory · Imaging Algorithm Development Department<br>
  July 2019 – March 2021 · Shenzhen, China</p>
</section>

</div>

{% include portfolio-tools.html %}
