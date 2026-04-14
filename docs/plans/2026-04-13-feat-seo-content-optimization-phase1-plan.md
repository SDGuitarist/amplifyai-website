---
title: "feat: SEO & Content Optimization Phase 1"
type: feat
status: active
date: 2026-04-13
origin: docs/brainstorms/2026-04-13-seo-content-optimization-brainstorm.md
feed_forward:
  risk: "Hospitality landing page may not convert without real case studies. Lead with Performance Intelligence Protocol framework instead of proof."
  verify_first: true
---

# feat: SEO & Content Optimization Phase 1

## Enhancement Summary

**Deepened on:** 2026-04-13
**Revised on:** 2026-04-13 (Codex plan review findings applied)
**Research agents used:** SEO best practices, GBP optimization, landing page conversion, performance, security, simplicity

### Key Improvements (from deepening)
1. **"Proof Stack" pattern** for hospitality page -- 4-layer trust structure + required concrete hospitality trust artifact
2. **GBP categories corrected** -- "IT Consultant" primary, not "Business management consultant"
3. **Title tag format standardized** -- "Primary Keyword + Location | Brand"
4. **Formspree spam protection** required before launch
5. **Dedicated hospitality Formspree form** for measurable conversion attribution

### Key Revisions (from Codex review)
1. **Success criteria fixed** -- Rich Results Test only for eligible pages, schema validator for rest. Hospitality inquiries measured via dedicated form with `source` field.
2. **Hospitality trust artifact required** -- generic creative proof not enough. Must include sample deliverable, ops teardown, or hospitality-adjacent testimonial.
3. **Core vs. Stretch separated** -- self-hosted fonts, branded OG images, custom 404, email capture moved to optional stretch.
4. **CSS architecture contradiction resolved** -- extraction happens incrementally while building pages, not as separate upfront workstream.
5. **workshops.html role clarified** -- canonical workshop hub. Homepage = teaser only. workshop.html = event detail.
6. **Plan Quality Gate fixed** -- "what must not change" lists actual invariants, acknowledges copy WILL change.
7. **Nav model per page type** -- workshop.html keeps focused event nav, new pages get full site nav.
8. **Calendly assumption removed** -- Formspree is the primary CTA mechanism. No unconfirmed dependencies.

## Overview

Optimize amplifyai.to for search visibility, local discovery, and conversion across two audience segments. Phase 1 covers technical SEO fixes on existing pages, three new targeted landing pages, and Google Business Profile creation.

Phase 2 (future, out of scope) will add a blog/content engine and AI search optimization.

## Problem Statement / Motivation

The site has solid design and copy but is nearly invisible to search engines:
- Title tag uses "AI Dual Literacy" -- a term nobody searches for
- Only 1 of 2 pages is in the sitemap
- No canonical URLs, no favicon, broken internal links
- No dedicated landing pages for the search terms people actually use ("AI consulting San Diego", "AI workshops San Diego", "AI for boutique hotels")
- No Google Business Profile exists -- critical for local consulting
- The workshop link on the homepage points to the old GitHub Pages URL, not workshop.html

(see brainstorm: docs/brainstorms/2026-04-13-seo-content-optimization-brainstorm.md)

## Proposed Solution

Three workstreams (CSS extraction happens incrementally during page building, not as a separate step):

1. **Technical SEO Fixes** -- fix existing pages (canonical, OG paths, favicon, title, sitemap, links)
2. **Landing Pages** -- three new pages targeting specific search queries (CSS components extracted from workshop.html as needed)
3. **Google Business Profile** -- create and optimize GBP (manual, non-code)

## Plan Quality Gate

1. **What exactly is changing?** Technical SEO tags on index.html and workshop.html. Shared landing-page CSS classes added to styles.css (incrementally, while building pages). Three new HTML pages. Favicon. Updated sitemap.xml. Google Business Profile created externally.
2. **What must not change?**
   - Design system (Fraunces + DM Sans fonts, warm linen color palette, 780px content column)
   - Brand voice (no em-dashes, banned word list, peer conversation tone per `content/site-copy.md`)
   - Zero-JavaScript architecture (no JS except JSON-LD schema)
   - Formspree form integration (form ID xpqodrkv must keep working)
   - Domain/DNS configuration (amplifyai.to via Porkbun, HTTPS)
   - Factual event details (workshop dates, prices, venue, capacity)
   - Note: homepage copy (titles, meta descriptions, nav structure) WILL change -- that is the point of this project.
