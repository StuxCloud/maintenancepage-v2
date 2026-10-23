# Contributing to maintenancepage-v2

Thank you for your interest in contributing! This repository is an archived, pinned snapshot of the green-era maintenancepage design, so its scope is intentionally narrow.

## Scope

This is **not** the actively developed template. That's [StuxCloud/maintenancepage](https://github.com/StuxCloud/maintenancepage). This repo preserves the pre-teal `v2` look as-is. Contributions here should keep the existing design working, not change it:

- Fixing broken links, encoding issues, or browser-compatibility bugs
- Keeping the page renderable as browsers and standards evolve

New features, redesigns, or styling changes belong in the live `maintenancepage` repository instead.

## Icons and link previews

The icon tags and the Discord link preview in each page's `<head>` (between the `BEGIN head tags` / `END head tags` comments) are generated: edit `scripts/build-head-tags.py` (add new pages to its `PAGES` list too; `build-sitemap.py` runs it for you) and run `python scripts/build-head-tags.py`. The icons themselves are `favicon.ico`, `apple-touch-icon.png`, `site.webmanifest` and `assets/icon-*.png`, made from the Stux.Cloud icon.

## Tests

Run `bash tests/run.sh` before every release. It needs Python 3 (and PHP 7.4 for the dev-server checks, which are skipped without it). It checks the version (`tests/version.sh`), that every page's Discord preview is valid, under 3,000 bytes and up to date (and that the 404 page has none), and that the icon set is complete and every page's `<head>` lists it.

## Versioning

This project uses [Date Versioning](https://datevers.ing). To release:

1. Add a `## vYY.MM.DD` entry at the top of `CHANGELOG.md`, with its sections in this order: Added, Changed, Fixed, Removed, Security, Deprecated.
2. Set `VERSION.md` to the same bare version (no `v`): today's **UTC** date as `YY.MM.DD`, or `YY.MM.DD-1`, `-2`… for later releases the same UTC day. Never a future date. Use UTC, not local time: just after midnight in the UK it is still the previous day in UTC.
3. Run `bash tests/run.sh` (it includes `tests/version.sh`).
4. Run `./commit.sh` (or `commit.bat` on Windows). It checks the version, commits and tags `vYY.MM.DD`, and never pushes.
