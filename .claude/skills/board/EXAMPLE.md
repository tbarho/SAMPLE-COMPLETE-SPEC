# Worked Example — TOPA Build Board

Reduction of the [Occam's Protocol App spec](https://dropfast.dev/s/rg9centz/) via *Mock → DONE Fast*. Points = 3 placeholder (adjust via poker).

## Step 1 — Reduction (order: SCREENS → COMPONENTS → INFRASTRUCTURE → API)

**SCREENS** (1 per `SCREEN:` in the spec)
- Sign In · Sign Up · Get Started · Program Details · Home · Workout Home · Perform Workout · Stop · Weight Selection · Weight Performance · Weight Verification

**COMPONENTS** (reused across ≥2 screens, deduped)
- Button · TextInput · DateInput · NumberInput · Tabs (Machine/Freeweight) · ExerciseTile · Link · NoteCard (cadence/how-to) · BigStat · StatusBar/PhoneChrome

**INFRASTRUCTURE** (arch decisions; unbreakable-systems items in bold)
- Repo · CI · Conventional Commits · Framework (Expo/React Native) · Navigation · Theming · State mgmt · Local storage/DB · **Clerk Auth** · RBAC/permissions · **Push notifications (next-workout reminder)** · **Calendar sync** · **Workout calc engine (starting weight + next date)**

**API**
- persist program · log workout + reps · compute next workout date · store/compute starting weight

## Step 2 — Inversion (build order)
`API → INFRASTRUCTURE → COMPONENTS → SCREENS`

## Step 3 — Velocity
- Fib `0,1,2,3,5,8,13,25`. Placeholder 3 each.
- Totals: SCREENS 33 · COMPONENTS 30 · INFRASTRUCTURE 39 · API 12 → **grand total 114 pts**. Weeks = 114 ÷ weekly velocity (set after week 1).

## Step 4 — Adjustments
- Lock spec/mocks; creep = next cycle. Re-audit changes in `SCREENS → COMPONENTS → INFRASTRUCTURE → API` order. ≤15min/day board. Storybook for components.
