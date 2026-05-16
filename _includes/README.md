# Website Components

This directory contains reusable Jekyll includes (components) for the Publishing Strategy Sessions website.

## Core Layout Components

### `head.html`
- HTML `<head>` section with meta tags, stylesheets, fonts
- Includes SEO plugin, feed meta, Google Fonts preconnect
- Includes analytics tracking

### `header.html`
- Site navigation and branding
- Responsive mobile menu
- Auto-generated navigation from site pages
- YouTube link in navigation

### `footer.html`
- Site footer with three columns: About, Connect, Resources
- Social media links
- Copyright notice
- Newsletter and RSS links

### `social.html`
- Social media icons component
- Used within footer

## Feature Components

### `hero.html`
Split-screen hero section with presenter image and CTA buttons.

**Parameters:**
- `title` - Hero heading (default: "Build a Sustainable, Profitable Publishing Business")
- `subtitle` - Hero description text

**Usage:**
```liquid
{%- include hero.html -%}

{%- include hero.html 
   title="Custom Title" 
   subtitle="Custom subtitle text" -%}
```

### `newsletter.html`
Newsletter signup section with email form.

**Parameters:**
- `title` - Section heading (default: "Get Weekly Publishing Strategies")
- `description` - Section description
- `action` - Form action URL (default: "#")
- `placeholder` - Email input placeholder (default: "your@email.com")
- `button_text` - Submit button text (default: "Subscribe")

**Usage:**
```liquid
{%- include newsletter.html -%}

{%- include newsletter.html 
   title="Join Our Community"
   action="https://your-newsletter-service.com/subscribe" -%}
```

### `scripts.html`
Interactive JavaScript functionality:
- Sticky header scroll effect
- Smooth scroll for anchor links
- Intersection Observer animations for feature cards and stats

Automatically included in all pages via `default.html` layout.

### `analytics.html`
Umami Analytics tracking script (production only).
- Automatically included in `<head>` via `head.html`
- Website ID: `d903c490-912e-402e-9521-0d9253a78a3e`
- Domain: `analytics.minz.at`

### `opengraph.html`
Comprehensive Open Graph and Twitter Card metadata.
- Automatically included in `<head>` via `head.html`
- Generates OG tags for proper social media sharing
- Supports page-level image overrides via frontmatter
- Article-specific metadata for blog posts
- Default image: `/assets/images/open-graph-thumbnail.png`

**Page-level customization:**
```yaml
---
layout: post
title: "Your Post Title"
description: "Custom OG description"
image: /assets/images/custom-post-image.png
---
```

## Component Architecture

```
_layouts/
  default.html     → Includes: head, header, footer, scripts
  home.html        → Includes: hero, newsletter
  post.html        → (extends default)
  page.html        → (extends default)

_includes/
  head.html        → Includes: opengraph, analytics
  header.html
  footer.html      → Includes: social
  social.html
  hero.html
  newsletter.html
  scripts.html
  analytics.html
  opengraph.html
```

## Making Changes

**To modify site-wide elements:**
- Navigation: Edit `header.html`
- Footer: Edit `footer.html`
- Meta tags: Edit `head.html`
- JavaScript: Edit `scripts.html`

**To modify homepage sections:**
- Hero: Edit `hero.html` or pass custom parameters
- Newsletter: Edit `newsletter.html` or pass custom parameters

**To add analytics/tracking:**
- Edit `analytics.html`

## Best Practices

1. **Keep components focused** - Each component should have a single responsibility
2. **Use parameters** - Make components flexible with `include` parameters
3. **Provide defaults** - Always set sensible default values
4. **Document parameters** - List all available parameters in this README
5. **Test changes** - Changes to components affect multiple pages
