# Testing Guide

This file defines the required local testing workflow for Dharma Siblings.

## 1) Prerequisites

- Ruby and Bundler installed.
- Project dependencies installed with:
  - `bundle install`
- Optional lint/link tools:
  - `npm install -g markdownlint-cli`
  - `pip install yamllint`
  - `cargo install lychee` (or your preferred install method)

## 2) Start Local Site

1. Run:
   - `bundle exec jekyll serve --livereload --trace`
2. Wait for:
   - `Server address: http://127.0.0.1:4000`
3. Keep this terminal running while testing pages.

## 3) Required Manual Rendering Checks

Open these routes in a browser and confirm each page renders without obvious layout/content issues:

- `/`
- `/pages/liturgy`
- `/pages/video-and-film`
- `/pages/artwork`
- `/pages/literature`
- `/pages/recipes`

For each changed page, verify:

- Page title and section headings are visible and correct.
- Left navigation includes expected items and excludes repo-only docs.
- Images, embeds, and downloads load correctly.
- Internal links navigate to the expected page/section.
- External links open the expected destination.

## 4) Viewport Checks

For changed pages, test both:

- Desktop width (about 1280px+)
- Mobile width (about 390px)

Confirm at both sizes:

- Navigation is usable.
- Text is readable and not cut off.
- Media does not overflow containers.

## 5) Required Local Validation Commands

Run these before opening/updating a PR:

1. `bundle exec jekyll build`
2. `markdownlint "**/*.md"`
3. `yamllint .`
4. `jq . renovate.json > /dev/null`
5. `yardstick -path . -format table`

Run when link updates are part of the change:

1. `lychee --verbose --exclude-mail --timeout 20 "**/*.md"`

## 6) Failure Handling

If a check fails:

- Fix source files (never edit `_site/` directly).
- Re-run the failed command.
- Re-run `bundle exec jekyll build` after fixes.
- Re-check affected pages in the browser.

## 7) Merge Readiness Checklist

Before merge, confirm all are true:

- Manual rendering checks completed for affected pages.
- Desktop and mobile checks completed.
- Required validation commands passed.
- `CHANGELOG.md` updated with user-facing and CI/policy changes.
