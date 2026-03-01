# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

```bash
# Install dependencies
npm install

# Start local dev server (hot reload at http://localhost:3000)
npm run start

# Build static site to ./build/
npm run build

# Serve the built site locally
npm run serve

# Clear Docusaurus cache
npm run clear
```

Deployment is handled automatically by GitHub Actions (`.github/workflows/deploy.yml`) on every push to `main`. It builds the site and deploys to GitHub Pages at https://heojaehong.github.io.

## Architecture

This is a **Docusaurus 3.9** static site running in **blog-only mode**.

**Key configuration decisions in `docusaurus.config.js`:**
- `docs: false` — the docs plugin is disabled entirely
- `blog.routeBasePath: '/'` — the blog is mounted at the site root (not `/blog/`)
- `onBrokenLinks: 'throw'` — broken links cause build failures
- `future.v4: true` — opted into Docusaurus v4 compatibility mode

**Content structure:**
- `blog/` — all blog posts; Docusaurus scans this directory automatically
  - `authors.yml` — defines blog author metadata (add new authors here)
  - `tags.yml` — defines allowed tags with permalinks (add new tags here)
  - Posts can be a single `.md`/`.mdx` file or a folder (for posts with assets)
- `src/css/custom.css` — global CSS overrides using Infima CSS variables
- `static/` — assets served at the root URL unchanged

**Blog post format:**
Posts use front matter for metadata. Folder-based posts (e.g., `blog/2025-12-03-hello/`) allow bundling images alongside the post file.

The `docs/` directory exists in the repo but is not rendered (docs plugin is disabled).
