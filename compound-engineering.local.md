# Review Context — Amplify AI Website

## Risk Chain

**Brainstorm risk:** "Whether the hospitality landing page will convert without real case studies."

**Plan mitigation:** Proof Stack pattern (specificity, credentials, testimonials, process) + concrete hospitality trust artifact. Lead with Performance Intelligence Protocol framework instead of proof.

**Work risk (from Feed-Forward):** "Whether the hospitality trust artifact (sample deliverable or ops teardown) will be specific and credible enough to close a boutique hotel operator."

**Review resolution:** Review flagged the trust artifact as not operator-grade. Reworked to ops teardown with explicit inputs (PMS data, review keyword extraction, vendor contracts), deliverable excerpts (property identity brief with keys/segment/RevPAR), and staff execution playbooks. Also fixed: broken form endpoint, missing nav links, schema email exposure, missing spam protection.

## Files to Scrutinize

| File | What changed | Risk area |
|------|-------------|-----------|
| hospitality.html | Full landing page with ops teardown trust artifact, Formspree form, 3 CTAs | Conversion copy credibility, form attribution |
| styles.css | +241 lines of shared `.landing-*` CSS extracted from workshop.html | Visual regression on workshop.html |
| index.html | Title/meta/schema overhaul, nav restructured, workshop section reduced | SEO signals, nav consistency |
| workshops.html | New canonical workshop hub | Content duplication with homepage teaser |
| about.html | New credentials page | Factual accuracy of claims |
| workshop.html | Added "Back to all workshops" link, kept focused event nav | Nav doesn't break conversion flow |

## Plan Reference

`docs/plans/2026-04-13-feat-seo-content-optimization-phase1-plan.md`
