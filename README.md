# jakobwes.github.io

Personal academic website, built with [al-folio](https://github.com/alshedivat/al-folio) (v1.x) and hosted on GitHub Pages. The template's own documentation is in `docs/`.

## Where things live

| What                                              | File                                                               |
| ------------------------------------------------- | ------------------------------------------------------------------ |
| Name, site URL, footer                            | `_config.yml` (top section)                                        |
| Bio, subtitle, address under the photo            | `_pages/about.md`                                                  |
| Photo                                             | `assets/img/prof_pic.jpg` (square, under ~200 KB)                  |
| Contact icons (email, Scholar, ORCID, GitHub, CV) | `_data/socials.yml`                                                |
| News items                                        | `_news/` (one file per item)                                       |
| Publications                                      | `_bibliography/papers.bib`                                         |
| Software                                          | `_pages/software.md`                                               |
| CV                                                | `assets/pdf/CV_Jakob_Wessel.pdf` (replace the file, keep the name) |
| Impressum / Datenschutz                           | `_pages/impressum.md`                                              |

Pages in the navbar are the files in `_pages/` with `nav: true`, ordered by `nav_order`.

## Common edits

**Add a news item.** Create `_news/YYYY-MM-short-name.md`:

```markdown
---
layout: post
date: 2026-11-15
inline: true
related_posts: false
---

New paper in [Journal](https://doi.org/...): one or two sentences.
```

The home page shows the five most recent items; all of them are listed at `/news/`.

**Add a publication.** Paste its BibTeX entry into `_bibliography/papers.bib` and add `doi`, `arxiv` (ID only) and, if relevant, `code` fields. These become buttons under the entry. Mark joint first authorship with `*` after the surname.

**Update the CV.** Overwrite `assets/pdf/CV_Jakob_Wessel.pdf`.

Every push to `main` rebuilds and redeploys the site through GitHub Actions (about 3–5 minutes).

## First-time setup

1. Create a public GitHub repository named `USERNAME.github.io` and push this folder to its `main` branch.
2. In `_config.yml`, set `url: https://USERNAME.github.io` (leave `baseurl` empty).
3. Fill in the TODOs in `_data/socials.yml` and the Scholar link in `_pages/publications.md`.
4. In the repository on GitHub: Settings → Actions → General → Workflow permissions → "Read and write permissions".
5. After the first successful run of the "Deploy site" action: Settings → Pages → Source "Deploy from a branch", branch `gh-pages`, folder `/ (root)`.
6. Optional: own domain. Add it under Settings → Pages → Custom domain, set the DNS records your registrar asks for, and change `url` in `_config.yml`.

## Previewing locally (optional)

**With Docker (easiest).** Install [Docker Desktop](https://www.docker.com/products/docker-desktop/), start it, then in this folder run:

```bash
docker compose up
```

The first run downloads a prebuilt image and takes a few minutes. When the log says the server is running, open http://localhost:8080. Edits to pages, news and the .bib file show up after a reload; changes to `_config.yml` restart the server automatically. Stop with Ctrl+C, then `docker compose down`.

**Without Docker.** Install Ruby 3.3 and ImageMagick, then run `bundle install` once and `bundle exec jekyll serve`, and open http://localhost:4000.

**Without anything local.** Push to GitHub; if the build fails, the "Deploy site" run under the Actions tab shows the error.
