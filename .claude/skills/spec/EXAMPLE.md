# Worked Example — The Occam's Protocol App (TOPA)

This is the reference output the `/spec` skill emulates, distilled from this repo's teaching artifact. Use it as the gold standard for tone, structure, and level of detail.

---

## 1. Overview & Primary User Stories

**Elevator pitch:** The Occam's Protocol App is an iOS and Android application that lets users easily manage their Occam's Protocol workout regimen, based on Tim Ferriss's *The 4-Hour Body*.

**Personas**

- `WORKOUT APP USER` — a busy person who wants to follow Occam's Protocol without building spreadsheets.

> This app has a single actor, so there is one persona. Multi-actor apps must list every distinct role (e.g. a patient portal → `PATIENT` + `PROVIDER`; a football play app → `COACH` + `PLAYER` + `PARENT`) and repeat the doc-2 and doc-3 blocks once per persona.

**Primary User Stories**

> **Scenario: Jeff (WORKOUT APP USER)**
>
> Jeff recently read *The 4-Hour Body* and wants to build muscle via Occam's Protocol, but he's a busy professional and father of 3 with no time to build spreadsheets to track weights and progress. He Googles "occams protocol iphone app," downloads TOPA, and at the gym the app guides him through setup, gathering required info in a few clicks and running all the starting-weight calculations for him. Days later the app notifies him his next workout is tomorrow; he opens it and is told exactly which exercises to do and how much weight to use. He repeats this through the 60-day cycle, gains 20 lbs of muscle, and feels great.

*[add more personas/scenarios here]*

---

## 2. Initial Persona Spec (high-level)

**As a `WORKOUT APP USER`, I need to:**

- Download the app from the App Store
- Download the app from Google Play
- Get Started
- Create an account
- See my next workout
- Sync to my calendar
- Start a workout
- Perform a workout
- Find my starting weight

---

## 3. Detailed Persona Spec (per-screen)

**As a `WORKOUT APP USER`, I need to:**

- **Get Started**
  - `SCREEN: Get Started Screen`
    - A single, friendly button
- **Create an account**
  - `SCREEN: Program Details Screen`
    - Requires: **name**, **email**, **start date**, **weight**
- **See my next workout** → `SCREEN: Home Screen`
- **Sync to my calendar** → `SCREEN: Home Screen`
- **Start a workout**
  - `SCREEN: Home Screen`
    - Tapping **"Work Out"** → routes to `Workout Home Screen`
- **Perform a workout**
  - `SCREEN: Workout Home Screen`
    - Shows the workout title (**A** or **B**)
    - Offers **Machine** & **Freeweight** options
    - **Workout A** exercises: Machine Pull Downs, Machine Shoulder Press, Freeweight Yates Row, Freeweight Overhead Press
    - Tapping an exercise → routes to `Perform Workout Screen`
  - `SCREEN: Perform Workout Screen`
    - Shows the exercise title & current weight to attempt
    - Shows lifting rules & cadence
    - Requires **# of reps**
    - Has a **"Done"** button:
      - If reps **≤ 6** → routes to `Stop Screen`
      - Else → routes to `Perform Workout Screen` (next exercise)
    - Has a **cancel** button → routes to `Home Screen`
  - `SCREEN: Stop Screen` — *purpose: stop the workout and add another rest day*
    - Shows the stop-alert message
    - Has a **"When should I workout again"** button → routes to `Home Screen` with an updated workout date
- **Find my starting weight**
  - `SCREEN: Weight Selection Screen`
    - Shows the title
    - Shows *"Use a weight you can do 5 times"*
    - Requires **lbs completed**
    - Has a **Next** button → routes to `Weight Performance Screen`
  - `SCREEN: Weight Performance Screen`
    - Tells me how to lift (fast up, 2 seconds down)
    - Has an **"I got 5"** button → routes to `Weight Performance Screen` with increasing weight
    - Has an **"I didn't get 5"** button → routes to `Weight Verification Screen` with 70% of last successful weight
  - `SCREEN: Weight Verification Screen`
    - Shows the starting weight
    - **Calculation:** `starting weight = last successful weight × 0.70`, rounded to the nearest double (5 lbs)
    - Has an **"Ok"** button → routes to `Perform Workout Screen` for that exercise

---

### Why this is the bar

- Every behavior in doc 2 reappears in doc 3 with a concrete `SCREEN:`.
- Every actionable screen states where it routes.
- Branching (`reps ≤ 6`) and math (`× 0.70`) are explicit.
- Detail is "sensible" — buildable without dictating pixels.
