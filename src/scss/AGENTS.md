# SCSS AGENTS.md

## SCSS Architecture Overview
This document contains **SCSS-specific implementation rules** for the project. It focuses purely on SCSS architecture, BEM methodology, and styling patterns. For component development workflow, see `/src/components/AGENTS.md`. For design system setup, see `/src/pages/prod/AGENTS.md`.

This project uses a modular SCSS architecture with component-driven styling, following BEM methodology and organized into logical layers for maintainability and scalability.

## File Structure & Organization

### Directory Layout
```scss
src/scss/
├── main.scss              # Main entry point - imports all SCSS files
├── base/                  # Base styles and resets
│   ├── _fonts.scss       # Font declarations and @font-face rules
│   ├── _normalize.scss   # CSS reset/normalize
│   ├── _typography.scss  # Typography system and text styles
│   └── _globals.scss     # Global styles and element defaults
├── layout/                # Layout and structural styles
│   ├── _container.scss   # Container and wrapper styles
│   └── _section.scss     # Section and content area styles
├── components/            # Component-specific styles
│   ├── _buttons.scss     # Button component styles
│   ├── _example-hero.scss # Example hero component
│   ├── _example-slider.scss # Example slider component
│   └── ...               # Other component styles
├── utils/                 # Utilities and variables
│   └── _variables.scss   # Design tokens and breakpoints
└── vendors/               # Third-party library styles
```

## Import Order & Dependencies

### Main SCSS Import Sequence
```scss
// 1. UTILS (variables, mixins, functions)
@use "./utils/variables" as *;

// 2. VENDORS (third-party libraries)
// @use "./vendors/library-name";

// 3. BASE (foundational styles)
@use "./base/fonts";
@use "./base/normalize";
@use "./base/typography";
@use "./base/globals";

// 4. LAYOUT (structural styles)
@use "./layout/container";
@use "./layout/section";

// 5. COMPONENTS (UI components)
@use 'components/buttons';
@use 'components/example-hero';
// ... other components
```

**CRITICAL**: Maintain this exact import order - variables must be loaded first, base styles before layout, layout before components.

## SCSS Conventions & Best Practices

### File Naming
- Use kebab-case: `_example-hero.scss`
- Prefix with underscore: `_filename.scss`
- Match component names exactly: `ExampleHero.astro` → `_example-hero.scss`

### Import Statements
- **ALWAYS** use `@use` instead of `@import`
- Use relative paths from the importing file
- Import order matters - follow the established sequence

### Variable Access & Imports
- **ALL files** that use variables must import them: `@use "../utils/variables" as *;`
- **Layout files** need to import variables: `@use "../utils/variables" as *;`
- **Component files** need to import variables: `@use "../utils/variables" as *;`
- **Base files** need to import variables: `@use "../utils/variables" as *;`
- **Utils files** are imported first in main.scss but NOT automatically available to other files
- **Critical**: If a file uses variables like `$md`, `$lg`, etc., it MUST import variables with `@use "../utils/variables" as *;`
- **Import order in main.scss** only determines compilation order, not variable availability

### BEM Methodology
Follow strict BEM naming convention:
```scss
.block {
  // Block styles
  
  &__element {
    // Element styles
    
    &--modifier {
      // Modifier styles
    }
  }
  
  &--modifier {
    // Block modifier
  }
}
```

**Examples from codebase:**
```scss
.example-hero {
  &__title-line {
    &--highlight { }
  }
  
  &__bg-shape {
    &--1 { }
    &--2 { }
    &--3 { }
  }
}
```

## Design System & Variables

### Breakpoints (Customizable Values)
```scss
// Define your own breakpoints based on your design needs
$xs: 0;
$sm: 576px;      // Small devices
$md: 768px;      // Medium devices (tablets)
$lg: 992px;      // Large devices (desktops)
$xl: 1200px;     // Extra large devices
$xxl: 1400px;    // Extra extra large devices
```

**Note**: Adjust these values based on your specific design requirements and device testing.

### Typography System
The typography system is implemented directly in `_typography.scss` with values embedded from your design system. This approach keeps typography self-contained and easier to maintain.

#### Typography Implementation Philosophy
- **Self-contained**: Typography values are embedded directly in `_typography.scss`
- **No abstraction**: Direct pixel values from your design system (Figma, Sketch, etc.)
- **Easy maintenance**: All typography rules in one file
- **Mobile-first**: Base styles are mobile, desktop styles are progressive enhancements
- **Nested media queries**: Responsive behavior is nested within each typography class
- **Clean inheritance**: Text color set at body level, typography classes inherit naturally
- **No redundancy**: Eliminated duplicate color declarations throughout typography classes
- **CSS custom properties**: Colors are defined as CSS variables for easy theming

