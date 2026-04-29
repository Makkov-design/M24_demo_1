# M24 Venture Capital — Project Documentation

**Landing Page · Full Project Documentation · v1.0 · April 2025**

> Single-file HTML · Inline CSS + JS · English only · No build step

---

## Table of Contents

1. [Project Overview](#1-project-overview)
2. [Design System — Colors](#2-design-system--colors)
3. [Design System — Typography](#3-design-system--typography)
4. [Design System — Animations](#4-design-system--animations)
5. [Design System — Components](#5-design-system--components)
6. [Page Structure](#6-page-structure)
7. [Section 1 — Navbar](#7-section-1--navbar)
8. [Section 2 — Hero](#8-section-2--hero)
9. [Section 3 — Three Columns](#9-section-3--three-columns)
10. [Section 4 — Why With Us](#10-section-4--why-with-us)
11. [Section 5 — Contact Form](#11-section-5--contact-form)
12. [Section 6 — Footer](#12-section-6--footer)
13. [Section 7 — Privacy Modal](#13-section-7--privacy-modal)
14. [Complete Content Reference](#14-complete-content-reference)
15. [Responsive Rules](#15-responsive-rules)
16. [Ready Prompts](#16-ready-prompts)

---

## 1. Project Overview

M24 Venture Capital is a Web3-native firm operating across three verticals: blockchain node validation, algorithmic/AI trading strategy development, and early-stage venture investment. The landing page serves as the primary public-facing presence — communicating credibility, technical depth, and portfolio reach to institutional and sophisticated retail audiences.

| Property | Value |
|---|---|
| **Deliverable** | Single `.html` file — all CSS and JS inline. No build step, no external frameworks. Deploy anywhere (GitHub Pages, Netlify, Vercel, Cloudflare Pages). |
| **Language** | English only. No i18n toggle. Copy is fixed (no CMS). |
| **Audience** | Institutional partners, protocol teams, crypto-native investors. |
| **Tone** | Technical, premium, non-hype. Zero "moon" language. |
| **Design aesthetic** | Dark luxury crypto-tech. Near-black background, lavender-violet gradient accents, mint-green status indicators. Refined and premium — not generic "Web3 blue". |

> **Note for AI tools:** This is a complete specification. Every section, every piece of copy, and every design token is defined in this document. Generate the full page from scratch as a single HTML file with inline CSS and JS. Do not use external CSS frameworks. Import Google Fonts via `<link>` tag only.

---

## 2. Design System — Colors

All colors are defined as CSS custom properties on `:root`. Never hardcode hex values in component styles — always reference variables.

### CSS Variables

```css
:root {
  --bg:             #0a0a0f;                  /* Main background — near-black, blue-tinted */
  --bg-card:        rgba(255,255,255,0.03);   /* Card/panel background */
  --bg-card-hover:  rgba(255,255,255,0.055);  /* Card hover state */
  --border:         rgba(255,255,255,0.07);   /* Default border color */
  --border-hover:   rgba(139,92,246,0.35);    /* Border on hover */
  --violet:         #8b5cf6;                  /* Primary accent */
  --violet-light:   #c4b0f0;                  /* Column titles, nav CTA, hover text */
  --violet-dim:     #a78bfa;                  /* "In Development" status, eyebrow labels */
  --green:          #6ee7b7;                  /* "Live" status, success states */
  --text-primary:   #f0eeff;                  /* Main headings and labels */
  --text-secondary: #888888;                  /* Body text, descriptions */
  --text-muted:     #555555;                  /* Form labels, copyright, tertiary */
  --glow:           rgba(139,92,246,0.08);    /* Atmospheric glow */
  --glow-strong:    rgba(139,92,246,0.15);    /* Strong glow on hover */
}
```

### Palette Reference

| Token | Hex | Usage |
|---|---|---|
| `--bg` | `#0a0a0f` | Main page background |
| `--bg-card` | `rgba(255,255,255,0.03)` | Cards, column panels |
| `--bg-card-hover` | `rgba(255,255,255,0.055)` | Card hover state |
| `--border` | `rgba(255,255,255,0.07)` | All borders |
| `--violet` | `#8b5cf6` | Accent color, buttons, pulsing dots |
| `--violet-light` | `#c4b0f0` | Column titles, CTA text, hover states |
| `--violet-dim` | `#a78bfa` | "In Development" badges, eyebrows |
| `--green` | `#6ee7b7` | "Live" badges, success button state |
| `--text-primary` | `#f0eeff` | Headings, primary labels |
| `--text-secondary` | `#888888` | Body text, subheadings |
| `--text-muted` | `#555555` | Form labels, copyright |

### Gradient — Hero Heading

```
linear-gradient(90deg, #c4b0f0 0%, #8b5cf6 35%, #c4b0f0 65%, #8b5cf6 100%)
background-size: 300% 100%
```
Applied as `background-clip: text` with shimmer animation (see Animations section).

---

## 3. Design System — Typography

### Font Import

```html
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;500;600;700;800&family=DM+Mono:wght@300;400;500&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet">
```

### Font Roles

| Family | Weights | Usage |
|---|---|---|
| **Syne** | 700, 800 | Hero title, section headings, column titles, card titles, logo text |
| **DM Sans** | 300, 400, 500 | All body text, form inputs, descriptions, footer |
| **DM Mono** | 300, 400, 500 | Status badges, form labels, eyebrow labels, nav CTA, copyright |

### Type Scale

| Element | Size | Weight | Family | Notes |
|---|---|---|---|---|
| Hero Title | `clamp(36px, 5.5vw, 72px)` | 700 | Syne | Gradient + shimmer, letter-spacing: -0.03em, line-height: 1.1 |
| Section Heading | `clamp(28px, 4vw, 48px)` | 700 | Syne | letter-spacing: -0.025em, line-height: 1.15 |
| Column Title | `13px` | 700 | Syne | Uppercase, letter-spacing: 0.1em, color: --violet-light |
| Card Title | `15px` | 600 | Syne | letter-spacing: -0.01em |
| Body / Description | `clamp(15px, 1.8vw, 18px)` | 300 | DM Sans | color: #888, line-height: 1.7 |
| Card Body | `13px` | 300 | DM Sans | color: #888, line-height: 1.7 |
| Network Item Name | `13.5px` | 400 | DM Sans | color: rgba(240,238,255,0.8) |
| Status Badge | `10px` | 400 | DM Mono | letter-spacing: 0.04em |
| Eyebrow Label | `11px` | 500 | DM Mono | Uppercase, letter-spacing: 0.12–0.14em |
| Form Label | `10px` | 400 | DM Mono | Uppercase, letter-spacing: 0.1em, color: --text-muted |
| Copyright | `11px` | 400 | DM Mono | letter-spacing: 0.04em, color: --text-muted |

---

## 4. Design System — Animations

### Shimmer — Hero Title

Applied to the gradient heading. Moves a light "sheen" across the text from left to right, looping infinitely.

```css
@keyframes shimmer {
  0%   { background-position: 0% 50%; }
  100% { background-position: 300% 50%; }
}

.hero-title {
  background: linear-gradient(90deg, #c4b0f0 0%, #8b5cf6 35%, #c4b0f0 65%, #8b5cf6 100%);
  background-size: 300% 100%;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  animation: shimmer 5s linear infinite;
}
```

### Pulsing Dot — Live Status (`#6ee7b7`)

```css
@keyframes pulse-green {
  0%, 100% { opacity: 1; box-shadow: 0 0 0 0 rgba(110,231,183,0.4); }
  50%       { opacity: 0.5; box-shadow: 0 0 0 4px rgba(110,231,183,0); }
}

.dot-live {
  width: 5px;
  height: 5px;
  border-radius: 50%;
  background: #6ee7b7;
  animation: pulse-green 1.8s ease-in-out infinite;
}
```

### Pulsing Dot — In Development (`#a78bfa`)

```css
@keyframes pulse-violet {
  0%, 100% { opacity: 1; box-shadow: 0 0 0 0 rgba(167,139,250,0.4); }
  50%       { opacity: 0.4; box-shadow: 0 0 0 4px rgba(167,139,250,0); }
}

.dot-dev {
  width: 5px;
  height: 5px;
  border-radius: 50%;
  background: #a78bfa;
  animation: pulse-violet 2.2s ease-in-out infinite;
}
```

### Page Load Fade-In

```css
@keyframes fadeInUp {
  from { opacity: 0; transform: translateY(24px); }
  to   { opacity: 1; transform: translateY(0); }
}

.hero-content    { animation: fadeInUp 1s ease both; }
.columns-section { animation: fadeInUp 1s 0.3s ease both; }
```

### Scroll-Triggered Cards (IntersectionObserver)

```js
const observer = new IntersectionObserver((entries) => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      entry.target.style.animation = 'fadeInUp 0.7s ease forwards';
      observer.unobserve(entry.target);
    }
  });
}, { threshold: 0.1 });

document.querySelectorAll('.why-card, .cta-wrapper').forEach(el => {
  el.style.opacity = '0';
  observer.observe(el);
});
```

### Atmospheric Glow (Hero)

```css
.hero::after {
  content: '';
  position: absolute;
  top: 20%;
  left: 50%;
  transform: translateX(-50%);
  width: 600px;
  height: 400px;
  background: radial-gradient(ellipse, rgba(139,92,246,0.12) 0%, transparent 70%);
  pointer-events: none;
  z-index: 0;
}
```

### Card Top-Edge Glow on Hover

```css
.why-card::before {
  content: '';
  position: absolute;
  top: 0; left: 0; right: 0;
  height: 1px;
  background: linear-gradient(90deg, transparent, rgba(139,92,246,0.4), transparent);
  opacity: 0;
  transition: opacity 0.3s;
}
.why-card:hover::before { opacity: 1; }
```

### Modal Entry

```css
@keyframes modalIn {
  from { opacity: 0; transform: scale(0.96) translateY(8px); }
  to   { opacity: 1; transform: scale(1) translateY(0); }
}
```

### Noise Texture Overlay (Body)

```css
body::before {
  content: '';
  position: fixed;
  inset: 0;
  background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.04'/%3E%3C/svg%3E");
  pointer-events: none;
  z-index: 0;
  opacity: 0.4;
}
```

---

## 5. Design System — Components

### Status Badge

Used next to each network/bot name in the three-column section.

```html
<!-- Live -->
<span class="status status-live">
  <span class="dot dot-live"></span> Live
</span>

<!-- In Development -->
<span class="status status-dev">
  <span class="dot dot-dev"></span> In Development
</span>
```

```css
.status {
  display: inline-flex;
  align-items: center;
  gap: 5px;
  font-family: 'DM Mono', monospace;
  font-size: 10px;
  letter-spacing: 0.04em;
  white-space: nowrap;
}

.status-live { color: #6ee7b7; }
.status-dev  { color: #a78bfa; }
```

### Why-Card

```html
<div class="why-card">
  <div class="why-icon">
    <svg viewBox="0 0 24 24"><!-- Lucide icon, stroke-only, 18px --></svg>
  </div>
  <div class="why-title">Card Title</div>
  <div class="why-text">Description text...</div>
</div>
```

```css
.why-card {
  background: var(--bg-card);
  border: 1px solid var(--border);
  border-radius: 14px;
  padding: 28px 26px;
  position: relative;
  overflow: hidden;
  transition: all 0.3s;
}
.why-card:hover {
  background: var(--bg-card-hover);
  border-color: rgba(139,92,246,0.25);
}
.why-icon {
  width: 40px; height: 40px;
  border-radius: 10px;
  background: rgba(139,92,246,0.1);
  border: 1px solid rgba(139,92,246,0.2);
  display: flex; align-items: center; justify-content: center;
  margin-bottom: 18px;
}
/* Icon: 18px, stroke-only SVG, stroke: #c4b0f0, stroke-width: 1.5 */
```

### Form Control

```html
<div class="form-group">
  <label for="field">Field Label</label>
  <input id="field" type="text" class="form-control" placeholder="...">
</div>
```

```css
.form-control {
  width: 100%;
  background: rgba(255,255,255,0.04);
  border: 1px solid rgba(255,255,255,0.09);
  border-radius: 8px;
  padding: 12px 16px;
  font-family: 'DM Sans', sans-serif;
  font-size: 14px;
  color: #f0eeff;
  outline: none;
  transition: all 0.2s;
}
.form-control:focus {
  border-color: rgba(139,92,246,0.4);
  background: rgba(139,92,246,0.04);
}
```

### Primary Submit Button

```css
.btn-submit {
  width: 100%;
  background: linear-gradient(135deg, #7c3aed 0%, #8b5cf6 100%);
  border: none;
  border-radius: 8px;
  padding: 14px 24px;
  font-family: 'DM Sans', sans-serif;
  font-size: 14px;
  font-weight: 500;
  color: white;
  cursor: pointer;
  transition: all 0.25s;
}
.btn-submit:hover {
  transform: translateY(-1px);
  box-shadow: 0 8px 30px rgba(139,92,246,0.35);
}
```

### Inline Logo SVG

Embed directly in the navbar HTML. Height 22px, width auto.

```html
<svg width="85" height="24" viewBox="0 0 85 24" fill="none"
     xmlns="http://www.w3.org/2000/svg"
     style="height:22px; width:auto; display:block;">
  <path d="M17.2795 24H13.851V12C13.851 10.4229 13.4624 8.98286 12.6853 7.68C11.9311 6.37714 10.9025 5.34857 9.59971 4.59429C8.29689 3.81714 6.85693 3.42857 5.27984 3.42857H3.42847V24H0V0H5.27984C7.4512 0 9.43971 0.537143 11.2454 1.61143C13.0739 2.68572 14.5138 4.09143 15.5652 5.82857C16.6166 4.09143 18.0452 2.68572 19.8508 1.61143C21.6793 0.537143 23.6793 0 25.8506 0H31.1305V24H27.702V3.42857H25.8506C24.2736 3.42857 22.8336 3.81714 21.5308 4.59429C20.2508 5.34857 19.2223 6.37714 18.4452 7.68C17.668 8.98286 17.2795 10.4229 17.2795 12V24Z" fill="#F5F5F5"/>
  <path d="M57.8441 24H35.5591V17.1429C35.5591 15.8857 35.8677 14.7429 36.4848 13.7143C37.1019 12.6629 37.9247 11.8286 38.9533 11.2114C40.0047 10.5943 41.1589 10.2857 42.416 10.2857H50.9872C51.9243 10.2857 52.7243 9.95429 53.3871 9.29143C54.0728 8.60572 54.4157 7.79429 54.4157 6.85714C54.4157 5.92 54.0728 5.12 53.3871 4.45714C52.7243 3.77143 51.9243 3.42857 50.9872 3.42857H37.2733V0H50.9872C52.2443 0 53.3871 0.308572 54.4157 0.925715C55.4671 1.54286 56.3013 2.37714 56.9184 3.42857C57.5356 4.45714 57.8441 5.6 57.8441 6.85714C57.8441 8.11429 57.5356 9.26857 56.9184 10.32C56.3013 11.3486 55.4671 12.1714 54.4157 12.7886C53.3871 13.4057 52.2443 13.7143 50.9872 13.7143H42.416C41.4789 13.7143 40.6675 14.0571 39.9818 14.7429C39.2961 15.4057 38.9533 16.2057 38.9533 17.1429V20.5714H57.8441V24Z" fill="#F5F5F5"/>
  <path d="M61.0007 0H64.4292V8.57143C64.4292 9.50857 64.7606 10.32 65.4235 11.0057C66.1092 11.6686 66.9206 12 67.8577 12H81.5715V0H85V24H81.5715V15.4286H67.8577C66.6006 15.4286 65.4463 15.12 64.3949 14.5029C63.3664 13.8857 62.5435 13.0629 61.9264 12.0343C61.3093 10.9829 61.0007 9.82857 61.0007 8.57143V0Z" fill="#F5F5F5"/>
</svg>
```

### Social Icon Button

```css
.social-btn {
  width: 36px; height: 36px;
  border-radius: 8px;
  background: rgba(255,255,255,0.04);
  border: 1px solid rgba(255,255,255,0.08);
  display: flex; align-items: center; justify-content: center;
  text-decoration: none;
  transition: all 0.2s;
}
.social-btn:hover {
  background: rgba(139,92,246,0.12);
  border-color: rgba(139,92,246,0.3);
}
/* Icon SVG fill: #888 default, #c4b0f0 on hover */
```

---

## 6. Page Structure

Single vertical scroll. No routing. Anchor links for smooth-scroll navigation.

```
┌────────────────────────────────────────────┐
│  NAVBAR  (position: fixed, z-index: 100)   │
├────────────────────────────────────────────┤
│                                            │
│  HERO  (min-height: 100vh)                 │
│    ↳ Atmospheric glow blob (::after)       │
│    ↳ Watermark text (absolute, z-index:0)  │
│    ↳ Foreground content (z-index:1)        │
│    ↳ Three columns (below content)         │
│                                            │
├────────────────────────────────────────────┤
│                                            │
│  WHY WITH US  (padding: 120px 48px)        │
│    ↳ Header + intro                        │
│    ↳ 6-card grid (3×2)                     │
│                                            │
├────────────────────────────────────────────┤
│                                            │
│  CONTACT / CTA  (id="contact")             │
│    ↳ Left: copy                            │
│    ↳ Right: contact form                   │
│                                            │
├────────────────────────────────────────────┤
│  FOOTER  (border-top, flex row)            │
├────────────────────────────────────────────┤
│  PRIVACY MODAL  (fixed overlay, z:1000)    │
└────────────────────────────────────────────┘
```

---

## 7. Section 1 — Navbar

**Position:** `fixed`, top-0, full width, `z-index: 100`
**Background:** `rgba(10,10,15,0.7)` + `backdrop-filter: blur(20px)` + `-webkit-backdrop-filter: blur(20px)`
**Border-bottom:** `1px solid rgba(255,255,255,0.04)`
**Padding:** `20px 48px` (desktop) / `16px 24px` (mobile)
**Layout:** `display: flex`, `justify-content: space-between`, `align-items: center`

### Left — Logo

M24 SVG inline (see Component above), `height: 22px`, wrapped in `<a href="#">`.
Hover: `opacity: 0.95 → 1.0`, transition 0.2s.

### Right — CTA Button

| Property | Value |
|---|---|
| Label | `"Get in touch"` |
| `href` | `#contact` (smooth scroll) |
| Background | `rgba(139,92,246,0.12)` |
| Border | `1px solid rgba(139,92,246,0.3)` |
| Text color | `#c4b0f0` |
| Font | DM Sans 500, 13px |
| Padding | `8px 20px` |
| Border-radius | `6px` |
| Hover bg | `rgba(139,92,246,0.22)` |
| Hover border | `rgba(139,92,246,0.5)` |

---

## 8. Section 2 — Hero

Full viewport height. Centered content. Three stacked layers.

### Layer 1 — Atmospheric Glow

Pseudo-element `::after` on `.hero`: radial-gradient, 600×400px, violet, centered. `pointer-events: none`, `z-index: 0`.

### Layer 2 — Watermark Text

| Property | Value |
|---|---|
| Text | `"M24 VENTURE CAPITAL"` |
| Position | `absolute`, `top:50%`, `left:50%`, `transform:translate(-50%,-50%)` |
| Font | Syne 800, `clamp(60px, 10vw, 140px)` |
| Color | `rgba(255,255,255,0.028)` — barely visible, atmospheric only |
| Letter-spacing | `-0.02em` |
| z-index | `0` |
| `aria-hidden` | `true` |

### Layer 3 — Foreground Content

**Eyebrow badge**
- Text: `"Est. 2022 · Web3 Infrastructure"`
- Font: DM Mono, 11px, uppercase, letter-spacing: 0.14em, color: `#a78bfa`
- Container: inline-flex, border `1px solid rgba(139,92,246,0.2)`, background `rgba(139,92,246,0.06)`, border-radius: 20px, padding: `6px 14px`
- Left element: 6px pulsing violet dot (`pulse-violet` animation)

**Main heading**

Three separate lines inside `<h1>`:
```
"Blockchain Validator."
"Algorithmic Trading."
"Venture Foundation."
```
- Font: Syne 700, `clamp(36px, 5.5vw, 72px)`, letter-spacing: `-0.03em`, line-height: `1.1`
- Color: gradient shimmer (see Animations section)
- Margin-bottom: `24px`

**Subheading**
- Text: `"Engineering reliability at every layer — from protocol validation to AI-driven strategies and early-stage venture investments."`
- Font: DM Sans 300, `clamp(15px, 1.8vw, 18px)`, line-height: `1.7`
- Color: `#888888`, max-width: `520px`, margin: `0 auto`, margin-bottom: `52px`

---

## 9. Section 3 — Three Columns

Positioned directly below hero text content, still inside the hero section.
Max-width: `1100px`, centered, padding: `0 48px`.

### Grid

```css
.columns-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 1px;                      /* gap = visible column divider */
  background: var(--border);     /* divider color fills the gap */
  border-radius: 16px;
  overflow: hidden;
  border: 1px solid var(--border);
}

.column-card {
  background: var(--bg-card);
  padding: 32px 28px;
  transition: background 0.3s;
}
.column-card:hover { background: var(--bg-card-hover); }
```

### Column Title Style

```css
.col-title {
  font-family: 'Syne', sans-serif;
  font-weight: 700;
  font-size: 13px;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  color: #c4b0f0;
  margin-bottom: 24px;
  display: flex;
  align-items: center;
  gap: 8px;
}
.col-title::before {
  content: '';
  display: block;
  width: 18px; height: 1px;
  background: #8b5cf6;
  opacity: 0.6;
}
```

### Column 1 — Validator

| Network | Status |
|---|---|
| Near Protocol | 🟢 Live |
| Satori Network | 🟣 In Development |
| Xai Games | 🟢 Live |
| Moonriver | 🟢 Live |

### Column 2 — AI Trading Strategies

| Strategy | Status |
|---|---|
| SOL Orderbook Scalper | 🟣 In Development |
| LuxAlgo Trading | 🟣 In Development |
| Wave Hybrid Bot | 🟣 In Development |
| Moby Sniper Bot | 🟣 In Development |
| Polymirror Bot | 🟢 Live |

### Column 3 — Venture Rounds

> No status badges. Items are prefixed with a small 3px violet dot (`opacity: 0.5`). These are historical investment rounds, not active live/dev systems.

- Manta Network
- Xai Games
- Humans AI
- Moonbeam
- Laos Network
- Near Protocol

### Item Row Style

```css
.network-item {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 10px 0;
  border-bottom: 1px solid rgba(255,255,255,0.04);
}
.network-item:last-child { border-bottom: none; }

.network-name {
  font-size: 13.5px;
  font-weight: 400;
  color: rgba(240,238,255,0.8);
}
```

---

## 10. Section 4 — Why With Us

**Container:** max-width `1100px`, padding `120px 48px`

### Header

| Element | Copy |
|---|---|
| Eyebrow | `"Why M24"` — DM Mono, 11px, uppercase, letter-spacing: 0.12em, color: `#a78bfa` |
| H2 | `"Built for performance."` + newline + `"Trusted for a reason."` |
| Intro | See full copy below |

**Intro paragraph:**
> "From blockchain validation to algorithmic trading and venture investments — every layer of M24 is engineered for reliability, transparency, and growth. We don't just build systems that work — we build systems you can depend on."

Font: DM Sans 300, 15px, max-width 600px, color `#888`, line-height `1.75`, margin-bottom `64px`.

### Card Grid

`display: grid`, `grid-template-columns: repeat(3, 1fr)`, `gap: 16px`

### All 6 Cards

| # | Title | Body |
|---|---|---|
| 1 | **Institutional Reliability** | "We operate on enterprise-grade infrastructure with SLO-defined performance, real-time monitoring, and proactive incident response. Every node and model follows SRE principles — because downtime isn't an option." |
| 2 | **Proven Security Architecture** | "All operations follow multi-layer security: key management via HSM, encrypted backups, and strict access controls. Our systems are continuously audited and aligned with ISO 27001 standards." |
| 3 | **Transparent Performance** | "We provide verifiable metrics — from validator uptime to AI strategy results. Clients access clear dashboards, real-time analytics, and performance audits you can trust." |
| 4 | **Non-Custodial by Design** | "M24 never takes custody of client assets. Our validators, trading strategies, and fund structures prioritize independence and full control over your capital." |
| 5 | **Global Redundancy** | "Our infrastructure spans multiple regions and providers to ensure zero single points of failure. Geo-distributed servers and automated failover protect uptime under any condition." |
| 6 | **Regulatory Clarity** | "We operate under strict compliance frameworks: AML/KYC, GDPR, and risk disclosure policies. Transparency isn't a checkbox — it's embedded in every process we build." |

**Icon style:** Inline SVG, `18px`, stroke-only, `stroke: #c4b0f0`, `stroke-width: 1.5`, `stroke-linecap: round`, `stroke-linejoin: round`, `fill: none`.
Suggested Lucide icons: `monitor`, `shield`, `trending-up`, `layers`, `globe`, `badge-check`.

---

## 11. Section 5 — Contact Form

**Anchor:** `id="contact"` — linked from navbar CTA.
**Outer padding:** `80px 48px 120px`
**Wrapper card:** bg `var(--bg-card)`, border `1px solid var(--border)`, border-radius `20px`, padding `64px`
**Inner layout:** `display: grid`, `grid-template-columns: 1fr 1fr`, `gap: 64px`

### Left Column — Copy

| Element | Copy |
|---|---|
| Eyebrow | `"Contact"` |
| H2 | `"Start a conversation."` |
| Paragraph | `"Whether you're looking to delegate validation, explore algorithmic strategies, or discuss a venture opportunity — we'd like to hear from you."` |

### Right Column — Form

| Field | Type | Label | Placeholder | Required |
|---|---|---|---|---|
| Name | `text` | `Name` | `"Your name"` | Yes |
| Company | `text` | `Company` | `"Company (optional)"` | No |
| Email | `email` | `Email` | `"your@email.com"` | Yes |
| Interest | `select` | `Area of interest` | `"Select one..."` | No |
| Message | `textarea` | `Message` | `"Tell us about your goals..."` | No |

> Name and Company share one row (`display: grid`, `grid-template-columns: 1fr 1fr`, `gap: 12px`).

**Select options:** Blockchain Validation / AI Trading Strategies / Venture Investment / General Inquiry

**Submit button:** Label `"Send message"`, full width.

**JS submit animation:**
```js
function handleSubmit(e) {
  e.preventDefault();
  const btn = document.getElementById('submit-btn');
  btn.textContent = 'Sending...';
  btn.disabled = true;
  setTimeout(() => {
    btn.textContent = 'Message sent ✓';
    btn.style.background = 'linear-gradient(135deg, #065f46, #059669)';
    document.getElementById('contact-form').reset();
    setTimeout(() => {
      btn.textContent = 'Send message';
      btn.style.background = '';
      btn.disabled = false;
    }, 4000);
  }, 1200);
}
```

> **Note:** The form uses a UI-only demo submit. Wire up a real endpoint (Formspree, Netlify Forms, or backend API) separately before launch.

**Below button note:** `"We typically respond within 24 hours. Your data is handled per our Privacy Policy."` — 11px, color `--text-muted`.

---

## 12. Section 6 — Footer

**Border-top:** `1px solid rgba(255,255,255,0.07)`
**Padding:** `40px 48px`
**Layout:** `display: flex`, `justify-content: space-between`, `align-items: center`

### Left — Legal

- **Line 1 (copyright):** `"© 2024 M24 Venture Capital. All rights reserved."` — DM Mono, 11px, letter-spacing: 0.04em, color: `#555`
- **Line 2 (links):** `"Privacy Policy"` · `"Terms of Use"` — 12px, color `#555`, hover: `#c4b0f0`. Both call `openPrivacy()`.

### Right — Social Icons

| Platform | Icon | `href` | `aria-label` |
|---|---|---|---|
| X (Twitter) | X logo SVG (not bird) | `#` — client replaces | `"X (Twitter)"` |
| LinkedIn | LinkedIn logo SVG | `#` — client replaces | `"LinkedIn"` |
| Discord | Discord logo SVG | `#` — client replaces | `"Discord"` |

> **Client action:** Replace all three `href="#"` values with real social URLs before launch. No other changes needed.

---

## 13. Section 7 — Privacy Modal

Triggered by "Privacy Policy" and "Terms of Use" clicks in footer.

| Property | Value |
|---|---|
| Overlay | `position: fixed`, `inset: 0`, `background: rgba(0,0,0,0.8)`, `backdrop-filter: blur(8px)`, `z-index: 1000` |
| Box | bg `#0f0f18`, border `1px solid rgba(139,92,246,0.2)`, border-radius `16px`, padding `48px`, max-width `640px`, `max-height: 80vh`, `overflow-y: auto` |
| Animation | `modalIn` keyframe: scale `0.96→1` + translateY `8px→0`, `0.25s ease` |
| Close triggers | × button top-right, `Escape` key, click on overlay background |
| Title | `"Privacy Policy"` — Syne 700, 22px |
| Date | `"Last updated: January 2025"` — placeholder, client updates |

### Placeholder Structure (client replaces with real legal text)

```
1. Information We Collect
2. How We Use Information
3. Data Retention
4. Your Rights (GDPR)
5. AML/KYC Compliance
6. Contact
```

### JS

```js
function openPrivacy() {
  document.getElementById('privacy-modal').classList.add('open');
  document.body.style.overflow = 'hidden';
}
function closePrivacy() {
  document.getElementById('privacy-modal').classList.remove('open');
  document.body.style.overflow = '';
}
function closePrivacyOutside(e) {
  if (e.target === document.getElementById('privacy-modal')) closePrivacy();
}
document.addEventListener('keydown', e => { if (e.key === 'Escape') closePrivacy(); });
```

---

## 14. Complete Content Reference

Every string on the page, in order. Single source of truth for copy.

### Navbar
```
CTA button: "Get in touch"
```

### Hero
```
Eyebrow:    "Est. 2022 · Web3 Infrastructure"
Heading:    "Blockchain Validator."
            "Algorithmic Trading."
            "Venture Foundation."
Subhead:    "Engineering reliability at every layer — from protocol
             validation to AI-driven strategies and early-stage
             venture investments."
```

### Three Columns
```
VALIDATOR
  Near Protocol         → Live
  Satori Network        → In Development
  Xai Games             → Live
  Moonriver             → Live

AI TRADING STRATEGIES
  SOL Orderbook Scalper → In Development
  LuxAlgo Trading       → In Development
  Wave Hybrid Bot       → In Development
  Moby Sniper Bot       → In Development
  Polymirror Bot        → Live

VENTURE ROUNDS
  Manta Network
  Xai Games
  Humans AI
  Moonbeam
  Laos Network
  Near Protocol
```

### Why With Us
```
Eyebrow:  "Why M24"
H2:       "Built for performance.
           Trusted for a reason."
Intro:    "From blockchain validation to algorithmic trading and venture
           investments — every layer of M24 is engineered for
           reliability, transparency, and growth. We don't just build
           systems that work — we build systems you can depend on."

Card 1 — Institutional Reliability
"We operate on enterprise-grade infrastructure with SLO-defined
performance, real-time monitoring, and proactive incident response.
Every node and model follows SRE principles — because downtime
isn't an option."

Card 2 — Proven Security Architecture
"All operations follow multi-layer security: key management via HSM,
encrypted backups, and strict access controls. Our systems are
continuously audited and aligned with ISO 27001 standards."

Card 3 — Transparent Performance
"We provide verifiable metrics — from validator uptime to AI strategy
results. Clients access clear dashboards, real-time analytics, and
performance audits you can trust."

Card 4 — Non-Custodial by Design
"M24 never takes custody of client assets. Our validators, trading
strategies, and fund structures prioritize independence and full
control over your capital."

Card 5 — Global Redundancy
"Our infrastructure spans multiple regions and providers to ensure
zero single points of failure. Geo-distributed servers and automated
failover protect uptime under any condition."

Card 6 — Regulatory Clarity
"We operate under strict compliance frameworks: AML/KYC, GDPR, and
risk disclosure policies. Transparency isn't a checkbox — it's
embedded in every process we build."
```

### Contact Form
```
Eyebrow:    "Contact"
H2:         "Start a conversation."
Paragraph:  "Whether you're looking to delegate validation, explore
             algorithmic strategies, or discuss a venture opportunity
             — we'd like to hear from you."
Button:     "Send message"
Note:       "We typically respond within 24 hours. Your data is
             handled per our Privacy Policy."
```

### Footer
```
Copyright: "© 2024 M24 Venture Capital. All rights reserved."
Links:     "Privacy Policy"  ·  "Terms of Use"
Socials:   X (Twitter)  ·  LinkedIn  ·  Discord
```

---

## 15. Responsive Rules

### Breakpoints

| Breakpoint | `max-width` | Key changes |
|---|---|---|
| **Tablet** | `900px` | Nav padding → `16px 24px`; hero padding → `100px 24px 60px`; columns grid → `1fr` (stacked); why-grid → `2 columns`; CTA wrapper padding → `36px 28px`; CTA inner → `1fr` (text above form); footer → column layout, gap `20px`; watermark → `clamp(36px, 8vw, 80px)` |
| **Mobile** | `600px` | Why-grid → `1fr`; form Name+Company row → `1fr`; hero title → `clamp(28px, 8vw, 48px)` |

### Fluid Text Sizing

All major text sizes use `clamp(min, vw, max)` — no abrupt jumps between breakpoints. Body and card text stay fixed.

```css
/* Examples */
.hero-title    { font-size: clamp(36px, 5.5vw, 72px); }
.section-heading { font-size: clamp(28px, 4vw, 48px); }
.hero-desc     { font-size: clamp(15px, 1.8vw, 18px); }
.hero-watermark { font-size: clamp(60px, 10vw, 140px); }
```

---

## 16. Ready Prompts

### Full Build Prompt — paste directly into Stitch / Claude Design

```
Build a single-file dark luxury landing page for M24 Venture Capital.
Output: one complete .html file, all CSS and JS inline, no frameworks.
Google Fonts import only. Language: English.

━━ FONTS ━━
Syne (700, 800) — headings and display text
DM Mono (400, 500) — monospace: labels, badges, copyright
DM Sans (300, 400, 500) — body text and forms

━━ COLOR TOKENS (:root CSS variables) ━━
--bg: #0a0a0f
--bg-card: rgba(255,255,255,0.03)
--bg-card-hover: rgba(255,255,255,0.055)
--border: rgba(255,255,255,0.07)
--border-hover: rgba(139,92,246,0.35)
--violet: #8b5cf6
--violet-light: #c4b0f0
--violet-dim: #a78bfa
--green: #6ee7b7
--text-primary: #f0eeff
--text-secondary: #888888
--text-muted: #555555
--glow: rgba(139,92,246,0.08)

━━ ANIMATIONS ━━
shimmer: background-position 0%→300%, 5s linear infinite — on hero title
pulse-green: opacity 1→0.5→1 + box-shadow pulse, 1.8s — on live dots (#6ee7b7)
pulse-violet: opacity 1→0.4→1 + box-shadow pulse, 2.2s — on dev dots (#a78bfa)
fadeInUp: opacity 0→1 + translateY(24px→0), 1s ease — on hero content
modalIn: scale(0.96→1) + translateY(8px→0), 0.25s — on modal open
IntersectionObserver: trigger fadeInUp on .why-card and .cta-wrapper when scrolled into view
Noise texture overlay: body::before, SVG fractalNoise, opacity 0.4, fixed, pointer-events:none
Atmospheric glow: .hero::after, radial-gradient violet, 600x400px, centered

━━ SECTION 1 — NAVBAR ━━
position: fixed, backdrop-filter: blur(20px), z-index: 100
Left: M24 SVG logo inline (see SVG below), height 22px
Right: "Get in touch" → href="#contact", ghost button, violet tint

M24 SVG logo paths (embed inline, fill #F5F5F5):
Path 1: M17.2795 24H13.851V12C13.851 10.4229 13.4624 8.98286 12.6853 7.68C11.9311 6.37714 10.9025 5.34857 9.59971 4.59429C8.29689 3.81714 6.85693 3.42857 5.27984 3.42857H3.42847V24H0V0H5.27984C7.4512 0 9.43971 0.537143 11.2454 1.61143C13.0739 2.68572 14.5138 4.09143 15.5652 5.82857C16.6166 4.09143 18.0452 2.68572 19.8508 1.61143C21.6793 0.537143 23.6793 0 25.8506 0H31.1305V24H27.702V3.42857H25.8506C24.2736 3.42857 22.8336 3.81714 21.5308 4.59429C20.2508 5.34857 19.2223 6.37714 18.4452 7.68C17.668 8.98286 17.2795 10.4229 17.2795 12V24Z
Path 2: M57.8441 24H35.5591V17.1429C35.5591 15.8857 35.8677 14.7429 36.4848 13.7143C37.1019 12.6629 37.9247 11.8286 38.9533 11.2114C40.0047 10.5943 41.1589 10.2857 42.416 10.2857H50.9872C51.9243 10.2857 52.7243 9.95429 53.3871 9.29143C54.0728 8.60572 54.4157 7.79429 54.4157 6.85714C54.4157 5.92 54.0728 5.12 53.3871 4.45714C52.7243 3.77143 51.9243 3.42857 50.9872 3.42857H37.2733V0H50.9872C52.2443 0 53.3871 0.308572 54.4157 0.925715C55.4671 1.54286 56.3013 2.37714 56.9184 3.42857C57.5356 4.45714 57.8441 5.6 57.8441 6.85714C57.8441 8.11429 57.5356 9.26857 56.9184 10.32C56.3013 11.3486 55.4671 12.1714 54.4157 12.7886C53.3871 13.4057 52.2443 13.7143 50.9872 13.7143H42.416C41.4789 13.7143 40.6675 14.0571 39.9818 14.7429C39.2961 15.4057 38.9533 16.2057 38.9533 17.1429V20.5714H57.8441V24Z
Path 3: M61.0007 0H64.4292V8.57143C64.4292 9.50857 64.7606 10.32 65.4235 11.0057C66.1092 11.6686 66.9206 12 67.8577 12H81.5715V0H85V24H81.5715V15.4286H67.8577C66.6006 15.4286 65.4463 15.12 64.3949 14.5029C63.3664 13.8857 62.5435 13.0629 61.9264 12.0343C61.3093 10.9829 61.0007 9.82857 61.0007 8.57143V0Z

━━ SECTION 2 — HERO ━━
min-height: 100vh, centered content
Layer 1: atmospheric glow blob (::after), radial-gradient violet
Layer 2: watermark "M24 VENTURE CAPITAL", Syne 800, clamp(60px,10vw,140px),
  color rgba(255,255,255,0.028), absolute centered, aria-hidden="true"
Layer 3 foreground:
  - Eyebrow badge: "Est. 2022 · Web3 Infrastructure" — DM Mono, pulsing violet dot, pill border
  - H1 three lines (Syne 700, gradient shimmer):
    "Blockchain Validator."
    "Algorithmic Trading."
    "Venture Foundation."
  - Subhead: "Engineering reliability at every layer — from protocol
    validation to AI-driven strategies and early-stage venture investments."

━━ SECTION 3 — THREE COLUMNS ━━
CSS grid 3fr, 1px gap (filled with --border color), border-radius 16px
Max-width 1100px, below hero heading text

VALIDATOR:
  Near Protocol         → Live (green dot #6ee7b7 + text)
  Satori Network        → In Development (violet dot #a78bfa + text)
  Xai Games             → Live
  Moonriver             → Live

AI TRADING STRATEGIES:
  SOL Orderbook Scalper → In Development
  LuxAlgo Trading       → In Development
  Wave Hybrid Bot       → In Development
  Moby Sniper Bot       → In Development
  Polymirror Bot        → Live

VENTURE ROUNDS (no status — small 3px violet dot prefix only):
  Manta Network, Xai Games, Humans AI, Moonbeam, Laos Network, Near Protocol

━━ SECTION 4 — WHY WITH US ━━
max-width 1100px, padding 120px 48px
Eyebrow: "Why M24"
H2: "Built for performance.\nTrusted for a reason."
Intro: "From blockchain validation to algorithmic trading and venture investments
  — every layer of M24 is engineered for reliability, transparency, and growth.
  We don't just build systems that work — we build systems you can depend on."

6 cards, 3×2 grid, each with icon (inline Lucide SVG, stroke-only, #c4b0f0) + title + body:
1. Institutional Reliability — "We operate on enterprise-grade infrastructure
   with SLO-defined performance, real-time monitoring, and proactive incident
   response. Every node and model follows SRE principles — because downtime
   isn't an option."
2. Proven Security Architecture — "All operations follow multi-layer security:
   key management via HSM, encrypted backups, and strict access controls. Our
   systems are continuously audited and aligned with ISO 27001 standards."
3. Transparent Performance — "We provide verifiable metrics — from validator
   uptime to AI strategy results. Clients access clear dashboards, real-time
   analytics, and performance audits you can trust."
4. Non-Custodial by Design — "M24 never takes custody of client assets. Our
   validators, trading strategies, and fund structures prioritize independence
   and full control over your capital."
5. Global Redundancy — "Our infrastructure spans multiple regions and providers
   to ensure zero single points of failure. Geo-distributed servers and
   automated failover protect uptime under any condition."
6. Regulatory Clarity — "We operate under strict compliance frameworks: AML/KYC,
   GDPR, and risk disclosure policies. Transparency isn't a checkbox — it's
   embedded in every process we build."

━━ SECTION 5 — CONTACT FORM ━━
id="contact", max-width 1100px, padding 80px 48px 120px
2-column grid: left=copy, right=form
Left: eyebrow "Contact" / h2 "Start a conversation." /
  p "Whether you're looking to delegate validation, explore algorithmic
  strategies, or discuss a venture opportunity — we'd like to hear from you."
Form: [Name] [Company] in one row | [Email] | [Interest select] | [Message textarea]
Select options: Blockchain Validation / AI Trading Strategies /
  Venture Investment / General Inquiry
Button: "Send message", full-width, violet gradient
JS fake submit: Sending... (1.2s) → Message sent ✓ (green, 4s) → reset
Note below: "We typically respond within 24 hours. Your data is handled per
  our Privacy Policy."

━━ SECTION 6 — FOOTER ━━
border-top, flex row space-between, padding 40px 48px
Left: "© 2024 M24 Venture Capital. All rights reserved."
      "Privacy Policy" · "Terms of Use" — both call openPrivacy()
Right: 3 icon buttons (36×36px, rounded) — X/Twitter, LinkedIn, Discord
  (SVG logos inline, href="#" placeholders — client replaces)

━━ SECTION 7 — PRIVACY MODAL ━━
id="privacy-modal", position fixed, backdrop-filter blur(8px)
Box: bg #0f0f18, violet border, border-radius 16px, padding 48px, max-width 640px
Title: "Privacy Policy", close × button top-right
Close on: button click, Escape key, overlay click
Content: 6 placeholder sections (client replaces with real legal text)

━━ RESPONSIVE ━━
@media (max-width: 900px):
  columns → 1 column stack
  why cards → 2 columns
  CTA → 1 column (text above form)
  footer → column layout
@media (max-width: 600px):
  why cards → 1 column
  form name+company row → 1 column
```

---

*Document maintained by M24 team. Update this file whenever page copy, structure, or design tokens change.*
