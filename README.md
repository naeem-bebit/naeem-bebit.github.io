# Data Science Blog

Personal blog built with [Hugo](https://gohugo.io/) and the [PaperMod](https://github.com/adityatelange/hugo-PaperMod) theme, deployed to GitHub Pages at https://naeem-bebit.github.io/

## Cloning

The theme is a git submodule, so clone with:

```bash
git clone --recurse-submodules https://github.com/naeem-bebit/naeem-bebit.github.io.git
```

(If you already cloned without it: `git submodule update --init --recursive`)

## Writing a post

Create a Markdown file at `content/posts/YYYY-MM-DD-slug.md` with front matter:

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

To keep a custom URL, add `url: "/my-slug/"` to the front matter.

## Previewing locally

Install [Hugo extended](https://gohugo.io/installation/) (v0.166.0 is used in CI), then run:

```bash
hugo server
```

and open http://localhost:1313/

## Deploying

Push to `master` — the GitHub Actions workflow (`.github/workflows/hugo.yml`) builds and deploys automatically.

One-time setup: in the repo, go to **Settings → Pages → Source** and select **GitHub Actions**.
