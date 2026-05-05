# Publishing Strategy Sessions Website

The companion website for the [Publishing Strategy Sessions YouTube channel](https://www.youtube.com/@PublishingStrategySessions) - a resource for indie authors and publishers building sustainable, profitable publishing businesses.

## Brand Identity

This site uses a professional, clean design optimized for readability:

### Typography
- **Headings**: Playfair Display (serif) - elegant, classic serif for titles and headings
- **Body Text**: Source Sans Pro (sans-serif) - clean, readable sans-serif for content

### Color Palette
- `#FDFCF9` - Warm off-white background
- `#FFFFFF` - Pure white
- `#172133` - Dark navy blue (primary dark text)
- `#070B1C` - Deep navy (darkest shade for footer)
- `#D97706` - Amber/orange (accent color for CTAs and links)

### Design Principles
- Clean, professional aesthetic appropriate for the publishing industry
- High contrast for readability (dark text on light backgrounds)
- Warm, inviting color scheme that feels premium but approachable
- Consistent use of amber accent color for calls-to-action and emphasis

## Development

### Prerequisites
- Ruby 3.4+
- Bundler

### Setup
```bash
# Install dependencies
/home/hberaud/.local/share/gem/ruby/3.4.0/bin/bundle install

# Start development server
/home/hberaud/.local/share/gem/ruby/3.4.0/bin/bundle exec jekyll serve

# Or use your local bundle shortcut
bundle exec jekyll serve
```

### Project Structure
```
.
├── _config.yml          # Site configuration
├── _posts/              # Blog posts (YYYY-MM-DD-title.markdown)
├── assets/
│   └── css/
│       └── style.scss   # Custom Minz branding styles
├── about.markdown       # About page
├── index.markdown       # Homepage
└── Gemfile              # Ruby dependencies
```

### Creating New Posts

Blog posts go in the `_posts/` directory with the naming format:
```
YYYY-MM-DD-title.markdown
```

Example post structure:
```markdown
---
layout: post
title: "Your Post Title"
date: 2026-05-02 12:00:00 +0200
categories: publishing strategy
---

Your content here...
```

### Custom Styling

The site's branding is defined in `assets/css/style.scss`, which:
- Imports Google Fonts (Playfair Display + Source Sans Pro)
- Overrides Minima theme with custom brand colors
- Applies custom typography throughout the site
- Styles links, buttons, headers, and footer with brand colors

To modify styling, edit `assets/css/style.scss`.

## Deployment

The site can be deployed to:
- **GitHub Pages** - Enable in repository settings
- **Netlify** - Connect repository and deploy
- **Vercel** - Import project and deploy
- **Self-hosted** - Build with `bundle exec jekyll build` and serve `_site/`

## About Publishing Strategy Sessions

Publishing Strategy Sessions is a YouTube channel and resource hub for indie authors and publishers:
- **Focus**: Actionable strategies for sustainable, profitable publishing businesses
- **Content**: Pricing strategies, book marketing, launch tactics, reader engagement, publishing tools
- **Approach**: No fluff—just proven tactics from analyzing successful indie authors
- **Audience**: Independent authors, self-publishers, publishing entrepreneurs

Watch on YouTube: [Publishing Strategy Sessions](https://www.youtube.com/@PublishingStrategySessions)
