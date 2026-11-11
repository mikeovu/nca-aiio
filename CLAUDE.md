# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

A static study site for the NVIDIA NCA-AIIO (AI Infrastructure and Operations) exam. It uses plain HTML/CSS with no build step, linter or tests. Preview it locally:

```bash
python3 -m http.server 8080
```

Every push to `main` deploys to GitHub Pages through `.github/workflows/pages.yml`, and you can also run that workflow by hand. Pages must have **Settings → Pages → Source** set to **GitHub Actions**.

## Structure

- `index.html` is the landing page, with one card per exam topic. The other three pages map to the blueprint topics: `essential-ai-knowledge.html` (1), `ai-infrastructure.html` (2) and `ai-operations.html` (3).
- Every topic page has the same sections in this order: a hero (topic number and exam weight), exam objectives (`ol.objectives` with `obj-num` like `3.1`), recommended training, course unit summaries, and study resources. The last three are `ul.links` lists.
- `assets/style.css` is the only stylesheet. Colors are CSS custom properties on `:root`, overridden in `@media (prefers-color-scheme: dark)`. The logo switches between `nvidia-logo.svg` and `nvidia-logo-white.svg` through a `<picture>` source.
- `reading/` holds the 14 course unit summary PDFs. Some units are linked from more than one topic page.
- `study-notes.html` lists all 14 course units. Each unit has a page at `notes/unit-NN-<slug>.html` with that unit's summary PDF, the topic chips, an optional **Notes** section (a `.toc` plus an `article.prose` holding notes converted from Markdown), and prev/next links. A unit built from several course transcripts (Units 3, 7, 8, 12) gets one `article.prose.lesson` per transcript: headings are demoted one level, and IDs are prefixed `lesson-<slug>-`. The `.toc-lessons` contents list groups sections by lesson. Pages in `notes/` use `../` for every asset and link. Unit pages without notes show a `p.empty` placeholder. When you add notes to one, also add the `Notes` tag to its row in `study-notes.html` and update the "Notes are done for N of 14 units" count in the lede.
- The source Markdown for the notes is in `nvidia_course_content/notes/`, and the raw transcripts are in `nvidia_course_content/transcripts/`.
- In each note, Key Terms link to official NVIDIA pages (nvidia.com, docs/developer/blogs.nvidia.com, build.nvidia.com), and the note ends with an "NVIDIA Documentation" section. Link the final URL after any redirect, and leave a term unlinked when no matching NVIDIA page exists. Don't point a term at a loosely related page. External links in the notes get `target="_blank" rel="noopener"`, like the rest of the site.

## Things to keep in sync by hand

- **Header, nav and footer are copied into every page**, including the 15 study-notes pages. Edit every file when they change. The nav has 4 links: the 3 topics plus Study Notes. On each topic page the matching nav link has `aria-current="page"`. The study-notes pages mark Study Notes instead. The inline script at the end of `<body>` scrolls that link into view on narrow screens.
- **Counts are hardcoded in several places.** When you add or remove a link, update all of these:
  - the `<span class="count">` in the topic page's section heading
  - the `card-meta` line on that topic's card in `index.html` (objectives, readings and unit PDFs)
  - the totals in the `index.html` hero lede ("14 unit PDFs and 23 readings")
- **Weight bars**: in `index.html`, the `weight-bar` width is scaled so the largest topic (40%) is 100%. It is not the raw exam percentage.
- **"Links checked" dates** appear in the `index.html` lede, every footer and `README.md`. Only add links that you have confirmed are live.

## Link conventions

- External links use `target="_blank" rel="noopener"` and `<span class="title">…</span><span class="meta">domain</span>`. Study resources are sorted alphabetically by title.
- PDF links URL-encode the filename (`reading/Unit%2005%20-%20...pdf`, and some actual filenames have typos or trailing spaces, like `Summary .pdf`). They set a clean `download="NCA-AIIO Unit NN - Title - Summary.pdf"` name, and the meta shows the file size plus `<span class="tag">PDF</span>`.

## Deployment caveat

The workflow uploads the whole repo root (`path: .`), so every committed file gets published. The user has committed `nvidia_course_content/` (the notes and transcripts), so it's published along with the site.
