# DESIGN SYSTEM AGENTS.md

## Design System Overview
This document provides a **blueprint for setting up a design system** for the project. It contains high-level design principles, visual guidelines, and system architecture. For component development workflow, see `/src/components/AGENTS.md`. For SCSS implementation rules, see `/src/scss/AGENTS.md`.

This document provides a blueprint for setting up a comprehensive design system for brand websites with consistent visual language, component patterns, and design tokens. The system will be built on Astro components with SCSS styling and follow established design principles.

## Design System Page Styling Rules

### Bootstrap-Based Styling
**CRITICAL RULE**: Design system pages (`/src/pages/dev/design-system/`) must use Bootstrap classes for styling, NOT custom CSS.

**Why**: Bootstrap is already imported in `DevLayout.astro` and provides consistent, professional styling for design system documentation.

**Implementation Requirements**:
- **Layout**: Use Bootstrap grid system (`row`, `col-*`, `container`)
- **Spacing**: Use Bootstrap spacing utilities (`py-5`, `mb-5`, `me-2`, `mb-2`)
- **Typography**: Use Bootstrap typography classes (`display-4`, `h3`, `h6`, `lead`)
- **Components**: Use Bootstrap components (`card`, `card-header`, `card-body`)
- **Utilities**: Use Bootstrap utility classes (`border`, `rounded`, `p-3`, `d-flex`, `gap-2`)
- **Responsive**: Leverage Bootstrap's responsive grid (`col-md-6 col-lg-4`)

**What NOT to do**:
- ❌ Don't add custom `<style>` blocks
- ❌ Don't create custom CSS classes for layout
- ❌ Don't use custom color variables or spacing
- ❌ Don't add custom media queries

**What TO do**:
- ✅ Use Bootstrap classes for all styling needs
- ✅ Leverage Bootstrap's responsive behavior
- ✅ Use Bootstrap's spacing and typography scale
- ✅ Keep custom classes only for component demonstrations (e.g., `.btn--primary`)

**Example Structure**:
```astro
<div class="container py-5">
  <div class="row">
    <div class="col-12">
      <h1 class="display-4 mb-3">Component Name</h1>
      <p class="lead text-muted mb-5">Description</p>
    </div>
  </div>
  
  <div class="row mb-5">
    <div class="col-12">
      <div class="card">
        <div class="card-header">
          <h2 class="h3 mb-0">Section Title</h2>
        </div>
        <div class="card-body">
          <div class="row g-4">
            <div class="col-md-6">
              <div class="border rounded p-3">
                <h4 class="h6 mb-3">Example Title</h4>
                <!-- Component examples here -->
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</div>
```

## Design System Architecture

// ... existing code ...
