# Changelog

All notable changes to this project will be documented here.

This project follows a spirit of mindful versioning: changes are recorded to help us reflect on the evolution of our shared space. ❤️

---

## [Unreleased]

---

## [v1.2.0] – 2026-06-17

Added

- `yardstick` GitHub Actions workflow (`.github/workflows/yardstick.yml`) with pinned tool version and PR/push checks.
- `CODEOWNERS` with default repository ownership rule.
- `SECURITY.md` with vulnerability reporting guidance.
- Yardstick badge in `README.md` project status section.
- `TESTING.md` with explicit local rendering checks, required validation commands, and merge-readiness checklist.
- `.lychee.toml` with explicit exclusions for domains that block automated crawlers or timeout from GitHub Actions runners, and for YouTube Privacy Enhanced Mode embed URLs.

Changed

- `check-links.yml`: upgraded `actions/checkout` v3 → v4, `lycheeverse/lychee-action` v1.8.0 → v2; dropped `--exclude-mail` flag (removed in lychee v0.23, mail links now excluded by default); added explicit `--config .lychee.toml`.
- `lint-markdown.yml`: upgraded `actions/checkout` v3 → v4, `actions/setup-node` v3 → v4.
- `yardstick.yml`: upgraded `actions/checkout` v5 → v6, `yardstick` tool v0.2.0 → v0.4.0.
- `AGENTS.md` expanded with explicit lint/test expectations, local rendering checks, and local Yardstick command guidance; corrected hardcoded absolute local path to `TESTING.md`; updated lychee command example.
- `pages/video-and-film.md` broken media links replaced with working video embeds and verified official channel/center links.
- `pages/liturgy.md` broken and outdated resource links refreshed across liturgy, sutra, and study sections.
- `pages/recipes.md` embedded video URL parameters updated to a working variant.
- `TODO.txt` link-repair notes reorganized for ongoing broken-link triage.
- `_config.yml` updated to exclude repository docs from generated site output and nav/search indexing.
- `_sass/custom/custom.scss` updated to restore visible logo rendering and increase header logo display size.
- `README.md` updated to include sections expected by repository policy checks; links updated to repository-relative markdown targets.
- GitHub workflow YAML files normalized for lint compliance.
- YAML lint workflow trigger adjusted to avoid duplicate runs on PRs.

Removed

- Tracked `_site/` generated artifacts removed from version control (files remain generated locally by Jekyll build).

---

## [v1.1.0] – 2025-08-24

Added

- Local Jekyll build support with `Gemfile` for development preview (`bundle exec jekyll serve`)
- Quick Links section expanded on homepage (`index.md`) to include all main pages

Changed

- Content files moved into new `/pages/` directory for cleaner repo structure:
  - `liturgy.md`
  - `recipes.md`
  - `video-and-film.md`
  - `artwork.md`
  - `literature.md`
- `_config.yml` navigation updated to reflect new `/pages/` paths
- Internal links in `index.md` and `README.md` updated to point to `/pages/...`
- `README.md` refreshed with clearer project title, structure, and direct links to site sections
- `index.md` (Group Compass) updated for consistency, clarity, and corrected Quick Links

---

## [v1.0.0] – 2025-05-02

Added

- Initial static site using GitHub Pages and Just the Docs theme
- Group Compass added as homepage
- Sidebar navigation enabled for:
  - Compass
  - Video and Film
  - Artwork
  - Literature
- Project status badges added to README:
  - Link check
  - Markdown lint
  - YAML lint
- `CONTRIBUTING.md` added with technical and non-technical contribution guidance
- `CHANGELOG.md` initialized to track site evolution
- `TODO.txt` added for roadmap planning
- `.editorconfig` added to ensure consistent formatting
- Custom logo and favicon added and configured in theme
- Submission guidelines added to content pages (e.g., how to suggest artwork, literature, or film)
- Community recommendation sections expanded with categorized entries
- License: [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/)
- Experimental video embed with YouTube fallback support using linked thumbnails

Changed

- `books.md` renamed to `literature.md`; config and links updated accordingly
- Markdown structure cleaned to satisfy `markdownlint` rules
- Heading levels and visual scale adjusted using theme's Sass overrides
- README restructured to include purpose, license, project badges, logo, and contribution instructions

Removed

- Spell check CI job (determined unnecessary given group needs and maintainability)

Infrastructure

- CI/CD pipeline configured with:
  - Markdown lint (`markdownlint`)
  - YAML lint (`yamllint`)
  - Link checking (`lychee`)
- Future deploy gating explored; staging branch under consideration

---

## [0.1.0] – 2025-04-XX

- Project seed created
- Group Compass authored and revised
- GitHub repo initialized and published
