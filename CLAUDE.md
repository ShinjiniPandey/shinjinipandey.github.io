# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

This is Shinjini Pandey's academic personal website, built with Jekyll using the [Academic Pages](https://academicpages.github.io/) theme (a fork of Minimal Mistakes). It is deployed via GitHub Pages at `https://shinjinipandey.github.io`.

## Local development

Prerequisites: Ruby with `ruby-dev`, `bundler`, and `nodejs`.

```bash
bundle install                          # install dependencies (delete Gemfile.lock if errors)
bundle exec jekyll liveserve            # serve at localhost:4000 with live reload
bundle exec jekyll serve --config _config.yml,_config.dev.yml  # use dev config overrides
```

The `_config.dev.yml` overrides `url` to `localhost:4000` and disables analytics/comments for local development.

## Site structure and content editing

**Where content lives:**
- `_pages/about.md` — homepage (permalink: `/`)
- `_pages/publication_final.md` — research/publications page (permalink: `/publication_final/`)
- `_pages/cv.md` — CV page linking to `/files/CV/Shinjini_CV.pdf`
- `_pages/Teaching.md` — teaching page
- `_pages/Fieldwork.md` — fieldwork photos page
- `_config.yml` — site-wide settings: author bio, social links, analytics tracking ID

**Key configuration in `_config.yml`:**
- Author profile (bio, avatar, social links) is under the `author:` key
- The `collections:` section defines `publication_final`, `portfolio`, `teaching`, and `talks`
- The `defaults:` section sets layouts and `author_profile: true` for each collection/page type

**Publications page (`_pages/publication_final.md`)** uses raw HTML with inline styles rather than a Jekyll collection — papers are listed directly in the Markdown file with `<details>`/`<summary>` toggles for abstracts.

**Static files** (PDFs, etc.) go in the `files/` directory and are served at `/files/filename`.

**Images** go in the `images/` directory.

## Theme and layout

Layouts are in `_layouts/`, includes in `_includes/`. The theme uses SCSS compiled from `assets/css/main.scss` (imports from `_sass/`). Font Awesome and Academicons icon fonts are in `assets/fonts/`.

The site uses `kramdown` as the Markdown processor with GFM input mode. HTML is valid inside `.md` files.

## Deployment

Pushing to the `master` branch on GitHub automatically triggers GitHub Pages deployment. The `_site/` directory is the local build output — it is not committed.