3. **How will we know it worked?**
   - Lighthouse SEO score >= 90 on all pages (target 95, accept 90)
   - Rich Results Test passes for pages with eligible schema: workshop.html (EducationEvent), hospitality.html (Service). Other pages validated via manual JSON-LD check or schema.org validator.
   - Hospitality consultation inquiries attributable via dedicated Formspree form with `source: hospitality` hidden field (see Workstream 3b). Baseline: 0 today. Target: >= 1 attributed inquiry within 60 days.
   - Sitemap includes all live pages with accurate lastmod dates
   - OG images render correctly when shared (test via Facebook Sharing Debugger / Twitter Card Validator)
   - GBP live and verification process started
   - All internal links return 200 (no 404s)
4. **What is the most likely way this plan is wrong?** The hospitality landing page copy may not convert without real case studies. We're betting that the Proof Stack pattern (specificity + credentials + micro-testimonials + process transparency) plus a concrete trust artifact (hospitality ops teardown example) is enough. If it's not, we'll know from zero attributed consultation inquiries after 60 days via the dedicated Formspree form.

---

## CSS Architecture (Not a Separate Workstream)

### Decision: One styles.css, extracted incrementally

- Keep one `styles.css` file. No separate `landing.css`. No build step.
- Shared landing-page classes (`.landing-hero`, `.persona-card`, `.landing-proof`, `.landing-register`, `.bottom-cta`, etc.) are extracted from workshop.html's inline styles **while building hospitality.html** (the first new page).
- This is NOT a separate upfront refactor. When building hospitality.html, identify which workshop.html inline styles are reusable, move those to styles.css, and reference them from both pages.
- After hospitality.html ships, workshop.html's inline `<style>` block should be reduced to page-specific overrides only.
- CSS at ~800 lines (~13KB) is fine as one file. GitHub Pages gzips it to ~3-4KB. Only reconsider splitting at 30KB+.

### Component extraction reference

These components in workshop.html's inline styles are candidates for extraction as they're needed by new pages:

| Component | workshop.html Lines | Proposed Class | Reused By |
|-----------|-------------------|----------------|-----------|
| Page hero grid | 37-80 | `.landing-hero` | hospitality, workshops, about |
| Persona cards | 82-130 | `.persona-card`, `.persona-grid` | hospitality, workshops |
| Proof/testimonial | 172-195 | `.landing-proof` | hospitality, workshops, about |
| Register/CTA section | 197-240 | `.landing-register` | hospitality, workshops |
| Fixed bottom CTA bar | 242-280 | `.bottom-cta` | hospitality |

Extract only what's needed by the page being built. Do not pre-extract unused components.

### Acceptance criteria

- [ ] Shared classes use `.landing-*` prefix in styles.css
- [ ] workshop.html inline `<style>` reduced to page-specific overrides (< 50 lines) after all pages ship
- [ ] workshop.html renders identically before and after extraction (visual check)
- [ ] No hardcoded colors or fonts -- use CSS custom properties from `:root`

---

## Workstream 2: Technical SEO Fixes

### 2a. Canonical URLs

Add to both pages:
```html
<!-- index.html -->
<link rel="canonical" href="https://amplifyai.to/">

<!-- workshop.html -->
<link rel="canonical" href="https://amplifyai.to/workshop.html">
```

### 2b. Absolute OG/Twitter Image Paths

Change on both pages:
```html
<!-- Before -->
<meta property="og:image" content="./images/alex-headshot.jpeg">

<!-- After -->
<meta property="og:image" content="https://amplifyai.to/images/alex-headshot.jpeg">
```

Same for `twitter:image` tags.

### 2c. Favicon

Create a simple favicon. Add to all pages:
```html
<link rel="icon" type="image/png" href="/favicon.png">
```