#### Typography Classes Structure (Customize for Your Project)
```scss
// Headlines (Mobile-First with Progressive Enhancement)
.h1, h1          // Define your own sizes and weights
.h2, h2          // Mobile: smaller, Desktop: larger
.h3, h3          // Use your design system values
.h4, h4          // Maintain consistent hierarchy

// Body Text (Fixed sizes, no responsive scaling)
.body-1          // Primary body text size
.body-1-medium   // Medium weight variant
.body-2          // Secondary body text size
.body-2-medium   // Medium weight variant
.body-3          // Small body text size
.body-3-medium   // Medium weight variant
.body-4          // Caption/small text size
.body-4-medium   // Medium weight variant

// Utility Classes (Override default text color)
.text-primary    // Your primary brand color
.text-secondary  // Your secondary text color
.text-muted      // Your muted text color
.text-dark       // Your dark text color
.text-info       // Your info color
.text-success    // Your success color
.text-warning    // Your warning color
.text-error      // Your error color
.tracking-tight  // Your letter-spacing value
```

#### Typography Color Strategy
```scss
body {
  color: var(--color-text-primary); // Uses CSS custom property
}

// Typography classes inherit color automatically
.h1, h1 {
  font-size: your-size;
  font-weight: your-weight;
  // color inherited from body
}

// Utility classes override color when needed
.text-primary {
  color: var(--color-primary); // Uses CSS custom property
}
```

### Color System
The color system is implemented using CSS custom properties (variables) defined at the `:root` level in `_globals.scss`. This approach provides flexibility for theming and runtime color changes.

#### Color Implementation Philosophy
- **CSS custom properties**: Colors defined as `--color-*` variables
- **Semantic naming**: Colors named by purpose, not appearance
- **Centralized definition**: All colors defined in one place
- **Easy theming**: Simple to create dark/light mode variations
- **Runtime flexibility**: Colors can be changed via JavaScript
- **Design system integration**: Colors extracted directly from Figma/Sketch

#### Color Categories Available
```scss
// Brand Colors
--color-primary: #your-primary-color;           // Main brand color
--color-secondary: #your-secondary-color;       // Secondary brand color
--color-info: #your-info-color;                 // Information color
--color-primary-blue: #your-blue-color;         // Primary blue accent

// Neutral Colors
--color-black: #your-black-color;               // Primary text color
--color-dark-grey: #your-dark-grey;            // Dark grey text
--color-grey: #your-grey-color;                // Medium grey text
--color-light-grey: #your-light-grey;          // Light grey text
--color-grey-blue: #your-grey-blue;            // Grey-blue accent
--color-silver: #your-silver-color;            // Light background
--color-white: #your-white-color;               // Pure white

// Color Shades (Darker variants)
--color-shade-1: #your-shade-1;                // 10% darker
--color-shade-2: #your-shade-2;                // 20% darker
--color-shade-3: #your-shade-3;                // 30% darker
--color-shade-4: #your-shade-4;                // 40% darker
--color-shade-5: #your-shade-5;                // 50% darker

// Color Tints (Lighter variants)
--color-tint-1: #your-tint-1;                  // 10% lighter
--color-tint-2: #your-tint-2;                  // 20% lighter
--color-tint-3: #your-tint-3;                  // 30% lighter
--color-tint-4: #your-tint-4;                  // 40% lighter
--color-tint-5: #your-tint-5;                  // 50% lighter

// Action Colors
--color-warning: #your-warning-color;           // Warning state
--color-error: #your-error-color;               // Error state
--color-success: #your-success-color;           // Success state

// Semantic Color Mappings
--color-text-primary: var(--color-black);       // Primary text
--color-text-secondary: var(--color-light-grey); // Secondary text
--color-text-muted: var(--color-grey);          // Muted text
--color-bg-primary: var(--color-white);         // Primary background
--color-bg-secondary: var(--color-silver);      // Secondary background
--color-border-light: var(--color-grey-blue);   // Light borders
```

#### Using Colors in Your SCSS
```scss
.component {
  // Use semantic color variables
  background-color: var(--color-bg-primary);
  color: var(--color-text-primary);
  border: 1px solid var(--color-border-light);
  
  // Use specific brand colors
  &--primary {
    background-color: var(--color-primary);
    color: var(--color-white);
  }
  
  // Use action colors
  &--success {
    background-color: var(--color-success);
    color: var(--color-white);
  }
}
```

**Key Benefits:**
- **Mobile-first**: Base styles are optimized for mobile devices
- **Progressive enhancement**: Desktop gets larger, more prominent typography
- **Nested structure**: Each class contains its own responsive behavior
- **Maintainable**: Easy to see mobile vs desktop styles in one place
- **Clean inheritance**: No redundant color declarations
- **DRY principle**: Text color defined once at body level
- **Flexible theming**: CSS custom properties enable easy color changes
- **Design system integration**: Colors directly from your design tools

