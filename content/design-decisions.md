# Design Decisions — Amplify AI

**Date:** 2026-03-28
**Direction:** Warm Editorial with Strong CTA Funnel

---

## Design References

| Site | What to steal | What to avoid |
|------|--------------|---------------|
| **justinwelsh.me** (PRIMARY) | End-to-end CTA funnel, clean tabs, headline + immediate CTA, story-driven scroll, credentials section | — |
| **weskao.com** | Typography warmth, simplicity, ~700px content column | No scroll content, no CTA |
| **khehy.com** | Personable headline, great headshot placement, "Start Here" concept | No CTA funnel |
| **amandanat.com** | Left-aligned tabs, social buttons, clean layout | No CTA |
| **kozyr.com** | Horizontal scroll on services cards | Dead end at bottom |

## Typography

**Display/Headings:** Fraunces (weight 600-700)
- Warm, has character ("wonk" variable), musician DNA
- Used for h1, h2, section headers

**Body:** DM Sans (weight 400, 500)
- Clean, modern, warmer than Inter
- Used for body text, nav, buttons, captions

**Import:**
```
@import url('https://fonts.googleapis.com/css2?family=Fraunces:opsz,wght@9..144,600;9..144,700&family=DM+Sans:wght@400;500;700&display=swap');
```

## Color Palette

| Role | Hex | Usage |
|------|-----|-------|
| Background | `#F5F0EB` | Main page background (warm linen) |
| Text | `#2C2421` | Primary text (warm dark brown) |
| Accent | `#B8703F` | CTAs, links, active states (cognac) |
| Secondary | `#8B7355` | Subheadings, borders, muted text |
| Card/Surface | `#E8DDD3` | Card backgrounds, section dividers |
| White | `#FEFCFA` | Hero text overlay, card highlights |

## Layout Principles

- **Content column:** max-width 780px, centered
- **Section spacing:** clamp(4rem, 8vw, 8rem) between sections
- **Line height:** 1.6 for body, 1.1-1.2 for headings
- **Paragraph width:** max 38rem (~65 chars per line)
- **Mobile-first:** breakpoints at 768px, 1024px

## Page Structure (Justin Welsh funnel model)

1. **Nav** — Clean tabs left-aligned. Links: Start Here, Workshops, About, Contact. Social icons (LinkedIn, Instagram) on right.
2. **Hero** — Personable headline (Khe Hy energy) + Alex's headshot + immediate CTA button underneath. Not a generic tagline. Something that shows personality.
3. **Story** — Scroll into Alex's journey. Short, punchy, peer-to-peer.
4. **What I Do** — Service cards (horizontal scroll on mobile like Kozyr, grid on desktop). Each card links to contact CTA.
5. **Workshops** — Upcoming events with details and register/learn more links.
6. **Social Proof** — Heather's quote + credentials list.
7. **Contact / Final CTA** — Strong closing CTA. Not an afterthought. "Let's talk" with email + phone.

## CTA Strategy (Justin Welsh model)

- **Hero CTA:** Primary button under the headline (e.g., "Let's Talk" or "Start Here")
- **Mid-page CTA:** After What I Do section (e.g., "Want to know what I'd build for your business?")
- **Final CTA:** Contact section with clear, warm invitation

Every section either tells the story or drives toward action. No dead ends.
