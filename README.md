# INCTN website

Official website of the **Italian Network for Computational and Theoretical Neuroscience (INCTN)**.

This repository contains the source code for the public website:

- `https://inctn.it`
- `https://www.inctn.it`

The site is built with **Jekyll 4**, managed with **Bundler**, and deployed to **GitHub Pages via GitHub Actions**.

---

## Purpose of this repository

This repository is meant to make it easy to:

- edit website content
- preview changes locally before publishing
- manage speakers, organizers, images, and downloadable files
- keep the public website version-controlled and reproducible

---

## Repository structure

The website currently includes:

- homepage:
  - `index.html`
- main pages:
  - `organizers.html`
  - `program.html`
  - `registration.html`
  - `society.html`
  - `speakers.html`
  - `venue.html`
  - `past_editions.html`
- collections:
  - `_organizers/`
  - `_speakers/`
- shared site structure:
  - `_layouts/`
  - `_includes/`
  - `_data/`
- styling:
  - `_sass/`
  - `css/`
- scripts:
  - `js/`
- assets:
  - `images/`
  - `files/`
- site configuration:
  - `_config.yml`
  - `.ruby-version`
  - `Gemfile`
  - `CNAME`
- deployment workflow:
  - `.github/workflows/pages.yml`

---

## Recommended editing workflow

The easiest and safest way to edit this site is:

1. clone the repository locally
2. open it in **Visual Studio Code**
3. install the Ruby dependencies locally in the repository
4. run Jekyll locally
5. preview the website in your browser
6. make changes
7. commit and push the changes to GitHub

For anything beyond a tiny typo fix, local editing is strongly preferred over editing directly in the GitHub web interface.

---

## Requirements

You need:

- **Git**
- **Ruby 3.0**
- **Bundler**
- **VS Code** (recommended, but any editor will work)

On Debian/Ubuntu systems, local builds may also require development packages such as `ruby-dev`, `build-essential`, and `zlib1g-dev`.

---

## First-time setup

Clone the repository:

```bash
git clone https://github.com/INCTN/inctn.github.io.git
cd inctn.github.io
```

Install Bundler for your user account if needed:

```bash
gem install --user-install bundler
```

Tell Bundler to install gems inside the repository instead of system-wide:

```bash
bundle config set --local path 'vendor/bundle'
```

Install dependencies:

```bash
bundle install
```

Start the local development server:

```bash
bundle exec jekyll serve --livereload
```

Then open:

```text
http://localhost:4000
```

The browser should reload automatically when you save a file.

---

## Ruby version

This repository pins the Ruby version in `.ruby-version`.

If you use a Ruby version manager such as `rbenv`, `asdf`, or `rvm`, make sure you are using the repository's configured Ruby version before running `bundle install`.

You can check the active Ruby version with:

```bash
ruby -v
```

---

## Day-to-day editing

### Editing normal pages

Most public pages are top-level files such as:

- `index.html`
- `organizers.html`
- `program.html`
- `registration.html`
- `society.html`
- `speakers.html`
- `venue.html`
- `past_editions.html`

These files usually contain:

- a YAML front matter block at the top
- page content below it

Example:

```yaml
---
title: Example page
description: Short description
image: /images/example.png
---
```

For simple content edits, usually only the text below the front matter needs to be changed.

---

### Editing speakers and organizers

The repository contains `_speakers/` and `_organizers/`, but for the current site structure the visible public content is primarily driven by the corresponding page files and templates.

If you need to update speaker or organizer information:

- first inspect `speakers.html` or `organizers.html`
- then check whether the relevant text or image reference is defined there directly or through an include/layout

When in doubt, search the repository for the person’s name before editing.

---

### Editing navigation, layout, or shared page structure

Only edit these if you want to change the structure of the whole site:

- `_layouts/`
- `_includes/`
- `_data/navigation.yml`
- `_data/footer.yml`

Changes in these files can affect many pages at once.

If you only want to update page text, dates, links, or people, do not start here.

---

### Editing styles

Site-wide styling lives in:

- `_sass/`
- `css/`

Only touch these files if you want to change the appearance of the site.

---

### Editing JavaScript

Interactive behavior lives in:

- `js/`

Only edit these files if you know that the change requires JavaScript.

---

### Images and downloadable files

Use:

- `images/` for images
- `files/` for PDFs and other downloadable materials

Use descriptive lowercase filenames with hyphens instead of spaces.

Good example:

```text
/images/keynote-speaker-2025.jpg
```

Less good:

```text
/images/IMG 1234 final NEW.jpg
```

---

## Safe editing rules

### Usually safe edits

These are generally safe for non-technical editors:

- correcting text
- updating dates, venue details, and contact information
- updating speaker or organizer information
- changing links
- adding or replacing images
- uploading PDFs to `files/`

### Edits that need extra care

These can affect the whole site:

- `_config.yml`
- `_layouts/`
- `_includes/`
- `_data/navigation.yml`
- `_data/footer.yml`
- `_sass/`
- `css/`
- `js/`
- `Gemfile`
- `.ruby-version`
- `.github/workflows/pages.yml`
- `CNAME`

If you are unsure whether a change is structural, ask a maintainer first.

---

## Important notes specific to this site

### 1. This site is deployed with GitHub Actions

The public website is built and deployed through the workflow in:

- `.github/workflows/pages.yml`

That means publishing is no longer tied to GitHub Pages' legacy branch-based Jekyll builder.

### 2. Do not remove the `CNAME` file

The `CNAME` file is part of the custom-domain configuration for GitHub Pages.

Do not remove or edit it unless you intentionally want to change the public domain of the website.

### 3. Be careful with `_config.yml`

`_config.yml` controls global Jekyll behavior and affects:

- site metadata
- generated URLs
- sitemap output
- SEO-related values
- enabled plugins

Always test locally after changing it.

---

## Suggested editing process

For each change:

1. pull the latest version
2. create a new branch if the change is substantial
3. run the local server
4. make the change
5. review the page in the browser
6. commit with a clear message
7. push to GitHub
8. open a pull request if review is needed

For very small edits, committing directly may be acceptable, but pull requests are safer for structural or visual changes.

---

## Useful Git commands

Get the latest version:

```bash
git pull
```

See what changed:

```bash
git status
git diff
```

Create a new branch:

```bash
git checkout -b update-homepage-text
```

Commit changes:

```bash
git add .
git commit -m "Update homepage text"
```

Push changes:

```bash
git push -u origin update-homepage-text
```

---

## Local preview and build

Run the local preview server:

```bash
bundle exec jekyll serve --livereload
```

Build the static site without serving it:

```bash
bundle exec jekyll build
```

The generated output is written to:

```text
_site/
```

---

## Publishing

This repository is published with **GitHub Actions**.

In most cases, once changes are pushed to the publishing branch, GitHub Actions will:

1. install the Ruby dependencies
2. build the site with Jekyll
3. deploy the generated site to GitHub Pages

If the site does not update immediately:

- wait a few minutes
- check the **Actions** tab on GitHub
- inspect the latest Pages deployment workflow run

---

## Troubleshooting

### `bundle install` fails

Possible causes include:

- wrong Ruby version
- missing Bundler
- missing system development packages
- stale `vendor/bundle` contents from an older Ruby version

Useful checks:

```bash
ruby -v
bundle -v
```

If needed, clean the local bundle and reinstall:

```bash
rm -rf vendor/bundle
bundle install
```

---

### `bundle exec jekyll serve` fails

Check for:

- Ruby version mismatch
- syntax errors in `_config.yml`
- invalid front matter in a page
- missing gems after a Gemfile change

Try:

```bash
bundle install
bundle exec jekyll build
```

If the build succeeds, try serving again.

---

### The site builds locally but looks broken

Check for:

- broken image paths
- invalid front matter
- missing closing HTML tags
- accidental changes in `_layouts/` or `_includes/`
- CSS or JS files not loading because of incorrect paths

---

### A page does not update locally

Make sure:

- the file was saved
- the Jekyll server is running
- the browser is not showing a cached version
- the page is actually linked from the navigation if relevant

---

## Style guidance for editors

- keep filenames lowercase
- use hyphens instead of spaces
- keep titles short and clear
- prefer internal links like `/program/` instead of full absolute URLs when linking within the site
- prefer paths like `/images/...` and `/files/...`
- preview every change locally before pushing

---

## Maintainers

If you are unsure whether a change is content-only or structural, ask a maintainer before editing shared templates, styles, configuration, or deployment files.