### Usage Guidelines
- **ALWAYS** use variables from `_variables.scss` for breakpoints
- **Use typography classes** from `_typography.scss` for consistent text styling
- Don't hardcode pixel values for responsive breakpoints
- Use semantic variable names that describe purpose, not appearance
- **Customize all values** to match your project's design system

## Component SCSS Structure

### Standard Component Template
```scss
// ==========================================================================
// Component Name
// ==========================================================================

.component-name {
  // Base styles
  
  &__element {
    // Element styles
  }
  
  &--modifier {
    // Modifier styles
  }
  
  // Responsive styles
  @media (min-width: $md) {
    // Medium+ styles
  }
  
  @media (min-width: $lg) {
    // Large+ styles
  }
}
```

*Note: For component-specific patterns and examples, see `/src/components/AGENTS.md`*

## Responsive Design Patterns

### Mobile-First Approach
```scss
.component {
  // Mobile styles (default)
  
  @media (min-width: $md) {
    // Desktop styles
  }
  
  @media (min-width: $lg) {
    // Large desktop styles
  }
}
```

### Breakpoint Usage
- Start with mobile styles as base
- Use `min-width` media queries for progressive enhancement
- Test across all breakpoints: `$xs`, `$sm`, `$md`, `$lg`, `$xl`, `$xxl`
- **Customize breakpoints** based on your content and design needs

## SCSS Features & Techniques

### Nesting
- Limit nesting to 3 levels maximum
- Use `&` for pseudo-classes and modifiers
- Keep selectors readable and maintainable

### Variables & Mixins
- Define reusable values in `_variables.scss` (breakpoints, global tokens)
- **Typography values are embedded directly** in `_typography.scss`
- Create mixins for repeated patterns
- Use semantic names: `$primary-color`, not `$blue`
- **Customize all variable names** to match your project's terminology

### Animations & Transitions
- Define keyframes at component level
- Use consistent timing functions: `ease-out`, `ease-in-out`
- Keep animations performant with `transform` and `opacity`

## File Creation & Maintenance

### Adding New SCSS Files
1. Create `_filename.scss` in appropriate directory
2. Follow the standard SCSS template structure
3. Import in `main.scss` following the established order
4. Use BEM methodology consistently
5. Include responsive styles for all breakpoints

### Updating Existing SCSS
- Maintain existing BEM structure
- Don't change class names without updating HTML
- Test responsive behavior across all breakpoints
- Ensure SCSS compiles without errors

### Typography Updates
- **All typography changes** go in `_typography.scss`
- Update values directly from your design system
- Test typography classes in design system pages
- Ensure responsive scaling works correctly
- **Use nested media queries** for responsive behavior
- **Text color changes** go in body selector, not individual classes
- **Customize all values** to match your project's needs

## Quality Standards

### Code Quality
- No unused SCSS rules
- Consistent indentation (2 spaces)
- Proper commenting for complex sections
- Semantic class names that describe purpose

### Performance
- Minimize CSS output size
- Use efficient selectors
- Avoid overly specific selectors
- Leverage CSS Grid and Flexbox for layouts

### Accessibility
- Maintain proper color contrast ratios
- Ensure focus states are visible
- Support reduced motion preferences
- Test with screen readers

## Project Customization

### What to Customize
- **Breakpoint values**: Adjust to your design needs
- **Typography sizes**: Use your design system values
- **Color values**: Replace with your brand colors
- **Font families**: Use your chosen fonts
- **Class names**: Adapt to your naming conventions
- **Component examples**: Replace with your actual components

### What to Keep
- **File structure**: The modular organization pattern
- **Import order**: The dependency management approach
- **BEM methodology**: The naming convention structure
- **Mobile-first approach**: The responsive design pattern
- **Nested media queries**: The SCSS organization technique
- **CSS custom properties**: The color system architecture
- **Semantic color naming**: The purpose-based color structure

### Color Customization
- **Replace all hex values** in `_globals.scss` with your brand colors
- **Maintain the semantic structure** (--color-primary, --color-text-primary, etc.)
- **Keep the CSS custom property approach** for flexibility
- **Update color swatches** in `/dev/design-system/colors-page` to match your palette
- **Test color contrast** for accessibility compliance
- **Consider dark mode** variations using the same variable structure

## Troubleshooting

### Common Issues
- **Import errors**: Check file paths and import order
- **Compilation failures**: Verify SCSS syntax and nesting
- **Missing styles**: Ensure component is imported in `main.scss`
- **Responsive issues**: Verify breakpoint variables are used correctly
- **Typography not working**: Check that `_typography.scss` is imported in `main.scss`

### Debugging
- Check browser dev tools for CSS conflicts
- Verify SCSS compilation in build output
- Test component isolation in dev pages
- Use browser responsive testing tools
- Test typography classes in your design system pages