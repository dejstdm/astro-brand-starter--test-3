# COMPONENTS AGENTS.md

## Component Development Overview
This document contains **component development workflow and patterns** for the project. It focuses purely on component creation, structure, and JavaScript integration. For SCSS implementation rules, see `/src/scss/AGENTS.md`. For design system setup, see `/src/pages/prod/AGENTS.md`.

This project follows a component-driven architecture where all UI elements are built as reusable, maintainable components. Components are organized by purpose and follow consistent patterns for structure, styling, and behavior.

## Component Architecture

### Component Categories
```
src/components/
├── prod/              # Production components
│   ├── Clients.astro
│   ├── Testimonial.astro
│   └── ...
├── examples/          # Example/demo components
│   ├── ExampleHero.astro
│   ├── ExampleSlider.astro
│   ├── ExampleAccordion.astro
│   └── ...
├── dev/              # Development-only components
│   ├── DevNav.astro
│   └── Welcome.astro
└── [future]          # Other production components
```

### Component Types
- **Prod Components**: Production-ready components for brand websites (in `/prod/`)
- **Example Components**: Demonstrations of design patterns and capabilities
- **Development Components**: Tools and navigation for development environment
- **Production Components**: Other reusable components for actual brand websites

## Component Structure Standards

### Component Validation Checklist
**BEFORE submitting any component, verify ALL of these are present**:

- [ ] `<section class="page-sec page-sec--component-name">` (both classes)
- [ ] `<div class="container">` (design system container)
- [ ] `<div class="component-name sec">` (both classes)
- [ ] `<div class="component-name__content sec__content">` (both classes)
- [ ] `<h2 class="component-name__title sec__title">` (both classes for titles)
- [ ] All required classes are present and correctly named
- [ ] No custom container structures or bypasses
- [ ] Test page created in `/src/pages/dev/components-pages/` directory
- [ ] Test page follows required structure with DevLayout

### Standard Component Template
```astro
---
// Component metadata and imports
---

<!-- Component HTML structure -->
<section class="page-sec page-sec--component-name">
  <div class="container">
    <div class="component-name sec">
      <div class="component-name__content sec__content">
        <!-- Component content -->
      </div>
    </div>
  </div>
</section>

<style>
  /* Component-specific styles (if needed) */
</style>

<script>
  // Component JavaScript (if needed)
</script>
```

### Required Component Elements
1. **Section Wrapper**: `<section class="page-sec page-sec--component-name">`
2. **Container**: `<div class="container">` for consistent spacing
3. **Component Root**: `<div class="component-name sec">`
4. **Content Wrapper**: `<div class="component-name__content sec__content">`

### Required Class Structure Rules
**CRITICAL RULE**: **EVERY component MUST follow this exact class structure**:

```astro
<section class="page-sec page-sec--component-name">
  <div class="container">
    <div class="component-name sec">
      <div class="component-name__content sec__content">
        <!-- Component content goes here -->
      </div>
    </div>
  </div>
</section>
```

**MANDATORY CLASS COMBINATIONS**:
- **Section**: `page-sec page-sec--component-name` (both classes required)
- **Component Root**: `component-name sec` (both classes required)
- **Content Wrapper**: `component-name__content sec__content` (both classes required)
- **Titles**: `component-name__title sec__title` (both classes required)

**NO EXCEPTIONS**: Never skip any of these required classes or create custom structures.

**CRITICAL RULE**: **EVERY component MUST use the design system container classes**:
- **Primary container**: Always use `<div class="container">` for main content areas
- **Full-width sections**: Use `<div class="container-fluid">` only when you need content to span the full viewport width
- **Additional containers**: Use other design system container classes as they become available (e.g., `container-sm`, `container-lg`, etc.)
- **No exceptions**: Never create custom containers or bypass the container system
- **Consistent spacing**: This ensures uniform margins, padding, and responsive behavior across all components
- **Future-proof**: The rule applies to ALL container types in the design system, not just the current ones

## Component Naming Conventions

### File Naming
- **PascalCase** for component files: `ExampleHero.astro`
- **kebab-case** for SCSS files: `_example-hero.scss`
- **kebab-case** for JavaScript modules: `example-hero.mjs`

