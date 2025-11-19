# Homepage Mockup Alternatives

This project includes 3 different homepage layout alternatives for the Synetica website, all using the tweakcn Graphite theme.

## Quick Start

1. **Install dependencies:**
   ```bash
   npm install
   ```

2. **Build Tailwind CSS:**
   ```bash
   npm run build
   ```

3. **Start Hugo development server:**
   ```bash
   hugo server
   ```

4. **View the alternatives:**
   - Comparison page: http://localhost:1313/
   - Alternative 1: http://localhost:1313/alternative-1/
   - Alternative 2: http://localhost:1313/alternative-2/
   - Alternative 3: http://localhost:1313/alternative-3/

## Layout Alternatives

### Alternative 1: Centered Hero
- **File:** `layouts/index/alternative1.html`
- **Characteristics:** Symmetrical, balanced layout with centered elements
- **Structure:** Full-width hero, two-column grids, centered sections

### Alternative 2: Asymmetric Split
- **File:** `layouts/index/alternative2.html`
- **Characteristics:** Dynamic, modern feel with asymmetric balance
- **Structure:** Split-screen hero, alternating left-right sections, offset positioning

### Alternative 3: Card-Based Modular
- **File:** `layouts/index/alternative3.html`
- **Characteristics:** Modular, component-based approach
- **Structure:** Card overlays, grid-based sections, masonry layouts

## Theme

All alternatives use the **tweakcn Graphite theme** with:
- CSS variables in `static/css/theme.css`
- Tailwind config in `tailwind.config.js`
- shadcn/ui component patterns

## Shared Components

- **Navigation:** `layouts/partials/nav.html`
- **Footer:** `layouts/partials/footer.html`
- **Base Layout:** `layouts/_default/baseof.html`

## Development

- **Watch mode for CSS:** `npm run dev` (runs Tailwind in watch mode)
- **Build CSS:** `npm run build` (minified production build)
- **Hugo server:** `hugo server` (with auto-reload)

## File Structure

```
/
├── layouts/
│   ├── _default/
│   │   └── baseof.html          # Base layout
│   ├── index/
│   │   ├── alternative1.html    # Alt 1 layout
│   │   ├── alternative2.html    # Alt 2 layout
│   │   ├── alternative3.html   # Alt 3 layout
│   │   └── list.html           # Comparison page
│   ├── partials/
│   │   ├── nav.html            # Navigation
│   │   ├── footer.html         # Footer
│   │   └── homepage/
│   │       ├── alternative1.html
│   │       ├── alternative2.html
│   │       └── alternative3.html
│   └── alternative-1/
│       └── single.html
│   └── alternative-2/
│       └── single.html
│   └── alternative-3/
│       └── single.html
├── content/
│   ├── _index.md               # Main homepage (comparison)
│   └── alternative-1/
│       └── _index.md
│   └── alternative-2/
│       └── _index.md
│   └── alternative-3/
│       └── _index.md
└── static/
    └── css/
        ├── theme.css           # Tweakcn Graphite theme variables
        ├── input.css           # Tailwind input
        └── main.css            # Compiled CSS
```

## Notes

- All three alternatives use the same content from the homepage content structure
- The layouts are fully responsive (mobile-first design)
- All alternatives share the same navigation and footer components
- The tweakcn Graphite theme provides consistent styling across all alternatives

