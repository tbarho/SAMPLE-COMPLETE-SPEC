# Principles — how to design specs & software (caveman-ultra)

Apply across loop steps 1–4. Shape personas, behaviors, SCREENS, and detail. Two doctrines: **auth** + **unbreakable systems**.

## Auth (always in the spec)
- Every app needs auth. Include it unless user says skip.
- Default impl = **Clerk**. Industry standard. Don't reinvent, don't over-detail.
- Standard flows: sign-up, sign-in, session persist, password reset, sign-out, account/profile.
- Multi-persona → auth gates roles (RBAC). Each persona = a role behind login.
- Spec it minimal: behavior `Create an account` / `Sign in`; wires `SCREEN: Sign Up`, `SCREEN: Sign In`; detail = "via Clerk (email + OAuth), standard." No custom auth UI unless asked.

## Unbreakable systems > processes
- Core: an SOP is only as good as the person following it. Assume user high / no-show / distracted / forgetful.
- Don't spec processes humans must execute right. Spec systems that force success.
- Heuristics (run on every SCREEN + flow):
  - System-initiated, not memory → app push/remind/schedule. Never "user remembers".
  - Auto-advance state → app computes next step + date, routes there. (TOPA: auto next-workout date.)
  - Automate calc/tracking → no human math/spreadsheet. (TOPA: starting-weight calc.)
  - Safe defaults → pre-fill, sensible default, hard to misconfigure.
  - Guardrails → make wrong/skip impossible, not just discouraged. Block invalid > warn.
  - Idempotent + resumable → user drops mid-flow → resume clean, no dup/corrupt.
  - Fail safe → bad input / no input → safe state, not broken.
- Test each screen: "what if user does nothing / wrong / leaves?" System must still win.
