---
name: spec
description: Generate engineer-ready wireframes + a persona spec for any app idea via a creative loop (personas & problem → initial spec → wireframe SCREENS → detailed per-screen spec), shipped as one self-contained monochrome-wireframe HTML page published to DropFast. Use when the user says /spec, asks to spec out an app, write a persona spec, design app wireframes, or turn an app idea into screen-by-screen requirements.
---

# /spec — Persona Spec Generator

App idea → cohesive wires + persona spec, shipped as one self-contained HTML page on DropFast. Modeled on this repo's teaching artifact. Artifacts = output of a creative process. Run the loop, don't fill a template.

- Content + phrasing gold standard: [EXAMPLE.md](EXAMPLE.md)
- Design doctrine (how to design, mandatory): [PRINCIPLES.md](PRINCIPLES.md)
- Visual rules for the HTML (mandatory): [DESIGN.md](DESIGN.md)

## Loop
Order. Iterate **2 ↔ 3 ↔ 4** till wires + spec consistent + minimal.

**1 — Personas & problem.** Derive complete, distinct persona set (roles, materially diff needs), each a 1-line problem. Never generic "user". Always include the auth role ([PRINCIPLES.md](PRINCIPLES.md)).
- patient portal → `PATIENT`, `PROVIDER` (+`ADMIN`) · football → `COACH`, `PLAYER`, `PARENT` · single-actor → one (`WORKOUT APP USER`)
- Write the elevator pitch + 1 named scenario per major persona.

**2 — Initial spec.** Per persona: `As a <PERSONA>, I need to:` + flat list of high-level behaviors (verbs, no screens). Minimal + complete = creative scaffold + fan-out contract. Include standard auth behaviors (Clerk) by default.

**3 — Wires (SCREENS) from the initial spec.** Per behavior, invent the *fewest* screens that satisfy it — creative but minimalist. Name `SCREEN: <Name>`, reuse across behaviors (one Home Screen), lay each flow as a monochrome wire row. Design **unbreakable systems, not processes** ([PRINCIPLES.md](PRINCIPLES.md)): system-initiated, auto-advance, guardrails, safe defaults.

**4 — Detailed spec from the wires.** Walk every SCREEN, state minimally what it must do: fields, controls, copy, routing, branching, calcs. Every screen in the spec exists in the wires + vice-versa.

## Fan-out (large apps)
Initial spec = parallelism contract. Dispatch 1 subagent per persona (or flow) → draft that slice's wires + detailed spec from the shared initial spec → reconcile (dedupe shared screens, unify naming/routing) → 1 cohesive doc. Shared initial spec ⇒ union stays coherent.

## Deliverable: single-file HTML
One self-contained `.html` (inline CSS, no external fonts/CDNs). Order: title + pitch + scenario(s) → **Wireframes** → **Detailed Persona Spec**. Initial spec = scaffold, not its own section (detailed top level already lists every behavior).
- **Write to `/tmp`, never the repo/working dir** — e.g. `/tmp/<app-slug>-spec/index.html`. It's a throwaway upload source; keep it out of the user's project.
- **Wireframes**: 1 grayscale CSS phone per `SCREEN:` (device border, no shadow; status bar; `X`-cross image boxes; dashed note boxes for logic/calcs). Each flow = its own horizontal scroll-snap row with `→` connectors; flows stack vertically. No color, no emoji.
- **Style**: white bg, system serif headings + sans body + mono code. Obey [DESIGN.md](DESIGN.md): contrast ≥4.5:1, no cards/side-stripes/eyebrows, display letter-spacing ≥ `-0.04em`, line length 65–75ch.
- **Publish**: upload that `/tmp` file to DropFast (public) via the dropfast skill; return URL; `PUT` same slug on edits. Ref: https://dropfast.dev/s/rg9centz/

## Detailed-spec phrasing (match the artifact exactly)
Nested markdown bullets: behavior → `SCREEN:` → that screen's requirements. Each screen's details indent 1 level under its `SCREEN:`. Literal voice:
- `SCREEN: <Name>` introduces a screen
- `Should require <field>` · `Should show <thing>` · `Should have "<label>" button`
- `Clicking "<X>" routes to "<Screen>"` · `Routes to "<Screen>"`
- branch as sibling lines: `If <cond>` / `Routes to "X"` / `else` / `Routes to "Y"`
- spell calcs out (`... with 70% of last successful weight`)

## Checklist
- [ ] Persona set correct + app-specific; auth included (Clerk); pitch + 1 scenario per major persona.
- [ ] Initial spec written + used to derive the wires.
- [ ] Wires minimal + monochrome, horizontal scroll rows, 1:1 w/ detailed spec, unbreakable-system design ([PRINCIPLES.md](PRINCIPLES.md)).
- [ ] Detailed spec artifact-phrased, nested bullets, routing/branch/calc explicit, screen names consistent.
- [ ] One self-contained HTML, published public to DropFast (URL returned), passes [DESIGN.md](DESIGN.md).
