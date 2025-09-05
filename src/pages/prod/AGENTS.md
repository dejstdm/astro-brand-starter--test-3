# PRODUCTION SYSTEM AGENTS.md

## Production System Overview
This document provides a **blueprint for setting up a production system** for the project. It contains high-level design principles, visual guidelines, and system architecture. For component development workflow, see `/src/components/AGENTS.md`. For SCSS implementation rules, see `/src/scss/AGENTS.md`.

This document provides a blueprint for setting up a comprehensive production system for brand websites with consistent visual language, component patterns, and design tokens. The system will be built on Astro components with SCSS styling and follow established design principles.

## Production System Architecture

### Core Principles
- **Component-Driven Development**: All UI elements are built as reusable components
- **Design Token System**: Centralized variables for colors, spacing, typography, and breakpoints
- **BEM Methodology**: Consistent CSS naming convention for maintainable styles
- **Mobile-First Responsive Design**: Progressive enhancement from mobile to desktop
- **Accessibility First**: WCAG compliance and inclusive design practices

### Production System Layers
```
┌─────────────────────────────────────┐
│           Design Tokens             │
│     (Colors, Typography, Spacing)   │
├─────────────────────────────────────┤
│         Base Components             │
│    (Typography, Layout, Reset)     │
├─────────────────────────────────────┤
│        Layout Components            │
│     (Container, Section, Grid)     │
├─────────────────────────────────────┤
│       UI Components                 │
│  (Buttons, Forms, Navigation)      │
├─────────────────────────────────────┤
│      Pattern Components             │
│   (Hero, Slider, Accordion)        │
└─────────────────────────────────────┘
```

## Design Tokens & Variables

### Color System
```scss
// EXAMPLE: Primary brand colors (replace with actual brand colors)
$primary-color: #0099f7;      // Main brand color
$secondary-color: #00c6ff;    // Secondary brand color
$accent-color: #ffe600;       // Accent/highlight color
$text-primary: #333333;       // Primary text color
$text-secondary: #666666;     // Secondary text color
$background-primary: #ffffff; // Primary background
$background-secondary: #f5f5f5; // Secondary background
```

*Note: Breakpoints, typography scale, and spacing system are documented in `/src/scss/AGENTS.md`*

## Component Design Patterns

### Hero Component Pattern
```scss
// EXAMPLE: Standard hero structure (adapt for your needs)
.hero {
  &__background    // Background elements and shapes
  &__content      // Main content wrapper
  &__text-section // Text content area
  &__visual-section // Image/visual area
  &__actions      // Call-to-action buttons
  &__features     // Feature highlights
  &__stats        // Statistics display
  &__banner       // Promotional banner
}
```

### Section Classes Pattern
```scss
// EXAMPLE: Consistent section structure (adapt for your needs)
.page-sec {
  // Page-level section wrapper
}

.sec {
  // Content section
  
  &__content {
    // Section content wrapper
  }
  
  &__title {
    // Section title styling
  }
}
```

### Button System
```scss
// EXAMPLE: Button variants (adapt for your needs)
.btn {
  &-primary     // Primary action buttons
  &-secondary   // Secondary action buttons
  &--modifier   // Button state modifiers
}
```

## Visual Design Guidelines

### Layout Principles
- **Container System**: Consistent max-width containers with responsive padding
- **Grid System**: CSS Grid and Flexbox for modern layouts
- **Spacing Rhythm**: Consistent vertical rhythm using established spacing scale
- **Visual Hierarchy**: Clear information architecture through typography and spacing

### Animation & Interaction
```scss
// EXAMPLE: Standard animation patterns (adapt for your needs)
@keyframes fadeInUp {
  // Consistent fade-in animation
}

@keyframes slideInLeft {
  // Slide-in animation for text
}

@keyframes float {
  // Floating animation for background elements
}

// Timing functions
transition: all 0.3s ease;        // Standard transitions
animation: fadeInUp 1s ease-out;  // Standard animations
```

### Visual Elements
- **Background Shapes**: Geometric elements for visual interest
- **Gradients**: Linear gradients for modern aesthetics
- **Backdrop Filters**: Blur effects for glass-morphism
- **Shadows**: Subtle shadows for depth and hierarchy

## Component Development Standards

### Component Structure
```astro
<!-- EXAMPLE: Standard component template (adapt for your needs) -->
<section class="page-sec page-sec--component-name">
  <div class="container">
    <div class="component-name sec">
      <div class="component-name__content sec__content">
        <!-- Component content -->
      </div>
    </div>
  </div>
</section>
```

### SCSS Organization
*See `/src/scss/AGENTS.md` for detailed SCSS structure and BEM methodology guidelines.*

### JavaScript Integration
```javascript
// EXAMPLE: Component JavaScript pattern (adapt for your needs)
export function componentName() {
  document.addEventListener('DOMContentLoaded', () => {
    // Component initialization
    // Event listeners
    // State management
  });
}
```




## Production System Maintenance

### Component Documentation
- **Example Components Showcase**: Create `/src/pages/dev/components-all/index.astro`
- **Prod Components Showcase**: Create `/src/pages/dev/prod-components/index.astro`
- **Individual Pages**: Create `/src/pages/dev/components-pages/`
- **Production Pages**: Create `/src/pages/prod/`

### Version Control
- **Component Updates**: Maintain backward compatibility
- **Design Token Changes**: Update all affected components
- **Breaking Changes**: Document in changelog and migration guide

### Quality Assurance
- **Visual Testing**: Test across all breakpoints and devices
- **Accessibility Testing**: Screen reader and keyboard navigation testing
- **Performance Testing**: CSS bundle size and rendering performance
- **Cross-browser Testing**: Ensure consistent behavior across browsers

## Production System Expansion

### Adding New Components
1. **Design Phase**: Define component purpose and visual requirements
2. **Development Phase**: Create Astro component with SCSS styling (see `/src/components/AGENTS.md`)
3. **Documentation Phase**: Add to component showcase and create usage examples
4. **Testing Phase**: Verify responsive behavior and accessibility
5. **Integration Phase**: Import into main SCSS and add to navigation

### Design Token Updates
- **Color Palette**: Maintain brand consistency across all components
- **Typography Scale**: Ensure readable and accessible text hierarchy
- **Spacing System**: Maintain visual rhythm and consistency
- **Breakpoint System**: Support new device requirements

### Pattern Evolution
- **Component Patterns**: Evolve based on usage and feedback
- **Layout Patterns**: Adapt to new content requirements
- **Interaction Patterns**: Improve user experience and accessibility
- **Visual Patterns**: Maintain brand identity while improving aesthetics