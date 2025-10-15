# Synetica Website

Synetica is a product launch partner that helps founders move from idea to traction in eight weeks through a Blueprint → Build & Benchmark → Go To Market → Grow framework. This repository will host the public marketing site that tells the Synetica story, showcases results, and captures qualified leads.

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
- **What we solve:** Most digital products fail because teams build before validating. Synetica leads with a Blueprint phase that sharpens ideas, aligns business goals, and prevents waste.
- **Who we serve:** Indonesian dreamers (solopreneurs, SMB founders) and growing businesses that need clarity, validation, and execution support.
- **How we win:** End-to-end accountability—from blueprinting and AI-assisted builds to validation, launch, and growth.

## Core Experience
- Credibility-first homepage highlighting marquee clients (Traveloka, Angkasa Pura, Astra) and proof of outcomes.
- Detailed storytelling around the 4B framework with timelines, deliverables, and decision checkpoints.
- Case study hub that reframes existing engagements as validation success stories.
- Consultation pathways combining lightweight inquiry forms with WhatsApp click-to-chat for rapid follow-up.
- Content and SEO foundation geared toward product planning and validation keywords.

## Architecture & Stack
- **Static generator:** Hugo (extended) for speed, SEO, and markdown-first content.
- **Styling:** Tailwind CSS JIT with shadcn/ui primitives, aligned to the Tweakcn `cmftuwple000004kv5zzr2ukn` theme tokens.
- **Tooling:** Node.js for asset pipeline, Go-based Hugo CLI, n8n automation for future content ingestion.
- **Hosting:** Netlify or Vercel with global CDN, HTTPS, and deploy previews.
- **Integrations:** Netlify Forms/Formspree (lead capture), Google Analytics 4 + Search Console + Microsoft Clarity, WhatsApp click-to-chat.

## Repository Status
Implementation is currently in planning. The PRD (`prd.md`) and brand brief (`brief.md`) capture the approved requirements and messaging. Hugo scaffolding, Tailwind configuration, and deployment workflows will be committed in upcoming milestones.

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
| Services & Methodology | 4B deep-dive, engagement models, team page | ⚙️ Planned |
| Contact & Lead Gen | Forms, WhatsApp integration, analytics optimization | ⚙️ Planned |

Details for each phase live in [`prd.md`](./prd.md).

## Content Sources & Strategy
- [`brief.md`](./brief.md) captures the brand story, positioning, and messaging pillars.
- [`prd.md`](./prd.md) translates the brief into functional, non-functional, and UX requirements.
- Case studies will reuse and reframe work delivered under the Softwareseni umbrella, emphasizing blueprint-first validation outcomes.

## Contributing
This is a private project maintained by the Synetica product and engineering team. Please:
1. Create a feature branch from `main`.
2. Open a pull request describing the change and referencing the relevant brief/PRD section.
3. Ensure Hugo builds succeed and linting/test scripts (to be added) pass before requesting review.

## License
© Synetica. All rights reserved. This repository is not licensed for public reuse.
