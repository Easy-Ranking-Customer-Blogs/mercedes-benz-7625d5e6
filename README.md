# Hugo Blog Template

Minimal Hugo template optimized for AEO (Answer Engine Optimization) and automated content publishing.

## Purpose

This template is designed specifically for:

- **AEO**: Optimized for LLM and answer engine visibility
- **Automated Publishing**: Content managed entirely through automated systems
- **Crawlability**: Clean structure for search engines and AI crawlers
- **Performance**: Fast loading for optimal indexing

## Template Configuration

This template is **dynamically configured per brand** when a new repository is created from this template.

### Automated Configuration

When a new brand repository is created via the `create-github-repo` edge function, the following files are automatically updated:

1. **`data/brand.yaml`** - Brand-specific metadata:

   - `name` - Brand name
   - `description` - Brand description (or auto-generated)
   - `keywords` - Array of brand-specific keywords
   - `google_site_verification` - Google Search Console verification tag
   - `google_analytics_id` - Google Analytics tracking ID

2. **`hugo.yaml`** - Site configuration:

   - `baseURL` - GitHub Pages URL for the brand
   - `title` - Brand name
   - `params.description` - Brand description for SEO
   - `params.keywords` - Brand keywords for SEO

3. **`content/_index.md`** - Homepage content:
   - `title` - Brand name
   - `description` - Brand description

### Accessing Brand Data in Templates

Hugo templates can access brand data via `.Site.Data.brand`:

- `.Site.Data.brand.name`
- `.Site.Data.brand.description`
- `.Site.Data.brand.keywords`
- `.Site.Data.brand.google_site_verification`
- `.Site.Data.brand.google_analytics_id`

Site configuration is also available via standard Hugo variables:

- `.Site.Title` - Brand name
- `.Site.Params.description` - Brand description
- `.Site.Params.keywords` - Brand keywords

### Custom Layouts

The template includes custom layout overrides in `layouts/partials/`:

- **`google_analytics.html`** - Integrates Google Analytics using brand data
- **`extend_head.html`** - Adds Google Site Verification meta tag
- **`home_info.html`** - Uses brand data for homepage content

### Updating Brand Configuration

To update brand settings, modify `data/brand.yaml` and/or `hugo.yaml` and push the changes. Hugo will automatically use the new values on the next build.

## Features

- **⚡ Lightning Fast**: Hugo builds in milliseconds
- **🔍 SEO/AEO Optimized**: Structured data and semantic HTML
- **📱 Responsive**: Works on all devices
- **🤖 Crawler-Friendly**: Clean markup for bots and LLMs
- **📊 Analytics Ready**: Google Analytics integration
- **🏷️ Structured Content**: Categories and tags for organization
- **📄 Auto TOC**: Table of contents for long-form content
- **📡 RSS Feed**: For feed-based discovery

## Quick Start

### Prerequisites

- [Hugo Extended](https://gohugo.io/installation/) v0.152.2 or higher

### Local Development

```bash
# Clone the repository
git clone <your-repo-url>
cd easyrank-starter-template

# Initialize theme submodule
git submodule update --init --recursive

# Run Hugo server
hugo server -D

# View at http://localhost:1313
```

### Building for Production

```bash
hugo --minify
```

The built site will be in the `public/` directory.

## Configuration

The template is pre-configured for AEO. Edit `hugo.toml` to set:

- Site title, description, and URL (automatically set per brand)
- Author/brand information
- Analytics tracking ID (optional)

## Content Structure

```
content/
├── _index.md           # Homepage
└── posts/              # Blog posts
    ├── _index.md       # Posts list page
    └── *.md            # Individual posts
```

## Publishing Content

Content is automatically published through the content management system. Posts appear in `content/posts/` with the format: `YYYY-MM-DD-title-slug.md`

### Required Front Matter

```yaml
---
title: "Post Title"
date: 2025-01-01T10:00:00Z
draft: false
categories: ["category"]
tags: ["tag1", "tag2"]
description: "SEO/AEO description"
---
```

**Note**: All content management happens through the automated publishing system. Do not manually edit posts.

## Theme: PaperMod

Uses [PaperMod](https://github.com/adityatelange/hugo-PaperMod) theme, configured for:

- Clean, semantic HTML
- Fast performance
- Optimal crawlability
- Structured content hierarchy

## GitHub Pages Deployment

This template includes a GitHub Actions workflow for automatic deployment to GitHub Pages.

### Setup

1. Go to repository Settings → Pages
2. Source: GitHub Actions
3. Push to `main` branch to trigger deployment

The workflow builds and deploys your site automatically on every push.

## Template Synchronization

Changes to this template automatically sync to all child repositories. Protected files (see `.templatesyncignore`) are never overwritten.

**Requirements:** `APP_ID` and `APP_PRIVATE_KEY` secrets configured.

## Updating the Theme

```bash
git submodule update --remote --merge
```

## Important Notes

- **No Manual Editing**: All content is managed through automated publishing
- **Automated Only**: This template is for automated publishing only
- **AEO Focus**: Optimized for LLM visibility, not human readers
- **Minimal UI**: Interface features are minimal by design

## Support

For questions or support, contact your content management team.

## License

MIT License - See LICENSE file for details.

---

Powered by [Hugo](https://gohugo.io)
