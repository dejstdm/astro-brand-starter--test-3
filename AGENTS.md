# AGENTS.md

## Project Overview
Astro-based design system starter for creating brand websites with component-driven development. The goal is to create HTML, SCSS, and JS that can be easily copy-pasted into other systems (e.g., Drupal themes) after build.

## Quick Start

### Setup Commands
- Install deps: `npm install`
- Start dev server: `npm run dev` (runs at `localhost:4321`)
- Build: `npm run build` (outputs to `./dist/`)
- Preview build: `npm run preview`
- Astro CLI: `npm run astro ...`

### Project Structure
```
src/
├── components/          # Reusable UI components
│   ├── examples/       # Example components (hero, slider, accordion, etc.)
│   ├── prod/           # Production-ready components
│   └── dev/           # Development-only components
├── scss/               # SCSS styles and variables
│   ├── base/          # Base styles (fonts, normalize, typography, globals)
│   ├── components/    # Component-specific styles
│   ├── layout/        # Layout styles (container, section)
│   └── utils/         # Variables and utilities
├── pages/              # Astro pages and routes
│   ├── dev/           # Development and component showcase pages
│   │   ├── components-all/     # Example components showcase
│   │   ├── prod-components/    # Production components showcase
│   │   ├── components-pages/   # Individual component test pages
│   │   └── design-system/      # Design system documentation
│   └── prod/           # Production system documentation
├── scripts/            # JavaScript modules and functions
└── public/             # Static assets (images, icons, favicon)
```

## Development Workflow

### 1. Component Development
- **Create Component**: See `/src/components/AGENTS.md` for detailed workflow
- **Style Component**: See `/src/scss/AGENTS.md` for SCSS guidelines
- **Test Component**: Test in `/src/pages/dev/` directory

### 2. Design System Setup
- **Design Tokens**: See `/src/pages/prod/AGENTS.md` for design system blueprint
- **Component Library**: Build reusable components following established patterns
- **Documentation**: Maintain component showcase and usage examples

### 3. Build & Deploy
- **Development**: `npm run dev` for hot reload development
- **Build**: `npm run build` generates static assets in `/dist/`
- **Output**: Copy HTML, CSS, and JS from `/dist/` to target system

## Key Principles

### Architecture
- **Component-Driven**: All UI elements as reusable components
- **Design System**: Consistent visual language and patterns
- **Mobile-First**: Progressive enhancement from mobile to desktop
- **Accessibility**: WCAG compliance and inclusive design

### Technology Stack
- **Astro**: Component framework for static site generation
- **SCSS**: CSS preprocessor with BEM methodology
- **JavaScript**: ES modules for component interactivity
- **Vite**: Build tool with hot reload and optimization

### Critical Development Rule
- **ONLY implement what is explicitly requested**: Do not add extra features, styles, or functionality beyond what the user specifically asks for
- **No assumptions**: If asked for color variables, only add color variables - do not add focus states, selection styles, or other unrelated features
- **Stick to the task**: This rule applies to SCSS, components, pages, and all project files
- **Ask for clarification**: If unsure about scope, ask the user rather than making assumptions

## File Organization

### Naming Conventions
- **Components**: PascalCase (e.g., `ExampleHero.astro`)
- **SCSS Files**: kebab-case with underscore prefix (e.g., `_example-hero.scss`)
- **JavaScript**: kebab-case (e.g., `example-hero.mjs`)

### Import Structure
- **SCSS**: Follow import order in `/src/scss/main.scss`
- **Components**: Import in appropriate dev pages for testing
- **JavaScript**: Import in component files or layouts as needed

## Getting Help

### Documentation
- **Component Development**: `/src/components/AGENTS.md`
- **SCSS Guidelines**: `/src/scss/AGENTS.md`
- **Design System**: `/src/pages/prod/AGENTS.md`

### Testing & Debugging
- **Visual Testing**: Use dev pages in `/src/pages/dev/`
- **Responsive Testing**: Test across all breakpoints
- **SCSS Compilation**: Check build output for errors
- **Hot Reload**: Works for `.astro`, `.scss`, and `.js` files

## Build Configuration

### Development
- Vite handles CSS with dev sourcemaps enabled
- Astro dev toolbar is disabled
- SASS compilation with source maps for development

### Production
- Output optimized for static hosting and integration
- CSS and JS minification
- Asset optimization for performance
