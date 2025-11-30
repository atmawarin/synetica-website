# Synetica Website - Epics and User Stories

**Created:** 2025-01-27  
**Author:** PM Agent  
**Version:** 1.0  
**Status:** Ready for Implementation

---

## Overview

This document refines the PRD epics into detailed, implementation-ready user stories. Each story includes:
- Clear user perspective (As a...)
- Business value (so that...)
- Technical acceptance criteria aligned with architecture
- Language that matches Synetica's voice: sharp, direct, outcome-focused

**Language Guidelines Applied:**
- Direct statements, no fluff
- Outcome-first framing
- Validation over assumption
- Think in systems, write in steps
- Confident but grounded

---

## Epic 1: Foundation & Core Infrastructure

**Epic Goal:** Build the technical foundation that lets us ship fast and iterate. This isn't just setup—it's the system that makes everything else possible. We deliver a working site from day one, not a placeholder.

**Priority:** P0 (Critical Path)  
**Estimated Duration:** 2-3 weeks

---

### Story 1.1: Astro Site Setup and Configuration

**As a** developer building the Synetica website,  
**I want** a properly configured Astro static site with Tailwind CSS and shadcn/ui components,  
**so that** we have a fast, maintainable foundation that ships production-ready code from the first commit.

#### Acceptance Criteria

1. **Astro 4.x initialized** with minimal starter template (no unnecessary dependencies)
2. **astro.config.mjs configured** with:
   - Site URL: `https://synetica.com`
   - Sitemap generation enabled
   - Compression plugin for HTML/CSS/JS
   - Tailwind integration
3. **Content collections schema** defined in `src/content/config.ts`:
   - Case studies collection with required fields (title, client, industry, challenge, solution, outcome, techStack, publishDate)
   - Blog collection with required fields (title, description, author, publishDate, tags)
4. **Tailwind CSS 3.x configured** with:
   - JIT compilation enabled
   - Tweakcn Graphite theme tokens (OKLCH colors) mapped in `tailwind.config.mjs`
   - Geist Mono font family configured for monospace typography
   - Custom animations for logo marquee and fade-in effects
5. **shadcn/ui initialized** with base components:
   - Button, Card, Input, Textarea, Label (committed to `src/components/ui/`)
   - Components use Tailwind utilities, no runtime dependencies
6. **Project structure** matches architecture:
   - `src/components/` (ui/, layout/, sections/, forms/)
   - `src/layouts/` (BaseLayout, PageLayout, CaseStudyLayout)
   - `src/pages/` with proper routing structure
   - `src/content/` for markdown collections
   - `public/` for static assets
7. **Build validation:**
   - `npm run build` completes successfully
   - `npm run dev` serves site locally without errors
   - No console errors or warnings
8. **Git setup:**
   - `.gitignore` excludes `node_modules/`, `.astro/`, `dist/`
   - Initial commit includes all configuration files

#### Technical Notes

- Use Astro's content collections API for type-safe content
- Configure PostCSS for Tailwind processing
- Set up TypeScript for better DX (optional but recommended)
- Reference: `docs/architecture.md` section 2.1 for directory structure

---

### Story 1.2: Hosting Infrastructure and Deployment Pipeline

**As a** content manager updating the website,  
**I want** automated deployments that go live within minutes of pushing code,  
**so that** we can ship updates fast without manual deployment steps.

#### Acceptance Criteria

1. **Netlify account configured** with site connected to GitHub repository
2. **Build settings configured:**
   - Build command: `npm run build`
   - Publish directory: `dist`
   - Node version: 20
3. **Custom domain configured:**
   - `synetica.com` (or staging domain) with HTTPS enabled
   - DNS records properly configured
4. **Deployment pipeline:**
   - Automatic deployment on push to `main` branch
   - Deploy previews for pull requests
   - Build status visible in GitHub PRs
5. **netlify.toml configured** with:
   - Redirect rules (portfolio → case-studies, services → solutions)
   - Custom 404 page handling
   - Security headers (X-Frame-Options, CSP, etc.)
   - Cache headers for static assets (fonts, images, CSS, JS)
6. **Error handling:**
   - Custom 404 page at `src/pages/404.astro`
   - Build failures send notifications
7. **Deploy previews functional:**
   - PRs generate preview URLs
   - Preview URLs accessible for stakeholder review

#### Technical Notes

- Netlify automatically detects Astro projects
- Use Netlify's form handling for contact forms (Story 5.1)
- Reference: `docs/architecture.md` section 7.1 for Netlify configuration

---

### Story 1.3: Basic Analytics and Performance Monitoring

**As a** product manager measuring website performance,  
**I want** Google Analytics 4 and Search Console tracking from day one,  
**so that** we can measure traffic, conversions, and SEO performance from launch.

#### Acceptance Criteria

1. **Google Analytics 4 property created:**
   - Measurement ID configured as environment variable `PUBLIC_GA_MEASUREMENT_ID`
   - Data stream configured for web
