# Synetica Website - AI Agent Guidelines

This document provides guidelines for AI agents working on the Synetica website project, ensuring consistency with our brand identity, technical requirements, and project goals.

## Project Context

### Brand Identity
- **Company**: Synetica - A tech-based business consultancy that helps founders and innovation teams move from clarity to traction — fast
- **Category**: Tech-Based Business Consultancy
- **Positioning**: Synetica blends the strategic depth of consulting with the execution power of a product studio
- **Archetype**: Builder-Sage Hybrid - Combines pragmatic execution with intelligent insight
- **Tone**: Smart, confident, and structured
- **Brand Essence**: "From idea to traction — within 8 weeks"
- **One Line**: "Launch your product in 8 weeks or less"
- **Brand Character**: Clear Thinking • Momentum • Structure • Human Tech + AI • Focus • Proof
- **Mission**: To fast-launch products that truly matter. We reduce waste, shorten time-to-market, and ensure adoption by bridging the gap between business strategy, design, and technology execution.

### Target Users
- **Primary**: Dreamers (Indonesian solopreneurs and aspiring entrepreneurs)
- **Secondary**: Growing Businesses (Established companies with pain points)
- **Language**: English-only for first version
- **Focus**: Clarity → Validation → Traction
- **Differentiator**: We stay from idea to adoption — combining business clarity, AI-assisted development, and real-world validation

### Core Framework
**2B2G Framework**: Blueprint → Build & Benchmark → Go To Market → Grow
- **Blueprint (2 weeks)**: Turning vision into a decision-ready plan with clear priorities, features, and validation steps
- **Build & Benchmark (6 weeks)**: Lean, AI-assisted engineering that delivers fast, focused, and reliable results. MVP tested with 30 real users to collect actionable feedback and validate usability, clarity, and performance before launch
- **Go To Market (3 months)**: Testing and measuring adoption before scaling, so every product is backed by evidence. Includes positioning, messaging, launch campaigns, onboarding, and performance tracking
- **Grow (ongoing)**: Post-launch optimization and marketing support to convert traction into long-term growth. Combines product iteration with AI-supported marketing campaigns and expert-led strategy

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
   - Use "tech-based business consultancy" as the primary category descriptor
   - Reference "Dreamers" and "Growing Businesses" as target segments
   - Emphasize "From idea to traction — within 8 weeks" as core promise
   - Use "Launch your product in 8 weeks or less" as the one-line value proposition
   - Use Builder-Sage Hybrid archetype in positioning
   - Emphasize that Synetica does both strategy and execution — we think, then build

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
   - Mobile-optimized for Indonesian Dreamers and Growing Businesses
   - Case study-driven persuasion

### Common Mistakes to Avoid

1. **Don't** refer to Synetica as a "product development studio" (use "tech-based business consultancy")
2. **Don't** refer to Synetica as a "Blueprint specialization company"
3. **Don't** use "SMBs and corporate innovation teams" or "Emerging Business" as target users (use "Growing Businesses")
4. **Don't** implement bilingual content in first version
5. **Don't** include blog/content management in MVP scope
6. **Don't** use outdated failure rate statistics (use 80%, not 70%)
7. **Don't** position Synetica as only strategy or only execution — we do both

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
- Highlight the 8-Week Product Launch™ methodology
- Emphasize the combination of strategic thinking and execution power
- Show how we bridge the gap between consultancies (strategy only) and dev shops (execution only)

### Writing Style & Language Guidelines

**PRIMARY PRINCIPLES** (These override all other guidelines when in conflict):
- **Grounded and authentic**: Use real examples, actual metrics, honest language. No hype, no exaggeration.
- **Rapid**: Get to the point fast. Cut unnecessary words. Short sentences preferred.
- **No Bullshit**: No fluff, no marketing speak, no vague promises. Say what you mean directly.
- **Sharp**: Every word must cut. Be precise, intentional, and clear. No filler.
- **Intentional**: Every sentence serves a purpose. If it doesn't add value, remove it.

**Writing Techniques**:
- **Direct statements**: Lead with clear assertions ("We deliver X", "You get Y"). No hedging.
- **Problem-solution structure**: Frame the problem first, then present Synetica as the solution. Be specific about the problem.
- **Contrast language**: Use "Not X, but Y" patterns to differentiate (e.g., "Not a prototype. Not a demo. A real product.")
- **Specific numbers**: Always include concrete metrics (8 weeks, 30 users, 80% success rate, IDR amounts). Ground claims in data.
- **Action-oriented**: Use active voice and strong verbs (deliver, validate, launch, build, test). Avoid passive voice.
- **Evidence over opinion**: Emphasize data, validation, and proof. No unsupported claims.
- **Short sentences**: Prefer brevity. If a sentence can be shorter, make it shorter. Cut words that don't add meaning.
- **Business language**: Use clear business terminology. Avoid technical jargon and marketing fluff.
- **Outcome-focused**: Connect features to business outcomes. Skip features that don't drive traction.
- **Comparison format**: When differentiating, use "vs. [Competitor Type]" with sharp, factual contrasts.

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
