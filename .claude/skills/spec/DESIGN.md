# Design rules (caveman-ultra)

Apply to the single-file HTML spec artifact. Keep every number/property/ban exact — code symbols never abbreviated.

Goal: ship production-grade, not prototype. Beautiful, responsive, fast, precise, bug-free, on-brand. Detail matter. No shortcut unless user ask. Battle-test (screenshot, browser).

## Color
- Verify contrast. Body text ≥4.5:1 vs bg. Large text (≥18px, or bold ≥14px) ≥3:1. Placeholder same 4.5:1.
- Top fail: muted gray body on tinted near-white. If close → push body toward ink. Light-gray "elegance" = #1 unreadable cause.
- Gray text on colored bg = washed. Use darker shade of bg's own hue, or alpha of text color.

## Typography
- Body line len cap 65–75ch.
- No pair similar-but-not-identical fonts (2 geometric sans / 2 humanist sans). Pair on contrast axis (serif+sans, geometric+humanist) OR 1 family multi-weight.
- Hero/display `clamp()` max ≤6rem (~96px).
- Display letter-spacing floor ≥ `-0.04em`. `-0.02em` to `-0.03em` plenty. Tighter → letters touch → cramped.
- `text-wrap: balance` on h1–h3. `text-wrap: pretty` on long prose.

## Layout
- Vary spacing = rhythm.
- Cards = lazy answer. Use only when truly best affordance. Nested cards always wrong.
- Flexbox 1D, Grid 2D. No Grid when `flex-wrap` simpler.
- Responsive grid no breakpoint: `repeat(auto-fit, minmax(280px, 1fr))`.
- Semantic z-index scale: dropdown → sticky → modal-backdrop → modal → toast → tooltip. No `999`/`9999`.

## Motion
- Intentional, part of build, not afterthought.
- No animate layout props unless needed.
- Ease-out exponential (quart/quint/expo). No bounce/elastic.
- Advanced → lib (motion, gsap, anime.js, lenis).
- `@media (prefers-reduced-motion: reduce)` mandatory → crossfade/instant fallback.
- Stagger list items OK. Tell = uniform reflex (1 identical entrance every section). Each reveal fit what it reveals. Not an excuse to ship zero motion.
- Reveal must enhance already-visible default. No gating content visibility on class-trigger transition (pauses on hidden tab/headless → ships blank).
- Premium materials beyond transform/opacity: blur, backdrop-filter, clip-path, mask, shadow/glow — when improve + stay smooth.

## Interaction
- Dropdown `position: absolute` inside `overflow: hidden`/`auto` → clipped. Use `<dialog>`/popover API, `position: fixed`, or portal.

## New projects only (no prior work)
- Color space: OKLCH.
- Cream/sand/beige bg = saturated AI default 2026. Whole warm-neutral band (OKLCH L 0.84–0.97, C<0.06, hue 40–100) reads cream regardless of name. Token names `--paper`/`--cream`/`--sand`/`--bone`/`--flour`/`--linen`/`--parchment`/`--wheat`/`--biscuit`/`--ivory` = tells. Brief "warm/magazine-warm/editorial" → do NOT make near-white warm-tinted bg (that's the AI move). Pick: (a) saturated brand body (terracotta/oxblood/deep ochre/near-black), (b) true off-white chroma 0 (or toward brand hue, not warmth-default), (c) darker mid-tone tinted neutral = brand's own. Warmth via accent+type+imagery, not bg.
- Tinted neutral: +0.005–0.015 chroma toward brand hue. No reflex warm/cool tint.
- Dark vs light never default. Write 1 sentence physical scene (who/where/ambient light/mood). If sentence don't force the answer → not concrete enough. Add detail till it do.
- Pick color strategy before colors. 4 steps on commitment axis:
  - Restrained: tinted neutral + 1 accent ≤10%. Product default.
  - Committed: 1 saturated color carries 30–60% surface. Identity pages.
  - Full palette: 3–4 named roles, each deliberate. Campaigns / data viz.
  - Drenched: surface IS the color. Heroes / campaign pages.

## ABSOLUTE BANS (match-and-refuse → rewrite element)
- Side-stripe borders: `border-left`/`border-right` >1px colored accent on card/list/callout/alert. Rewrite: full border, bg tint, leading number/icon, or nothing.
- Gradient text: `background-clip: text` + gradient. Use 1 solid color; emphasis via weight/size.
- Glassmorphism as default. Rare + purposeful, or nothing.
- Hero-metric template (big number, small label, supporting stats, gradient accent). SaaS cliché.
- Identical card grids (same-size icon+heading+text repeated).
- Tiny uppercase tracked eyebrow above every section. 1 named kicker = brand voice; eyebrow every section = AI grammar. Different cadence.
- Numbered section markers as default scaffold (`01`/`02`/`03`) on every section. Numbers earn place only when section IS a real sequence + order carries info reader needs.
- Text overflow container. Test heading copy every breakpoint; overflow → reduce `clamp()` max or rewrite copy. Viewport = part of design.

### Codex-specific defects (refuse → rewrite)
- `border: 1px solid X` + `box-shadow: 0 Npx Mpx` with M≥16px same element = ghost-card. Pick one: single solid border at brand color, OR shadow ≤8px blur. Never both decorative.
- `border-radius: 32px+` on card/section/input. Cards top 12–16px. Full-pill OK tags/buttons only. 24/28/32/40px on card = tell.
- Hand-drawn/sketchy SVG (`loose-sketch`/`*-sketch`/`doodle`/`wavy`; `feTurbulence`/`feDisplacementMap` grain; 5–30 path crude scenes). = amateur. Can't render real → ship no illustration.
- `repeating-linear-gradient(...)` stripe bg. No.
- Meta-criticism copy (name concept + ironic modifier; strawman to "correct"). Make the specific claim.

## Slop test
- "AI made that" w/o doubt → fail.
- First-order: can guess theme+palette from category alone → first training reflex. Rework scene+strategy till not obvious from domain.
- Second-order: can guess aesthetic family from category+anti-ref ("AI tool not SaaS-cream → editorial-typographic"; "fintech not navy-gold → terminal dark") → trap 1 tier deeper. Rework till both not obvious.