2. **GA4 tracking code integrated:**
   - Analytics component created at `src/components/layout/Analytics.astro`
   - Component included in `BaseLayout.astro`
   - Page view tracking functional on all pages
3. **Search Console verified:**
   - Site ownership verified via HTML meta tag or DNS
   - Sitemap submitted (`/sitemap.xml`)
   - Basic property settings configured
4. **Performance monitoring:**
   - Lighthouse CI configured in GitHub Actions (optional)
   - Core Web Vitals tracking enabled in GA4
5. **Privacy compliance:**
   - Analytics respects user privacy (no PII collected)
   - Cookie consent banner (future: Story 5.5)
6. **Data validation:**
   - Real-time reports show page views
   - Events fire correctly (test with GA4 DebugView)

#### Technical Notes

- Use Astro's `import.meta.env.PUBLIC_*` for public env vars
- Analytics script loads asynchronously to avoid blocking
- Reference: `docs/architecture.md` section 4.1 for analytics integration

---

### Story 1.4: Mobile-First Responsive Framework

**As a** mobile user browsing from Indonesia,  
**I want** the website to load in under 3 seconds and work perfectly on my phone,  
**so that** I can explore Synetica's services without frustration.

#### Acceptance Criteria

1. **Mobile-first CSS:**
   - Tailwind breakpoints configured (sm: 640px, md: 768px, lg: 1024px, xl: 1280px)
   - All components use mobile-first utility classes
2. **Performance targets met:**
   - LCP < 2.5s on 3G connection (tested with Lighthouse mobile throttling)
   - TTI < 3s on mobile devices
   - Total page size < 500KB (HTML + CSS + JS + images)
   - CSS bundle < 50KB after Tailwind purging
3. **Responsive layout:**
   - Navigation converts to hamburger menu on mobile (< 768px)
   - Hero section stacks vertically on mobile
   - Grid layouts adapt (4-col → 2-col → 1-col)
   - Touch targets minimum 44x44px
4. **Cross-browser compatibility:**
   - Tested on Chrome, Safari, Firefox (latest versions)
   - No layout breaks or JavaScript errors
5. **Accessibility (WCAG AA):**
   - Color contrast ratios meet 4.5:1 (normal text) and 3:1 (large text)
   - Keyboard navigation functional (Tab, Enter, Space)
   - Focus indicators visible on all interactive elements
   - Screen reader tested (basic check with browser dev tools)
6. **Indonesian network optimization:**
   - Images optimized (WebP with fallbacks, responsive srcset)
   - Fonts use `font-display: swap` to prevent FOIT
   - Critical CSS inlined, non-critical CSS deferred

#### Technical Notes

- Use Astro's `<Image>` component for automatic optimization
- Test with Lighthouse mobile preset and throttled 3G
- Reference: `docs/architecture.md` section 5 for performance optimization

---

## Epic 2: Credibility-First Homepage & Trust Building

**Epic Goal:** Build a homepage that stops skeptical visitors. Lead with proof (client logos), then show the system (2B2G), then invite action. No fluff, no vague promises—just clear evidence that we deliver.

**Priority:** P0 (Critical Path)  
**Estimated Duration:** 2-3 weeks  
**Dependencies:** Epic 1 complete

---

### Story 2.1: Hero Section with Value Proposition

**As a** potential client visiting the Synetica website,  
**I want** to immediately understand what we do and see proof we've worked with serious companies,  
**so that** I can decide in seconds whether we're worth exploring further.

#### Acceptance Criteria

1. **Hero headline:**
   - Text: "What If You Could Launch a Validated Product in 8 Weeks?"
   - Typography: Geist Mono, bold, large (mobile: 2xl, desktop: 4xl)
   - Color: foreground (dark text on light background)
2. **Tagline:**
   - Text: "A real product tested by real users — ready to scale."
   - Typography: Geist Mono, medium weight, smaller than headline
   - Positioned directly below headline
3. **Subheadline:**
   - Text: "We're a tech-based business consultancy that helps you launch the right product—fast. Gain clarity, build what matters, validate early, and launch with confidence in just 8 weeks."
   - Typography: Geist Mono, regular weight, readable size
   - Max-width constrained for readability (mobile: full, desktop: ~700px)
4. **Visual design:**
   - Grid background pattern (subtle, blueprint-like aesthetic)
   - Monospace typography throughout (Geist Mono)
   - Clean, minimal layout with ample white space
   - No hero image (text-first approach)
5. **Call-to-action buttons:**
   - Primary: "See Our Process" (links to `/process`)
   - Secondary: "View Client Results" (links to `/case-studies`)
   - Button styles match shadcn/ui button component
   - Mobile: Stacked vertically, full width
   - Desktop: Horizontal layout
6. **Performance:**
   - Hero section LCP < 2.5s on mobile
   - No layout shift (CLS < 0.1)
   - Text visible immediately (no font loading delay)

