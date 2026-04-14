---
title: "SEO Phase 1: Landing Pages, Proof Stack Pattern, and Trust Artifact Design"
type: web-patterns
status: resolved
date: 2026-04-14
project: amplifyai-website
tags: [seo, landing-pages, css-architecture, trust-artifact, formspree, static-html]
origin: docs/plans/2026-04-13-feat-seo-content-optimization-phase1-plan.md
---

# SEO Phase 1: Landing Pages, Proof Stack Pattern, and Trust Artifact Design

## Problem

A static HTML consulting website needed to go from 2 pages to 10, targeting two distinct audience segments (creatives and boutique hotels), without a build step, framework, or CMS. Key challenges:

1. Technical SEO was incomplete (no canonical URLs, relative OG paths, weak title/schema)
2. No landing pages existed for the actual search terms people use
3. The highest-value page (hospitality) had no case studies or client proof
4. CSS was split between a shared stylesheet and large inline blocks on workshop.html
5. Navigation was inconsistent across pages with no shared include system

## What Worked

### 1. Incremental CSS extraction over upfront refactor

**Decision:** Extract shared `.landing-*` CSS components from workshop.html's inline styles *while building the first new page* (hospitality.html), not as a separate workstream.

**Why it worked:** The alternative (refactor workshop.html first, then build pages) would have risked breaking the live event page 11 days before a workshop. By extracting only what the new page needed, each component was immediately tested in context. Workshop.html kept its inline styles intact and still renders correctly.

**Pattern:** When adding pages to a static site, extract shared CSS on demand. Don't pre-extract components you haven't tested on a real page.

### 2. Proof Stack pattern for landing pages without case studies

**The problem:** The hospitality page needed to close boutique hotel operators, but there were zero clients and zero case studies. Generic "trust us" copy wouldn't work.

**The Proof Stack (4 layers, in order):**
1. **Specificity of problem.** Name the exact pain in the prospect's language ("Your team spends hours reconciling bookings across 3 properties"). Specificity signals experience without needing a case study.
2. **Credential anchors.** One line of hard facts: years, events, education, awards. Real photo.
3. **Micro-testimonials.** Even from adjacent domains. Specific outcome quotes beat long stories.
4. **Process transparency.** Show the engagement model step-by-step. Prospects buy process, not promises.

**Key lesson:** The Proof Stack framework alone is not enough. It needs a concrete trust artifact (see Risk Resolution below).

### 3. Operator-grade trust artifact over generic hypothetical

**First attempt (failed):** Narrative summary ("we'd build a system that pulls from a curated database..."). Read like a pitch deck, not a deliverable.

**What worked:** An ops teardown formatted as an actual consulting deliverable:
- Named explicit inputs a GM would recognize (PMS data, TripAdvisor keyword extraction, vendor contract terms)
- Included a concrete property identity brief excerpt with industry metrics (42 keys, 2.3-night avg stay, Tablet Hotels as booking source)
- Showed what deliverables actually contain (90-day calendar with events tagged by type, F&B revenue projections, cross-property conflict flags)
- Staff playbooks in checklist format with specific touchpoint scripts

**Pattern:** When you don't have case studies, show what the deliverable looks like. Specificity of output beats vagueness of promise. Use the prospect's vocabulary (RevPAR, keys, OTA, F&B uplift), not yours.

### 4. Shared Formspree form with hidden source field for attribution

**Decision:** Use one Formspree form (`xpqodrkv`) across both homepage and hospitality page, with a hidden `source=hospitality` field for attribution.

**Why:** Creating a dedicated form required account access that wasn't available during the work session. The hidden field provides attribution without blocking launch. A dedicated form can be created later for inbox routing.

**Pattern:** Don't let "ideal infrastructure" block launch. Hidden fields on shared forms give you attribution data now. Upgrade to separate forms when the volume justifies it.

### 5. Honeypot spam protection over reCAPTCHA

**Decision:** Added `_gotcha` honeypot field (hidden via `display:none`) instead of reCAPTCHA.

**Why:** Zero JavaScript policy on the site. reCAPTCHA requires JS. Formspree's `_gotcha` honeypot catches most bots without any user friction or JS dependency.

### 6. Nav duplication with type comments

**Pattern:** Static HTML sites without includes need duplicated nav blocks. Mark each with `<!-- NAV: full-site -->` or `<!-- NAV: event-focused -->` so edits stay in sync. At 10 pages this is manageable. Revisit at 15+.

## What Didn't Work

### 1. Planning for a dedicated Formspree form that couldn't be created

The plan specified a dedicated hospitality Formspree form, but creating it required account login during the session. The placeholder `HOSPITALITY_FORM_ID` shipped as a broken form endpoint. Lesson: if a dependency requires human action (account login, API key creation), flag it as a pre-work item, not an in-session task.

### 2. Blog page navs diverged from site nav pattern

The blog pages (built in a prior session) used a different nav order (Writing first) from the site-wide pattern. This wasn't caught until the review phase. Lesson: when adding pages in separate sessions, verify nav consistency across all pages, not just the ones you're touching.

## Risk Resolution

**Flagged risk (brainstorm):** "Whether the hospitality landing page will convert without real case studies."

**Flagged risk (plan):** "The hospitality landing page copy may not convert without real case studies. We're betting that the Proof Stack pattern plus a concrete trust artifact is enough."

**Feed-Forward (plan):** `verify_first: true` — "Hospitality landing page may not convert without real case studies. Lead with Performance Intelligence Protocol framework instead of proof."

**What actually happened:**
1. First version of the trust artifact was a narrative summary. Review correctly flagged it as not operator-grade.
2. Reworked to an ops teardown with industry-specific inputs, deliverable excerpts, and hospitality terminology.
3. The page now reads as a consulting proposal preview, not a marketing pitch.

**Lesson learned:** "Lead with framework" (the plan's mitigation) was necessary but not sufficient. The framework needed to be expressed as a concrete deliverable sample, not described abstractly. The artifact's credibility comes from specificity of outputs and use of the prospect's vocabulary, not from the framework name.

**Measurable outcome:** Hospitality inquiry count via `source=hospitality` field. Baseline: 0. Target: >= 1 within 60 days. No data yet (just launched).

## Files and Architecture

| Component | Location | Notes |
|-----------|----------|-------|
| Shared landing CSS | `styles.css` (`.landing-*` prefix) | Extracted from workshop.html inline styles |
| Hospitality page | `hospitality.html` | Proof Stack + ops teardown artifact |
| Workshops hub | `workshops.html` | Canonical listing, homepage is teaser only |
| About page | `about.html` | Credentials, philosophy, Person schema |
| SVG favicon | `favicon.svg` | "A" lettermark in cognac, no PNG needed |
| Sitemap | `sitemap.xml` | 10 pages, all with lastmod dates |

## Applies To

- Any static HTML site adding landing pages without a build step
- Consulting/service pages without case studies or client proof
- Multi-page static sites needing consistent navigation
- Formspree forms needing attribution across multiple pages
