# Repository Guidelines

This guide outlines how to work inside the Dharma Siblings Jekyll site so contributor agents can deliver precise, reviewable changes.

## Project Structure & Module Organization

`index.md` is the landing page; curated content lives in `pages/*.md` using kebab-case names such as `pages/video-and-film.md`. Static media belongs in `assets/` (`assets/images` for artwork and logos). Styles sit in `_sass/`, while `_config.yml` defines navigation and metadata. `_site/` is build output—inspect it for verification only. When adding content, copy an existing front-matter block so navigation stays consistent.

## Build, Test, and Development Commands

- `bundle install` - install the GitHub Pages gem set pinned in `Gemfile.lock`.
- `bundle exec jekyll serve --livereload` - run the site locally at `http://127.0.0.1:4000`.
- `bundle exec jekyll build` - verify the production build and refresh `_site/`.
- `markdownlint "**/*.md"` - same Markdown gate used in CI (install via `npm install -g markdownlint-cli`).
- `yamllint .` - run YAML linting across workflow files and site config.
- `jq . renovate.json > /dev/null` - validate JSON-based configuration files before committing.
- `yardstick -path . -format table` - run repository policy checks locally when validating CI/config hygiene.
- `lychee --verbose --exclude-mail --timeout 20 "**/*.md"` - optional local link checking; run when link changes are in scope.

## Coding Style & Naming Conventions

`.editorconfig` enforces UTF-8, LF line endings, and two-space indents for Markdown, YAML, JSON, and shell snippets, avoid tabs. Markdown files may retain deliberate double-space breaks, so keep `trim_trailing_whitespace` off when editing prose. Keep front-matter keys lowercase with hyphenated words (`layout`, `title`, `nav_order`), and name new content files `topic-or-medium.md` to preserve clean URLs. Never use 'em' dashes.

## Committing and Pushing Code

Never commit or push anything without explicit permission from the user.
Before merge, update `CHANGELOG.md` to reflect all user-facing, CI, or policy changes included in the PR.

## Testing Guidelines

Follow [`TESTING.md`](/home/ejh/Repos/Dharma-Siblings/TESTING.md) as the required source of truth for local verification before opening or merging a PR.

- Treat manual local rendering checks as mandatory for content, navigation, and styling changes.
- Treat lint/build checks in `TESTING.md` as required PR gates.
- Run Lychee when link checks are in scope.
- Use descriptive section headings (`## Practice Resources - Chanting`) so anchor links remain stable.
- When referencing downloads or images, ensure the file exists under `assets/` and the relative path works locally.

## Linting Scope for Config Files

- Treat `_config.yml`, `.github/workflows/*.yml`, and any new `*.yml`/`*.yaml` files as required `yamllint` targets.
- Treat `renovate.json` and any future `*.json` config as required JSON syntax checks with `jq`.
- Treat Markdown front matter errors as build blockers, verify with `bundle exec jekyll build --trace` when linting passes but pages still fail.
- Do not edit `_site/` directly; regenerate it from source files and validate source lint results instead.

## Security & Configuration Tips

Do not store secrets or unpublished member data, everything under version control is public. When editing `_config.yml`, keep navigation URLs relative (no trailing `.html` unless required) to appease the link checker. For external embeds, either reuse allowed tags from `.markdownlint.json` or fall back to screenshots to avoid custom exceptions.