#### Technical Notes

- Use `Hero.astro` component in `src/components/sections/`
- Grid background implemented via CSS (see `docs/architecture.md` section 3.3)
- CTA buttons track clicks via analytics (Story 1.3)
- Reference: `index.html` mockup for visual reference

---

### Story 2.2: Major Client Logo Display and Trust Indicators

**As an** Indonesian entrepreneur evaluating service providers,  
**I want** to see recognizable company names we've worked with,  
**so that** I can trust we have experience with serious businesses.

#### Acceptance Criteria

1. **Logo marquee section:**
   - Heading: "Trusted by Leading Companies Across Indonesia"
   - Typography: Geist Mono, medium weight, centered
   - Positioned below hero section, above case studies
2. **Client logos displayed:**
   - Traveloka logo (optimized image, WebP format)
   - Angkasa Pura logo
   - Astra logo
   - Logos grayscale by default, color on hover (if clickable)
3. **Logo optimization:**
   - Images optimized (WebP with PNG fallback)
   - Responsive sizing (mobile: smaller, desktop: larger)
   - Lazy loading for below-fold logos
   - Alt text: "{{Client Name}} logo"
4. **Credentials displayed:**
   - ISO 27001 certification badge
   - AWS Partner badge
   - Brief text: "ISO 27001 Certified • AWS Partner"
5. **Success metrics (optional):**
   - Brief stat: "80% of products we build reach market fit"
   - Or: "8 weeks average time to validated product"
6. **Interactive behavior:**
   - Logos link to relevant case studies when available
   - Smooth hover transitions (opacity or color change)
   - Infinite scroll animation for marquee (if multiple logos)

#### Technical Notes

- Use `TrustLogos.astro` component
- Implement CSS animation for marquee (see `docs/architecture.md` section 3.2)
- Logo images stored in `public/images/logos/`
- Reference: `docs/ux-design-specification.md` section 6.1 for component details

---

### Story 2.3: Navigation Structure and Information Architecture

**As a** website visitor exploring Synetica's services,  
**I want** clear navigation that helps me find what I need quickly,  
**so that** I don't waste time hunting for information.

#### Acceptance Criteria

1. **Primary navigation menu:**
   - All 11 top-level items: Home, Solutions, Products, Industries, Company, Process, Case Studies, Blog, Resources, Contact, Partnership
   - Desktop: Horizontal layout, visible on all pages
   - Mobile: Hamburger menu icon, slide-out drawer
2. **Partnership handling:**
   - Navigation item visible but non-clickable (or shows "Coming Soon" on click)
   - Link disabled until Phase II/III implementation
   - Visual indicator (grayed out or "Coming Soon" badge)
3. **Mobile navigation:**
   - Hamburger icon (3 lines) in top-right on mobile (< 768px)
   - Slide-out drawer from right with all navigation items
   - Smooth animation (slide-in/out)
   - Close button (X) in drawer
   - Overlay background (semi-transparent) when drawer open
4. **Navigation hierarchy:**
   - Active page highlighted (underline or background color)
   - Dropdown menus for sections with sub-pages (future)
   - Breadcrumb navigation on deeper pages (optional)
5. **Footer navigation:**
   - Footer includes all 11 navigation items in organized columns
   - Contact information (email, phone, offices)
   - Social links (LinkedIn, Twitter, etc.)
   - Legal links (Privacy Policy, Terms of Service)
6. **Utility bar (persistent):**
   - "Book Consultation" button (links to `/contact`)
   - "WhatsApp" button (opens WhatsApp chat)
   - Language toggle (EN/ID) - visible but non-functional until user story prioritization
   - Sticky on scroll (desktop) or fixed bottom (mobile)

#### Technical Notes

- Use `Header.astro` and `Navigation.astro` components
- Mobile menu uses shadcn/ui Sheet component or custom drawer
- Reference: `docs/information-architecture.md` for full navigation structure
- Reference: `docs/ux-design-specification.md` section 4.1 for navigation patterns

---

### Story 2.4: Process Overview Teaser

**As a** visitor curious about how Synetica works differently,  
**I want** a brief introduction to the 2B2G methodology on the homepage,  
**so that** I can understand the system before committing to reading the full process page.

#### Acceptance Criteria

1. **Section heading:**
   - Text: "How We Build Differently"
   - Typography: Geist Mono, bold, large
   - Centered or left-aligned (match design system)
2. **2B2G Methodology visualization:**
   - Four phases displayed: Blueprint → Build & Benchmark → Go To Market → Grow
   - Visual representation: Timeline or cards layout
   - Each phase shows:
     - Phase number (1, 2, 3, 4)
     - Phase name (Blueprint, Build & Benchmark, etc.)
     - Duration badge (2 weeks, 6 weeks, 3 months, Ongoing)
     - Brief outcome-focused description (1-2 sentences)
