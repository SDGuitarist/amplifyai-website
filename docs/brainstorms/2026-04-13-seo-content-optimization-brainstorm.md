# SEO & Content Optimization for amplifyai.to

**Date:** 2026-04-13
**Status:** Brainstorm complete
**Next:** Plan Phase 1 (Technical SEO + Landing Pages + GBP)

## What We're Building

A two-phase SEO and content optimization strategy for amplifyai.to:

**Phase 1 (this project):** Technical SEO fixes, targeted landing pages for key search terms, and Google Business Profile creation/optimization.

**Phase 2 (future):** Full content engine (blog/resources section) + AI search optimization (ChatGPT, Perplexity, Gemini visibility).

## Why This Approach

- Ship what moves the needle now (rankings, local search, conversions), plan the content engine later
- The site already has a solid technical foundation (meta tags, OG, schema) but gaps exist
- Two distinct audience segments need different conversion paths
- Google Business Profile is a high-ROI quick win for local consulting

## Audience Segments & Conversion Paths

### Segment 1: Creatives & Small Business Owners
- **Search terms:** "AI workshops San Diego", "AI for small business", "learn AI for my business"
- **Budget:** Lower -- not likely to hire for consulting directly
- **Conversion path:** Workshop signups (funnel to consulting later)
- **Content need:** Landing page focused on workshops, practical AI skills

### Segment 2: Boutique Hotels / Hospitality
- **Search terms:** "AI consulting hospitality", "AI for boutique hotels", "hotel AI adoption"
- **Budget:** Higher -- can afford consulting/implementation sprints
- **Conversion path:** Direct consultation inquiry
- **Content need:** Landing page with hospitality-specific case studies, complex systems language
- **Note:** Target small-to-mid boutique hotels with multiple properties or complex operations, NOT luxury chains (they don't hire solo operators)

## Current Site Audit Findings

### What's Working
- Meta description, Open Graph tags, Twitter Cards present
- Structured data (ProfessionalService schema) exists
- robots.txt and sitemap.xml in place
- Clean, modern design with good typography

### What Needs Fixing (Phase 1)
1. **Sitemap:** Only lists homepage -- workshop.html missing, no landing pages
2. **No canonical URLs:** Missing `<link rel="canonical">` on all pages
3. **OG image uses relative path:** Should be absolute URL
4. **No favicon**
5. **Title tag:** "AI Dual Literacy" is not a search term anyone uses -- needs keyword optimization
6. **Meta description:** Only targets creatives, needs to also signal hospitality
7. **No dedicated landing pages** for key search queries
8. **No Google Business Profile** exists yet
9. **No internal linking structure** between pages

## Phase 1 Scope

### Technical SEO
- Fix canonical URLs on all pages
- Absolute OG image URLs
- Add favicon
- Optimize title tags and meta descriptions for search terms
- Update sitemap.xml with all pages
- Add FAQ schema markup
- Improve heading hierarchy (H1, H2, H3 structure)
- Page speed audit and fixes

### Landing Pages (3-5 new pages)
- **AI Workshops San Diego** -- targets creatives + small biz, CTA = workshop signup
- **AI Consulting for Hospitality** -- targets boutique hotels, CTA = book consultation
- **About / Credentials** -- builds authority, links to both segments
- Possibly: **AI for Small Business** (if distinct enough from workshops page)
- Possibly: **Case Studies / Results** (even with limited examples)

### Google Business Profile
- Create GBP for Amplify AI
- Set correct category (IT Consulting, Business Consulting)
- Add services, photos, business hours
- Link to website
- Plan for collecting reviews post-workshop

## Phase 2 Roadmap (Future)
- Blog/resources section with regular content
- AI search optimization (structured data for AI crawlers, FAQ-rich content)
- Content calendar tied to workshop schedule
- Case studies as they accumulate
- Email capture / newsletter integration

## Key Decisions
1. **Phase 1 first, Phase 2 later** -- ship technical fixes + landing pages before building content engine
2. **Two audience segments, two conversion paths** -- workshops for creatives/small biz, consulting for hospitality
3. **AI search optimization deferred to Phase 2** -- basics only in Phase 1 (schema, headings)
4. **Google Business Profile included in Phase 1** -- high ROI, local search critical for consulting

## Open Questions
- None remaining -- all resolved through discussion.

## Feed-Forward
- **Hardest decision:** Where to draw the line between Phase 1 and Phase 2. AI search optimization is tempting to include now, but it's evolving fast and would expand scope.
- **Rejected alternatives:** (1) Technical fixes only -- too small to move the needle. (2) Full content engine in one shot -- too much scope, risk of never shipping.
- **Least confident:** Whether the hospitality landing page will convert without real case studies. May need to lead with the Performance Intelligence Protocol framework instead of proof.
