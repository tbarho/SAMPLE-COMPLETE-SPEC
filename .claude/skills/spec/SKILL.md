---
name: spec
description: Generate a complete, engineer-ready persona spec for any app idea, modeled on the layered waterfall-alternative spec in this repo (elevator pitch → high-level user stories → detailed per-screen behaviors). Use when the user says /spec, asks to spec out an app, write a persona spec, turn an app idea into requirements, or produce screen-by-screen behavior docs.
---

# /spec — Persona Spec Generator

Turn a one-line app idea into the same layered, persona-driven spec format demonstrated in this repo's teaching artifact. The output is detailed enough that nearly any engineer can implement it, without being a rigid waterfall doc.

See [EXAMPLE.md](EXAMPLE.md) for a full worked reference (The Occam's Protocol App).

## Inputs

Take the app idea as given. Only ask clarifying questions if a core dimension is missing — cap at 3:
- Platform(s) (iOS, Android, web, ...)
- Primary persona (who, and their motivating pain)
- The one core job the app must nail

If the user says "just generate it" or gives enough, make sensible assumptions and note them in an `Assumptions` line rather than blocking.

## Output: 3 layered documents

Always produce all three, in order, in a single response (or as files if asked). Use the exact nesting markers `●` / `○` / `■`.

### 1. Overview & Primary User Stories
- **Elevator pitch**: 1–2 sentences. What it is, who it's for, the platform.
- **Primary User Stories**: 1–2 named persona scenarios written as short narratives ("Scenario: <Name>"). Show the persona's pain → how they find the app → the happy-path payoff. End with `[add more personas/scenarios here]`.

### 2. Initial Persona Spec (high-level)
- One line per persona: `● As a <PERSONA>, I need to:`
- Nested `○` bullets: the high-level behaviors/jobs (download, onboard, see X, perform Y...). No screen detail yet — verbs only.

### 3. Detailed Persona Spec (per-screen)
Expand every `○` behavior from doc 2. For each:
- `■ SCREEN: <Screen Name>`
- `■` required fields, controls, copy, and rules of that screen
- **Routing**: state transitions explicitly — `Routes to "<Screen>"`.
- **Branching**: conditional flows as `If <condition> → Routes to "X"` / `else → Routes to "Y"`.
- **Calculations**: spell out any formula in plain math (e.g. `start weight = last success × 0.70, round to nearest 5`).

## Quality bar (mirror the artifact)
- Persona-driven throughout — every behavior traces to "As a <PERSONA>, I need to".
- Every behavior maps to at least one `SCREEN:`.
- Every screen with an action states where it routes.
- Conditional logic and math are explicit, never implied.
- "Sensible detail": enough to build, not over-specified. Prefer the app's real edge cases over filler.
- Name screens consistently — the same screen referenced in routing must match its `SCREEN:` heading exactly.

## Checklist before returning
- [ ] All 3 docs present, in order, correct nesting markers.
- [ ] Each high-level behavior expanded into ≥1 screen.
- [ ] All routes/branches/calcs explicit and screen names consistent.
- [ ] Assumptions noted if any were made.
- [ ] (Optional) Offer to add a wireframe description or screen list next.