### Class Naming
- **BEM Methodology**: `.block__element--modifier`
- **Component Prefix**: `.component-name` as root class
- **Section Classes**: `.page-sec`, `.sec`, `.sec__content`, `.sec__title`

*Note: For detailed SCSS examples and BEM patterns, see `/src/scss/AGENTS.md`*

## Component Development Workflow

### 1. Component Creation
```bash
# Create component files
touch src/components/examples/NewComponent.astro
touch src/scss/components/_new-component.scss
touch src/scripts/modules/new-component.mjs

# Create test page in CORRECT location
touch src/pages/dev/components-pages/new-component-page.astro
```

### 2. Component Structure
```astro
---
// Import required components and layouts
import DevLayout from '../../layouts/DevLayout.astro';
---

<DevLayout>
  <section class="page-sec page-sec--new-component">
    <div class="container">
      <div class="new-component sec">
        <div class="new-component__content sec__content">
          <h2 class="new-component__title sec__title">Component Title</h2>
          <!-- Component content -->
        </div>
      </div>
    </div>
  </section>
</DevLayout>
```

### 3. Test Page Creation
**CRITICAL RULE**: **EVERY component MUST have a test page in the correct location**:

```bash
# Test page location - NEVER create in wrong directory
src/pages/dev/components-pages/component-name-page.astro  # ✅ CORRECT
src/pages/dev/component-name-page.astro                  # ❌ WRONG
```

**Required Test Page Structure**:
```astro
---
import DevLayout from '../../layouts/DevLayout.astro';
import ComponentName from '../../components/examples/ComponentName.astro';
---

<DevLayout title="Component Name">
  <div class="component-showcase">
    <h1>Component Name</h1>
    <p>Component description and usage guidelines.</p>
    
    <ComponentName />
  </div>
</DevLayout>
```

### 3. SCSS Integration
- Create `_new-component.scss` in `/src/scss/components/`
- Follow SCSS structure guidelines in `/src/scss/AGENTS.md`
- Use BEM methodology for class naming
- Include responsive styles for all breakpoints

### 4. JavaScript Integration
```javascript
// new-component.mjs
export function newComponent() {
  document.addEventListener('DOMContentLoaded', () => {
    // Component initialization
    const component = document.querySelector('.new-component');
    
    // Event listeners
    // State management
    // Interactions
  });
}
```

### 5. Import Registration
- Add component SCSS import to `/src/scss/main.scss`
- Follow import order guidelines in `/src/scss/AGENTS.md`

```javascript
// Import in appropriate page or layout
import { newComponent } from '../../scripts/modules/new-component.mjs';
```

## Component Patterns

### Hero Component Pattern
```astro
<!-- Standard hero structure -->
<section class="page-sec page-sec--hero">
  <div class="container">
    <div class="hero sec">
      <!-- Background Elements -->
      <div class="hero__background">
        <div class="hero__bg-shape hero__bg-shape--1"></div>
      </div>
      
      <!-- Main Content -->
      <div class="hero__content sec__content">
        <div class="hero__text-section">
          <h1 class="hero__title sec__title">Hero Title</h1>
          <p class="hero__subtitle">Hero subtitle</p>
          <div class="hero__actions">
            <!-- Call-to-action buttons -->
          </div>
        </div>
        
        <div class="hero__visual-section">
          <!-- Images or visual elements -->
        </div>
      </div>
    </div>
  </div>
</section>
```

### Interactive Component Pattern
```astro
<!-- Component with JavaScript functionality -->
<div class="interactive-component" data-component="interactive">
  <button class="interactive-component__trigger js__trigger">
    Trigger Action
  </button>
  
  <div class="interactive-component__content">
    <!-- Dynamic content -->
  </div>
</div>

<script>
  // Component-specific script
  const component = document.querySelector('[data-component="interactive"]');
  // Component logic
</script>
```

### Form Component Pattern
```astro
<!-- Form component structure -->
<form class="form-component" data-component="form">
  <div class="form-component__field">
    <label class="form-component__label" for="input-id">Label</label>
    <input 
      class="form-component__input" 
      id="input-id" 
      type="text" 
      required
    />
  </div>
  
  <button class="form-component__submit btn btn-primary" type="submit">
    Submit
  </button>
</form>
```

