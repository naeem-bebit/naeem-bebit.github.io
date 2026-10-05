# Data Science Blog

Personal blog built with [Hugo](https://gohugo.io/) and the [PaperMod](https://github.com/adityatelange/hugo-PaperMod) theme, deployed to GitHub Pages at https://naeem-bebit.github.io/

## Cloning

The theme is a git submodule, so clone with:

```bash
git clone --recurse-submodules https://github.com/naeem-bebit/naeem-bebit.github.io.git
```

(If you already cloned without it: `git submodule update --init --recursive`)

## Writing a post

Create a Markdown file at `content/posts/my-slug.md` — the file name (minus `.md`) becomes the URL (`/posts/my-slug/`). Hugo does **not** strip a `YYYY-MM-DD-` prefix like Jekyll does, so don't prefix the name with a date. Put the date in the front matter instead:

```yaml
---
title: "My Post Title"
date: 2026-10-05
summary: "Short description shown in lists and search results"
tags:
  - Python
ShowToc: true
---

Post content here.
```

To use a custom URL (e.g. a short root-level `/my-topic/` like the older posts), add `url: "/my-topic/"` to the front matter.

## Previewing locally

Install [Hugo extended](https://gohugo.io/installation/) (v0.166.0 is used in CI), then run:

```bash
hugo server
```

and open http://localhost:1313/

## Deploying

Push to `master` — the GitHub Actions workflow (`.github/workflows/hugo.yml`) builds and deploys automatically.

One-time setup: in the repo, go to **Settings → Pages → Source** and select **GitHub Actions**.
