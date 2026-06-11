# Design

## Theme

Dark, near-black engineered surface. Single fixed ambient field (two faint azure radial washes + 64px hairline grid, masked). No glass, no gradient text, no glow blobs.

## Color

| Token | Value | Role |
|---|---|---|
| `--bg` | `#0a0c10` | body, near-black w/ cool tint |
| `--surface` | `#11141a` | panels, cards |
| `--surface-2` | `#161a22` | raised cells / hover |
| `--border` | `rgba(255,255,255,.08)` | hairlines |
| `--border-strong` | `rgba(255,255,255,.15)` | emphasized borders |
| `--ink` | `#f2f5f8` | primary text |
| `--muted` | `#9aa6b6` | secondary text |
| `--faint` | `#828c9a` | labels (AA floor) |
| `--accent` | `#4f9dff` | the one accent; live/actionable only |
| `--accent-soft` | `rgba(79,157,255,.12)` | accent fills |
| `--accent-ink` | `#04101f` | dark text on accent |

Strategy: Restrained. Accent carries <10% of surface.

## Typography

- Display + body: **Geist** (400–800). Mono: **Geist Mono** (400/500) for labels, terminals, metrics.
- H1: `clamp(2.35rem, 5.4vw, 4.1rem)`, -.032em, 700.
- Section H2: `clamp(1.7rem, 3.4vw, 2.6rem)`, -.03em.
- Kickers: mono 12px uppercase .12em tracked, accent color (established brand system — keep).
- Body 16px / 1.6; muted for secondary.

## Motion

- Easing tokens: `--ease-out: cubic-bezier(0.23,1,0.32,1)`, `--ease-in-out: cubic-bezier(0.77,0,0.175,1)`.
- Lenis smooth scroll (duration 1.4, expo-out) + proximity section snap (26% viewport, services/approach/contact).
- Scroll reveals: `.reveal` → `.in` (translateY 18px fade, IO-triggered, once).
- Line reveals: `[data-line-reveal]` paragraphs split into masked lines, slide up staggered 88ms.
- Press feedback: `scale(.97)` on buttons.
- Canvas networks (hero / band / footer): drifting nodes, proximity lines, data pulses; pauses offscreen.
- Animations forced on (owner decision; do not re-gate behind prefers-reduced-motion).

## Components

- **Panel**: surface, 1px border, 16px radius, deep soft shadow. Variants: ops dashboard (sparkline tracks uptime value), deploy card (packet → amber boot → blue ready → collapse).
- **Terminal**: traffic-light bar + mono body, sequence-driven typing (finishes before carousel advances).
- **Carousel**: native CSS scroll-snap viewport, dot indicators (gray → accent pill).
- **Service grid**: one bordered panel, shared hairlines (NOT floating cards); accent top-line sweeps in on hover.
- **Stats**: bordered grid, count-up on reveal, accent top-lines staggered.
- **Buttons**: solid slate secondary / accent primary, 11px radius.
- **Footer**: CTA band w/ sweeping accent underline, network canvas, icon-only watermark (virtup-mark.png).

## Layout

- Max width 1140px, 24px gutters.
- Section rhythm: `clamp(46px, 6vw, 82px)` block padding.
- Hero: 2-col (text / panel-carousel), terminal stage centered below.
- z-scale: bg 0 → base 1 → header 100 → menu 200.
