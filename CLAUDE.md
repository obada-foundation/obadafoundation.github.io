# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## PRIORITY INSTRUCTION: Content Changes First

**ALWAYS check if the user is requesting simple content/text changes BEFORE doing anything else.**

When a user requests any change to website content (updating text, adding information, changing descriptions, etc.), you MUST:

1. **First determine if this is a simple content change** - any request involving:
   - Updating existing text on pages
   - Adding new content to existing pages  
   - Changing descriptions, dates, names, or other text content
   - Rephrasing or rewriting existing content

2. **If it IS a content change, immediately use the content-editor agent** instead of direct file editing
   - The content-editor agent handles the complete Git workflow automatically
   - It creates proper branches, commits, and pull requests
   - It ensures safe content-only modifications
   - It's specifically designed for this project's workflow

3. **Only use direct editing tools** if:
   - The user explicitly requests to handle Git operations themselves
   - The change involves technical/structural modifications beyond content
   - The user specifically asks NOT to use the agent

This prioritization ensures proper Git workflow and pull request creation for all content changes.

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

## Git Workflow

### Branch Strategy
- **Main Branch Protection**: Never commit directly to `main`
- **Feature Branches**: Create feature branches for all changes
- **Pull Requests**: All changes must go through pull requests for review

### Workflow Steps
```bash
# Create and switch to feature branch
git checkout -b your-feature-name

# Make your changes and commit
git add .
git commit -m "Short descriptive message"

# Push feature branch
git push -u origin your-feature-name

# Create pull request via GitHub UI
# After approval and merge, clean up
git checkout main
git pull origin main
git branch -d your-feature-name
```

### Commit Message Standards
- **Keep commits short and descriptive**
- **No attribution in commit messages** (Git tracks authorship automatically)
- Use past tense: "Added feature" not "Add feature"
- Examples:
  - ✅ "Updated DAO member information"
  - ✅ "Fixed navigation menu styling"
  - ❌ "Updated DAO member information by John Smith"
  - ❌ "This commit fixed the navigation menu styling issue that was reported"

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

## Content Editing Restrictions

**IMPORTANT: User content editing is strictly limited to the following:**

### Allowed Modifications
- **Page Content**: Text content within Markdown files (`.md`) in all content directories:
  - Root level pages (`index.md`, `press.md`, etc.)
  - `/dao/` directory pages
  - `/obada-foundation/` directory pages
  - `/tech-resources/` directory pages
  - `/webpage-concepts/` directory pages
  - `/example-pages/` directory pages
- **Config Text Values**: Only text values within `_config.yml` (site title, description, etc.)

### FORBIDDEN Modifications
- **NO system files**: Never modify `Gemfile`, `Gemfile.lock`, or any Ruby configuration
- **NO structural files**: Never modify `_config.yml` structure, only text values within it
- **NO theme files**: Never modify `_sass/`, `_includes/`, or any theme-related files
- **NO build files**: Never modify anything in `_site/` directory
- **NO asset files**: Never modify images, CSS, JS, or other assets
- **NO new files**: Never create new files unless explicitly requested for content pages
- **NO system directories**: Never modify `.git/`, build artifacts, or system files

### Content Editing Guidelines
- Always preserve Jekyll front matter (the YAML between `---` markers)
- Maintain existing markdown formatting and structure
- Keep navigation properties (`nav_order`, `parent`, `has_children`) intact
- Only modify the actual content text, not the page structure

## Content Editor Agent

For content-only changes, use the **content-editor** agent available in `.claude/agents/content-editor.md`. This agent automatically handles the complete Git workflow for text changes without requiring technical knowledge.