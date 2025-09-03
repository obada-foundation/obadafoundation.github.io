# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Jekyll-based GitHub Pages website for the OBADA Foundation (Open Blockchain for Asset Disposition Architecture). The site serves as the main web presence for the nonprofit coalition focused on IT asset disposition (ITAD) standards and blockchain protocols.

## Site Architecture

- **Jekyll Static Site**: Uses the `pmarsceill/just-the-docs` remote theme
- **GitHub Pages**: Hosted directly from the repository
- **Content Structure**: 
  - Main content in Markdown files at root and in organized directories
  - DAO-related content in `/dao/` directory
  - Foundation information in `/obada-foundation/` directory
  - Technical resources in `/tech-resources/` directory
  - Press and project information in dedicated sections

## Development Commands

Since this is a Jekyll GitHub Pages site, local development typically uses:

```bash
# Install Jekyll and dependencies (if not already installed)
gem install jekyll bundler

# Serve the site locally (if Gemfile exists)
bundle exec jekyll serve

# Alternative if no Gemfile
jekyll serve
```

The site automatically builds and deploys when changes are pushed to the main branch.

## Content Management

- **Front Matter**: All content pages use Jekyll front matter with `title`, `nav_order`, `permalink`, etc.
- **Navigation**: Hierarchical navigation controlled by `nav_order` and `parent`/`has_children` properties
- **Search**: Search functionality enabled via `search_enabled: true` in `_config.yml`
- **Assets**: Images stored in `/assets/images/` directory

## Key Configuration

- **Theme**: Uses Just the Docs theme for documentation-style layout
- **Search**: Built-in search enabled
- **Navigation**: Custom navigation structure with hierarchical organization
- **Branding**: OBADA logo and foundation-specific styling

## Content Areas

- **Foundation Info**: Mission, board of directors, corporate documents
- **DAO Section**: Member information, documents, applications, presentations  
- **Technical Resources**: GitHub links, blockchain explorer, demo videos
- **Projects**: Standards and protocol development information

## Customization

- Custom SCSS in `_sass/custom/custom.scss` and `_sass/navigation.scss`
- Custom includes in `_includes/` for navigation and site components
- Theme configuration through `_config.yml`