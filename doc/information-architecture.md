# Synetica Website Information Architecture

## 1. Objectives & Inputs
- **Business goals:** Accelerate qualified consultations, establish credibility, differentiate Synetica’s 2B2G™ Methodology (Blueprint → Build & Benchmark → Go To Market → Grow) with an 8-week launch framing.
- **Primary personas:**
  - **Dreamers** – solopreneurs and SMB founders seeking clarity and validation before committing budget.
  - **Growing Businesses** – corporate innovation teams needing structured, end-to-end delivery without draining internal resources.
- **Source artefacts:** [`brief.md`](./brief.md) (brand narrative) and [`prd.md`](./prd.md) (requirements & UX direction).

## 2. Top-Level Navigation
| Label | Purpose | Key CTAs |
|-------|---------|----------|
| **Home** | Immediate value proposition, marquee proof, fast links into Process & Case Studies. | "View Our Process", "See Client Results", "Book Consultation" |
| **Process** | Explain 2B2G framework end-to-end with timelines, deliverables, and proof. | "Download Blueprint Overview", "Schedule Strategy Call" |
| **Case Studies** | Showcase validation outcomes across industries with filters. | "Explore Case Study", "Talk About Similar Project" |
| **Services** | Detail engagement models (Blueprint-only, full cycle, retainers) with comparison matrix. | "Request Scoping Call", "Ask About Pricing" |
| **Insights** | Thought leadership hub (articles, guides, lead magnets) supporting SEO strategy. | "Read Guide", "Get Checklist" |
| **Team** | Establish expertise, Softwareseni heritage, certifications, and Yogyakarta advantage. | "Meet the Team", "Start a Conversation" |
| **Contact** | Conversion endpoint with form, WhatsApp CTA, and office info. | "Submit Brief", "Chat on WhatsApp" |

**Utility bar:** persistent "Book Consultation", "WhatsApp", and future language toggle (EN/ID). Consider variant CTA: "Book 8-Week Launch Consult".

## 3. Secondary & Tertiary Structure
### Home
1. Hero: headline + supporting copy, dual CTA buttons (Process / Consultation).
2. Trust band: client logos, outcome metrics, credential badges.
3. Process teaser: 2B2G snapshot with quick links.
4. Featured case study: persona-aligned success story with proof metric.
5. Services ribbon: concise engagement cards.
6. Testimonials strip.
7. Footer CTA: consultation form teaser + WhatsApp.

### Process
1. Overview: promise, 8-week framing (From idea to traction — within 8 weeks), methodology value props.
2. Individual phase sections (Blueprint, Build & Benchmark, Go To Market, Grow): each with problem solved, deliverables, tooling, validation checkpoints, and timebox (2w / 4–5w / 2mo / ongoing).
3. Engagement models: how clients enter (phase-only vs. full cycle).
4. FAQ: timelines, collaboration expectations, AI tooling transparency.

### Case Studies
1. Gallery grid: filters for persona (Dreamer, Enterprise) and industry (Fintech, Logistics, Aviation, etc.).
2. Feature cards: problem statement + quantitative outcome + relevant phase icons.
3. Detail template:
   - Context & challenge
   - Blueprint insights (research, prioritisation)
   - Build decisions (architecture, AI acceleration)
   - Benchmark & validation (tests, metrics)
   - Growth results (adoption, revenue, efficiency)
   - Testimonial pull quote + CTA.
4. Related stories carousel.

### Services
1. Engagement comparison matrix (Blueprint vs. Full 2B2G™ cycle vs. Grow retainer).
2. Deliverables list per stage with proof assets.
3. Pricing guidance (ranges / starting points) and time expectations.
4. Common scenarios (e.g., Validation Sprint, Corporate Accelerator).
5. CTA panel for scheduling consultation.

### Insights
1. Content categories: Blueprinting, Validation, AI tooling, Growth tactics.
2. Resource cards with estimated read time and target persona tags.
3. Lead magnet section (e.g., "Blueprint Checklist", "Validation Scorecard").
4. Search & filter controls.

### Team
1. Founders & leadership bios with global experience highlights.
2. Advisory network / partner ecosystem.
3. Culture values and working model.
4. Careers teaser (future-ready placeholder).

### Contact
1. Primary consultation form (name, email, company, challenge summary, desired timeline).
2. Progressive disclosure for BANT follow-up (budget, authority, needs, timeline) post-submission.
3. WhatsApp quick action button.
4. Office map, hours, and alternative contact channels.

## 4. Persona Journey Mapping
### Dreamers (Solopreneurs / SMB Founders)
1. Entry via Home hero or Insight article.
2. Skim Process (Blueprint focus) → review Blueprint deliverables.
3. Jump to case study tagged “Dreamer” with tangible validation outcome.
4. CTA: Book consultation / download Blueprint checklist.

### Growing Businesses (Corporate Innovation Teams)
1. Entry via trust band (logos) or enterprise case study.
2. Deep dive into Process (full 2B2G cycle) + Services comparison.
3. Review Team credentials and certifications.
4. CTA: Request scoping workshop / schedule executive briefing.

### Reinforcement Points
- Persistent utility CTAs (Consultation, WhatsApp, 8-Week Launch Consult).
- Contextual CTAs within case studies and phase sections.
- Proof assets (metrics, testimonials) aligned to persona at each stage.

## 5. Content Inventory & Metadata Plan
- Maintain content matrix with fields: Page, Section, Persona, Funnel Stage, 2B2G Phase, Proof Type, Language, Owner, Status, Last Review.
- Use tags to power filters (e.g., `persona:dreamer`, `phase:benchmark`).
- Prioritise seed content: 5 flagship case studies, Blueprint deliverable examples, two insight articles per persona.

## 6. Validation Approach
1. **Stakeholder Card Sort:** Confirm shared mental model for navigation labels and priority pages.
2. **Prototype Tree Test:** Validate findability of key tasks (e.g., "Where do I learn about Blueprint deliverables?").
3. **Click-Path Usability Checks:** Low-fidelity wireframes tested with 3–5 users per persona, measuring CTA discovery and comprehension.
4. Iterate IA based on failure points and record rationale for any structural changes.

## 7. Implementation Notes
- Navigation and footer structures should be configurable via Hugo data files for future updates.
- Surface metadata tags within content front matter to enable automated filtering later.
- Ensure sitemap.xml reflects IA hierarchy for SEO crawl efficiency once implemented.
