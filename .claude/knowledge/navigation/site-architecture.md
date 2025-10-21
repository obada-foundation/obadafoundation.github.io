---
title: Site Architecture Guide
category: navigation
tags: [jekyll, structure, navigation, architecture]
last_updated: 2025-10-17
---

# Site Architecture Guide

**Purpose:** Comprehensive technical reference explaining how the OBADA Foundation Jekyll website is structured and functions.

**Audience:** AI agents and developers making content changes to the website.

---

## Table of Contents

1. [Overview](#overview)
2. [Jekyll Fundamentals](#jekyll-fundamentals)
3. [Just the Docs Theme](#just-the-docs-theme)
4. [Front Matter System](#front-matter-system)
5. [Navigation Architecture](#navigation-architecture)
6. [URL and Permalink System](#url-and-permalink-system)
7. [File Organization](#file-organization)
8. [Build and Deployment](#build-and-deployment)

---

## Overview

The OBADA Foundation website is a **Jekyll-based static site** hosted on **GitHub Pages**. It uses the **Just the Docs** theme to provide clean, organized documentation-style navigation and presentation.

### Key Technologies

| Component | Technology | Purpose |
|-----------|-----------|---------|
| Static Site Generator | Jekyll 3.9.0 | Converts markdown to HTML |
| Theme | Just the Docs | Provides layout and navigation |
| Hosting | GitHub Pages | Automated build and hosting |
| Styling | SCSS/SASS | Custom styling overrides |
| Search | Built-in (theme) | Client-side search functionality |

---

## Jekyll Fundamentals

### What is Jekyll?

Jekyll is a **static site generator** that transforms plain text files (markdown) into a complete website. It:

1. Reads markdown files (`.md`)
2. Processes front matter (YAML metadata)
3. Applies layouts and templates
4. Generates static HTML pages
5. Outputs complete website to `_site/` directory

### Build Process

```
Source Files → Jekyll Processing → Static HTML Output
    ↓               ↓                    ↓
 *.md files    Parse & Convert      _site/ folder
Front matter   Apply templates      Ready to serve
Includes       Process SASS         Deployed to web
```

### Special Directories

| Directory | Purpose | Editable? |
|-----------|---------|-----------|
| `_config.yml` | Site-wide configuration | ⚠️ **Caution** |
| `_includes/` | Reusable template components | ❌ **No** |
| `_sass/` | Stylesheet components | ❌ **No** |
| `_site/` | Generated output (build artifact) | ❌ **Never** |
| `assets/` | Images, static files | ⚠️ **Caution** |
| Content folders | Actual page content | ✅ **Yes** |

---

## Just the Docs Theme

### Theme Overview

**Just the Docs** is a documentation-focused Jekyll theme that provides:

- Hierarchical navigation with parent/child relationships
- Built-in search functionality
- Mobile-responsive design
- Table of contents generation
- Clean, professional appearance

### Theme Configuration

The theme is configured in `_config.yml`:

```yaml
remote_theme: pmarsceill/just-the-docs
title: OBADA
description: The Open Blockchain for Asset Disposition Architecture
search_enabled: true
logo: "/assets/images/obada-logo.svg"
```

### Navigation Features

1. **Hierarchical Structure:** Pages can have parent/child relationships
2. **Automatic Ordering:** Uses `nav_order` to control sequence
3. **Expandable Sections:** Parent pages with `has_children: true`
4. **Breadcrumbs:** Disabled on this site (`breadcrumbs: false`)

---

## Front Matter System

### What is Front Matter?

Front matter is **YAML metadata** at the top of each markdown file, enclosed between triple dashes (`---`). It controls how Jekyll processes and displays the page.

### Standard Front Matter Fields

```yaml
---
title: Page Title Here              # Required: Display name
permalink: /custom-url/             # Optional: Custom URL path
nav_order: 2                        # Optional: Navigation position
parent: Parent Page Name            # Optional: Parent in hierarchy
has_children: true                  # Optional: Has child pages
has_toc: false                      # Optional: Show table of contents
---
```

### Field Descriptions

| Field | Required | Purpose | Example |
|-------|----------|---------|---------|
| `title` | ✅ Yes | Page display name | `title: About Us` |
| `permalink` | ⚠️ Top-level only | Custom URL path | `permalink: /dao/` |
| `nav_order` | ⚠️ Siblings | Order among siblings | `nav_order: 3` |
| `parent` | For child pages | Parent page title | `parent: Our Projects` |
| `has_children` | For parent pages | Indicates children exist | `has_children: true` |
| `has_toc` | Optional | Show table of contents | `has_toc: false` |

### Front Matter Rules

**Critical Rules:**

1. **Never modify navigation properties** unless restructuring site
2. **Title must exactly match** parent references in child pages
3. **Permalink must be unique** and start/end with `/`
4. **Front matter must be valid YAML** (indentation matters!)

---

## Navigation Architecture

### How Navigation Works

Navigation in Just the Docs is **hierarchical and declarative**:

1. Pages declare their **position** using `nav_order`
2. Pages declare their **parent** using `parent: "Parent Title"`
3. Parents declare they **have children** using `has_children: true`
4. Jekyll builds navigation tree automatically

### Navigation Hierarchy Example

```
Home (nav_order: 1)
└─ OBADA Foundation (nav_order: 1, parent: "Our Projects")
   ├─ Mission (nav_order: 1, parent: "OBADA Foundation")
   ├─ Board of Directors (nav_order: 2, parent: "OBADA Foundation")
   └─ Corporate Documents (nav_order: 3, parent: "OBADA Foundation")
```

### Breaking Navigation

**What breaks navigation:**

- ❌ Changing `title` without updating child `parent` references
- ❌ Typo in `parent` field (must match parent `title` exactly)
- ❌ Missing `has_children: true` on parent with children
- ❌ Duplicate `nav_order` values among siblings
- ❌ Invalid YAML syntax in front matter

---

## URL and Permalink System

### Default URL Generation

Without a `permalink`, Jekyll generates URLs from file paths:

```
File: obada-foundation/mission.md
URL:  /obada-foundation/mission/
```

### Custom Permalinks

Pages can specify custom URLs using `permalink`:

```yaml
---
title: OBADA DAO
permalink: /dao/          # Custom URL (not /dao/index/)
---
```

### Permalink Rules

1. **Must start with `/`** (e.g., `/dao/` not `dao/`)
2. **Should end with `/`** (e.g., `/dao/` not `/dao`)
3. **Must be unique** across entire site
4. **Commonly used for** index pages and top-level sections

### URL vs File Path

**Important:** URL path and file path can differ!

```
File Path:     dao/index.md
Permalink:     /dao/
Rendered URL:  https://obadafoundation.org/dao/
```

When referencing pages or linking, **use the permalink**, not the file path!

---

## File Organization

### Directory Structure

```
obadafoundation.github.io/
├── _config.yml                    # Site configuration
├── _includes/                     # Template components (DO NOT EDIT)
├── _sass/                         # Stylesheets (DO NOT EDIT)
├── _site/                         # Build output (NEVER EDIT)
├── assets/                        # Images and static files
│   └── images/                    # Logo, icons, photos
│
├── dao/                           # OBADA DAO content
│   ├── index.md                   # DAO landing page
│   ├── dao-members.md             # Member information
│   ├── faq.md                     # FAQ page
│   └── documents/                 # DAO documents
│       └── index.md               # Documents landing
│
├── obada-foundation/              # Foundation content
│   ├── index.md                   # Foundation landing
│   ├── mission.md                 # Mission statement
│   ├── bod.md                     # Board of directors
│   └── corporate-docs/            # Corporate documents
│       └── index.md               # Documents landing
│
├── tech-resources/                # Technical documentation
│   ├── index.md                   # Tech resources landing
│   ├── github.md                  # GitHub links
│   └── blockchain-explorer.md     # Explorer documentation
│
├── projects/                      # Projects section
│   ├── index.md                   # Projects landing
│   └── standard.md                # Standards information
│
├── webpage-concepts/              # Conceptual explanations
│   └── index.md                   # Concepts landing
│
├── home/                          # Home section pages
│   ├── calendar.md                # Events calendar
│   └── meetings.md                # Meeting schedules
│
├── index.md                       # Homepage (root /)
├── press.md                       # Press page
└── 404.md                         # Error page
```

### Index Files

**Purpose of `index.md`:**

Index files serve as **landing pages** for sections. They typically:

- Have `has_children: true` in front matter
- Use custom `permalink` (e.g., `/dao/`)
- Contain overview or introduction content
- Act as navigation hub for child pages

---

## Build and Deployment

### Local Development

**Starting local server:**

```bash
cd obadafoundation.github.io
bundle exec jekyll serve
```

**Access at:** `http://localhost:4000` (or `http://127.0.0.1:4000`)

### Build Process

1. Jekyll reads all markdown files
2. Processes front matter
3. Applies theme layouts
4. Converts markdown to HTML
5. Outputs to `_site/` directory
6. Serves static files

### GitHub Pages Deployment

**Automatic deployment:**

1. Push changes to `main` branch on GitHub
2. GitHub Actions automatically triggers build
3. Jekyll processes all files
4. Site deployed to `https://obadafoundation.org`
5. Changes live within 1-2 minutes

### Build Artifacts

- `_site/` folder contains generated HTML
- **Never commit** `_site/` folder to repository
- **Never edit** files in `_site/` (they're regenerated)

---

## Key Takeaways

### For Content Editors

✅ **Safe to edit:**
- Page content (text, markdown)
- Dates, names, descriptions
- Links and references

❌ **Do not edit:**
- Navigation properties (`nav_order`, `parent`, `has_children`)
- Permalinks (unless restructuring)
- `_config.yml` structure
- Theme files (`_includes/`, `_sass/`)

### For Understanding the Site

1. **Jekyll converts markdown → HTML** using templates and layouts
2. **Front matter controls** how pages are processed and displayed
3. **Navigation is hierarchical** using parent/child relationships
4. **URLs can differ** from file paths via permalinks
5. **Theme provides structure**, content files provide substance
6. **GitHub Pages automates** build and deployment

---

**Last Updated:** 2025-10-13
**Maintained By:** OBADA Foundation Development Team