## Component Styling Guidelines

### CSS Organization
- **Component-specific styles**: In component SCSS file
- **Global styles**: In base SCSS files
- **Layout styles**: In layout SCSS files
- **Utility styles**: In utils SCSS files

*Note: For detailed SCSS patterns, responsive design, and animations, see `/src/scss/AGENTS.md`*

## Component JavaScript Standards

### Module Pattern
```javascript
// Standard component module
export function componentName() {
  // Component initialization
  function init() {
    // Setup code
  }
  
  // Event handlers
  function handleEvent(event) {
    // Event logic
  }
  
  // Public API
  return {
    init,
    destroy: () => {
      // Cleanup code
    }
  };
}
```

### Event Handling
```javascript
// Event delegation pattern
document.addEventListener('click', (event) => {
  if (event.target.matches('.component__trigger')) {
    // Handle trigger click
  }
});

// Component-specific events
const component = document.querySelector('.component');
component.addEventListener('custom-event', handleCustomEvent);
```

### State Management
```javascript
// Simple state management
class ComponentState {
  constructor() {
    this.state = {
      isOpen: false,
      currentStep: 0
    };
  }
  
  setState(newState) {
    this.state = { ...this.state, ...newState };
    this.render();
  }
  
  render() {
    // Update UI based on state
  }
}
```

## Component Testing & Documentation

### Development Testing
- **Visual Testing**: Test in `/src/pages/dev/` directory
- **Responsive Testing**: Test across all breakpoints
- **Interaction Testing**: Verify JavaScript functionality
- **Accessibility Testing**: Check keyboard navigation and screen readers

### Component Documentation
```astro
<!-- Component documentation template -->
<div class="component-docs">
  <h2 class="component-docs__title">Component Name</h2>
  
  <div class="component-docs__description">
    <p>Component description and usage guidelines.</p>
  </div>
  
  <div class="component-docs__example">
    <!-- Live component example -->
  </div>
  
  <div class="component-docs__code">
    <h3>HTML Structure</h3>
    <pre><code><!-- Component HTML --></code></pre>
    
    <h3>SCSS Classes</h3>
    <pre><code>/* Component SCSS */</code></pre>
    
    <h3>JavaScript Usage</h3>
    <pre><code>// Component JavaScript</code></pre>
  </div>
</div>
```

## Component Maintenance

### Version Control
- **Component Updates**: Maintain backward compatibility
- **Breaking Changes**: Document in changelog
- **Deprecation**: Provide migration path for old components

### Performance Optimization
- **Lazy Loading**: Load components when needed
- **Code Splitting**: Separate component JavaScript
- **CSS Optimization**: Minimize unused styles
- **Image Optimization**: Use appropriate image formats and sizes

### Accessibility Maintenance
- **ARIA Labels**: Keep labels up to date
- **Focus Management**: Ensure logical tab order
- **Screen Reader**: Test with assistive technologies
- **Color Contrast**: Maintain accessibility standards

## Component Library Integration

### Design System Integration
- **Example Components Showcase**: Add to `/src/pages/dev/components-all/index.astro`
- **Prod Components Showcase**: Add to `/src/pages/dev/prod-components/index.astro`
- **Individual Pages**: Create in `/src/pages/dev/components-pages/`
- **Documentation**: Update design system documentation

### Layout Guidelines
- **Development Pages**: Use `DevLayout` for component test pages and showcase pages
- **Production Pages**: Use `ProdLayout` for production system pages
- **Component Showcases**: Both example and prod showcases use `DevLayout` as they are development tools

### Component Registry
```javascript
// Component registry for dynamic loading
const componentRegistry = {
  'example-hero': () => import('./ExampleHero.astro'),
  'example-slider': () => import('./ExampleSlider.astro'),
  // ... other components
};

// Dynamic component loading
function loadComponent(name) {
  return componentRegistry[name]?.();
}
```

### Component Dependencies
- **External Libraries**: Document required dependencies
- **Internal Dependencies**: List required components and utilities
- **Version Requirements**: Specify compatible versions
- **Fallbacks**: Provide fallback behavior when dependencies fail
