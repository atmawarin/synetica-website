# Figma Make Implementation Guide for Synetica Website

> **Purpose:** Step-by-step guide for using Figma Make to transform the UX Design Specification into functional prototypes and web apps

## What is Figma Make?

Figma Make is an AI-powered, prompt-to-app tool that transforms Figma designs into functional prototypes, web apps, and interactive UI. Through conversation, you can:

- Turn your UX design specification into working prototypes
- Preview designs in functional form
- Iterate and improve through AI-powered conversations
- Publish functional prototypes as websites with dedicated URLs

**Key Features:**
- Attach existing Figma designs, components, and Community content to prompts
- Point to specific parts of the preview to improve
- Collaborate with your team in conversations
- Share and publish functional prototypes

**Access:** Available for Full seats on paid Figma plans. Can be tried on other seats and plans.

---

## Prerequisites

1. **Figma Account:** Paid plan with Full seat access (or trial access)
2. **UX Design Specification:** `docs/ux-design-specification.md` (completed)
3. **Design Direction Mockup:** `docs/ux-design-directions.html` (reference)
4. **Figma Desktop App:** For best experience with MCP integration

---

## Implementation Strategy

### Phase 1: Create Base Figma Design File

**Step 1.1: Set Up Figma File**
1. Open Figma Desktop App
2. Create new Figma file: "Synetica Website - Design System"
3. Set up frames for key screens:
   - Desktop: 1440px width
   - Tablet: 768px width
   - Mobile: 375px width

**Step 1.2: Apply Design System**
1. Import or create color styles from Graphite theme:
   - Primary: `oklch(0.4891 0 0)`
   - Background: `oklch(0.9551 0 0)`
   - Foreground: `oklch(0.3211 0 0)`
   - All other colors from specification
2. Set up typography styles:
   - Heading: Montserrat (700, 600, 500 weights)
   - Body: Montserrat (400 weight)
   - Accent: Georgia (400, 700 weights)
3. Create component library based on shadcn/ui patterns

**Step 1.3: Design Key Screens**
Create high-fidelity designs for:
- Homepage (Hero, Framework, Case Studies)
- Framework Detail Page
- Case Study Detail Page
- Contact/Consultation Page

---

## Phase 2: Using Figma Make

### Step 2.1: Create Figma Make File

1. In Figma, go to **File → New → Make File**
2. Or use the Figma Make interface directly
3. This creates a new Make file where you can prompt-to-code

### Step 2.2: Initial Prompt Strategy

**Prompt Template for Homepage:**

```
Create a functional prototype for the Synetica website homepage based on this UX specification:

Design Direction: Credibility-First Dashboard
- Top horizontal navigation with logo, Services/Case Studies/About/Contact links, and "Workflow Demo" CTA button
- Hero section with:
  * Client logos (Traveloka, Angkasa Pura, Astra) prominently displayed
  * Headline: "Launch your product in 8 weeks or less"
  * Tagline: "From idea to traction — within 8 weeks"
  * Description text
  * Primary CTA: "See How We Work"
- 2B2G Framework section with 4 cards (Blueprint, Build & Benchmark, Go To Market, Grow)
- Case Studies section with 3 client cards
- Footer with contact information

Design System:
- Colors: Graphite theme (oklch color space)
- Typography: Montserrat for headings/body, Georgia for accents
- Spacing: 4px base unit
- Components: shadcn/ui style with Graphite theme

Requirements:
- Responsive (mobile-first)
- WCAG AA accessible
- Non-salesy, professional tone
- Clean, minimal aesthetic matching meter.com inspiration
```

### Step 2.3: Attach Design Context

**Option A: Attach Figma Design File**
1. In Figma Make conversation, attach your Figma design file
2. Reference specific frames/components
3. AI will use design as visual reference

**Option B: Reference UX Specification**
1. Upload or reference `docs/ux-design-specification.md`
2. Point to specific sections (Design Direction, Components, etc.)
3. AI will use specification as context

**Option C: Use Design Direction Mockup**
1. Reference `docs/ux-design-directions.html`
2. Use as visual guide for layout and structure

### Step 2.4: Iterative Refinement

**Example Refinement Prompts:**

```
1. "Make the client logos more prominent in the hero section"
2. "Add hover effects to the framework cards with smooth transitions"
3. "Implement the expandable framework details component"
4. "Add mobile hamburger menu for navigation"
5. "Style the consultation form modal with proper validation"
```