3. **Outcome-focused descriptions:**
   - Blueprint: "Turn your vision into a decision-ready plan. We map assumptions, prioritize features, and design the smallest test that can prove or kill your idea."
   - Build & Benchmark: "Build fast, test with real users. We ship an MVP in 6 weeks, then validate with 30 users before scaling."
   - Go To Market: "Launch with evidence, not hope. We test positioning, messaging, and channels before investing in scale."
   - Grow: "Optimize what works, kill what doesn't. We measure, iterate, and scale based on real user behavior."
4. **Visual design:**
   - Cards or timeline layout (mobile: stacked, desktop: horizontal)
   - Icons or emojis for each phase (optional)
   - Hover effects (subtle elevation or border color change)
5. **Call-to-action:**
   - "Learn More About Our Process" button (links to `/process`)
   - Or: "See How It Works" with arrow icon
6. **Success statistics (optional):**
   - Brief metric: "80% of products we build reach market fit"
   - Or: "Average 8 weeks from idea to validated product"

#### Technical Notes

- Use `ProcessSection.astro` component
- Individual phase cards use `ProcessPhase.astro` component
- Reference: `docs/ux-design-specification.md` section 6.1 for component patterns
- Language must match Synetica voice: direct, outcome-focused, no fluff

---

## Epic 3: Case Study System & Solution Showcase

**Epic Goal:** Show prospects exactly what success looks like. Case studies aren't just portfolio pieces—they're proof that our system works. Each case study connects solution → methodology → outcome, so prospects can see themselves in the results.

**Priority:** P0 (Critical Path)  
**Estimated Duration:** 2-3 weeks  
**Dependencies:** Epic 1, Epic 2 (Story 2.1, 2.2)

---

### Story 3.1: Case Study Gallery Page

**As a** potential client researching Synetica's track record,  
**I want** to browse case studies filtered by industry and solution type,  
**so that** I can quickly find examples relevant to my needs.

#### Acceptance Criteria

1. **Gallery page route:**
   - URL: `/case-studies`
   - Page component: `src/pages/case-studies/index.astro`
2. **Page layout:**
   - Heading: "Case Studies" (Geist Mono, large, bold)
   - Subheading: "Real products, real results. See how we help companies move from idea to traction."
   - Grid layout for case study cards (mobile: 1 col, tablet: 2 col, desktop: 3 col)
3. **Filter functionality:**
   - Filter by industry: Fintech, Logistics, Enterprise, Automotive, Hospitality, Aviation, etc.
   - Filter by solution type: Investor Apps, Management Systems, Platforms, etc.
   - Filter UI: Dropdown or button group (shadcn/ui Select component)
   - Active filters highlighted
   - "Clear filters" button
4. **Case study cards:**
   - Each card shows:
     - Client logo or project thumbnail
     - Client name (bold)
     - Industry tag (badge)
     - Brief description (2-3 sentences)
     - Key outcome metric (optional: "Reduced time to market by 60%")
     - "Read Full Case Study" CTA button
   - Cards use `CaseStudyCard.astro` component
   - Hover effect: Subtle elevation or border color change
5. **Content source:**
   - Case studies loaded from Astro content collections (`src/content/case-studies/`)
   - Only published case studies shown (draft: false)
   - Sorted by publishDate (newest first) or featured (featured first)
6. **Performance:**
   - Images lazy-loaded
   - Page load < 3s on mobile
   - Smooth filter transitions (no page reload)

#### Technical Notes

- Use Astro's `getCollection()` API to fetch case studies
- Filter logic in Astro component (client-side filtering via JavaScript islands if needed)
- Reference: `docs/architecture.md` section 2.2 for content collections schema
- Reference: `docs/ux-design-specification.md` section 6.1 for card component

---

### Story 3.2: Individual Case Study Template and Content Structure

**As a** prospect reading a case study,  
**I want** to understand the challenge, solution, and business outcomes,  
**so that** I can envision how Synetica might help with my project.

#### Acceptance Criteria

1. **Case study page route:**
   - URL: `/case-studies/[slug]` (dynamic route)
   - Page component: `src/pages/case-studies/[...slug].astro`
   - Uses Astro's `getStaticPaths()` to generate pages from content collection
2. **Page layout:**
   - Hero section with:
     - Client logo (large)
     - Project title (h1)
     - Brief description (subtitle)
     - Hero image or background (optional)
   - Main content sections:
     - **The Challenge** (h2): Problem statement, context, constraints
     - **Our Approach** (h2): How we solved it, methodology applied
     - **The Results** (h2): Business outcomes, metrics, success indicators
     - **Technology Stack** (h2): Tech badges (React, Node.js, etc.)
   - Sidebar or footer with:
     - Related case studies (3-4 cards)
     - Consultation CTA ("Want similar results? Let's talk.")
3. **Content structure:**
   - Markdown frontmatter matches content collection schema:
     - title, client, industry, description, challenge, solution, outcome
     - metrics (array of {label, value})
     - techStack (array of strings)
     - image, featured, publishDate
   - Markdown body contains detailed narrative