**Decision:** Single 32x32 PNG. Generate a simple "A" lettermark using the Fraunces font in cognac (#B8703F) on transparent background. Apple touch icon and multi-size favicons are stretch items.

### 2d. Title Tag Optimization

**Research insight:** Use format "Primary Keyword + Location | Brand" -- front-load the keyword, keep under 60 characters.

| Page | Current Title | New Title | Chars |
|------|--------------|-----------|-------|
| index.html | "Amplify AI \| AI Dual Literacy" | "AI Consulting & Workshops in San Diego \| Amplify AI" | 53 |
| workshop.html | "Amplify: The Power of Human-Led AI \| April 25, San Diego" | Keep as-is (event-specific, good) | 58 |

### 2e. Meta Description Updates

**Research insight:** Include a CTA verb in every meta description. Stay 130-155 characters.

| Page | Current | New | Chars |
|------|---------|-----|-------|
| index.html | "AI consulting and workshops for creative businesses and small teams. Built by a musician who runs his business on 5 AI apps. San Diego." | "AI consulting and workshops for creative businesses and boutique hotels in San Diego. Built by a musician running 5 AI apps daily. Book a free intro call." | 155 |

Workshop page description is already strong -- keep as-is.

### 2j. Add width/height Attributes to Images

**Why:** Missing width/height on `<img>` tags causes Cumulative Layout Shift (CLS), a Core Web Vitals penalty.

**Fix:** Add explicit `width` and `height` attributes to every `<img>` tag matching actual display dimensions.

### 2f. Update OG Tags to Match

Update `og:title` and `og:description` on index.html to match the new title and description.

### 2g. Sitemap Update

```xml
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
  <url>
    <loc>https://amplifyai.to/</loc>
    <lastmod>2026-04-13</lastmod>
    <priority>1.0</priority>
  </url>
  <url>
    <loc>https://amplifyai.to/workshop.html</loc>
    <lastmod>2026-04-12</lastmod>
    <priority>0.9</priority>
  </url>
  <!-- New landing pages added as they're created -->
</urlset>
```

### 2h. Fix Internal Links

| Location | Current | Fix |
|----------|---------|-----|
| index.html line 169 | Links to `sdguitarist.github.io/amplify-workshop-assets/07-website-hero.html` | Change to `./workshop.html` |
| workshop.html nav brand (line 466) | Links to `#` | Change to `https://amplifyai.to/` |

### 2i. Schema Markup Improvements

**Research insight:** Google's AI Mode (Gemini) now uses schema to verify claims and assess source credibility for AI Overview citations. Accurate, complete schema matters beyond traditional rich results.

Add missing properties to existing schema:

**index.html ProfessionalService:**
- Add `"areaServed": {"@type": "City", "name": "San Diego"}`
- Add `"priceRange": "$$"`
- Add `"image": "https://amplifyai.to/images/alex-headshot.jpeg"`
- Add `"knowsAbout": ["Artificial Intelligence", "AI Automation", "Business Process Optimization"]`
- Add `"hasOfferCatalog"` with services listed as `Offer` items
- Add `"openingHours"` (or "by appointment" indicator)

**workshop.html EducationEvent:**
- Add `"image": "https://amplifyai.to/images/sdsff-alex-presenting.jpg"`
- Verify all required properties present: `startDate` (ISO 8601), `endDate`, `location`, `offers` with price/currency/availability -- without these, Google ignores the event entirely

**Person schema (founder):**
- Add `"knowsAbout"`, `"award"` (SDSFF "A Cut Above"), `"alumniOf"` if applicable

### Files changed

- `index.html` -- canonical, OG paths, title, meta description, OG tags, schema, internal link fix, favicon link
- `workshop.html` -- canonical, OG paths, schema, nav brand link fix, favicon link
- `sitemap.xml` -- add workshop.html, update lastmod dates
- New file: `favicon.png` (single 32x32 PNG is sufficient for Phase 1)

### Security Note (from Security Review)

- **Enable Formspree spam protection** (honeypot field or reCAPTCHA) before launch. Without it, forms get spammed within days.
- Use a dedicated business email in schema markup, not a personal email. Schema PII WILL be scraped by bots.
- Do not add raw `mailto:` links in HTML. Use Formspree as the contact channel.

### Acceptance criteria

- [ ] Both pages have `<link rel="canonical">` with correct absolute URLs
- [ ] All OG and Twitter image paths are absolute (`https://amplifyai.to/...`)
- [ ] Favicon displays in browser tab on all pages
- [ ] index.html title starts with primary keyword, contains "San Diego"
- [ ] index.html meta description includes a CTA verb and mentions hospitality
- [ ] sitemap.xml lists all pages with current lastmod dates
- [ ] Homepage workshop link goes to `./workshop.html`
- [ ] Workshop nav brand links to homepage
- [ ] All `<img>` tags have explicit width/height attributes
- [ ] Formspree has spam protection enabled
- [ ] Rich Results Test passes for workshop.html (EducationEvent) and hospitality.html (Service)
- [ ] JSON-LD validated via schema.org validator for all other pages
- [ ] Lighthouse SEO score >= 90 on all pages (target 95)

---

## Workstream 3: Landing Pages

### Navigation model (per page type)

Not all pages need the same nav. The nav should match the page's conversion goal:

| Page | Nav Type | Rationale |
|------|----------|-----------|
| index.html | Full site nav (Workshops, Consulting, About, Contact) | Discovery/hub page, users explore |
| workshops.html | Full site nav | Discovery page, users explore |
| hospitality.html | Full site nav | Users may want to learn more before converting |
| about.html | Full site nav | Authority page, links everywhere |
| workshop.html | Focused event nav (brand -> home, #who, #takeaway, #register) | **Keep as focused conversion page.** On-page anchors reduce distraction. Adding full site nav risks pulling users away from registration. Only add a subtle "Back to all workshops" link. |

Nav HTML is duplicated per page (no includes in static HTML). Keep a `<!-- NAV: full-site -->` or `<!-- NAV: event-focused -->` comment at the top of each nav block so edits stay in sync.

### Shared HTML template for new pages

```
<!DOCTYPE html>
<html lang="en">
<head>
  <!-- Standard meta (charset, viewport) -->
  <!-- SEO (title, description, canonical) -->
  <!-- Open Graph + Twitter Cards -->
  <!-- Favicon -->
  <!-- Styles: styles.css (includes shared landing components) -->
  <!-- Schema markup (JSON-LD) -->
</head>
<body>
  <nav> <!-- full-site nav or event-focused nav per table above --> </nav>
  <section class="landing-hero"> <!-- page-specific hero --> </section>
  <section> <!-- page-specific content sections --> </section>
  <section class="landing-proof"> <!-- testimonials/credentials --> </section>
  <section class="landing-register"> <!-- CTA section --> </section>
  <footer> <!-- shared footer --> </footer>
</body>
</html>
```

### 3a. workshops.html -- "AI Workshops San Diego"

**Role clarification -- the three workshop-related pages:**
- **index.html** = teaser/summary only. Brief "Upcoming Workshops" section with 1-2 event cards linking out. No full event details, no past events.
- **workshops.html** = canonical workshop hub. ALL upcoming + past workshop listings live here. This is the single source of truth for workshop content.
- **workshop.html** = single-event detail page (April 25). Deep content, registration CTA, event-specific schema.

**Justification:** This page exists primarily as an SEO landing page for "AI workshops San Diego" (a real search term with local intent). Without it, no page targets this keyword cluster. The homepage teaser is not enough -- Google needs a dedicated, keyword-optimized page. Keep scope lean: reuse existing components, no elaborate design.

**URL:** `https://amplifyai.to/workshops.html`

**Target keywords:** "AI workshops San Diego", "AI workshop for small business", "learn AI hands-on"

**Title:** "AI Workshops in San Diego | Amplify AI"

**Schema:** `ItemList` of `EducationEvent` entries

**Content sections:**
1. Hero: "Hands-On AI Workshops in San Diego" + subhead about learning AI by building with it
2. Upcoming workshops (links to individual event pages like workshop.html)
3. Past workshops (compact grid with date, title, one-line description, photo if available)
4. Who these are for (persona cards: creatives, small biz owners, event planners)
5. Brief about Alex + link to about.html
6. CTA: Link to the current workshop page (e.g., workshop.html)

### Research Insights (Conversion)

**Workshop listing patterns:**
- **Split "Upcoming" (prominent) from "Past" (compact grid below).** Past events are social proof.
- **Sold-out events:** Keep visible with a "Sold Out" badge. Social proof that events fill up.
- **Future-facing CTA:** When no events are scheduled, the page needs at minimum a "Contact us about upcoming workshops" link to the homepage form. Full email capture/newsletter system is out of scope for Phase 1 (see Stretch Items).

**CTA:** Links to specific workshop pages (e.g., workshop.html for April 25).

### 3b. hospitality.html -- "AI Consulting for Hospitality"

**URL:** `https://amplifyai.to/hospitality.html`

**Target keywords:** "AI consulting hospitality", "AI for boutique hotels", "hotel AI adoption"

**Title:** "AI Consulting for Boutique Hotels & Hospitality | Amplify AI"

**Schema:** `Service` with `areaServed` and `serviceType`

**Content sections:**
1. Hero: "AI Systems for Boutique Hotels That Actually Work" + subhead about complex operations
2. The problem: boutique hotels juggling reservations, staffing, guest experience, multi-property coordination -- without enterprise budgets
3. The approach: Performance Intelligence Protocol framework (see brainstorm: Feed-Forward risk -- lead with framework, not case studies)
   - Frame as: "30 years of live performance judgment, codified into decision systems for hospitality"
   - Focus on the methodology, not proof-by-example
4. What an engagement looks like (AI Readiness Assessment -> Implementation Sprint -> Ongoing Support)
5. Who this is for (persona: 2-10 property boutique hotel operator, complex systems, ready for AI but doesn't know where to start)
6. Who this is NOT for (luxury chains with enterprise IT departments, hotels looking for chatbots only)
7. About Alex (brief authority section)
8. CTA: "Book a Free 30-Minute Discovery Call" -- dedicated hospitality Formspree form (see CTA Attribution below)

### CTA Attribution (Measurable Conversion Path)

The hospitality page MUST have an attributable conversion path so we can measure whether it works.

**Primary mechanism: Dedicated Formspree form for hospitality inquiries.**
- Create a NEW Formspree form (separate from the homepage form xpqodrkv)
- Include a hidden field: `<input type="hidden" name="source" value="hospitality">`
- Form fields: name, email, business name, number of properties, "What's your biggest operational challenge?"
- This form is the hospitality page's CTA destination. No Calendly dependency.

**Why not Calendly:** Calendly account does not exist and is not confirmed. Do not plan around it. If a Calendly account is created later, it can replace or supplement the form -- but the form ships now with zero dependencies.

**Measuring success:** Compare inquiry count from this form (source=hospitality) against baseline (0). Target: >= 1 within 60 days.

### Research Insights (Conversion -- Feed-Forward Risk Mitigation)

**This is the plan's highest-risk page. Research confirms the approach is sound but requires a concrete trust artifact beyond generic patterns.**

**"Proof Stack" pattern:**
Layer these four elements top-to-bottom on the page:

1. **Specificity of problem.** Name the exact pain: "Your team spends 6 hours/week reconciling bookings across 3 properties" or "Your guest follow-up process breaks every time you add a new channel." Specificity signals experience without needing a case study.
2. **Credential anchors.** One line: "30 years building systems for live performance and hospitality operations." Real photo of Alex (not stock).
3. **Micro-testimonials.** Heather Hilton's testimonial from workshops. LinkedIn recommendations acceptable. The bar is "specific outcome," not "long story."
4. **Process transparency.** Show the 3-step engagement model (AI Readiness Assessment -> Implementation Sprint -> Ongoing Support).

**REQUIRED: One concrete hospitality trust artifact.**
Generic creative-world proof (workshop testimonials, film awards) is not enough to close a boutique hotel operator. Before this page is considered complete, it MUST include at least ONE of:
- A sample AI Readiness Assessment deliverable (redacted/example format showing what the hotel gets)
- A worked hospitality ops teardown (e.g., "Here's how we'd analyze a 3-property hotel's booking workflow")
- A specific hospitality workflow example with before/after (even hypothetical, clearly labeled)
- A hospitality-adjacent testimonial or LinkedIn recommendation from someone in operations/events

This artifact is the page's credibility anchor. Without it, the Proof Stack is just a framework and the "Who This Is NOT For" section signals confidence without backing it up.

**"Who This Is NOT For" -- confirmed proven pattern:**
- Negative qualification: exclusion increases perceived selectivity and honesty
- 3-5 bullet points, direct language
- Filters bad-fit leads, signals confidence, reframes qualifying readers as "chosen"

**CTA placement (3 spots, one message):**
1. **Hero section** (above fold) -- catches the 5-10% who already know they want to talk
2. **After the Proof Stack** (mid-page) -- catches the "now I'm convinced" moment
3. **Sticky bottom bar on mobile, inline on desktop** -- persistent low-pressure option
- One primary CTA ("Book a Discovery Call") repeated in 3 spots. Do not scatter 6+ CTAs.

**Service schema for this page:**
```json
{
  "@type": "Service",
  "name": "AI Implementation Sprint for Hospitality",
  "description": "AI consulting for boutique hotels and hospitality businesses",
  "provider": {"@type": "Person", "name": "Alex Guillen"},
  "areaServed": {"@type": "City", "name": "San Diego"},
  "serviceType": "Consulting"
}
```
Note: Price removed from schema. Do not publish consulting prices in structured data -- it signals a fixed-price commodity, not a custom engagement.

### 3c. about.html -- "About / Credentials"

**URL:** `https://amplifyai.to/about.html`

**Target keywords:** "Alex Guillen AI consultant", "Amplify AI San Diego"

**Title:** "About Alex Guillen | Amplify AI - San Diego AI Consultant"

**Schema:** `Person` with `knowsAbout`, `jobTitle`, `award`

**Content sections:**
1. Hero: Photo + "I build AI systems that run my music business. Now I'm teaching what worked."
2. The story (expanded from index.html "Start Here" section, but more detailed)
3. Credentials and recognition (SDSFF "A Cut Above" award, workshop history, film work)
4. What I believe about AI (AI Dual Literacy philosophy -- the concept lives here, not in the homepage title)
5. Current projects / what I'm working on
6. CTA: Split -- "Attend a Workshop" + "Book a Consultation"

### Files created

- `workshops.html` (plural -- workshop listing page)
- `hospitality.html`
- `about.html`

### Files changed

- `sitemap.xml` -- add all 3 new pages
- `index.html` -- update to full site nav, reduce workshop section to teaser linking to workshops.html
- `workshop.html` -- keep focused event nav, add subtle "Back to all workshops" link only
- `styles.css` -- shared `.landing-*` classes extracted during page building

### Acceptance criteria

- [ ] Each landing page has unique title, meta description, canonical URL, OG tags
- [ ] Each landing page has appropriate schema markup (JSON-LD validated via schema.org or Rich Results Test where eligible)
- [ ] Nav matches the per-page-type model (full site nav on new pages, event-focused nav preserved on workshop.html)
- [ ] workshops.html is the single canonical workshop hub (upcoming + past). Homepage has teaser only.
- [ ] hospitality.html uses Proof Stack pattern with at least ONE concrete hospitality trust artifact
- [ ] hospitality.html includes "Who This Is NOT For" section
- [ ] hospitality.html CTA submits to dedicated Formspree form with `source: hospitality` hidden field
- [ ] about.html consolidates credentials and philosophy
- [ ] All new pages use shared `.landing-*` CSS classes from styles.css (no large inline style blocks)
- [ ] All pages render correctly on mobile (test at 375px, 768px)
- [ ] All pages pass Lighthouse SEO >= 90 (target 95)

---

## Workstream 4: Google Business Profile

This is manual work, not code. Documenting the steps here for completeness.

### Setup steps

1. Go to business.google.com and create a new profile
2. Business name: "Amplify AI" (NEVER add keywords to the name -- "Amplify AI - Best AI Consultant San Diego" will get flagged and suspended)
3. Select "Service-area business" -- hide home address entirely
4. **Primary category:** "IT Consultant" (closest verified Google category to AI consulting)
5. **Secondary categories (max 2-3):** "Computer Training School" (for workshops), "Management Consultant"
6. Service area: San Diego, CA + 2-3 adjacent cities you actually serve (Carlsbad, La Jolla). Stay within 2-hour driving radius.
7. Contact: phone from schema (619-755-3246), website: https://amplifyai.to
8. **Description (750 chars max, first 250 most important):** Front-load with business name, what you do, location, primary keyword. Example opener: "Amplify AI is a San Diego AI consulting firm that helps creative businesses and boutique hotels implement AI workflows, automation, and hands-on AI workshops."
9. Add services as separate line items: "AI Strategy Consulting," "AI Workflow Automation," "Hands-On AI Workshops," "AI Readiness Assessment," "AI Implementation Sprint"
10. **Photos: Upload 10+ in first month, aim for 20+ over time.** Priority types: workshop action shots, you presenting, headshot, logo. File naming: use descriptive names like "ai-workshop-san-diego.jpg" not "IMG_4532.jpg"
11. Set business hours (or "by appointment")
12. Request verification (postcard or phone)

### Ongoing GBP Maintenance

**Research insight:** Profiles without updates for 30+ days see measurable impression drops.

- Post once per week minimum
- Use "Event" posts for workshops (stay visible until event date -- longer than standard 7-day post lifespan)
- Use "Update" posts for tips or results. Include a photo and CTA in every post
- Add new photos monthly to signal freshness

### Post-workshop review plan

- **Generate a Google review QR code** and display it at the end of every workshop
- Send thank-you email within 24 hours with direct review link
- Ask for reviews that mention the specific service ("AI workshop," "consulting") -- keyword-rich reviews help ranking
- Goal: 5+ reviews in first month. A burst of positive reviews can shift local pack positioning within 2-3 weeks.

### Suspension triggers to avoid

- Never add keywords to business name
- Do not make drastic edits to name, category, or address all at once
- Do not create duplicate listings
- Do not use virtual office or coworking address without dedicated signage
- Max 3-4 categories total -- category stuffing triggers suspensions

### Acceptance criteria

- [ ] GBP created as service-area business with home address hidden
- [ ] Primary category: "IT Consultant"
- [ ] Description front-loads keywords in first 250 characters
- [ ] Website URL linked to https://amplifyai.to
- [ ] At least 10 photos uploaded with descriptive filenames
- [ ] Services listed as separate line items
- [ ] Verification process started
- [ ] Google review QR code generated for April 25 workshop

---

## Implementation Order

### Core Phase 1 (must ship)

| Step | Work | Est. Lines | Dependencies |
|------|------|-----------|--------------|
| 1 | Technical SEO fixes on existing pages (2a-2j) | ~80 | None |
| 2 | hospitality.html + extract shared CSS from workshop.html | ~350 new | Step 1 |
| 3 | workshops.html (lean -- reuse extracted components) | ~200 new | Step 1 |
| 4 | about.html | ~200 new | Step 1 |
| 5 | Homepage updates (nav, workshop teaser, link to workshops.html) | ~30 | Steps 2-4 |
| 6 | Sitemap update (all pages) | ~20 | Steps 2-4 |
| 7 | Formspree: enable spam protection + create hospitality form | Config | Before launch |
| 8 | Google Business Profile creation | 0 (manual) | Step 1 |

**Hospitality page first** (highest risk -- verify Proof Stack + trust artifact before building other pages).

Steps 1 and 8 can start in parallel. Steps 2, 3, 4 are sequential (2 first to extract CSS, then 3 and 4 reuse it).

### Optional Stretch Items (nice-to-have, not required for Phase 1)

These came from deepening research. They improve quality but are not in the original brainstorm scope:

| Item | Rationale for deferral |
|------|----------------------|
| Self-host Google Fonts | ~100-300ms LCP improvement, but site already has no JS and loads fast. Do if time permits. |
| Branded OG images (1200x630px cards) | Best practice, but current headshot OG images work. Create if time permits. |
| Custom 404.html | Good practice with 5 pages, but GitHub Pages default 404 is functional. Low priority. |
| Newsletter/email capture on workshops.html | Requires choosing and integrating a capture system (Formspree, Buttondown, etc.) -- separate project. Phase 1 uses "Contact us" link as fallback. |
| WebP image conversion | Performance improvement, not SEO-critical. |
| Apple touch icon / manifest.json | Single favicon.png is sufficient for Phase 1. |

## Technical Considerations

- **No build step.** Everything is raw HTML/CSS served by GitHub Pages. Keep it that way.
- **Image optimization.** Consider converting key images to WebP with JPEG fallback using `<picture>` elements. Not blocking for Phase 1 but worth doing.
- **Mobile-first.** All new pages must work at 375px. Existing breakpoints: 768px and 1024px.
- **Consultation booking mechanism.** **Decision: Dedicated Formspree form** for hospitality inquiries (separate from homepage form). No Calendly dependency -- Calendly account does not exist and is not confirmed. The Formspree form includes a hidden `source: hospitality` field for attribution. If Calendly is set up later, it can supplement or replace the form.
- **URL structure.** New pages use flat, keyword-rich filenames at root: `workshops.html`, `hospitality.html`, `about.html`. No subdirectories (GitHub Pages serves static files, no routing). This keeps URLs clean and SEO-friendly.
- **Navigation per page type.** See "Navigation model" table in Workstream 3. New pages get full site nav. workshop.html keeps its focused event nav. Nav HTML duplicated per page with type comments for sync.
- **OG images for new pages.** Use existing photos (presenting photo for workshops, headshot for about/hospitality). Branded 1200x630 cards are a stretch item, not core.
- **Analytics.** Google Analytics (GA4) setup is deferred to Phase 2. Phase 1 success is measured via Lighthouse scores, Rich Results Test, and manual checks. Note: without GA4, we cannot measure traffic or conversion rates -- this is a known gap.
- **Formspree.** The existing form (ID: xpqodrkv) works for the homepage contact form.
- **No JavaScript.** The site currently has zero JS (only JSON-LD). Keep it that way unless there's a strong reason.
- **GitHub Pages cache behavior.** Cache headers are fixed: 10 minutes for HTML, 1 year for assets. You cannot change them. For image updates, use renamed files (e.g., `headshot-v2.webp`) to bust cache. For page renames, add a simple HTML meta-refresh redirect at the old path (no server-side redirects available).
- **Nav duplication.** Acceptable at this scale. Use `<!-- NAV: full-site -->` or `<!-- NAV: event-focused -->` comments for sync. Revisit at 8+ pages.

## Dependencies & Risks

| Risk | Likelihood | Impact | Mitigation |
|------|-----------|--------|------------|
| Hospitality page doesn't convert without case studies | Medium | Medium | Lead with framework, specificity, "not for" section. Measure after 30 days. |
| CSS extraction breaks workshop.html layout | Low | High | Visual regression check before/after. Git commit before starting extraction. |
| GBP verification takes weeks | Medium | Low | Start early. Non-blocking for website work. |
| New pages dilute existing SEO signals | Low | Low | Proper canonical URLs and internal linking prevent this. |

## Success Metrics

**Measurable at launch:**
- Lighthouse SEO score >= 90 on all pages (target 95)
- Rich Results Test passes for eligible pages (workshop.html EducationEvent, hospitality.html Service)
- JSON-LD validates via schema.org validator on all pages
- All internal links return 200 (no 404s)
- OG images render correctly (test via Facebook Sharing Debugger)
- Formspree spam protection enabled on all forms

**Measurable within 30 days:**
- GBP verification process completed
- Homepage title appears in Google search results for "Amplify AI"
- sitemap.xml submitted to Google Search Console

**Measurable within 60 days:**
- >= 1 consultation inquiry attributed to hospitality page (via dedicated Formspree form with `source: hospitality`)
- GBP appearing in local search results for "AI consulting San Diego"

## Sources & References

### Origin

- **Brainstorm document:** [docs/brainstorms/2026-04-13-seo-content-optimization-brainstorm.md](../brainstorms/2026-04-13-seo-content-optimization-brainstorm.md)
- Key decisions carried forward: Phase 1/Phase 2 split, two audience segments, AI search deferred, GBP included

### Internal References

- Design system: `content/design-decisions.md`
- Voice rules: `content/site-copy.md:110-119` (banned words, voice self-check)
- Brand voice: `amplify-workshop-assets/context/brand-voice.md` (separate repo)
- Current schema: `index.html:33-58` (ProfessionalService), `workshop.html:419-458` (EducationEvent)
- CSS custom properties: `styles.css:12-24`

### External References (from Deepening Research)

**SEO:**
- [Google Rich Results Test](https://search.google.com/test/rich-results)
- [Google Event Structured Data Docs](https://developers.google.com/search/docs/appearance/structured-data/event)
- [Canonicalization and SEO Guide](https://searchengineland.com/canonicalization-seo-448161)
- [Schema Markup 2026 Guide](https://almcorp.com/blog/schema-markup-detailed-guide-2026-serp-visibility/)

**Google Business Profile:**
- [Google Official: SAB Guidelines](https://support.google.com/business/answer/9157481)
- [Google Official: Business Representation](https://support.google.com/business/answer/3038177)
- [GBP Suspension Prevention](https://www.20minutemarketing.com.au/blog/google-business-profile-suspension-prevention-recovery)

**Conversion Patterns:**
- [Consulting Success: Optimal Landing Page](https://www.consultingsuccess.com/the-optimal-landing-page-for-consultants)
- [CTA Placement Strategies](https://avintivmedia.com/blog/cta-placement-strategies-that-work/)

## Feed-Forward

- **Hardest decision:** What constitutes a sufficient "concrete hospitality trust artifact." A sample readiness assessment is the most achievable, but it requires Alex to create something that looks like a real deliverable before having a real client. The alternative (worked ops teardown) requires hospitality domain knowledge that may need research.
- **Rejected alternatives:** (1) Calendly as primary CTA -- unconfirmed dependency, replaced with dedicated Formspree form. (2) Full email capture on workshops.html -- requires choosing and integrating a capture system, deferred to stretch. (3) CSS as separate upfront workstream -- premature, extraction happens incrementally. (4) Same nav on all pages -- workshop.html keeps focused event nav for conversion.
- **Least confident:** Whether the hospitality trust artifact (sample deliverable or ops teardown) will be specific and credible enough to close a boutique hotel operator. The Proof Stack framework is research-backed, but the artifact itself depends on Alex's ability to translate performance/music systems thinking into hospitality-specific language. Review should scrutinize whether the artifact reads as genuine domain expertise or as a generic template.