**Pointing to Specific Parts:**
- Click on elements in the preview
- Reference them in prompts: "Make this button larger" or "Change the color of this section"

---

## Phase 3: Component Implementation

### Step 3.1: Framework Phase Card Component

**Prompt:**
```
Create a reusable Framework Phase Card component with:
- Icon/emoji at top (🧠, ⚙️, 📣, 📈)
- Phase title (e.g., "Blueprint")
- Timeline badge (e.g., "2 weeks")
- Brief description
- Expandable section that shows full details on click
- "Learn More" link to dedicated page

States: Default, Hover, Expanded
Accessibility: ARIA expanded state, keyboard navigation
```

### Step 3.2: Case Study Card Component

**Prompt:**
```
Create a Case Study Card component with:
- Client name/logo
- Industry tag
- Brief description
- "Read Full Story" link

Variants: Grid card, Featured card, Compact card
Hover effect: Subtle shadow elevation
```

### Step 3.3: Consultation CTA Button

**Prompt:**
```
Create a Consultation CTA Button component with:
- Text: "Workflow Demo" or "See How We Work"
- Primary style: Medium gray background (oklch(0.4891 0 0)) with white text
- Hover: Slight opacity change
- Variants: Primary, Secondary, Ghost

Must feel non-salesy and approachable
```

### Step 3.4: Navigation Component

**Prompt:**
```
Create a responsive Navigation component:
- Desktop: Horizontal nav with logo, links, CTA button
- Mobile: Hamburger menu icon, slide-out drawer
- Active state: Underline or subtle background
- Sticky header on scroll
```

---

## Phase 4: User Journey Implementation

### Step 4.1: Understanding Journey (Homepage)

**Prompt:**
```
Implement the "Understanding Synetica" user journey:
- Hero section with client logos and value proposition
- Framework overview cards (expandable on click)
- Smooth scroll to framework section
- Optional: Navigate to dedicated framework page

Use hybrid approach: Main content on homepage with expandable sections + optional deep-dive pages
```

### Step 4.2: Credibility Verification Journey

**Prompt:**
```
Implement the "Verifying Credibility" journey:
- Client logos prominently displayed
- Case study cards with click-to-expand or navigate to full page
- Credentials section (ISO 27001, AWS Partner, team expertise)
- Smooth transitions between sections
```

### Step 4.3: Consultation Request Journey

**Prompt:**
```
Implement the consultation request flow:
- "Workflow Demo" button opens modal or navigates to contact page
- Simple form: Name, Email, Company, Message
- WhatsApp alternative button
- Form validation with inline error messages
- Success confirmation toast notification
```

---

## Phase 5: Responsive Implementation

### Step 5.1: Breakpoint Implementation

**Prompt:**
```
Implement responsive breakpoints:
- Mobile: 0-768px (single column, hamburger menu)
- Tablet: 768-1024px (2-column grids)
- Desktop: 1024px+ (multi-column grids)

Adapt:
- Navigation: Horizontal → Hamburger
- Framework cards: 4 columns → 2 columns → 1 column
- Case studies: 3 columns → 2 columns → 1 column
- Hero: Horizontal logos → Stacked logos
```

### Step 5.2: Mobile Optimization

**Prompt:**
```
Optimize for mobile:
- Touch targets minimum 44x44px
- Adequate spacing between interactive elements
- Full-width forms on mobile
- Full-screen modals on small devices
- Optimize images for mobile networks (WebP, lazy loading)
```

---

## Phase 6: Accessibility Implementation

### Step 6.1: WCAG AA Compliance

**Prompt:**
```
Implement WCAG AA accessibility:
- All interactive elements keyboard accessible
- Visible focus indicators (oklch(0.4891 0 0) ring)
- ARIA labels on all interactive elements
- Proper heading hierarchy (h1 → h2 → h3)
- Alt text for all images
- Form labels properly associated
- Skip to main content link
- Color contrast meets 4.5:1 for normal text, 3:1 for large text
```

### Step 6.2: Screen Reader Support

**Prompt:**
```
Add screen reader support:
- ARIA roles: button, navigation, article, region
- ARIA expanded states for framework cards
- Descriptive labels for all actions
- Announce state changes (expanded/collapsed)
```

---

## Phase 7: Performance Optimization

### Step 7.1: Load Time Optimization

