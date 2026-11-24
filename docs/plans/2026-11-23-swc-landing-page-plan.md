# Plan: SWC class landing page + email sign-up (2026-11-23)

**Why:** Growth strategy (`~/Projects/human-led-ai/docs/pilot-prep/2026-11-23-growth-strategy-class-and-consulting.md`
sections 4-5): one page on Alex's own domain that ads, posts and free sessions point to, with a button to SWC
registration and an email sign-up so new people become reachable.

## 1. What changes
- New page `swc.html` (amplifyai.to/swc.html), built from the `nov20.html` template (same nav, footer, styles).
- Register button links to `https://registration.xendirect.com/swccd/courseDisplay.cfm?schID=1901`.
- Updates sign-up: NO go-between (Alex, 2026-11-23, after Formspree was proposed). A `mailto:alex@amplifyai.to` button with a prefilled subject, and an `sms:` link to 619-755-3246. Formspree rejected.
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
- WHEN a visitor taps "Email me to get updates" THE SYSTEM SHALL open their email app addressed to alex@amplifyai.to
  with the subject prefilled. Verify: href check + Alex taps it once on his iPhone and sends a test to himself.
- WHEN a visitor taps "Or text" THE SYSTEM SHALL open a text to 619-755-3246. Verify: href check + iPhone tap.
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
- **Alex's heads-up (2026-11-23):** Formspree is a go-between like FormSubmit and Jotform, which failed silently
  for weeks in 2026; last recorded test March 30. Gates: (1) test submission from Alex's iPhone in Safari arrives
  in his inbox BEFORE any ad money; (2) repeat that test weekly while ads run; (3) Formspree only collects, so the
  48-hour follow-up and monthly newsletter need a sending tool (decision owed before the first free session).

- **Decision 2026-11-23 (Alex): "I'm uncomfortable using a go between. This killed us last time."** Formspree removed; sign-up is a direct email or text to Alex. Trade-off accepted: more friction per sign-up, zero silent-failure path. A newsletter tool (where the list itself lives) is a separate decision before the first free session.
