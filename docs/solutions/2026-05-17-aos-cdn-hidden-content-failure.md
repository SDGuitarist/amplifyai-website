---
title: AOS CDN Hidden Content Failure
date: 2026-05-17
tags: [mobile, aos, cdn, conversion, landing-page, fail-hidden]
severity: P0
root_cause: fail-hidden-third-party-dependency
---

# AOS CDN Hidden Content Failure

## Problem

The amplifyai.to landing page used AOS (Animate On Scroll) loaded from unpkg.com CDN.
AOS CSS sets `opacity: 0` on all elements with `data-aos` attributes by default, then
AOS.init() reveals them on scroll. If the AOS JS fails to load or execute for any reason,
all content below the hero stays invisible forever.

17 elements had `data-aos` attributes, including:
- Every section below the hero
- All persona cards, testimonials, and FAQ items
- The `#register` form (the conversion target)

This is a **fail-hidden** design. The page bets its entire conversion path on a third-party
CDN being available, unblocked, and executing correctly in every browser environment.

## Root Cause

The root cause is the fail-hidden AOS dependency pattern itself, not any specific browser
or network failure. AOS works in two stages:

1. **CSS** sets `[data-aos] { opacity: 0; transform: ... }` -- elements start invisible
2. **JS** calls `AOS.init()` which adds classes to reveal elements on scroll

If CSS loads but JS doesn't, elements are permanently invisible. This can happen due to:
- CDN outage or slow response (unpkg.com is a free CDN with no SLA)
- Content blockers, ad blockers, or privacy extensions blocking the script
- Network timeouts on slow mobile connections
- In-app browsers (Instagram, Facebook, LinkedIn) with restricted JS execution
- Browser tracking prevention (Safari ITP, Firefox ETP) deprioritizing cross-origin requests

We did not confirm that any specific mechanism was actively blocking AOS. The fix is
warranted regardless: a conversion page should never depend on a third-party animation
library to be *visible*. The fail-hidden pattern is the bug, not any particular trigger.

The `AOS.init()` call had no `window.AOS` guard -- if the JS didn't load, it would throw
`ReferenceError: AOS is not defined` and break any subsequent scripts too.

## Fix

1. Removed all 17 `data-aos` and `data-aos-delay` attributes
2. Removed AOS CSS link (`unpkg.com/aos@2.3.1/dist/aos.css`)
3. Removed AOS JS script and `AOS.init()` call
4. Compressed mobile hero layout so CTA is above fold on iPhone SE (375x667):
   - Hid hero-label, hero-eyebrow, and hero-value-prop on mobile (redundant with h1 and details strip)
   - Reduced hero padding, h1/sub/details spacing, and button size
   - Compacted nav padding on mobile
5. Verified with Playwright at iPhone SE viewport: CTA at 459px, bottom bar at 483px, 24px clearance

**Why remove entirely instead of self-hosting with guards?**
AOS adds zero conversion value on a single-page workshop landing page. Scroll animations
are cosmetic. The risk (invisible content) vs reward (fade-in effect) is entirely negative.

## How to Verify Before Any Future Paid Campaign

Run this checklist before launching any ad campaign that sends traffic to the landing page:

### Content visibility
```bash
# No third-party CSS or JS can hide content
grep -c 'data-aos' index.html        # must be 0
grep -c 'unpkg\|cdnjs\|jsdelivr' index.html  # check for new CDN deps
```

### Mobile CTA test (real device required)
1. Open the page on an actual iPhone (SE or mini) in Safari
2. Verify the "Reserve Your Seat" button is fully visible without scrolling
3. Verify the bottom sticky CTA bar is visible
4. Check that the details strip (date, location, price) is readable

### Instagram in-app browser test
1. Post or DM the URL in Instagram
2. Tap the link to open in Instagram's in-app browser
3. Verify all sections are visible (Instagram's browser has limited JS support and aggressive resource restrictions)
4. Verify the registration form is visible and fields are interactive
5. Repeat on Facebook Messenger and LinkedIn in-app browsers if running ads on those platforms

### JS-disabled test
1. Disable JavaScript in browser (Safari > Develop > Disable JavaScript)
2. Reload the page
3. All content including #register form must be visible and readable
4. Form still submits (it's a standard POST form, not JS-dependent)

### Analytics degradation test
1. Block googletagmanager.com in browser
2. Reload the page
3. All content renders normally
4. Form submission still works (formsubmit.co is the action, not JS)

## Pattern to Avoid

Never use a third-party animation library that sets `opacity: 0` as a default state on
conversion-critical content. If you must animate, either:
- Use CSS-only animations that start visible and enhance progressively
- Self-host the library with a guard: `if (window.AOS) AOS.init(); else /* ensure visible */`
- Never put `data-aos` on forms, CTAs, or any element the user needs to see to convert

## May 21, 2026: Same Bug, Different Files

**The May 17 fix only removed AOS from index.html.** filmnet.html and sdifn.html were missed. This went unnoticed for 4 days because:

1. The May 17 fix was scoped to index.html specifically
2. No one ran the verification grep on the other landing pages
3. filmnet.html is the page linked in all FilmNet outreach (401-person email list)

**Discovery:** Spec flow analysis agent flagged it while reviewing the May 30 workshop validation plan. The agent checked the actual file on disk and found AOS still present.

**Impact:** Message 2 (going to 401 FilmNet members) was about to send people to filmnet.html with the same CDN vulnerability that broke registration for 3 weeks. If unpkg.com hiccupped or any recipient's content blocker fired, the registration form would be invisible again.

**Fix (commit `0307836`, May 21):** Same treatment as index.html. Removed AOS CSS, JS, init, and all data-aos attributes from both filmnet.html and sdifn.html.

**Lesson:** When fixing a pattern-level bug, grep ALL files in the project, not just the one that was reported. The verification checklist above says `grep -c 'data-aos' index.html` but should say:

```bash
# Check ALL HTML files, not just index.html
grep -rc 'data-aos' *.html        # must be 0 across all files
grep -rc 'unpkg\|cdnjs\|jsdelivr' *.html  # check for new CDN deps
```

**Updated verification checklist item:**
```bash
# Before any outreach or ad campaign
for f in *.html; do
  count=$(grep -c 'data-aos' "$f" 2>/dev/null || echo 0)
  if [ "$count" -gt 0 ]; then echo "FAIL: $f has $count AOS attributes"; fi
done
```

## Related

- WebKit Tracking Prevention: https://webkit.org/tracking-prevention/
- GA4 enhanced measurement: https://support.google.com/analytics/answer/9216061
- Plan doc: `docs/plans/2026-05-17-safari-mobile-engagement-fix.md`
- May 21 fix commit: `0307836` (filmnet.html + sdifn.html)
- Validation plan: `~/Projects/docs/plans/2026-05-21-feat-may30-workshop-validation-plan.md`
