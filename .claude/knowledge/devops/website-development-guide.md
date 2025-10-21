---
title: OBADA Website Development Guide
category: devops
tags: [jekyll, just-the-docs, yaml, navigation, development]
last_updated: 2025-10-17
---

# OBADA Website Development Guide

## The Technology Stack

The OBADA Foundation website uses three key technologies working together:

### 1. Jekyll (The Converter)
**What it does:** Converts your markdown files (`.md`) into HTML
**Think of it as:** A translator that turns simple text into web pages
**Repository:** https://github.com/jekyll/jekyll

### 2. Just the Docs (The Framework/Theme)
**What it does:** Provides navigation, styling, and page structure
**Think of it as:** The design system and navigation engine
**Repository:** https://github.com/pmarsceill/just-the-docs

### 3. YAML Front Matter (The Navigation Controller)
**What it does:** Controls how pages appear in navigation
**Think of it as:** Manual settings you have to update in every file
**The Pain Point:** You must manually edit YAML in each file to change navigation

**About YAML:** YAML (YAML Ain't Markup Language) is a **standard data format**, NOT specific to Jekyll. It's used by many systems (Docker, Kubernetes, GitHub Actions, etc.). Jekyll just uses it for configuration. Learn more: https://yaml.org/

## How It All Works Together

```
Markdown Files (content)
    ↓
YAML Front Matter (navigation settings)
    ↓
Jekyll (converts to HTML)
    ↓
Just the Docs Theme (applies styling + navigation)
    ↓
Complete Website
```

---

## Just the Docs Theme Explained

### What Just the Docs Provides

- **Hierarchical Navigation** - Parent/child page relationships
- **Search Functionality** - Built-in site search
- **Table of Contents** - Auto-generated from headings
- **Mobile Responsive** - Works on all devices
- **Clean Design** - Professional documentation look

### Configuration

Set in `_config.yml`:
```yaml
remote_theme: pmarsceill/just-the-docs
title: OBADA
description: The Open Blockchain for Asset Disposition Architecture
search_enabled: true
```

---

## YAML Front Matter Navigation System

**What is YAML?** YAML is a **standard human-readable data format** (like JSON or XML). It's NOT Jekyll-specific - it's used across the industry for configuration files. Jekyll uses YAML for page metadata between `---` markers, but the YAML syntax itself is a universal standard.

### The Manual Navigation Problem

**Just the Docs requires you to manually set navigation in every file's YAML front matter.** This means:
- Want to change page order? Edit the `nav_order` in multiple files
- Want to rename a parent page? Update `parent` in all child files
- Want to reorganize sections? Manual YAML editing across many files

**There's no automatic navigation** - it's all controlled by YAML settings you maintain by hand.

### YAML Front Matter Fields

```yaml
---
title: Page Title               # Required: Display name in navigation
nav_order: 2                    # Number controlling sort order among siblings
parent: Parent Page Name        # Exact title of parent page (must match!)
has_children: true              # Set on parent pages with child pages
has_toc: false                  # Show/hide table of contents
permalink: /custom-url/         # Optional custom URL
---
```

### Navigation Rules

1. **nav_order determines position** - Lower numbers appear first
2. **parent must exactly match parent's title** - Typos break navigation
3. **has_children required** - Parent pages need this set to `true`
4. **Everything is manual** - No auto-generation or automatic updates

### Example Navigation Structure

```yaml
# Homepage
---
title: Home
nav_order: 1
---

# Parent page
---
title: OBADA Foundation
nav_order: 2
parent: Our Projects
has_children: true
---

# Child page
---
title: Mission
nav_order: 1
parent: OBADA Foundation  # Must exactly match parent title!
---
```

### What Breaks Navigation

❌ **Changing a parent's title** without updating all children's `parent` fields
❌ **Typo in parent field** - `parent: "OBADA Foundaton"` won't match
❌ **Missing has_children** on a parent page
❌ **Duplicate nav_order** values among siblings
❌ **Invalid YAML syntax** (spacing/indentation errors)

---

## Jekyll Local Development Server

### Starting the Server

```bash
cd /Users/hom/Sync/MasterFiles/external-repos/obadafoundation.github.io
bundle exec jekyll serve
```

**Runs at:** http://127.0.0.1:4000/

**What happens:**
- Converts all `.md` files to HTML
- Applies Just the Docs theme
- Watches for changes and auto-rebuilds
- Lets you preview before pushing to GitHub

### Starting in Background

```bash
bundle exec jekyll serve --detach
```

Runs in background so you can keep working.

### Stopping the Server

**Foreground mode:** Press `Ctrl+C`

**Background mode:**
```bash
pkill -f "jekyll serve"
```

**Find and kill by PID:**
```bash
ps aux | grep jekyll
kill <process_id>
```

### Check if Running

```bash
ps aux | grep jekyll | grep -v grep
```

If you see output → running
If nothing → stopped

---

## Common Commands

```bash
# Install dependencies (first time or after Gemfile changes)
bundle install

# Serve locally with auto-rebuild
bundle exec jekyll serve

# Serve in background
bundle exec jekyll serve --detach

# Build without serving
bundle exec jekyll build

# Clean generated files
bundle exec jekyll clean
```

---

## Making Content Changes

### Safe Content Edits

1. **Edit markdown content** - Change text in `.md` files
2. **Jekyll auto-rebuilds** - Changes appear immediately if server running
3. **Preview locally** - Check at http://127.0.0.1:4000/
4. **Push to GitHub** - When satisfied, commit and push

### Don't Touch

❌ **YAML front matter** (unless restructuring navigation)
❌ **_config.yml** (site-wide settings)
❌ **_includes/** folder (theme templates)
❌ **_sass/** folder (theme styles)
❌ **_site/** folder (auto-generated, never edit)

---

## GitHub Pages Deployment

When you push to `main` branch:

1. GitHub automatically runs Jekyll
2. Applies Just the Docs theme
3. Converts markdown → HTML
4. Publishes to https://obadafoundation.org

**No manual deployment needed!** Changes live in 1-2 minutes.

---

## Navigation Management Pain Points

### The Problem

Because Just the Docs uses manual YAML-based navigation:

1. **Reorganizing is tedious** - Must edit YAML in multiple files
2. **Easy to break** - One typo in `parent` field breaks child pages
3. **No automation** - Can't bulk rename or reorder easily
4. **Hard to maintain** - More pages = more manual YAML to manage

### Best Practices

- **Plan navigation structure first** before creating many pages
- **Use consistent naming** for parent titles (exact matches required)
- **Test after changes** - Check nav bar after renaming parents
- **Document structure** - Keep track of parent/child relationships
- **Be careful with titles** - Changing a parent title requires updating all children

---

## Troubleshooting

### Server won't start
```bash
bundle install
```

### Port already in use
```bash
pkill -f "jekyll serve"
bundle exec jekyll serve
```

### Changes not appearing
1. Check server running: `ps aux | grep jekyll`
2. Hard refresh: `Cmd+Shift+R` (Mac) or `Ctrl+Shift+R` (Windows)
3. Restart server: `pkill -f "jekyll serve" && bundle exec jekyll serve`

### Navigation broken
1. Check for typos in `parent` fields
2. Verify parent has `has_children: true`
3. Check for duplicate `nav_order` values
4. Validate YAML syntax (spacing matters!)

---

## Preview URLs

- Homepage: http://127.0.0.1:4000/
- Mission: http://127.0.0.1:4000/obada-foundation/mission/
- DAO: http://127.0.0.1:4000/dao/
- Any page: http://127.0.0.1:4000/[permalink]/

The permalink comes from the page's YAML front matter.

---

## Key Takeaways

1. **Jekyll converts** markdown to HTML
2. **Just the Docs provides** navigation, styling, and structure
3. **YAML front matter controls** navigation (manually, painfully)
4. **Navigation is fragile** - Easy to break with typos or wrong field values
5. **Test locally first** - Always preview before pushing
6. **GitHub Pages auto-deploys** - No manual deployment needed

---

## For More Details

**Detailed site structure:** See `.claude/knowledge/navigation/site-architecture.md`
**Just the Docs docs:** https://just-the-docs.github.io/just-the-docs/
**Jekyll docs:** https://jekyllrb.com/docs/