**Prompt:**
```
Optimize for Indonesian mobile networks (sub-3 second load):
- Lazy load images below the fold
- Use WebP format with fallbacks
- Inline critical CSS
- Preload Montserrat and Georgia fonts
- Minimize JavaScript bundle
- Optimize images (responsive srcset)
```

---

## Phase 8: Publishing and Sharing

### Step 8.1: Publish Prototype

1. In Figma Make, click **Publish**
2. Get dedicated URL for your functional prototype
3. Share with team for feedback
4. Test on different devices and networks

### Step 8.2: Iterate Based on Feedback

1. Collect feedback from team/stakeholders
2. Use refinement prompts to improve
3. Point to specific elements that need changes
4. Republish updated version

---

## Best Practices

### Prompting Tips

1. **Be Specific:** Reference exact colors, spacing, typography from specification
2. **Reference Components:** "Use the Framework Phase Card component we created earlier"
3. **Iterate Incrementally:** Make small changes, test, then refine
4. **Use Visual References:** Attach Figma designs or reference HTML mockup
5. **Test Responsively:** Always check mobile, tablet, desktop views

### Collaboration

1. **Share Conversations:** Team members can join Make conversations
2. **Simultaneous Editing:** Multiple people can modify generated code
3. **Version Control:** Keep track of iterations and decisions

### Integration with Development

1. **Export Code:** Figma Make generates React/HTML/CSS code
2. **Code Review:** Review generated code before production use
3. **Design System Sync:** Ensure Make output aligns with shadcn/ui + Graphite theme
4. **Hugo Integration:** Adapt Make output for Hugo static site structure

---

## Troubleshooting

### Common Issues

**Issue: Design doesn't match specification**
- **Solution:** Attach UX specification document, reference specific sections
- **Solution:** Use more detailed prompts with exact values

**Issue: Components not consistent**
- **Solution:** Create components first, then reference them in prompts
- **Solution:** Use "Use the [Component Name] component we created" in prompts

**Issue: Responsive behavior not working**
- **Solution:** Explicitly request breakpoint implementation
- **Solution:** Test on different screen sizes and refine

**Issue: Accessibility not meeting standards**
- **Solution:** Explicitly request WCAG AA compliance in prompts
- **Solution:** Test with keyboard navigation and screen readers

---

## Next Steps After Figma Make

1. **Code Review:** Review generated code for quality and consistency
2. **Hugo Integration:** Adapt code for Hugo static site structure
3. **Component Library:** Extract reusable components
4. **Testing:** Test on real devices, especially Indonesian mobile networks
5. **Performance Audit:** Run Lighthouse, optimize further if needed
6. **Accessibility Audit:** Run axe DevTools, fix any issues
7. **Content Integration:** Add actual content (case studies, framework details)
8. **Deployment:** Deploy to Netlify/Vercel with Hugo build

---

## Resources

- [Figma Make Documentation](https://help.figma.com/hc/en-us/articles/31304485164695)
- [Figma MCP Server](https://developers.figma.com/docs/figma-mcp-server) - For AI agent integration
- [UX Design Specification](./ux-design-specification.md) - Complete design reference
- [Design Direction Mockup](./ux-design-directions.html) - Visual reference
- [Tweakcn Graphite Theme](https://tweakcn.com/editor/theme?theme=graphite) - Color system reference

---

## Example Complete Prompt

Here's a comprehensive prompt you can use to get started:

```
Create a functional prototype for the Synetica website homepage based on the attached UX design specification.

Key Requirements:
1. Design Direction: Credibility-First Dashboard
2. Design System: shadcn/ui with Tweakcn Graphite theme
3. Typography: Montserrat (headings/body), Georgia (accents)
4. Responsive: Mobile-first, 3 breakpoints (mobile/tablet/desktop)
5. Accessibility: WCAG AA compliant

Sections to implement:
- Top navigation (horizontal, hamburger on mobile)
- Hero with client logos, headline, CTA
- 2B2G Framework cards (4 phases, expandable)
- Case studies section (3 cards)
- Footer

Components needed:
- Framework Phase Card (expandable)
- Case Study Card
- Consultation CTA Button
- Navigation (responsive)

Make it feel professional, trustworthy, and non-salesy. Optimize for fast loading on mobile networks.
```

---

_This guide provides a structured approach to using Figma Make to implement the Synetica website UX design. Adjust prompts based on your specific needs and iterate as you refine the prototype._

