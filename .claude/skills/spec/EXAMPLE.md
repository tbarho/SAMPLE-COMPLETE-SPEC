# Worked Example — The Occam's Protocol App (TOPA)

This is the reference output the `/spec` skill emulates, distilled from this repo's teaching artifact. Use it as the gold standard for tone, nesting, and level of detail.

---

## 1. Overview & Primary User Stories

**Elevator pitch**: The Occam's Protocol App is an iOS and Android application that lets users easily manage their Occam's Protocol workout regimen, based on Tim Ferriss's *The 4-Hour Body*.

**Primary User Stories**

Scenario: Jeff
Jeff recently read *The 4-Hour Body* and wants to build muscle via Occam's Protocol, but he's a busy professional and father of 3 with no time to build spreadsheets to track weights and progress. He Googles "occams protocol iphone app," downloads TOPA, and at the gym the app guides him through setup, gathering required info in a few clicks and running all the starting-weight calculations for him. Days later the app notifies him his next workout is tomorrow; he opens it and is told exactly which exercises to do and how much weight to use. He repeats this through the 60-day cycle, gains 20 lbs of muscle, and feels great.

`[add more personas/scenarios here]`

---

## 2. Initial Persona Spec (high-level)

● As a WORKOUT APP USER, I need to:
○ Download the app from the App Store
○ Download the app from Google Play
○ Get Started
○ Create an account
○ See my next workout
○ Sync to my calendar
○ Start a workout
○ Perform a workout
○ Find my starting weight

---

## 3. Detailed Persona Spec (per-screen)

● As a WORKOUT APP USER, I need to:
○ Get Started
■ SCREEN: Get Started Screen
■ Single, friendly button
○ Create an account
■ SCREEN: Program Details Screen
■ Should require name
■ Should require email
■ Should require start date
■ Should require weight
○ See my next workout
■ SCREEN: Home Screen
○ Sync to my calendar
■ SCREEN: Home Screen
○ Start a workout
■ SCREEN: Home Screen
■ Clicking "Work Out" routes to "Workout Home Screen"
○ Perform a workout
■ SCREEN: Workout Home Screen
■ Should show workout title (A or B)
■ Should allow Machine & Freeweight options
■ Workout A: Machine Pull Downs, Machine Shoulder Press, Freeweight Yates Row, Freeweight Overhead Press
■ Clicking an exercise routes to "Perform Workout Screen"
■ SCREEN: Perform Workout Screen
■ Should show exercise title & current weight to attempt
■ Should show lifting rules & cadence
■ Should require # of reps
■ Should show "Done" button
■ If reps ≤ 6 → Routes to "Stop Screen"
■ else → Routes to "Perform Workout Screen" (next exercise)
■ Should show cancel button → Routes to "Home Screen"
■ SCREEN: Stop Screen — purpose: stop the workout and add another rest day
■ Should show the stop alert message
■ Should have "When should I workout again" button → Routes to "Home Screen" with updated workout date
○ Find my starting weight
■ SCREEN: Weight Selection Screen
■ Should show title
■ Should show "Use a weight you can do 5 times"
■ Should require lbs completed
■ Should show Next button → Routes to "Weight Performance Screen"
■ SCREEN: Weight Performance Screen
■ Should tell me how to lift (fast up, 2 seconds down)
■ Should have "I got 5" button → Routes to "Weight Performance Screen" with increasing weight
■ Should have "I didn't get 5" button → Routes to "Weight Verification Screen" with 70% of last successful weight
■ SCREEN: Weight Verification Screen
■ Should show starting weight
■ Calculation: starting weight = last successful weight × 0.70, rounded to nearest double (5 lbs)
■ Should have "Ok" button → Routes to "Perform Workout Screen" for that exercise

---

### Why this is the bar
- Every behavior in doc 2 reappears in doc 3 with a concrete `SCREEN:`.
- Every actionable screen states its route.
- Branching (`reps ≤ 6`) and math (`× 0.70`) are explicit.
- Detail is "sensible" — buildable without dictating pixels.
