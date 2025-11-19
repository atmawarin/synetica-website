# Research Responsibility: Brief vs PRD

**Date:** 2025-01-27  
**Analyst:** Mary (Business Analyst)

## Quick Answer

**Brief** = Identifies WHAT research is needed and WHY (strategic context)  
**PRD** = References research findings and incorporates them into requirements

## Detailed Breakdown

### Brief Responsibilities (Strategic Level)

The Brief should **identify research needs** as:
- **Gaps in understanding** that need to be filled
- **Strategic questions** that must be answered before proceeding
- **Market/competitive context** that informs positioning
- **User validation needs** that confirm assumptions

**Example from our brief:**
```markdown
### Areas Needing Further Research

- **Competitive Analysis:** Deep competitive analysis of Blueprint methodology 
  positioning in Indonesian market...
- **SEO Keyword Research:** Comprehensive SEO keyword research for case study 
  content strategy...
```

**Why in Brief?** These are strategic business questions that inform the overall approach, not implementation details.

### PRD Responsibilities (Requirements Level)

The PRD should **reference research results** and **incorporate findings** into:
- **Functional Requirements** - Requirements informed by research findings
- **Non-Functional Requirements** - Technical requirements based on research
- **Success Metrics** - Metrics validated through research
- **User Stories** - User needs validated through research

**Example:**
```markdown
**FR15:** The website must implement SEO-optimized content structure based on 
keyword research findings (see Research: SEO Keyword Analysis), targeting 
high-value search terms identified in competitive analysis...
```

**Why in PRD?** Requirements should be based on evidence, not assumptions.

## Research Workflow Timing

### Phase 0: Discovery (Optional)
- **brainstorm-project** - Creative exploration
- **research** - Domain/competitive analysis ← **Use this for competitive analysis**
- **product-brief** - Strategic product planning

### Phase 1: Planning
- **prd** - Detailed requirements (should reference research findings)

### When to Run Research

**Before PRD (Ideal):**
- Competitive Analysis → Informs positioning in PRD
- User Research → Validates personas and pain points in PRD
- SEO Research → Informs content strategy in PRD

**During/After PRD (Acceptable):**
- Technology Stack Evaluation → Informs Architecture (Phase 2)
- Market Validation → Can refine PRD if needed

## Our Current Situation

### Research Already Identified in Brief ✅
- Competitive Analysis
- SEO Keyword Research  
- User Research & Validation
- Market Validation
- Content Strategy Execution
- Client Repositioning Strategy
- Technology Stack Evaluation
- Legal and Business Structure

### Research Status
- **Not Yet Conducted** - All research items are identified but not completed
- **Brief Updated** - Research needs clearly documented
- **PRD Status** - PRD exists but may need updates after research

## Recommendation

### Option A: Run Research Now (Before Architecture)
**Pros:**
- Architecture decisions informed by research
- PRD can be refined with research findings
- Better technology stack evaluation

**Cons:**
- Delays architecture phase
- May discover things that require PRD changes

### Option B: Run Research During Architecture Phase
**Pros:**
- Faster progression
- Technology evaluation happens at right time

**Cons:**
- Architecture may need revision after research
- Some decisions made without full context

### My Recommendation: **Hybrid Approach**

1. **Run High-Priority Research Now:**
   - Competitive Analysis (informs positioning)
   - SEO Keyword Research (informs content strategy)
   - User Research (validates assumptions)

2. **Defer to Architecture Phase:**
   - Technology Stack Evaluation (right time for this)
   - Technical Feasibility Studies (needs architecture context)

3. **Update PRD After Research:**
   - Incorporate findings into requirements
   - Refine success metrics based on research
   - Update assumptions section

## Next Steps

1. **Decide on Research Priority** - Which research is most critical now?
2. **Run Research Workflows** - Use analyst workflows for competitive analysis, SEO research, user research
3. **Update PRD** - Incorporate findings into requirements
4. **Proceed to Architecture** - With research-informed context

---

**Bottom Line:** Brief identifies research needs, PRD incorporates research findings into requirements. Research can happen in Phase 0 (Discovery) or during Planning/Architecture phases depending on priority.

