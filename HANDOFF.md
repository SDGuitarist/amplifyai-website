# Amplify AI Website — Handoff

**Date:** 2026-04-14
**Branch:** main
**Phase:** Work (SEO Phase 1 — Steps 1-6 complete, pre-launch tasks remain)
**Last session:** SEO Phase 1 implementation — technical fixes, 3 new landing pages, homepage updates

---

## Current State

Multi-page consulting website for Amplify AI is **live** at:
- **Live URL:** https://amplifyai.to
- **GitHub Pages:** https://sdguitarist.github.io/amplifyai-website/ (redirects to custom domain)
- **Backup domain:** `amplifyai.me` (GoDaddy, forwarding to amplifyai.to — set by user)

### What Was Done (March 28)

1. **Brainstormed** brand identity, target market, phased launch strategy
2. **Codex-reviewed** brainstorm (two rounds of fixes applied)
3. **Planned** MVP build with 5 phases, copy safety tiers, DNS fallback strategy
4. **Codex-reviewed** plan (5 fixes applied)
5. **Created repo** `SDGuitarist/amplifyai-website` with GitHub Pages enabled
6. **Purchased domains:** `amplifyai.to` (Porkbun) + `amplifyai.me` (GoDaddy)
7. **Configured DNS** at Porkbun (4 A records + CNAME, verified resolving)
8. **Drafted all copy** in `content/site-copy.md` with Tier 1/Tier 2 safety labels
9. **Voice-reviewed copy** via Claude AI Project (5 fixes applied)
10. **Researched design** with 3 parallel agents (8 reference sites, 3 design directions, 4 font pairings)
11. **Built full site:** index.html + styles.css with all sections
12. **Added Film Festival Workshop** card (April 4, Industry Tap Room, Escondido, free)
13. **Added contact form** (Formspree, ID not yet connected)

### What Was Done (March 30)

14. **Connected Formspree** — form ID `xpqodrkv`, email verified, test submission received
15. **Domain switchover** — CNAME file added, all URLs updated to `amplifyai.to`, HTTPS verified
16. **Social media logos** — replaced text links with inline SVG icons (LinkedIn + Instagram) in nav

### What Was Done (April 12)

17. **Workshop landing page** — dedicated `workshop.html` for April 25 ad campaign

### What Was Done (April 13-14)

