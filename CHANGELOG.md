# Changelog

All notable changes to maintenancepage-v2 are documented here.

Since v26.10.23 this project uses [Date Versioning](https://datevers.ing) (`YY.MM.DD`, the UTC release date, with `-1`, `-2`… for later releases the same day); earlier releases used Semantic Versioning.

## v26.10.26

### Security

- CI uses Node.js 24 instead of the end-of-life Node.js 20, which has no fix for the Brotli decoder vulnerability CVE-2026-111497

## v26.10.23-1

### Added

- A full icon set: `favicon.ico` (16, 32 and 48px) and `apple-touch-icon.png` at the site root, and a `site.webmanifest` with 192px, 512px and maskable icons, all made from the Stux.Cloud icon, so the page has a proper icon in browser tabs, bookmarks and on phone home screens (the home-screen icons sit on a white background, as iOS would otherwise fill the icon's transparent corners with black). Every page, the 404 page included, lists the same icons in its `<head>`
- Discord link previews: sharing any page in Discord shows a custom preview in the Stux.Cloud brand colour, with the page's name, what it is and a few links (the maintenance page links to Stux.Cloud's own sites; the other pages link back home). Names and descriptions show as plain text, and the 404 page has none. They're pre-built into each page's `<head>` by `python scripts/build-head-tags.py`
- `bash tests/run.sh`, which runs the version check and then checks the Discord previews (valid JSON, under Discord's 3,000 bytes, none on the 404 page), the icon set and every page's `<head>` tags

### Changed

- The tab icon is the new `favicon.ico` on every page, in place of the icons loaded from the brand's media host
- `scripts/build-sitemap.py` now runs `scripts/build-head-tags.py` after regenerating the sitemap page
- The local dev server serves `site.webmanifest` as `application/manifest+json`, the way GitHub Pages does

## v26.10.23

### Added

- `tests/version.sh`, which checks that `VERSION.md` is a valid Date Version, a real calendar date not in the future, and the same as the newest entry in this changelog

### Changed

- Switched from Semantic Versioning to [Date Versioning](https://datevers.ing): releases are numbered by their UTC release date as `YY.MM.DD`, with `-1`, `-2`… for later releases the same day. This release follows v2.0.4
- `commit.sh` and `commit.bat` refuse a `VERSION.md` that isn't a valid Date Version or is dated in the future (UTC), and warn when it's dated before today
- `README.md` and `CONTRIBUTING.md` describe Date Versioning and the release steps

## v2.0.4

### Fixed

- The footer's copyright line had a second, hidden copy of the © icon inside its screen-reader text; it's gone, leaving the visible icon and a plain "©" for screen readers. Nothing changes on screen

## v2.0.3

### Changed

- The footer no longer says "Stux.Cloud is operated by Stux Group Ltd."; that belongs on the Imprint, which still says it. The copyright line names Stux.Cloud instead of Stux.Group ("© 2026 Stux.Cloud. All rights reserved.")

## v2.0.2

### Fixed

- The light/dark choice was saved in the browser under `stuxedo-theme`, a name left over from the Stuxedo page this design was built from; it's now `stuxcloud-theme` on every page, and the Cookies Policy names it correctly. Nothing else in this archived design changes

## v2.0.1

### Fixed

- The imprint said this page is published as Stux.Cloud, "which is operated by Stux.Cloud, which is operated by" Stux Group Ltd, repeating itself; it now reads "published as Stux.Cloud, which is operated by" Stux Group Ltd

## v2.0.0

### Added

- Archived [StuxCloud/maintenancepage](https://github.com/StuxCloud/maintenancepage) at commit `cc3a787` (`v1.1.2`), the last state before Stux.Cloud's rebrand from two-tone green to single teal, preserving history up to that point as this repository's own `main` branch

### Changed

- Served from `maintenancepage-v2.stux.cloud` instead of `maintenancepage.stux.cloud` (CNAME, canonical URLs, sitemap and robots.txt)
- Logo, icon and favicon now point at the archived green assets under `https://global.media.stux.cloud/v2/` instead of the live Stux.Cloud brand assets, which are now teal
- README and CONTRIBUTING describe this repository as an archive
