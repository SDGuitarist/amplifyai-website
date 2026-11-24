# Plan: SWC class landing page + email sign-up (2026-11-23)

**Why:** Growth strategy (`~/Projects/human-led-ai/docs/pilot-prep/2026-11-23-growth-strategy-class-and-consulting.md`
sections 4-5): one page on Alex's own domain that ads, posts and free sessions point to, with a button to SWC
registration and an email sign-up so new people become reachable.

## 1. What changes
- New page `swc.html` (amplifyai.to/swc.html), built from the `nov20.html` template (same nav, footer, styles).
- Register button links to `https://registration.xendirect.com/swccd/courseDisplay.cfm?schID=1901`.
- Email sign-up: plain HTML POST to the existing, tested Formspree form `xpqodrkv`, hidden field `source=swc-landing`.
- GA4 `G-FH4JJG7QRY` and Meta Pixel `1505523111107753` (same IDs as index.html); events on register click and sign-up.
- `sitemap.xml` gets the new URL.

## 2. What must not change
- No other page edited. No payment handled on this page (SWC takes payment).
- No mention of the instructor's Spanish (Alex, 2026-11-23). No consulting pitch on this page.
- No JavaScript required for the form or the register link to work (Safari lesson, May 2026).

## 3. Acceptance tests (EARS)
- WHEN the page loads on an iPhone-size WebKit browser THE SYSTEM SHALL show the headline and the Register button
  without JavaScript. Verify: Playwright WebKit, JS disabled, screenshot shows both.
- WHEN a visitor taps Register THE SYSTEM SHALL open the SWC listing for schID=1901. Verify: link href check +
  fetch of the target returns the "Practical AI for Everyday Work" listing (Alex's browser if the fetcher is blocked).
- WHEN a visitor submits name and email THE SYSTEM SHALL post them to Formspree `xpqodrkv` with `source=swc-landing`.
  Verify: one real test submission by Alex (or with his yes), seen in his inbox.
- WHEN the page loads THE SYSTEM SHALL fire GA4 page_view and Meta PageView. Verify: network requests in a browser.
- THE SYSTEM SHALL contain no em dashes and pass `voice-mechanical.py` on the page text.

## 4. Most likely way this is wrong
- A fact on the page drifts from SWC's listing (dates, times, price). Mitigation: every fact copied from the
  listing HTML saved 2026-11-23 and listed in a fact ledger.
- Formspree's free tier caps monthly submissions (limit not checked); a cap would silently drop sign-ups.
  Mitigation: Alex checks his Formspree plan before ads launch.

## Execution Path
- **Target:** amplifyai.to/swc.html on phones (iPhone Safari first) and desktop browsers.
- **Mechanism:** GitHub Pages serves `main`; publishing is `git push` to `main`.
- **Prerequisites:** GitHub push access (ALREADY HAVE); Formspree form `xpqodrkv` (ALREADY HAVE, tested Mar 2026);
  Formspree plan limit checked (MUST OBTAIN, Alex, before ads); WebKit test browser (MUST OBTAIN, Claude installs).
- **Who:** Claude builds and tests locally and shows screenshots; Alex approves; Claude pushes only on Alex's yes;
  Alex then opens the live page on his iPhone, taps Register, and sends one test sign-up.
- **Trigger:** Alex's yes after seeing the screenshots. Codex spot-check before the late-January ad test.

## Feed-Forward
- **Hardest decision:** Formspree (already wired, no new account) vs a newsletter tool (list + automatic
  follow-up). Chose Formspree now so the page can ship this week; contacts export to a newsletter tool later.
- **Rejected alternatives:** a new page on SWC's site (not ours to edit); a Square or Jotform step (middleman
  failures in 2026); JavaScript-only form (Safari blank-page history).
- **Least confident:** whether Formspree's free tier limit is high enough once ads run.