4. **Visual elements:**
   - Screenshots or diagrams (optimized images)
   - Before/after comparisons (if applicable)
   - User flow illustrations (if applicable)
   - Tech stack badges (visual chips)
5. **2B2G Methodology integration:**
   - "How We Achieved This" section showing methodology phases applied
   - Timeline visualization (if applicable)
   - Links to detailed methodology page (`/process`)
6. **Call-to-action:**
   - "See Similar Results" button (links to filtered case studies)
   - "Get Started" button (links to `/contact` with pre-filled message referencing case study)
   - WhatsApp CTA (optional)

#### Technical Notes

- Use `CaseStudyLayout.astro` for consistent layout
- Images optimized via Astro's `<Image>` component
- Reference: `docs/architecture.md` section 2.2 for content schema
- Language must match Synetica voice: outcome-focused, validation over assumption

---

### Story 3.3: Signature Case Studies Content Creation

**As a** content manager building credibility,  
**I want** compelling case studies that demonstrate our methodology value,  
**so that** prospects can see concrete examples of our approach delivering results.

#### Acceptance Criteria

1. **Traveloka case study:**
   - Repositioned as product development success story
   - Emphasizes validation/planning preventing costly mistakes
   - Includes specific metrics (if available)
   - Highlights 2B2G methodology application
2. **Angkasa Pura case study:**
   - Highlights systematic approach
   - Shows enterprise methodology application
   - Includes technical details and business outcomes
3. **Astra case study:**
   - Showcases enterprise methodology application
   - Emphasizes strategic value delivery
   - Includes client testimonial (if available)
4. **Additional case studies:**
   - At least 2 more case studies featuring different solution types
   - Variety in industries (fintech, logistics, enterprise, etc.)
   - Each emphasizes validation/planning value
5. **Content quality:**
   - Each case study follows template structure (Challenge → Approach → Results)
   - SEO-optimized content targeting relevant keywords
   - Language matches Synetica voice: direct, outcome-focused, no fluff
6. **Content format:**
   - Markdown files in `src/content/case-studies/`
   - Proper frontmatter with all required fields
   - Images optimized and stored in `public/images/case-studies/`

#### Technical Notes

- Content creation is manual (n8n automation is future work)
- Reference: `docs/language.md` for writing style guidelines
- Each case study should connect solution → methodology → outcome

---

### Story 3.4: Case Study to Methodology Bridge

**As a** case study reader impressed by results,  
**I want** to understand how Synetica's process ensures these outcomes,  
**so that** I can evaluate the methodology for my own project needs.

#### Acceptance Criteria

1. **"How We Achieved This" section:**
   - Included in each case study page
   - Explains 2B2G methodology phases applied to the project
   - Shows timeline (if applicable)
   - Links to detailed methodology page (`/process`)
2. **Methodology visualization:**
   - Visual representation of phases (timeline or cards)
   - Highlights which phases were most critical for this project
   - Shows deliverables from each phase
3. **Success metrics tied to methodology:**
   - Metrics connected to specific methodology phases
   - Example: "Blueprint phase identified 3 critical assumptions. Testing these in Week 2 saved 6 months of development."
4. **Related content:**
   - "Learn More About Our Process" CTA linking to `/process`
   - "See Similar Results" linking to filtered case studies
5. **Consultation CTA:**
   - "Want similar results? Let's talk." button
   - Links to `/contact` with pre-filled message referencing the case study
   - WhatsApp option with pre-filled message

#### Technical Notes

- This section is part of the case study template
- Use `ProcessPhase.astro` component for methodology visualization
- Reference: `docs/ux-design-specification.md` for component patterns

---

## Epic 4: Services & Methodology Deep-Dive

**Epic Goal:** Convert case study interest into service inquiries. Prospects who read case studies want to know: "Can you do this for me?" Answer that question clearly, then make it easy to start a conversation.

**Priority:** P1 (High Value)  
**Estimated Duration:** 2-3 weeks  
**Dependencies:** Epic 3 (for case study references)

---

### Story 4.1: 2B2G™ Methodology Deep-Dive Page

**As a** prospect convinced by case study results,  
**I want** to understand exactly how the 2B2G methodology works and what I'll receive,  
**so that** I can evaluate if this fits my project needs and timeline.

#### Acceptance Criteria

1. **Page route:**
   - URL: `/process`
   - Page component: `src/pages/process/index.astro`
2. **Page structure:**
   - Hero section: "The 2B2G Framework: From Idea to Traction in 8 Weeks"
   - Introduction: Brief overview of the framework
   - Four main sections (one per phase):
     - **Blueprint (2 weeks)**
     - **Build & Benchmark (6 weeks)**
     - **Go To Market (3 months)**
     - **Grow (Ongoing)**
