# Synetica Website - AI Agent Guidelines

This document provides guidelines for AI agents working on the Synetica website project, ensuring consistency with our brand identity, technical requirements, and project goals.

## Project Context

### Brand Identity
- **Company**: Synetica - A product development studio that delivers end-to-end validation journeys
- **Archetype**: Builder-Sage Hybrid - Combines pragmatic execution with intelligent insight
- **Tone**: Smart, confident, and structured
- **Brand Essence**: "From idea to traction — within 8 weeks"
- **Brand Character**: Clear Thinking • Momentum • Structure • Human Tech + AI • Focus • Proof

### Target Users
- **Primary**: Dreamers (Indonesian solopreneurs and aspiring entrepreneurs)
- **Secondary**: Emerging Business (Established companies with pain points)
- **Language**: English-only for first version
- **Budget Ranges**: IDR 50-150M (Dreamers), IDR 150-500M (Emerging Business)

### Core Framework
**2B2G Framework**: Blueprint → Build & Benchmark → Go To Market → Grow
- **Blueprint (2 weeks)**: Validated problem statement, user personas, technical architecture
- **Build & Benchmark (4-5 weeks)**: AI-accelerated MVP with real user validation
- **Go To Market (2 months)**: User activation and adoption campaigns
- **Grow (ongoing)**: Optimization, retention, and scaling

## Technical Guidelines

### Architecture & Stack
- **Static Generator**: Hugo (extended) for speed, SEO, and markdown-first content
- **Styling**: Tailwind CSS JIT with shadcn/ui primitives
- **Theme**: Tweakcn `cmftuwple000004kv5zzr2ukn` with Synetica brand tokens
- **Typography**: Modern geometric sans-serif primary, humanist sans-serif secondary
- **Hosting**: Netlify/Vercel with global CDN
- **Integrations**: Netlify Forms, Google Analytics 4, Search Console, Microsoft Clarity, WhatsApp

### Content Strategy
- **Language**: English-only for first version
- **Content Types**: Case studies, methodology explanations, team credentials
- **SEO Focus**: Product development and validation keywords
- **Case Studies**: Reposition existing Softwareseni clients (Traveloka, Angkasa Pura, Astra)

## Agent Guidelines

### When Working on This Project

1. **Always Reference Documentation**
   - Check `doc/brief.md` for brand positioning and target users
   - Review `doc/prd.md` for technical requirements and user stories
   - Consult `doc/brand-guide-brief.md` for visual identity guidelines

2. **Maintain Brand Consistency**
   - Use "product development studio" not "Blueprint specialization company"
   - Reference "Dreamers" and "Emerging Business" as target segments
   - Emphasize "From idea to traction — within 8 weeks" as core promise
   - Use Builder-Sage Hybrid archetype in positioning

3. **Technical Requirements**
   - Follow Hugo static site architecture
   - Implement mobile-first responsive design
   - Target Indonesian network conditions (sub-3-second load times)
   - Use English-only content for first version
   - Implement credibility-first homepage approach

4. **Content Guidelines**
   - Lead with client logos and success metrics
   - Show methodology through case studies, not abstract descriptions
   - Use solution-to-methodology flow in user experience
   - Emphasize validation and planning over just development

5. **User Experience Focus**
   - Credibility-first navigation with major client logos
   - Progressive value revelation (recognition → curiosity → understanding → action)
   - Mobile-optimized for Indonesian Dreamers and Emerging Business
   - Case study-driven persuasion

### Common Mistakes to Avoid

1. **Don't** refer to Synetica as a "Blueprint specialization company"
2. **Don't** use "SMBs and corporate innovation teams" as target users
3. **Don't** implement bilingual content in first version
4. **Don't** include blog/content management in MVP scope
5. **Don't** use outdated failure rate statistics (use 80%, not 70%)

### Key Metrics & KPIs
- **Website Traffic**: 1,000+ monthly unique visitors by month 6, 3,000+ by month 12
- **Lead Generation**: 20+ qualified consultations monthly by month 6
- **Conversion**: 25% of consultation requests convert to paid engagements
- **Client Success**: 80% proceed to Build & Benchmark, 70% complete full framework

### File Structure
```
/
├── doc/                          # Documentation
│   ├── brief.md                  # Project brief and brand positioning
│   ├── prd.md                    # Product requirements document
│   ├── brand-guide-brief.md      # Visual identity and brand guidelines
│   └── information-architecture.md
├── README.md                     # Project overview
└── agents.md                     # This file
```

### Development Phases
1. **Foundation & Core Infrastructure** - Hugo setup, hosting, analytics
2. **Credibility-First Homepage** - Hero, trust indicators, navigation
3. **Case Study System** - Gallery, templates, methodology bridge
4. **Services & Methodology** - 2B2G deep-dive, engagement models
5. **Contact & Lead Gen** - Forms, WhatsApp, analytics optimization

## Best Practices

### Code Quality
- Follow Hugo best practices for static site generation
- Implement proper Tailwind CSS utility classes
- Ensure mobile-first responsive design
- Optimize for Indonesian network conditions
- Maintain clean, semantic HTML structure

### Content Creation
- Write for English-proficient Indonesian entrepreneurs
- Use clear, confident, and structured tone
- Emphasize validation and planning methodology
- Include specific business outcomes and metrics
- Reference major client relationships for credibility

### SEO & Performance
- Implement comprehensive SEO optimization
- Target product development and validation keywords
- Ensure sub-3-second page load times
- Use proper meta tags and structured data
- Optimize images and assets for mobile

### User Experience
- Lead with credibility and client logos
- Progressive disclosure of methodology
- Clear consultation pathways
- Mobile-optimized interactions
- Accessible design (WCAG AA standards)

## Resources

### Documentation
- [Project Brief](./doc/brief.md) - Brand positioning and target users
- [Product Requirements](./doc/prd.md) - Technical specifications and user stories
- [Brand Guidelines](./doc/brand-guide-brief.md) - Visual identity and design system

### External References
- [Hugo Documentation](https://gohugo.io/documentation/)
- [Tailwind CSS](https://tailwindcss.com/docs)
- [shadcn/ui Components](https://ui.shadcn.com/)
- [Tweakcn Theme](https://tweakcn.com/)

### Key Contacts
- **Project Owner**: Synetica Product Team
- **Technical Lead**: Synetica Engineering Team
- **Brand Guidelines**: See `doc/brand-guide-brief.md`

---

*This document should be updated whenever project requirements, brand guidelines, or technical specifications change. Always refer to the latest documentation in the `doc/` folder for the most current information.*
