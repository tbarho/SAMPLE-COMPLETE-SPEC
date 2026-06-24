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
- The set of personas (see below) — only if it's genuinely ambiguous who uses the app
- The one core job the app must nail

If the user says "just generate it" or gives enough, make sensible assumptions and note them in an `Assumptions` line rather than blocking.

## Step 0: Identify the personas (do this first)

Before writing anything, derive the **complete, distinct set of personas (actors/roles)** the app actually requires — not a single generic "user". A persona is a role with materially different needs, permissions, or flows. Think through who creates, consumes, approves, administers, or is acted upon in the app.

Examples of correct persona sets:
- **Patient portal** → `PATIENT`, `PROVIDER` (and often `ADMIN`/`SCHEDULER`)
- **Football play app** → `COACH`, `PLAYER`, `PARENT`
- **Marketplace** → `BUYER`, `SELLER`, `ADMIN`
- **Food delivery** → `CUSTOMER`, `DRIVER`, `RESTAURANT`
- **Single-actor app** (e.g. a personal workout tracker) → just `WORKOUT APP USER`

Rules:
- Name each persona by its role (UPPERCASE), not "user". Only collapse to one persona if the app truly has one actor.
- Keep personas distinct and roughly non-overlapping; if two "roles" share all behaviors, merge them.
- Docs 1–3 below must cover **every** persona in this set.

## Output: 3 layered documents

Always produce all three, in order, in a single response (or as files if asked). Use **clean, properly-nested Markdown** — nested bullet lists with 2-space indents, bold labels for personas/behaviors, and `inline code` for screen names. Mirror [EXAMPLE.md](EXAMPLE.md) exactly. Do not use raw `●`/`○`/`■` glyphs (they don't render as nested lists).

### 1. Overview & Primary User Stories
- **Elevator pitch**: 1–2 sentences. What it is, who it's for, the platform.
- **Personas**: a short bullet list naming each persona and its one-line motivation.
- **Primary User Stories**: one named scenario per major persona, as short narratives in a blockquote (`> **Scenario: <Name> (<PERSONA>)**`). Show the persona's pain → how they find/use the app → the happy-path payoff. End with `*[add more personas/scenarios here]*`.

### 2. Initial Persona Spec (high-level)
Repeat this block **for each persona** in the set:
- Bold persona header: `**As a \`<PERSONA>\`, I need to:**`
- A flat bullet list of that persona's high-level behaviors/jobs (onboard, see X, perform Y...). No screen detail yet — verbs only.

### 3. Detailed Persona Spec (per-screen)
Repeat **for each persona**, expanding every behavior from that persona's doc-2 block as a nested list. For each:
- A behavior bullet, then a nested `` `SCREEN: <Screen Name>` `` bullet (or `behavior → \`SCREEN: ...\`` when one-to-one).
- Sub-bullets for required fields, controls, copy, and rules of that screen.
- **Routing**: state transitions explicitly — `→ routes to \`<Screen>\``.
- **Branching**: nest conditional flows — `If <condition> → routes to \`X\`` / `Else → routes to \`Y\``.
- **Calculations**: spell out any formula in inline code (e.g. `` `start weight = last success × 0.70` ``, round to nearest 5).

## Quality bar (mirror the artifact)
- **Correct personas**: the persona set matches what the app genuinely requires (e.g. patient portal → patient + provider), each named by role, distinct, and all covered in docs 1–3.
- Persona-driven throughout — every behavior traces to a specific "As a <PERSONA>, I need to".
- Every behavior maps to at least one `SCREEN:`.
- Every screen with an action states where it routes.
- Conditional logic and math are explicit, never implied.
- "Sensible detail": enough to build, not over-specified. Prefer the app's real edge cases over filler.
- Name screens consistently — the same screen referenced in routing must match its `SCREEN:` heading exactly.

## Checklist before returning
- [ ] Persona set is correct & app-specific; every persona appears in docs 1, 2, and 3.
- [ ] All 3 docs present, in order, as clean nested Markdown (renders correctly).
- [ ] Each high-level behavior expanded into ≥1 screen.
- [ ] All routes/branches/calcs explicit and screen names consistent.
- [ ] Assumptions noted if any were made.
- [ ] (Optional) Offer to add a wireframe description or screen list next.
