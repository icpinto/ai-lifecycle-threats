

# Threats Across the AI Lifecycle

Live site: **[https://icpinto.github.io/ai-lifecycle-threats/](https://icpinto.github.io/ai-lifecycle-threats/)**
Docs theme: **just-the-docs** (dark scheme, sidebar nav, search)

## Overview

This repository hosts a documentation site that organizes AI/MLOps security threats across the full lifecycle—**Data Engineering**, **Experiment / Development**, and **Production**—with detailed subsections and diagram placeholders. Content is written in Markdown so it’s easy to edit and review via pull requests.


## Repository structure

```
.
├─ _config.yml
├─ index.md
├─ data-engineering.md
├─ data-engineering/
│  ├─ data-acquisition.md
│  ├─ data-preprocessing.md
│  ├─ data-analysis.md
│  └─ data-preparation.md
├─ experiment-development.md
├─ experiment-development/
│  ├─ versioned-data.md
│  ├─ model-training.md
│  ├─ model-validation.md
│  ├─ mlops-pipeline.md
│  └─ code-repository.md
├─ production.md
├─ production/
│  ├─ ml-metadata-store.md
│  ├─ model-export.md
│  ├─ model-registry.md
│  ├─ ai-system.md
│  ├─ monitoring.md
│  ├─ input-data.md
│  └─ output-data.md
└─ assets/
   └─ diagrams/
      ├─ data-engineering.svg
      ├─ experiment-development.svg
      └─ production.svg
```

## Quick start (GitHub Pages)

1. Push this repo to GitHub (or fork it).
2. Go to **Settings → Pages**

   * **Source:** `main`
   * **Folder:** `/ (root)`
3. Wait for the build to finish, then open the site URL shown by Pages.

   * Project site URL is typically: `https://<username>.github.io/<repo>/`

### Important: URL & baseurl

Because this is a *project site*, `baseurl` must be set so CSS/JS load correctly.

In `_config.yml`:

```yml
url: https://icpinto.github.io
baseurl: /ai-lifecycle-threats
remote_theme: just-the-docs/just-the-docs
plugins:
  - jekyll-remote-theme
color_scheme: dark
search_enabled: true
```

If you ever convert to a **user site** (repo named `icpinto.github.io`), set `baseurl: ""`.

## Editing content

* Edit any `.md` page directly in GitHub or locally—changes will rebuild the site.
* Keep examples in the format:

  ```md
  - **Some risk:** Short description.  
  > **Ex:** Concrete, real-world example.
  ```
* Order pages via front matter:

  ```yml
  ---
  title: Model Training
  parent: Experiment / Development Stage
  nav_order: 2
  ---
  ```

### Adding a new page

1. Create a new `.md` file under the appropriate section folder.
2. Include front matter like:

   ```yml
   ---
   title: New Topic
   parent: Production (Serving & Operations)
   nav_order: 8
   ---
   ```
3. The page will appear automatically in the sidebar under its parent.

## Diagrams

Replace the placeholders in `assets/diagrams/` with your own `.svg`/`.png`.
Example filename conventions already match the section landing pages.


## Troubleshooting

* **No styles / missing sidebar**: Check `_config.yml` `url` and `baseurl`.
* **Pages not updating**: Confirm the Pages build passed (Repo → Actions → Pages build).
* **Broken links**: Verify file paths and front matter `title`/`parent` names.

## Contributing

1. Create a feature branch.
2. Make edits and ensure examples use `> **Ex:**` style.
3. Open a PR for review.






