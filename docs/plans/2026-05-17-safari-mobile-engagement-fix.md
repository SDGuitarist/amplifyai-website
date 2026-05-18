---
title: Safari Mobile Engagement Fix
date: 2026-05-17
phase: work
feed_forward:
  risk: "AOS fail-hidden pattern can make entire page invisible below the hero"
  verify_first: true
---

# Safari Mobile Engagement Fix

## Root Cause

The landing page at amplifyai.to uses AOS (Animate On Scroll) loaded from unpkg.com CDN.
AOS CSS sets `opacity: 0` on all `[data-aos]` elements by default. AOS JS then reveals
them on scroll via `AOS.init()`.

**The root cause is the fail-hidden AOS dependency pattern itself.** Any failure that
prevents AOS JS from loading or executing will leave content permanently invisible:
- CDN outage or timeout (unpkg.com has no SLA)
- Content/ad blockers removing the script
- In-app browsers (Instagram, Facebook, LinkedIn) restricting JS execution
- Slow mobile networks timing out the request
- Browser tracking prevention deprioritizing cross-origin requests

We did not confirm any specific browser mechanism was actively blocking AOS. The fix is
warranted regardless: a conversion page must not depend on a third-party animation library
to be *visible*.

**Failure mode:** If AOS CSS loads but AOS JS does not:
- All `[data-aos]` elements stay at `opacity: 0` forever
- `AOS.init()` throws `ReferenceError: AOS is not defined` (no guard was present)
- Every section below the hero is invisible, including the `#register` form

**Affected elements (17 total):**
- The Problem section
- Who This Is For section + 4 persona cards
- What You Walk Away With + example card + photo
- 3 testimonial cards
- Why Now section
- About Alex + endorsement
- FAQ section
- Register section with form -- THE CONVERSION TARGET

## What Exactly Is Changing

1. Remove all 17 `data-aos` and `data-aos-delay` attributes from index.html
2. Remove AOS CSS link (unpkg.com/aos@2.3.1/dist/aos.css)
3. Remove AOS JS script (unpkg.com/aos@2.3.1/dist/aos.js)
4. Remove AOS.init() call
5. Compress mobile hero so CTA is visible on iPhone SE (375x667) with Safari chrome
6. Verify with headless browser at actual iPhone SE viewport dimensions

## What Must Not Change

- GA4 tracking (gtag.js) and all custom event tracking (scroll depth, CTA clicks, form submit)
- Form action, hidden fields, and submission flow
- All visible content and copy (desktop layout unchanged)
- Visual design (colors, typography, layout)
- Bottom sticky CTA bar
- Nav behavior

## Acceptance Tests

### Happy Path
- WHEN a user loads the page with JS disabled THE SYSTEM SHALL display all sections fully visible
- WHEN a user loads the page and unpkg.com is unreachable THE SYSTEM SHALL display all content normally
- WHEN a user scrolls to #register THE SYSTEM SHALL show the registration form with all fields interactive

### Error Cases
- WHEN gtag.js fails to load THE SYSTEM SHALL still render all content (analytics degrades gracefully via `typeof gtag === 'function'` guards already in place)
- WHEN Google Fonts CDN fails THE SYSTEM SHALL fall back to Georgia/system-ui (already handled)

### Mobile
- WHEN viewed on iPhone SE (375x667) with Safari chrome THE SYSTEM SHALL show the hero CTA ("Reserve Your Seat") above the bottom sticky bar without scrolling
- WHEN opened in Instagram's in-app browser THE SYSTEM SHALL show all content visible and the registration form interactive

### Verification Commands
```bash
grep -c 'data-aos' index.html          # returns 0
grep -c 'unpkg.com/aos' index.html     # returns 0
grep -c 'AOS.init' index.html          # returns 0
grep -c 'gtag' index.html              # returns 11 (5 config + 6 event tracking)
```

## Most Likely Way This Plan Is Wrong

The mobile hero compression hides the hero-label, hero-eyebrow, and hero-value-prop on
screens under 600px. If someone expects to see "Hands-On AI Workshop for Filmmakers /
San Diego" on mobile, it won't be there (the details strip has the same info). This is a
tradeoff: CTA visibility vs context density. The details strip (date, location, price)
preserves the essential info.

## Feed-Forward

- **Hardest decision:** Whether to self-host AOS with guards vs remove it entirely. Removing is correct because AOS adds zero conversion value -- scroll animations on a 1-page workshop landing page are cosmetic. The risk/reward is entirely negative.
- **Rejected alternatives:** (1) Self-hosting AOS with a window.AOS guard -- still adds complexity for zero conversion benefit. (2) CSS-only scroll animations via IntersectionObserver -- same risk of hiding content if the observer setup fails. (3) Keeping mobile hero spacing loose and relying only on bottom bar CTA -- the hero CTA in context (after date/location/price) is the primary conversion path.
- **Least confident:** Whether the Instagram in-app browser handles the remaining external dependencies (Google Fonts, gtag.js) gracefully. We removed the AOS failure path, but did not test in-app browsers directly. The pre-campaign checklist now requires this test.