18. **SEO brainstorm** — `docs/brainstorms/2026-04-13-seo-content-optimization-brainstorm.md`
19. **SEO plan** — `docs/plans/2026-04-13-feat-seo-content-optimization-phase1-plan.md` (deepened + Codex-reviewed)
20. **Hospitality research** — AI in guest experiences, boutique hotel operator challenges
21. **Hospitality trust artifact** — `content/hospitality-trust-artifact.md` (Alex's version, 30-year event producer angle)
22. **Writing section shipped** — 5 new pages:
    - `blog.html` — Writing index
    - `dual-literacy.html` — Flagship essay (Dual Literacy framework, Culture Stack)
    - `blog-ai-literacy-training-gap.html` — Post 1
    - `blog-what-schools-need.html` — Post 2
    - `blog-two-skills-educators.html` — Post 3
23. **Blog CSS** — article styles, blog grid, highlight boxes, author box, CTA added to `styles.css`

### What Was Done (April 14 — SEO Phase 1)

24. **Writing CTA** — link card section added to homepage between Social Proof and Contact
25. **Technical SEO fixes** across all pages:
    - Canonical URLs on all 7 existing pages
    - Absolute OG/Twitter image paths everywhere
    - Title optimized: "AI Consulting & Workshops in San Diego | Amplify AI"
    - Meta description updated with hospitality mention and CTA verb
    - Schema improved: areaServed, priceRange, image, knowsAbout, alumniOf (Berklee)
    - Workshop schema: image property added
    - Broken workshop link fixed (github.io -> ./workshop.html)
    - Workshop nav brand fixed (# -> /)
    - SVG favicon created and linked on all pages
    - Sitemap lastmod dates updated
26. **hospitality.html** — new landing page targeting boutique hotel operators:
    - Proof Stack pattern (specificity, credentials, testimonial, process transparency)
    - Worked trust artifact (Guest Experience Calendar example)
    - "Who This Is NOT For" negative qualification section
    - 3 CTA placements (hero, after proof, sticky bottom bar)
    - Dedicated Formspree form with `source=hospitality` hidden field
    - Service schema with areaServed
    - **NOTE: Formspree form ID is placeholder `HOSPITALITY_FORM_ID` — needs real ID**
27. **workshops.html** — canonical workshop hub:
    - Upcoming events (April 25) with link to workshop.html detail page
    - Past events (SDSFF Apr 4 & 11, FilmNet Oct 2025, LAGF May 2025)
    - Persona cards, brief about section
    - ItemList schema with EducationEvent entries
28. **about.html** — credentials and philosophy page:
    - Full story (expanded from homepage "Start Here")
    - Credentials (Berklee, SDSFF award, 2500+ events, workshop history)
    - AI Dual Literacy philosophy with link to essay
    - Person schema with knowsAbout, alumniOf, award
29. **Homepage updates:**
    - Nav links to /workshops.html hub instead of #workshops anchor
    - Nav brand links to / instead of #
    - Workshop section reduced to single upcoming event teaser
    - Past events removed (live on workshops.html)
30. **Shared CSS extracted** — `.landing-*` components moved from workshop.html inline styles to styles.css (hero grid, persona cards, proof section, CTA/register, bottom bar, process steps, not-for list)
31. **Sitemap updated** — 10 pages total

### What's Live

**Homepage** (index.html) — 9 sections:
1. Nav (Start Here, Services, Workshops, Writing, Contact + social links)
2. Hero (headshot, headline, positioning, CTA)
3. Start Here / Story (Alex's journey, voice-approved)
4. What I Do (3 service cards)
5. Mid CTA
6. Workshops (teaser — 1 upcoming event + link to hub)
7. Social Proof (Heather Hilton + credentials)
8. Writing (link card to /blog.html)
9. Contact (form + email + phone)
10. Footer

**Workshop detail** (workshop.html) — April 25 event page (focused nav, inline styles)

**Workshops hub** (workshops.html) — All upcoming + past events

**Hospitality** (hospitality.html) — Boutique hotel consulting landing page

**About** (about.html) — Credentials, story, philosophy

**Writing section** (5 pages) — Dual Literacy essay + 3 education posts + blog index

---

## Next Actions (Priority Order)

### DONE

1. ~~Formspree form~~ (2026-03-30)
2. ~~Domain switchover~~ (2026-03-30)
3. ~~Past workshops section~~ (2026-04-06)
4. ~~Workshop landing page~~ (2026-04-12)
5. ~~Writing/blog section~~ (2026-04-14)
6. ~~Writing section live / Berklee email~~ (2026-04-14)
7. ~~Technical SEO fixes~~ (2026-04-14)
8. ~~hospitality.html~~ (2026-04-14)
9. ~~workshops.html~~ (2026-04-14)
10. ~~about.html~~ (2026-04-14)
11. ~~Homepage nav + workshop teaser~~ (2026-04-14)
12. ~~Sitemap (all 10 pages)~~ (2026-04-14)

### P0 — Review Fixes Applied (2026-04-14)

13. ~~**Hospitality form fixed**~~ — Uses shared Formspree ID `xpqodrkv` with `source=hospitality` hidden field for attribution. Dedicated form can be created later for separate inbox routing.
14. ~~**Spam protection added**~~ — Honeypot (`_gotcha`) field on both homepage and hospitality forms. Formspree's built-in spam filtering is also active on form `xpqodrkv`.
15. ~~**Trust artifact reworked**~~ — Operator-grade ops teardown with explicit inputs (PMS data, review analysis, vendor contracts), concrete deliverable excerpts (property identity brief), staff execution playbooks, hospitality terminology (RevPAR, keys, OTA, F&B uplift).
16. ~~**Nav standardized**~~ — About link added to full-site nav on all pages. "Back to all workshops" link on workshop.html. Workshops.html links to about.html.
17. ~~**Security fixes**~~ — Personal email removed from schema markup and raw mailto: link removed from homepage contact section. Phone + form are the contact paths.

### P0 — Still Blocking

### P1 — Soon After Launch

15. **Google Business Profile** — Create, optimize, start verification (manual, non-code — see plan Workstream 4)
16. **Workshop.html CSS cleanup** — Migrate remaining inline `<style>` to use shared `.landing-*` classes (optional, cosmetic)
17. **Homepage Step 5 tweaks** — Hero tagline update (add hospitality mention), services card linking, nav order finalization (deferred per user request)

### P2 — Post Phase 1

18. **Self-host Google Fonts** (stretch, ~100-300ms LCP improvement)
19. **Branded OG images** (1200x630 cards)
20. **Custom 404.html**
21. **Email capture / newsletter system**
22. **Google Analytics (GA4)**
23. **AI search optimization** (Phase 2 from brainstorm)

---

## Key Files

| File | Purpose |
|------|---------|
| `index.html` | Homepage (hub + teaser sections) |
| `workshop.html` | April 25 workshop detail page (focused nav) |
| `workshops.html` | Workshop listing hub (upcoming + past) |
| `hospitality.html` | Boutique hotel consulting landing page |
| `about.html` | Credentials, story, philosophy |
| `blog.html` | Writing index page |
| `dual-literacy.html` | Flagship essay |
| `blog-ai-literacy-training-gap.html` | Post 1 |
| `blog-what-schools-need.html` | Post 2 |
| `blog-two-skills-educators.html` | Post 3 |
| `styles.css` | Full stylesheet (includes shared `.landing-*` components) |
| `favicon.svg` | SVG favicon ("A" lettermark in cognac) |
| `content/site-copy.md` | Approved copy draft with Tier 1/Tier 2 labels |
| `content/design-decisions.md` | Design direction, fonts, colors, reference sites |
| `content/hospitality-trust-artifact.md` | Hospitality ops teardown (Alex's version) |
| `docs/brainstorms/2026-04-13-*.md` | SEO brainstorm |
| `docs/plans/2026-04-13-*.md` | SEO Phase 1 plan (deepened + Codex-reviewed) |
| `images/alex-headshot.jpeg` | Hero photo |
| `images/sdsff-alex-presenting.jpg` | Workshop OG image |
| `images/sdsff-room-wide.jpg` | Workshop photo |
| `robots.txt` | SEO (points to amplifyai.to) |
| `sitemap.xml` | SEO (all 10 pages) |
| `CNAME` | Custom domain config for GitHub Pages |

## Design System

- **Fonts:** Fraunces (headings, 600/700) + DM Sans (body, 400/500)
- **Background:** `#F5F0EB` (warm linen)
- **Text:** `#2C2421` (warm dark brown)
- **Accent:** `#B8703F` (cognac)
- **Secondary:** `#8B7355` (muted bronze)
- **Surface:** `#E8DDD3` (card backgrounds)

## Formspree Forms

| Form | ID | Location | Purpose |
|------|----|----------|---------|
| Homepage contact | `xpqodrkv` | index.html | General inquiries. Honeypot (`_gotcha`) enabled. |
| Hospitality | `xpqodrkv` (shared) | hospitality.html | Attributed via hidden `source=hospitality` field. Honeypot (`_gotcha`) enabled. Dedicated form ID optional upgrade. |

## Domain Info

| Domain | Registrar | Renewal | Status |
|--------|-----------|---------|--------|
| `amplifyai.to` | Porkbun | $51.80/yr, expires 2027-03-28 | Live, HTTPS active |
| `amplifyai.me` | GoDaddy | $29.99/yr, expires 2027-03-28 | 301 forwarding to amplifyai.to |

## Related Docs (in amplify-workshop-assets repo)

- Brainstorm: `docs/brainstorms/2026-03-28-amplify-ai-consulting-website-brainstorm.md`
- Plan: `docs/plans/2026-03-28-feat-amplify-ai-consulting-website-mvp-plan.md`
- Brand voice: `context/brand-voice.md`

---

## Laptop Transfer Notes

This project must be cloned to the new laptop. Key things:

1. **Repo:** `git clone https://github.com/SDGuitarist/amplifyai-website.git`
2. **All code is on GitHub** — nothing local-only. Safe to clone fresh.
3. **DNS is at Porkbun** — login credentials needed for domain management
4. **GoDaddy** — `amplifyai.me` domain management
5. **Formspree** — account active (alex@alexguillenmusic.com), form ID: `xpqodrkv`
6. **Related project:** `amplify-workshop-assets` has the brainstorm + plan docs

## Session Start Prompt

```
cd /Users/alejandroguillen/Projects/amplifyai-website
Read HANDOFF.md.
P0: Create hospitality Formspree form, replace placeholder ID, enable spam protection on both forms.
P1: Google Business Profile setup, workshop.html CSS cleanup, homepage Step 5 tweaks.
```
