# Amplify AI Website — Handoff

**Date:** 2026-03-28
**Branch:** main
**Phase:** Work (Phase D complete, Phase E pending)
**Last session:** Full site built and live at project URL

---

## Current State

Single-page consulting website for Amplify AI is **live** at:
- **Project URL:** https://sdguitarist.github.io/amplifyai-website/
- **Custom domain:** `amplifyai.to` (DNS resolving to GitHub Pages IPs, domain NOT yet attached to repo)

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

### What's Live

7 sections on the page:
1. Nav (Start Here, Services, Workshops, Contact + social links)
2. Hero (headshot, headline, positioning, CTA)
3. Start Here / Story (Alex's journey, voice-approved)
4. What I Do (3 service cards)
5. Mid CTA
6. Workshops (Film Festival Apr 4 + Amplify Apr 25)
7. Social Proof (Heather Hilton + credentials)
8. Contact (form + email + phone)
9. Footer

---

## Next Actions (Priority Order)

### P0 — Before April 4 (Film Festival)

1. **Connect Formspree form ID** — Create account at formspree.io, get form ID, update `action` URL in index.html. The form displays but doesn't submit without this.
2. **Domain switchover** — One commit: add `CNAME` file + update 5 absolute URLs (og:url, og:image, JSON-LD url, robots.txt Sitemap, sitemap.xml loc). See plan Phase E Step 2 for exact checklist.
3. **Verify at custom domain** — Test at `amplifyai.to` after switchover. Check mobile, OG tags, contact links.

### P1 — Before April 25 (Amplify Workshop)

4. **Add past workshops** — FilmNet AI filmmaking panel + Los Angeles Classical Guitar Festival Workshop. Create a "Past Events" section or integrate into Workshops section.
5. **Phase 2 build** — "For Businesses" page, Projects/Portfolio, Google Analytics, enhanced design polish.
6. **Update Amplify Workshop price** — Verify $150 is correct post-early-bird.

### P2 — Post April 25

7. **LinkedIn post** — "Built a consulting website in one session" (see ideas.md)
8. **Video tutorial** — Walk through the website build workflow for content/course
9. **Gated content** — Package video + guide + prompt templates on amplifyai.to
10. **Phase 3** — Blog, free resources, link hub, `amplifyai.me` redirect

---

## Key Files

| File | Purpose |
|------|---------|
| `index.html` | Single-page site (all sections) |
| `styles.css` | Full stylesheet (Fraunces + DM Sans, warm linen palette) |
| `content/site-copy.md` | Approved copy draft with Tier 1/Tier 2 labels |
| `content/design-decisions.md` | Design direction, fonts, colors, reference sites |
| `images/alex-headshot.jpeg` | Hero photo |
| `robots.txt` | SEO (uses project URL, update on switchover) |
| `sitemap.xml` | SEO (uses project URL, update on switchover) |
| `CNAME` | Does NOT exist yet. Add on domain switchover. |

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
| `amplifyai.to` | Porkbun | $51.80/yr, expires 2027-03-28 | DNS configured, not attached to repo |
| `amplifyai.me` | GoDaddy | $29.99/yr, expires 2027-03-28 | Purchased, no DNS configured |

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
5. **Formspree** — account will need to be created (not yet set up)
6. **Related project:** `amplify-workshop-assets` has the brainstorm + plan docs

## Session Start Prompt

```
Read ~/Projects/amplifyai-website/HANDOFF.md.
Continue from Phase E: domain switchover + Formspree setup.
```
