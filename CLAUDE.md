# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Jekyll-based website for **Publishing Strategy Sessions**, a YouTube channel and resource hub for indie authors and publishers. The site uses the Minima theme with extensive custom branding and styling.

## Development Commands

```bash
# Install dependencies (first time or after Gemfile changes)
bundle install

# Start development server (auto-reloads on file changes)
bundle exec jekyll serve

# Build static site for production
bundle exec jekyll build
# Output goes to _site/ directory
```

The development server runs at `http://localhost:4000` and auto-regenerates when files change. **Note:** Changes to `_config.yml` require a server restart.

## Architecture & Structure

### Layout Inheritance

Jekyll uses a layout inheritance system:

- `_layouts/default.html` - Base template with HTML structure, includes header/footer, scroll effects JavaScript
- `_layouts/home.html` - Homepage layout (extends default) with hero section, features grid, stats, newsletter
- `_layouts/post.html` - Blog post layout (extends default) with post-specific styling
- `_layouts/page.html` - Static page layout (extends default)

All layouts reference includes from `_includes/`:
- `head.html` - Meta tags, stylesheets, fonts
- `header.html` - Site navigation and logo
- `footer.html` - Footer with links and social
- `social.html` - Social media icons component

### Styling Architecture

**Critical:** All custom styling lives in `assets/css/style.scss`, which imports Minima then completely overrides it.

The SCSS file defines:
- Brand color palette (SCSS variables at top of file)
- Typography system (Playfair Display for headings, Source Sans Pro for body)
- Component styles (hero, feature cards, newsletter section, stats grid, buttons)
- Responsive breakpoints (mobile at 800px)
- CSS animations and transitions

**Never modify Minima theme files directly** - all overrides go in `style.scss`.

### Brand Identity

Defined in `README.md` and implemented in `assets/css/style.scss`:

**Typography:**
- Headings: Playfair Display (serif) - elegant, classic
- Body: Source Sans Pro (sans-serif) - clean, readable

**Colors:**
```scss
$brand-background: #FDFCF9;    // Warm off-white
$brand-white: #FFFFFF;          // Pure white
$brand-dark-navy: #172133;      // Primary dark text
$brand-deep-navy: #070B1C;      // Darkest shade (footer)
$brand-accent: #D97706;         // Amber/orange (CTAs, links)
$brand-accent-light: #F59E0B;   // Lighter amber
$brand-accent-dark: #B45309;    // Darker amber
```

**When adding new UI elements**, use these existing variables rather than hardcoded colors.

### Content Structure

**Blog Posts:** Go in `_posts/` with strict naming: `YYYY-MM-DD-title.markdown`

Example frontmatter:
```yaml
---
layout: post
title: "Your Post Title"
date: 2026-05-02 12:00:00 +0200
categories: publishing strategy
---
```

**Pages:** Top-level `.markdown` files (`about.markdown`, `index.markdown`) with layout specified in frontmatter.

### JavaScript Functionality

`_layouts/default.html` includes inline JavaScript for:
- Sticky header scroll effect (adds `.scrolled` class after 50px scroll)
- Smooth scroll for anchor links (e.g., newsletter signup link)
- Intersection Observer for fade-in animations on feature cards and stats

**When adding new animated sections**, follow the existing pattern: set initial opacity/transform in JavaScript, add to observer.

## Site Configuration

`_config.yml` contains:
- Site metadata (title, description, email, URLs)
- Social media usernames
- Theme and plugin configuration
- Build settings

**Social links** are automatically generated from `twitter_username` and `github_username` config values.

## Key Files to Modify

| Task | File(s) |
|------|---------|
| Add blog post | `_posts/YYYY-MM-DD-title.markdown` |
| Change brand colors | `assets/css/style.scss` (SCSS variables) |
| Modify homepage sections | `_layouts/home.html` |
| Change navigation | `_includes/header.html` |
| Update footer | `_includes/footer.html` |
| Add new page | Create `pagename.markdown` in root |
| Change site metadata | `_config.yml` |

## Design Patterns

### Reusable Components in home.html

**Hero Section:**
```html
<div class="hero-section">
  <div class="wrapper">
    <h1>Title</h1>
    <p class="hero-subtitle">Subtitle</p>
    <div class="cta-buttons">
      <a href="#" class="btn btn-primary"><span>Text</span></a>
    </div>
  </div>
</div>
```

**Feature Cards:**
```html
<div class="features-grid">
  <div class="feature-card">
    <span class="feature-icon">📊</span>
    <h3>Title</h3>
    <p>Description</p>
  </div>
</div>
```

**Stats Section:**
```html
<div class="stats-section">
  <div class="wrapper">
    <div class="stats-grid">
      <div class="stat-item">
        <span class="stat-number">40-60%</span>
        <span class="stat-label">Label</span>
      </div>
    </div>
  </div>
</div>
```

**Button Classes:**
- `.btn.btn-primary` - Amber button (primary CTAs)
- `.btn.btn-secondary` - Outlined white button (hero section)
- `.btn.btn-outline` - Outlined amber button

### Responsive Behavior

Mobile breakpoint at `800px` defined in `style.scss`:
- Hero h1 reduces from 4rem to 2.75rem
- Feature cards stack to single column
- Newsletter form inputs go full width
- Stats grid becomes single column

**When adding new sections**, include mobile styles in the media query.

## Deployment Options

From README.md - site can be deployed to:
- **GitHub Pages** - Enable in repository settings
- **Netlify** - Connect repository and deploy
- **Vercel** - Import project and deploy
- **Self-hosted** - Run `bundle exec jekyll build` and serve `_site/`

All deployment platforms will automatically detect this as a Jekyll site.

## Content Guidelines

From README.md - this site focuses on:
- Actionable strategies for sustainable, profitable publishing businesses
- Content areas: pricing strategies, book marketing, launch tactics, reader engagement, publishing tools
- Audience: independent authors, self-publishers, publishing entrepreneurs
- Tone: "No fluff—just proven tactics"

**When writing content**, maintain this professional, actionable tone without excessive marketing language.
