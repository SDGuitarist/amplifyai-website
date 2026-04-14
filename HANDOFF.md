# Amplify AI Website — Handoff

**Date:** 2026-04-14
**Branch:** main
**Phase:** Work (SEO Phase 1 in progress, Writing section shipped)
**Last session:** Blog/Writing section + SEO planning + hospitality research

---

## Current State

Single-page consulting website for Amplify AI is **live** at:
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
24. **Nav updated** — "Writing" link added to homepage nav
25. **Sitemap updated** — all new pages included

### What's Live

**Homepage** (index.html) — 9 sections:
1. Nav (Start Here, Services, Workshops, **Writing**, Contact + social links)
2. Hero (headshot, headline, positioning, CTA)
3. Start Here / Story (Alex's journey, voice-approved)
4. What I Do (3 service cards)
5. Mid CTA
6. Workshops (upcoming + past events)
7. Social Proof (Heather Hilton + credentials)
8. Contact (form + email + phone)
9. Footer

**Workshop page** (workshop.html) — April 25 event detail page

**Writing section** (5 pages) — Dual Literacy essay + 3 education posts + blog index

---

## Next Actions (Priority Order)

### DONE

1. ~~Formspree form~~ (2026-03-30)
2. ~~Domain switchover~~ (2026-03-30)
3. ~~Past workshops section~~ (2026-04-06)
4. ~~Workshop landing page~~ (2026-04-12)
5. ~~Writing/blog section~~ (2026-04-14)

### P0 — Before Berklee Email (April 14)

6. ~~**Writing section live**~~ — Done. 4 essays + blog index at amplifyai.to/blog.html

### P1 — SEO Phase 1 (next session)

Plan doc: `docs/plans/2026-04-13-feat-seo-content-optimization-phase1-plan.md`

7. **Technical SEO fixes** — canonical URLs, absolute OG paths, favicon, title tag optimization, meta descriptions, schema improvements, fix broken internal links, img width/height
8. **hospitality.html** — Proof Stack + trust artifact + dedicated Formspree form. Extract shared CSS from workshop.html incrementally.
9. **workshops.html** — canonical workshop hub (upcoming + past). Homepage becomes teaser only.
10. **about.html** — credentials, Berklee, SDSFF award, Dual Literacy philosophy
11. **Formspree spam protection** — enable before launch
12. **Google Business Profile** — create, optimize, start verification

### P2 — Post Phase 1

13. **Self-host Google Fonts** (stretch, ~100-300ms LCP improvement)
14. **Branded OG images** (1200x630 cards)
15. **Custom 404.html**
16. **Email capture / newsletter system**
17. **Google Analytics (GA4)**
18. **AI search optimization** (Phase 2 from brainstorm)

---

## Key Files

| File | Purpose |
|------|---------|
| `index.html` | Homepage (all sections) |
| `workshop.html` | April 25 workshop detail page |
| `blog.html` | Writing index page |
| `dual-literacy.html` | Flagship essay |
| `blog-ai-literacy-training-gap.html` | Post 1 |
| `blog-what-schools-need.html` | Post 2 |
| `blog-two-skills-educators.html` | Post 3 |
| `styles.css` | Full stylesheet (includes blog/article styles) |
| `content/site-copy.md` | Approved copy draft with Tier 1/Tier 2 labels |
| `content/design-decisions.md` | Design direction, fonts, colors, reference sites |
| `content/hospitality-trust-artifact.md` | Hospitality ops teardown (Alex's version) |
| `docs/brainstorms/2026-04-13-*.md` | SEO brainstorm |
| `docs/plans/2026-04-13-*.md` | SEO Phase 1 plan (deepened + Codex-reviewed) |
| `images/alex-headshot.jpeg` | Hero photo |
| `robots.txt` | SEO (points to amplifyai.to) |
| `sitemap.xml` | SEO (all 7 pages) |
| `CNAME` | Custom domain config for GitHub Pages |

## Design System

- **Fonts:** Fraunces (headings, 600/700) + DM Sans (body, 400/500)
- **Background:** `#F5F0EB` (warm linen)
- **Text:** `#2C2421` (warm dark brown)
- **Accent:** `#B8703F` (cognac)
- **Secondary:** `#8B7355` (muted bronze)
- **Surface:** `#E8DDD3` (card backgrounds)

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
Read HANDOFF.md and docs/plans/2026-04-13-feat-seo-content-optimization-phase1-plan.md.
Continue P1 SEO work: technical SEO fixes on existing pages, then hospitality.html.
```
