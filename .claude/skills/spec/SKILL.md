---
name: spec
description: Generate engineer-ready wireframes + a persona spec for any app idea by running a short creative loop (define personas & problem → initial spec → wireframe SCREENS → detailed per-screen spec), delivered as one self-contained monochrome-wireframe HTML page published to DropFast. Use when the user says /spec, asks to spec out an app, write a persona spec, design app wireframes, or turn an app idea into screen-by-screen requirements.
---

# /spec — Persona Spec Generator

Turn an app idea into a cohesive set of **wireframes + a persona spec**, shipped as one self-contained HTML page published to DropFast. Modeled on this repo's teaching artifact. These artifacts are the *output of a creative process* — run the loop below, don't just fill a template.

- Content & phrasing gold standard: [EXAMPLE.md](EXAMPLE.md)
- Visual rules for the HTML (mandatory): [DESIGN.md](DESIGN.md)

## The loop

Run in order; iterate **2 ↔ 3 ↔ 4** until the wires and the spec are mutually consistent and minimal.

**1 — Define the persona(s) & problem.** Derive the complete, distinct set of personas (roles with materially different needs), each with a one-line problem. Never a generic "user".
- patient portal → `PATIENT`, `PROVIDER` (+`ADMIN`) · football app → `COACH`, `PLAYER`, `PARENT` · single-actor → one (e.g. `WORKOUT APP USER`)
- Write the elevator pitch and one named scenario per major persona.

**2 — Write the initial spec.** Per persona: `As a <PERSONA>, I need to:` + a flat list of high-level behaviors (verbs only, no screens yet). Keep it minimal and complete — this is the creative scaffold and the fan-out contract.

**3 — Design the wires (SCREENS) from the initial spec.** For each behavior, invent the *fewest* screens that satisfy it — creative but minimalist. Name each `SCREEN: <Name>`, reuse screens across behaviors (one Home Screen, etc.), and lay each flow out as a monochrome wireframe row.

**4 — Write the detailed spec from the wires.** Walk every SCREEN and state, minimalistly, what it must do: fields, controls, copy, routing, branching, calculations. Every screen in the spec must exist in the wires, and vice-versa.

## Fan-out (large apps)
The initial spec is the contract for parallelism: dispatch one subagent per persona (or per flow) to draft that slice's wires + detailed spec from the shared initial spec, then reconcile — dedupe shared screens, unify naming and routing — into one cohesive doc. Because every slice traces to the same initial spec, the union stays coherent.

## Deliverable: single-file HTML artifact
One self-contained `.html` (inline CSS, no external fonts/CDNs). Order: title + elevator pitch + scenario(s) → **Wireframes** → **Detailed Persona Spec**. The initial spec stays a working scaffold; it is *not* rendered as its own section, because the detailed spec's top level already lists every behavior.
- **Wireframes**: one grayscale CSS phone per `SCREEN:` (device border, no shadow; status bar; `X`-cross image boxes; dashed note boxes for logic/calcs). Each flow is its **own horizontal scroll-snap row** with `→` connectors; flows stack vertically. No color, no emoji.
- **Style**: white bg, system serif headings + sans body + mono code. Obey [DESIGN.md](DESIGN.md): contrast ≥4.5:1, no cards/side-stripes/eyebrows, display letter-spacing ≥ `-0.04em`, line length 65–75ch.
- **Publish**: drop to DropFast (public) via the dropfast skill; return the URL; `PUT` the same slug in place on later edits. Reference: https://dropfast.dev/s/rg9centz/

## Detailed-spec phrasing (match the artifact exactly)
Nested markdown bullets, three levels (persona → behavior → screen/requirement). Use the artifact's literal voice:
- `SCREEN: <Name>` introduces a screen
- `Should require <field>` · `Should show <thing>` · `Should have "<label>" button`
- `Clicking "<X>" routes to "<Screen>"` · `Routes to "<Screen>"`
- branches as sibling lines: `If <cond>` / `Routes to "X"` / `else` / `Routes to "Y"`
- spell calculations out (e.g. `... with 70% of last successful weight`)

## Checklist
- [ ] Persona set correct & app-specific; pitch + one scenario per major persona.
- [ ] Initial spec written, and actually used to derive the wires.
- [ ] Wires minimal & monochrome, horizontal scroll rows, 1:1 with the detailed spec.
- [ ] Detailed spec phrased like the artifact, nested markdown bullets, routing/branch/calc explicit, screen names consistent.
- [ ] One self-contained HTML, published public to DropFast (URL returned), passes [DESIGN.md](DESIGN.md).
