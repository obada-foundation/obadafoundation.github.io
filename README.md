# OBADA Foundation Website

The official website for the OBADA Foundation (Open Blockchain for Asset Disposition Architecture), a 501(c)(3) nonprofit coalition focused on IT asset disposition (ITAD) standards and blockchain protocols.

## About

This Jekyll-based GitHub Pages website serves as the main web presence for the OBADA Foundation. The foundation develops and maintains open-source blockchain protocols to enable tracking and documentation of IT assets across their lifecycle.

## Quick Start

### Prerequisites

- Ruby and Jekyll
- Git

### Local Development

```bash
# Clone the repository
git clone https://github.com/obadafoundation/obadafoundation.github.io.git
cd obadafoundation.github.io

# Install Ruby (if not already installed) - see Jekyll installation guide:
# https://jekyllrb.com/docs/installation/

# Install Jekyll and dependencies (if not already installed)
gem install jekyll bundler

# Create a local Gemfile for development (Gemfile is in .gitignore)
# Create this file with the following content:
cat > Gemfile << 'EOF'
source "https://rubygems.org"

gem "jekyll", "~> 3.9.0"
gem "github-pages", group: :jekyll_plugins
gem "webrick"
gem "just-the-docs"
EOF

# Install dependencies and serve
bundle install
bundle exec jekyll serve
```

The site will be available at `http://localhost:4000`

### Deployment

The site automatically builds and deploys to GitHub Pages when changes are pushed to the `main` branch.

## Site Structure

```
├── _config.yml          # Jekyll configuration
├── _includes/           # Reusable template components
├── _sass/              # Custom SCSS stylesheets
├── assets/             # Images and static assets
├── dao/                # DAO-related content and documents
├── obada-foundation/   # Foundation information
├── tech-resources/     # Technical documentation and resources
└── index.md           # Homepage
```

## Content Areas

- **Foundation Information**: Mission, board of directors, corporate documents
- **DAO Section**: Member information, documents, applications, presentations
- **Technical Resources**: GitHub links, blockchain explorer, demo videos
- **Projects**: Standards and protocol development information

## Features

- **Documentation Theme**: Uses Just the Docs theme for clean, organized layout
- **Search Functionality**: Built-in search across all content
- **Hierarchical Navigation**: Organized content structure with parent/child relationships
- **Mobile Responsive**: Optimized for all device sizes
- **Custom Branding**: OBADA Foundation styling and logo integration

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test locally using Jekyll serve
5. Submit a pull request

### Content Guidelines

- Use Jekyll front matter for all pages with `title`, `nav_order`, and `permalink`
- Store images in `/assets/images/`
- Follow the existing navigation structure using `parent` and `has_children` properties
- Maintain consistent formatting and style

## Technology Stack

- **Static Site Generator**: Jekyll
- **Theme**: [Just the Docs](https://github.com/pmarsceill/just-the-docs)
- **Hosting**: GitHub Pages
- **Styling**: SCSS with custom overrides
- **Search**: Built-in theme search functionality

## License

Copyright © 2017-2025 OBADA Foundation

## Contact

- Website: [obadafoundation.org](https://www.obadafoundation.org)
- Email: [bizops@obada.io](mailto:bizops@obada.io)
- LinkedIn: [OBADA Foundation](https://linkedin.com/company/obadafoundation)