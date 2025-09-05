# PROD COMPONENTS SHOWCASE AGENTS.md

## Purpose and Overview
This directory contains the **production components showcase page** that displays all production-ready components in one comprehensive view. This page serves as a central hub for reviewing and testing all prod components together.

## Page Structure

### Location
- **Path**: `/src/pages/dev/prod-components/index.astro`
- **URL**: `/dev/prod-components/`
- **Layout**: Uses `DevLayout` (this is a development/presentation page)

### Purpose
- **Component Gallery**: Visual showcase of all production components
- **Quick Testing**: Allows developers to see all prod components in action
- **Documentation Hub**: Links to individual component test pages
- **Quality Assurance**: Enables comprehensive visual testing

## Implementation Guidelines

### Component Listing Rules
- **List ALL prod components** from `/src/components/prod/` directory
- **Link to test pages** in `/src/pages/dev/components-pages/`
- **Include component previews** by importing and displaying actual components
- **Maintain consistent styling** with the existing example components showcase

### Required Elements
```astro
---
// Import DevLayout for development pages
import DevLayout from '../../../layouts/DevLayout.astro';

// Import ALL prod components
import Clients from '../../../components/prod/Clients.astro';
import Testimonial from '../../../components/prod/Testimonial.astro';
// ... other prod components
---

<DevLayout>
  <!-- Page header -->
  <div class="container py-5">
    <h1 class="display-4 mb-4 text-center">Production Components</h1>
    <p class="lead text-center text-muted mb-5">
      Production-ready components for brand websites
    </p>
  </div>

  <!-- Component sections with links -->
  <!-- Each component gets its own section with:
       1. Title with link to test page
       2. Live component preview
  -->
</DevLayout>
```

### Styling Guidelines
- **Reuse existing styles** from `/dev/components-all/index.astro`
- **Consistent component sections** with proper spacing
- **Link styling** with hover effects and external link icons
- **Responsive layout** using Bootstrap grid system

## Maintenance Rules

### Adding New Prod Components
When a new production component is added:
1. **Add import** statement for the new component
2. **Create component section** following the established pattern
3. **Add link** to the component's test page
4. **Test the showcase page** to ensure proper display

### Component Organization
- **Alphabetical order** for component imports and sections
- **Consistent naming** matching the component file names
- **Proper links** to corresponding test pages in `/dev/components-pages/`

## Navigation Integration

### DevNav Updates
The DevNav component should include a link to this showcase page:
- **Location**: Under "Dev Pages" dropdown
- **Label**: "Prod Components"
- **URL**: `/dev/prod-components/`

### Cross-References
- **Example Components**: Link to `/dev/components-all/` for comparison
- **Design System**: Link to design system documentation
- **Individual Pages**: Links to each component's test page

## Quality Standards

### Visual Consistency
- **Match example showcase styling** for familiar user experience
- **Proper spacing** between component sections
- **Clear visual hierarchy** with consistent typography
- **Responsive behavior** across all device sizes

### Performance
- **Efficient imports** - only import components that are displayed
- **Lazy loading** if needed for large number of components
- **Optimized CSS** using existing styles where possible

### Accessibility
- **Proper heading structure** (h1, h2, h3 hierarchy)
- **Descriptive link text** for component test pages
- **Alt text** for any icons or images
- **Keyboard navigation** support for all interactive elements

## Usage Context

### Target Users
- **Developers**: Quick overview of available prod components
- **Designers**: Visual reference for component capabilities
- **Project Managers**: Component inventory and progress tracking
- **QA Teams**: Comprehensive testing environment

### Development Workflow Integration
- **Component Development**: Test new components in isolation and in context
- **Design Reviews**: Present all components for stakeholder approval
- **Documentation**: Central reference for component capabilities
- **Testing**: Verify component compatibility and visual consistency