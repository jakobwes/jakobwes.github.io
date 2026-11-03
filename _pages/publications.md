---
layout: page
permalink: /publications/
title: publications
# Plain text only: this also goes into the page's meta tags (search results, link previews), where HTML breaks the page.
description: Publications by Jakob Wessel.
nav: true
nav_order: 1
_styles: >
  .post-header .post-description { display: none; }
  .post-description { font-size: 1rem; margin-top: 1rem; }
  .post-description a { color: var(--global-theme-color); }
  .publications .author sup { font-weight: bold; }
  .publications .title a { color: inherit; }
---

<!-- To add a paper: add its BibTeX entry to _bibliography/papers.bib. Nothing else needs changing. -->

<p class="post-description">See also my <a href="https://scholar.google.com/citations?user=L_xWSBoAAAAJ">Google Scholar</a> profile. <b>*</b> denotes joint first authorship.</p>

<div class="publications">

{% bibliography %}

</div>

<script>
  document.addEventListener("DOMContentLoaded", () => {
    document.querySelectorAll(".publications .title").forEach((title) => {
      const entry = title.parentElement;
      const link =
        entry.querySelector('.links a[href^="https://doi.org/"]') ||
        entry.querySelector('.links a[href*="arxiv.org/abs/"]');
      if (!link || title.querySelector("a")) return;
      const a = document.createElement("a");
      a.href = link.href;
      a.textContent = title.textContent;
      title.replaceChildren(a);
    });
  });
</script>