3. **Each phase section includes:**
   - Phase number and name
   - Duration badge
   - Deliverables list (specific, not vague)
   - Timeline breakdown (Week 1-2, etc.)
   - Key activities (what we do)
   - Outcomes (what you get)
   - Example: "In Blueprint, we map your riskiest assumptions and design tests to validate them. Deliverables: validated problem statement, user personas, prioritized feature list, technical architecture, 60-day roadmap."
4. **Visual workflow:**
   - Interactive timeline or flowchart showing methodology progression
   - Phase dependencies clearly shown
   - Hover states reveal more details
5. **Language:**
   - Direct, outcome-focused descriptions
   - No fluff, no vague promises
   - Validation over assumption language
   - Example: "We test this in Week 2 to decide what to build in Week 4."
6. **Call-to-action:**
   - "Ready to start? Let's talk." button (links to `/contact`)
   - "See Case Studies" button (links to `/case-studies`)
   - WhatsApp CTA

#### Technical Notes

- Use `ProcessPhase.astro` components for each phase
- Interactive timeline can use JavaScript islands (Astro) for interactivity
- Reference: `docs/language.md` for writing style
- Reference: `docs/ux-design-specification.md` for component patterns

---

### Story 4.2: Service Offering Pages

**As a** business owner planning a product development project,  
**I want** clear descriptions of Synetica's service offerings,  
**so that** I can understand pricing structure and choose the right collaboration approach.

#### Acceptance Criteria

1. **Solutions page route:**
   - URL: `/solutions`
   - Page component: `src/pages/solutions/index.astro`
2. **Service offerings listed:**
   - Blueprint (standalone service)
   - Build MVP (standalone service)
   - Go To Market (standalone service)
   - Optimize Growth (standalone service)
   - Product Rescue (standalone service)
   - Corporate Accelerator (standalone service)
   - Full 2B2G Framework (all phases)
3. **Each service page includes:**
   - Service name and brief description
   - What's included (deliverables list)
   - Timeline (duration)
   - Pricing guidance ("Starting at IDR X" or "Contact for pricing")
   - Who it's for (target audience)
   - Case study examples (links to relevant case studies)
   - "Get Started" CTA
4. **Comparison table (optional):**
   - Helps prospects choose appropriate service level
   - Shows differences between services
   - Highlights recommended service for different scenarios
5. **Language:**
   - Outcome-focused descriptions
   - Clear, no jargon
   - Example: "Blueprint turns your vision into a decision-ready plan. You get validated assumptions, prioritized features, and a roadmap—in 2 weeks."
6. **Navigation:**
   - Links from Solutions index to individual service pages
   - Breadcrumb navigation
   - Related services suggested

#### Technical Notes

- Individual service pages: `/solutions/blueprint`, `/solutions/build-mvp`, etc.
- Use consistent layout component
- Reference: `docs/language.md` for writing style

---

### Story 4.3: Team and Credentials Page

**As a** decision-maker evaluating Synetica,  
**I want** to understand the team's expertise and international experience,  
**so that** I can trust they have the skills to execute my project successfully.

#### Acceptance Criteria

1. **Page route:**
   - URL: `/company/team` or `/company/credentials`
   - Page component: `src/pages/company/team.astro`
2. **Team section:**
   - Team member profiles (if available)
   - Each profile includes:
     - Name and role
     - Brief bio highlighting international experience
     - Key expertise areas
     - Photo (optimized image)
3. **Credentials section:**
   - ISO 27001 certification (badge and description)
   - AWS Partner status (badge and description)
   - Other certifications or partnerships
4. **Yogyakarta office advantages:**
   - Cost benefits explanation
   - Quality of talent
   - Time zone advantages
   - Example: "Yogyakarta office delivers enterprise-grade quality at 40% lower cost than Jakarta or Singapore."
5. **Company evolution:**
   - Story of rebrand from Softwareseni to Synetica
   - Emphasizes shift from software house to tech-based business consultancy
   - Highlights strategic value focus
6. **Client testimonials:**
   - Testimonials focusing on team expertise and outcomes
   - Real quotes from clients (if available)
   - Client names and companies (with permission)

#### Technical Notes

- Team photos stored in `public/images/team/`
- Use consistent card layout for team members
- Reference: `docs/language.md` for writing style

---

### Story 4.4: About Synetica and Company Positioning

**As a** prospect researching Synetica's background,  
**I want** to understand the company story and strategic positioning,  
**so that** I can evaluate if they align with my business goals and values.

#### Acceptance Criteria

1. **Page route:**
   - URL: `/company/about` or `/company`
   - Page component: `src/pages/company/about.astro`
2. **Company story:**
   - Rebrand story emphasizing tech-based business consultancy positioning
   - Key message: "We think, then build. We blend strategic depth with execution power."
   - Differentiation from traditional software houses clearly articulated
   - Example: "Unlike consultancies that stop at strategy or agencies that jump straight into execution, Synetica does both."
