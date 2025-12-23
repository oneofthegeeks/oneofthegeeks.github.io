# Copilot Instructions for oneofthegeeks.github.io

## Project Overview

This is a personal blog/portfolio site built with Jekyll using the Chirpy theme. The site runs at https://oneofthegeeks.com and features technical posts with affiliate product links.

**Key stack:**
- Jekyll (static site generator) with Chirpy theme v7.4+
- Ruby/Bundler for dependencies
- Custom Ruby plugin for git-based post modification tracking
- Liquid templating for dynamic includes (product links, etc.)

## Workflows

### Development
```bash
./tools/run.sh              # Run jekyll serve with live reload (default)
./tools/run.sh -p           # Production mode
./tools/run.sh -H 0.0.0.0   # Bind to all interfaces
```

### Testing & Building
```bash
./tools/test.sh             # Build site and run html-proofer validation
bundle exec jekyll build    # Incremental build to _site/
```

**Key files:**
- [_config.yml](_config.yml) — Jekyll configuration, site metadata, analytics
- [Gemfile](Gemfile) — Ruby dependencies; regenerate lockfile if Gemfile changes
- [tools/run.sh](tools/run.sh) — Development server wrapper
- [tools/test.sh](tools/test.sh) — Build + html-proofer test suite

## Content Structure

### Posts
Location: `_posts/` with filename format `YYYY-MM-DD-slug.md`

**Post frontmatter template:**
```yaml
---
title: "Post Title"
date: 2025-12-23 10:00:00 -0700
categories: [Category Name]
tags: [tag1, tag2]
toc: true
comments: true
---
```

**Special notes:**
- Use category names that match folder structure in `_site/categories/`
- Tags auto-generate tag pages in `_site/tags/`
- [_plugins/posts-lastmod-hook.rb](_plugins/posts-lastmod-hook.rb) automatically detects last modification from git history; no manual `last_modified_at` needed

### Data Files & Includes
- [_data/products.yml](_data/products.yml) — Affiliate product definitions (ASIN or URL, display text)
- [_includes/amazon_link.html](_includes/amazon_link.html) — Reusable include for affiliate links

**Usage in posts:**
```liquid
{% include amazon_link.html product="raspberry_pi_4_4gb" %}
```

The include pulls product metadata from `_data/products.yml` and generates Amazon affiliate links with tag parameter.

### Tabs (Navigation)
Location: `_tabs/` — These become top-level navigation items
Examples: [_tabs/about.md](_tabs/about.md), [_tabs/archives.md](_tabs/archives.md), [_tabs/disclosure.md](_tabs/disclosure.md)

## Key Patterns & Conventions

### Liquid Templating
- Use `{% include amazon_link.html product="key" %}` for product links (never hardcode Amazon URLs in posts)
- Product keys must exist in [_data/products.yml](_data/products.yml)
- Products support either `asin` (preferred) or `url` field; `text` controls display text

### Git Integration
- Post modification dates are auto-derived from git history via [_plugins/posts-lastmod-hook.rb](_plugins/posts-lastmod-hook.rb)
- Only posts with >1 commit will have `last_modified_at` set
- No manual YAML modification needed for this field

### Build Output
- All built files go to `_site/` (gitignored)
- Built post URLs: `_site/posts/{slug}/index.html`
- Category pages: `_site/categories/{category-name}/index.html`
- Tag pages: `_site/tags/{tag-name}/index.html`

## Common Tasks

**Add a new product affiliate link:**
1. Add entry to [_data/products.yml](_data/products.yml) with ASIN or URL and display text
2. Reference via `{% include amazon_link.html product="key_name" %}` in posts

**Create a new post:**
1. Create `_posts/YYYY-MM-DD-slug.md` with frontmatter
2. Use categories and tags that match site structure
3. Embed affiliate links via Liquid include (see above)
4. Run `./tools/run.sh` to preview; changes live-reload

**Add navigation item:**
1. Create new `.md` file in `_tabs/` directory
2. Will auto-appear in top navigation after rebuild

**Validate before publishing:**
1. Run `./tools/test.sh` to build and run html-proofer checks
2. Verify all affiliate links are defined in [_data/products.yml](_data/products.yml)

## Dependencies & Environment

- Ruby (version per `.ruby-version` if present; Gemfile pins Jekyll and Chirpy versions)
- Bundler: `bundle install` (run after updating Gemfile)
- html-proofer: Included in Gemfile under `:test` group for link validation

## Architecture Notes

The site follows Chirpy theme conventions with minimal customization:
- Theme provides layouts, styles, and default includes
- Custom plugin adds git-aware post metadata
- Data-driven affiliate links reduce hardcoding in content
- Simple git-based last-modified tracking (no additional database needed)
