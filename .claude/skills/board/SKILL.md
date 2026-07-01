---
name: board
description: Turn a completed /spec (wireframes + persona spec) into a fast, buildable project board using Ty Barho's "Mock to DONE Fast" method — reduce mocks into SCREENS/COMPONENTS/INFRASTRUCTURE/API, invert the order for build, add velocity points, and ship it as a single self-contained HTML artifact on DropFast that links back to the spec. Use when the user says /board, asks to reduce a spec/mocks into tasks, build a project board or build plan, estimate/point a build, or go from mock to done.
---

# /board — Mock → DONE Fast

Consume a `/spec` artifact (its `SCREEN:` list + wires + detailed spec) → emit a build board as one self-contained HTML page on DropFast that **links back to the spec**. Method = Ty Barho's *Mock to DONE Fast*. Output artifact, not CSV.

- Design rules for the HTML (mandatory): [../spec/DESIGN.md](../spec/DESIGN.md)
- Content gold standard: [EXAMPLE.md](EXAMPLE.md)
- Reference output: https://dropfast.dev/s/2265uqt7/ (board for spec https://dropfast.dev/s/rg9centz/)

## Input
A spec URL (DropFast) or the spec itself. Pull SCREENS straight from its `SCREEN:` headings; derive COMPONENTS from the wires; carry auth = Clerk from the spec's PRINCIPLES.

## Step 1 — Reduction
Reduce mocks → task list. Buckets **IN ORDER** (order = speed): `SCREENS → COMPONENTS → INFRASTRUCTURE → API`.
- **SCREENS** — 1 per `SCREEN:` in the spec. Easiest, just list.
- **COMPONENTS** — any UI reused across ≥2 screens (Button, TextInput, Tabs, ExerciseTile…). Walk each screen, list comps, dups OK → dedupe.
- **INFRASTRUCTURE** — every arch decision (repo, CI, conventional commits, framework, navigation, theming, state, storage, **Clerk auth**, RBAC, push/notifications, calc engine). Unbreakable-systems items (notifications, auto-advance, calc) live here.
- **API** (optional) — endpoints to add/change. New API → separate effort.

## Step 2 — Inversion
Reverse for build: `API → INFRASTRUCTURE → COMPONENTS → SCREENS`. API persists/auth first → infra patterns/scale → components = blocks → screens fast (routing+data+perms+comps ready).

## Step 3 — Velocity
Point every item. Adjusted Fibonacci `0,1,2,3,5,8,13,25` (0 = chore/bug, 25 = epic to break down). Default 3 while drafting. Estimate via fast Planning Poker: 2–4 people, 10s vote, 2min if split. Don't map points → time early. Sum per epic + grand total; note "weeks = total ÷ weekly velocity (after week 1)".

## Step 4 — Adjustments
Scope creep = main risk. Mock changes → re-audit in `SCREENS → COMPONENTS → INFRASTRUCTURE → API` order, coordinate with in-flight devs. Lock spec/mocks (creep = next cycle). Protect eng time (≤15min/day board). Storybook for components. Take time on patterns.

## Deliverable: single-file HTML
One self-contained `.html`, **write to `/tmp/<app-slug>-board/index.html`** (never the repo). Order: title + link to the spec → Step 1 Reduction (4 bucket tables, right-aligned Points col) → Step 2 Inversion (build-order strip + why) → Step 3 Velocity (fib scale, poker, totals) → Step 4 Adjustments.
- **Link to the spec**: prominent link to the spec's DropFast URL in the header + footer. SCREENS reference the spec's wireframes.
- **Style**: obey [../spec/DESIGN.md](../spec/DESIGN.md) — white bg, tables not cards, hairline dividers, system serif headings + sans body + mono for points/scales, contrast ≥4.5:1. Numbered steps OK here (real sequence).
- **Publish**: upload that `/tmp` file to DropFast (public) via the dropfast skill; return the URL; `PUT` same slug on edits.

## Checklist
- [ ] Every spec `SCREEN:` appears in the SCREENS epic; components deduped; infra includes Clerk auth + unbreakable-system items.
- [ ] Reduction in bucket order; build order inverted.
- [ ] Points on every item (fib), epic + grand totals shown.
- [ ] Links back to the spec (header + footer); passes [../spec/DESIGN.md](../spec/DESIGN.md).
- [ ] One self-contained HTML in `/tmp`, published public to DropFast (URL returned).