3. **Mission and vision:**
   - Mission: "Help founders and innovation teams move from clarity to traction—fast."
   - Vision: "Become the go-to partner for product success in Indonesia and Southeast Asia."
   - Reflects product success focus
4. **Geographic advantages:**
   - Indonesian market expertise
   - Yogyakarta cost advantages
   - International experience
5. **Future vision:**
   - Selective venture capital model (if applicable)
   - Growth plans
   - Market positioning
6. **Positioning statement:**
   - Clear positioning as product success partners, not just developers
   - Builder-Sage Hybrid archetype reflected
   - Example: "We're co-pilots for founders—from blank canvas to blueprint to build to traction."

#### Technical Notes

- Language must match Synetica voice: sharp, direct, outcome-focused
- Reference: `docs/language.md` for complete writing guidelines
- Reference: `docs/brief.md` for brand positioning

---

## Epic 5: Contact & Lead Generation Optimization

**Epic Goal:** Convert website interest into qualified sales opportunities. Every form submission, WhatsApp click, and CTA should be tracked, measured, and optimized. We're not just collecting leads—we're qualifying them.

**Priority:** P0 (Critical Path)  
**Estimated Duration:** 2-3 weeks  
**Dependencies:** Epic 1 (for analytics), Epic 2 (for CTAs)

---

### Story 5.1: Consultation Request Forms and Contact System

**As a** prospect ready to discuss my project with Synetica,  
**I want** simple contact options that capture my requirements efficiently,  
**so that** I can get relevant information and start the consultation process.

#### Acceptance Criteria

1. **Contact page route:**
   - URL: `/contact`
   - Page component: `src/pages/contact/index.astro`
2. **Initial contact form:**
   - Simple form with fields:
     - Name (required)
     - Email (required)
     - Company (optional)
     - Message/Project description (required)
   - Uses Netlify Forms for submission
   - Honeypot field for spam protection
3. **Form validation:**
   - HTML5 validation (required fields, email format)
   - Client-side validation feedback (inline error messages)
   - Error states: Red border, error message below field
   - Success state: Redirect to `/contact/success` page
4. **BAND qualification (future):**
   - Follow-up form for BAND scoring (Budget, Authority, Need, Decision)
   - Scoring rubric: Budget (5 points, 50% weight), Authority (2 points), Need (2 points), Decision (1 point)
   - Minimum 6 points to qualify
   - Budget is required to proceed (0 points = disqualification)
5. **Form submission handling:**
   - Netlify Forms processes submission
   - Email notification sent to team
   - Automated confirmation email to user (optional)
   - Success page shows confirmation message
6. **Analytics tracking:**
   - Form submission tracked in GA4 (custom event)
   - Form name tracked for attribution
   - Conversion goal configured in GA4
7. **Mobile optimization:**
   - Form fields full width on mobile
   - Touch-friendly inputs (minimum 44px height)
   - Fast loading and submission

#### Technical Notes

- Use `ContactForm.astro` component
- Netlify Forms configuration in `netlify.toml`
- Reference: `docs/architecture.md` section 4.2 for form handling
- Reference: `docs/band-scoring-rubric.md` for BAND details

---

### Story 5.2: WhatsApp Click-to-Chat Integration

**As an** Indonesian entrepreneur who prefers immediate communication,  
**I want** to quickly connect with Synetica via WhatsApp for urgent questions,  
**so that** I can get fast responses during my decision-making process.

#### Acceptance Criteria

1. **WhatsApp button component:**
   - Component: `src/components/WhatsAppButton.astro`
   - Multiple variants: Primary button, secondary button, icon-only
2. **WhatsApp link format:**
   - URL: `https://wa.me/{{PHONE_NUMBER}}?text={{ENCODED_MESSAGE}}`
   - Phone number: Environment variable `PUBLIC_WHATSAPP_NUMBER`
   - Pre-filled message: "Hi Synetica! I'm interested in learning more about your 8-Week Product Launch program."
3. **Button placement:**
   - Header utility bar (desktop)
   - Fixed bottom button (mobile)
   - Footer
   - Contact page
   - Case study pages (optional)
4. **Message templates:**
   - Different messages for different contexts:
     - General inquiry: "Hi Synetica! I'm interested in learning more about your services."
     - Case study: "Hi Synetica! I saw your {{CLIENT}} case study and want to discuss similar results."
     - Process page: "Hi Synetica! I want to learn more about the 2B2G Framework."
5. **Analytics tracking:**
   - WhatsApp clicks tracked in GA4 (custom event)
   - Location tracked (header, footer, contact page, etc.)
   - Conversion goal configured
