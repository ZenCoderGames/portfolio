# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a static HTML portfolio website for Srinavin Nair, a game programmer/designer with 10+ years of industry experience. The site showcases professional projects (including AAA titles like God of War: Ragnarok), independent games, design articles, programming guides, AI projects, and creative explorations.

## Architecture

### Single-Page HTML Architecture
- **No build system**: All pages are standalone HTML files with embedded CSS and JavaScript
- **No external dependencies**: Uses native browser APIs and vanilla JavaScript only
- **No package management**: No npm, yarn, or other package managers

### Directory Structure
```
portfolio/
├── index.html                    # Main landing page with all sections
├── professional/                 # Professional game projects
│   ├── god-of-war-ragnarok.html
│   ├── rival-crimson-chaos.html
│   ├── blood-tales.html
│   ├── days-of-discord.html
│   ├── dungeon-rampage.html
│   └── ps-home-games.html
├── independent/                  # Independent game projects
│   ├── anti-chess.html
│   ├── hexacore.html
│   └── raven-conspiracy.html
├── design/                       # Game design articles and analysis
│   ├── randomness-in-gameplay.html
│   └── star-wars-jedi-fallen-order.html
├── programming/                  # Technical programming guides
│   └── unity-features.html
├── ai-projects/                  # AI/ML projects
│   └── json-data-viewer.html
├── exploration/                  # Creative work (art, music)
│   ├── art.html
│   └── music.html
└── resources/                    # Media assets (images, GIFs, videos)
    └── design/
        ├── art/
        ├── ps_home/
        ├── randomness/
        └── rival_cxc/
```

## Design System

All pages share a consistent design language defined through CSS custom properties:

```css
:root {
    --primary-bg: #ffffff;
    --header-bg: #373945;
    --secondary-bg: #f5f5f5;
    --text-dark: #5a799f;
    --text-light: #3d7cad;
    --accent-blue: #0dd6f9;
    --nav-bg: #32373c;
    --border-color: #e0e0e0;
}
```

### Page Templates

**Main Landing Page (index.html)**
- Header with sticky navigation
- Hero section with introduction
- Multiple sections (professional, independent, design, programming, ai-projects, exploration)
- Projects grid layout with hover effects
- Mobile-responsive navigation toggle
- Smooth scrolling between sections
- Footer with copyright

**Project Detail Pages**
- Header with back navigation link
- Project hero section with title and metadata (Engine, Role, etc.)
- Content section with headings, paragraphs, lists
- Embedded YouTube videos using responsive iframe containers
- Footer matching main page

### Responsive Design
- Mobile breakpoint at 768px
- Grid layouts collapse to single column on mobile
- Navigation converts to hamburger menu on mobile
- Font sizes and spacing adjust for smaller screens

## Common Development Tasks

### Viewing the Site Locally
Since this is a static HTML site with no dependencies:
```bash
# Option 1: Open directly in browser
start index.html

# Option 2: Use a simple HTTP server (if Python is installed)
python -m http.server 8000
# Then navigate to http://localhost:8000
```

### Adding a New Project

1. **Choose the appropriate category folder**: professional/, independent/, design/, programming/, ai-projects/, or exploration/

2. **Create a new HTML file** using an existing project page as a template

3. **Update index.html** to add the project card in the corresponding section:
```html
<div class="project-card">
    <h3><a href="category/project-name.html">Project Title</a></h3>
    <p>Brief description of the project.</p>
</div>
```

4. **Update project metadata** in the hero section:
```html
<p><strong>Engine:</strong> Unity/Unreal/Custom</p>
<p><strong>Role:</strong> Your role on the project</p>
```

### Adding Media

**Images**: Place in `resources/` under the appropriate subfolder (design/, professional/, etc.)

**YouTube Videos**: Use the responsive iframe pattern:
```html
<div style="position: relative; padding-bottom: 56.25%; height: 0; overflow: hidden; max-width: 100%; margin-bottom: 30px;">
    <iframe style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;"
            src="https://www.youtube.com/embed/VIDEO_ID"
            title="Video Title"
            frameborder="0"
            allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
            referrerpolicy="strict-origin-when-cross-origin"
            allowfullscreen>
    </iframe>
</div>
```

### Styling Consistency

When modifying styles, remember:
- All pages embed their own CSS (no external stylesheets)
- Changes to global styles require updating all HTML files
- Maintain the established color scheme using CSS custom properties
- Keep the same header/footer structure across all pages
- Preserve responsive breakpoints and mobile behavior

### Version Control

The project uses Git:
- Main branch: `main`
- Recent work includes Unity features documentation and project page content
- Commit messages should clearly describe changes

## Important Notes

- **No JavaScript frameworks**: Site uses vanilla JavaScript for navigation toggle and smooth scrolling
- **Self-contained pages**: Each HTML file is completely standalone with embedded styles
- **Mobile-first approach**: All layouts must work on mobile devices
- **Consistent navigation**: Back links should always point to the correct section anchor (e.g., `../index.html#professional`)
- **Asset organization**: Keep media assets organized in the resources/ folder by category
