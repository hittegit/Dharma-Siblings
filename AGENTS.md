# Repository Guidelines

This guide outlines how to work inside the Dharma Siblings Jekyll site so contributor agents can deliver precise, reviewable changes.

## Project Structure & Module Organization
`index.md` is the landing page; curated content lives in `pages/*.md` using kebab-case names such as `pages/video-and-film.md`. Static media belongs in `assets/` (`assets/images` for artwork and logos). Styles sit in `_sass/`, while `_config.yml` defines navigation and metadata. `_site/` is build output—inspect it for verification only. When adding content, copy an existing front-matter block so navigation stays consistent.

## Build, Test, and Development Commands
- `bundle install` — install the GitHub Pages gem set pinned in `Gemfile.lock`.
- `bundle exec jekyll serve --livereload` — run the site locally at `http://127.0.0.1:4000`.
- `bundle exec jekyll build` — verify the production build and refresh `_site/`.
- `markdownlint "**/*.md"` — same Markdown gate used in CI (install via `npm install -g markdownlint-cli`).
- `yamllint .` and `lychee --verbose --exclude-mail --timeout 20 "**/*.md"` — replicate YAML linting and link checking before pushing.

## Coding Style & Naming Conventions
`.editorconfig` enforces UTF-8, LF line endings, and two-space indents for Markdown, YAML, JSON, and shell snippets—avoid tabs. Markdown files may retain deliberate double-space breaks, so keep `trim_trailing_whitespace` off when editing prose. Keep front-matter keys lowercase with hyphenated words (`layout`, `title`, `nav_order`), and name new content files `topic-or-medium.md` to preserve clean URLs. Never use 'em' dashes.

## Commiting and Pushing Code
Never commit or push anything without explicit permission from the user.

## Testing Guidelines
Visually confirm edits with `bundle exec jekyll serve`, then run `markdownlint`, `yamllint`, and the Lychee command before opening a PR. Use descriptive section headings (`## Practice Resources — Chanting`) so anchor links remain stable. When referencing downloads or images, ensure the file exists under `assets/` and the relative path works locally.

## Security & Configuration Tips
Do not store secrets or unpublished member data—everything under version control is public. When editing `_config.yml`, keep navigation URLs relative (no trailing `.html` unless required) to appease the link checker. For external embeds, either reuse allowed tags from `.markdownlint.json` or fall back to screenshots to avoid custom exceptions.