6. **Visual design:**
   - WhatsApp green color (#25D366) for icon variant
   - Clear icon (WhatsApp logo SVG)
   - Accessible: Alt text, keyboard navigation

#### Technical Notes

- Use `WhatsAppButton.astro` component
- Reference: `docs/architecture.md` section 4.3 for WhatsApp integration
- Analytics tracking via `trackWhatsAppClick()` function

---

### Story 5.3: Microsoft Clarity Heatmap and Behavior Analytics

**As a** product manager optimizing website conversion,  
**I want** detailed user behavior insights through heatmaps and session recordings,  
**so that** I can identify optimization opportunities for client logo placement and user engagement.

#### Acceptance Criteria

1. **Clarity integration:**
   - Clarity project ID: Environment variable `PUBLIC_CLARITY_PROJECT_ID`
   - Tracking code integrated in `BaseLayout.astro`
   - Loads on all pages
2. **Heatmap data collection:**
   - Homepage heatmaps (click, scroll, move)
   - Case study page heatmaps
   - Contact page heatmaps
   - Data visible in Clarity dashboard
3. **Session recording:**
   - Session recordings enabled
   - Privacy compliance (no PII recorded)
   - Recordings available in Clarity dashboard
4. **Click tracking:**
   - Client logo clicks tracked
   - CTA button clicks tracked
   - Navigation clicks tracked
   - Form interactions tracked
5. **Scroll depth analysis:**
   - Scroll depth data collected
   - Identifies where users drop off
   - Content optimization opportunities identified
6. **Privacy compliance:**
   - No PII recorded
   - Cookie consent (future: Story 5.5)
   - GDPR compliance (if applicable)

#### Technical Notes

- Use `Clarity.astro` component
- Reference: `docs/architecture.md` section 4.1 for Clarity integration
- Clarity script loads asynchronously

---

### Story 5.4: Advanced Analytics and Conversion Tracking

**As a** business owner measuring website ROI,  
**I want** comprehensive analytics showing lead quality, source attribution, and conversion optimization data,  
**so that** I can make data-driven decisions about marketing investment and website improvements.

#### Acceptance Criteria

1. **GA4 conversion goals:**
   - Consultation form submission (primary goal)
   - WhatsApp click (secondary goal)
   - Case study view (engagement goal)
   - Methodology page view (engagement goal)
2. **Search Console integration:**
   - Keyword performance tracking
   - Search impressions and clicks
   - Average position tracking
   - Click-through rate (CTR) analysis
3. **UTM parameter tracking:**
   - Campaign attribution (utm_source, utm_medium, utm_campaign)
   - Source tracking for all external links
   - Conversion paths analyzed
4. **Custom events:**
   - Case study engagement (time on page, scroll depth)
   - Methodology page views
   - CTA clicks (tracked by location)
   - Form field interactions (optional)
5. **Lead scoring (future):**
   - Based on BAND criteria and engagement
   - Scoring logic defined (not implemented in MVP)
6. **Analytics dashboard:**
   - Monthly analytics report (manual or automated)
   - Key metrics: Traffic, conversions, source attribution, user behavior
   - Insights and recommendations

#### Technical Notes

- GA4 events tracked via `trackEvent()` function
- Reference: `docs/architecture.md` section 4.1 for analytics integration
- Custom events defined in `src/lib/analytics.ts`

---

## Story Prioritization and Sequencing

### Phase 1: Foundation (Weeks 1-3)
- Epic 1: All stories (Foundation & Core Infrastructure)
- **Goal:** Working site deployed with basic functionality

### Phase 2: Credibility (Weeks 4-6)
- Epic 2: All stories (Credibility-First Homepage)
- **Goal:** Homepage establishes trust and guides users to case studies

### Phase 3: Proof (Weeks 7-9)
- Epic 3: All stories (Case Study System)
- **Goal:** Case studies demonstrate results and methodology value

### Phase 4: Conversion (Weeks 10-12)
- Epic 4: Stories 4.1, 4.2 (Methodology & Services)
- Epic 5: Stories 5.1, 5.2 (Contact & WhatsApp)
- **Goal:** Clear pathways from interest to consultation

### Phase 5: Optimization (Weeks 13-14)
- Epic 4: Stories 4.3, 4.4 (Team & About)
- Epic 5: Stories 5.3, 5.4 (Analytics & Tracking)
- **Goal:** Complete site with full analytics and optimization

---

## Language Guidelines Summary

When writing copy for any story, follow these rules:

1. **Direct statements:** "We deliver X" not "We aim to deliver X"
2. **Outcome-first:** "You get validated assumptions in 2 weeks" not "We provide strategic consulting"
3. **Validation over assumption:** "We test this in Week 2" not "We assume this will work"
4. **Think in systems, write in steps:** "First we map, then we test, then we build"
5. **Confident but grounded:** "We recommend..." not "We guarantee..."
6. **No fluff:** Cut words that don't add value. Every sentence serves a purpose.

**Reference:** `docs/language.md` for complete writing guidelines and examples.

---

## Version History

| Date | Version | Changes | Author |
|------|---------|---------|--------|
| 2025-01-27 | 1.0 | Initial epics and stories document | PM Agent |

