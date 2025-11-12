# Synetica Website

Synetica is a tech-based business consultancy that helps founders and innovation teams move from clarity to traction — fast. We combine strategic thinking, product design, and technology execution to validate ideas and scale outcomes. Through our 8-Week Product Launch™ and 2B2G framework (Blueprint → Build & Benchmark → Go To Market → Grow), we take clients from idea to a validated product people can actually use and love. This repository hosts the public marketing site that tells the Synetica story, showcases results, and captures qualified leads.

## Table of Contents
- [Overview](#overview)
- [Core Experience](#core-experience)
- [Architecture & Stack](#architecture--stack)
- [Repository Status](#repository-status)
- [Getting Started](#getting-started)
- [Project Roadmap](#project-roadmap)
- [Content Sources & Strategy](#content-sources--strategy)
- [Contributing](#contributing)
- [License](#license)

## Overview
- **What we solve:** The hardest part isn't building — it's knowing what to build and where to start. Many founders jump straight into development without clear synergy between business output and final product. Synetica fixes this by helping you plan first, build only what matters, and test early. Our blueprint-first approach gives you a clear path, predictable costs, and confidence that every step is backed by evidence, not opinion.
- **Who we serve:** Dreamers (Indonesian solopreneurs and aspiring entrepreneurs) and Growing Businesses (established companies with pain points) who need clarity, validation, and traction for their digital products.
- **How we win:** Unlike traditional consultancies that stop at strategy or agencies that jump straight into execution, Synetica does both — we think, then build. We bridge the gap between business strategy, design, and technology execution, delivering validated products in 8 weeks through our 2B2G framework.

## Core Experience
- Credibility-first homepage highlighting marquee clients (Traveloka, Angkasa Pura, Astra) and proof of outcomes
- Detailed storytelling around the 2B2G framework and 8-Week Product Launch™ with timelines, deliverables, and decision checkpoints
- Case study hub that reframes existing engagements as product development success stories
- Consultation pathways combining lightweight inquiry forms with WhatsApp click-to-chat for rapid follow-up
- English-only content targeting Indonesian Dreamers and Growing Businesses segments
- Content and SEO foundation geared toward tech-based business consultancy, product validation, and 8-week launch keywords
- Emphasis on the unique positioning: strategic depth of consulting combined with execution power of a product studio

## Architecture & Stack
- **Static generator:** Hugo (extended) for speed, SEO, and markdown-first content.
- **Styling:** Tailwind CSS JIT with shadcn/ui primitives, aligned to the Tweakcn `cmftuwple000004kv5zzr2ukn` theme tokens.
- **Tooling:** Node.js for asset pipeline, Go-based Hugo CLI, n8n automation for future content ingestion.
- **Hosting:** Netlify or Vercel with global CDN, HTTPS, and deploy previews.
- **Integrations:** Netlify Forms/Formspree (lead capture), Google Analytics 4 + Search Console + Microsoft Clarity, WhatsApp click-to-chat.

## Repository Status
Implementation is currently in planning. The PRD (`doc/prd.md`) and brand brief (`doc/brief.md`) capture the approved requirements and messaging. Hugo scaffolding, Tailwind configuration, and deployment workflows will be committed in upcoming milestones.

## Getting Started
> 🚧 **Planned workflow.** Commands below will apply once the Hugo project files are added.

### Prerequisites
- Go 1.21+
- Hugo Extended 0.124+
- Node.js 18+ and npm 9+

### Initial Setup
```bash
git clone git@github.com:atmawarin/synetica-website.git
cd synetica-website
npm install
hugo server -D
```

- `npm install` will set up the Tailwind/postcss toolchain.
- `hugo server -D` runs a local development server with draft content enabled.

### Production Build
```bash
npm run build      # runs Tailwind build and hugo --minify
```

Deployment is handled by the hosting platform (Netlify/Vercel) and triggered on pushes to `main`.

## Project Roadmap
| Phase | Focus | Status |
|-------|-------|--------|
| Foundation & Core Infrastructure | Hugo setup, Tailwind pipeline, hosting, analytics | ⚙️ Planned |
| Credibility-First Homepage | Hero, trust indicators, navigation | ⚙️ Planned |
| Case Study System | Gallery, individual templates, methodology bridge | ⚙️ Planned |
| Services & Methodology | 2B2G deep-dive, engagement models, team page | ⚙️ Planned |
| Contact & Lead Gen | Forms, WhatsApp integration, analytics optimization | ⚙️ Planned |

Details for each phase live in [`doc/prd.md`](./doc/prd.md).

## Content Sources & Strategy
- [`doc/brief.md`](./doc/brief.md) captures the brand story, positioning, and messaging pillars
- [`doc/prd.md`](./doc/prd.md) translates the brief into functional, non-functional, and UX requirements
- [`doc/brand-guide-brief.md`](./doc/brand-guide-brief.md) defines the visual identity and brand guidelines
- Case studies will reuse and reframe work delivered under the Softwareseni umbrella, emphasizing product development success outcomes

## Contributing
This is a private project maintained by the Synetica product and engineering team. Please:
1. Create a feature branch from `main`.
2. Open a pull request describing the change and referencing the relevant brief/PRD section.
3. Ensure Hugo builds succeed and linting/test scripts (to be added) pass before requesting review.

## License
© Synetica. All rights reserved. This repository is not licensed for public reuse.
