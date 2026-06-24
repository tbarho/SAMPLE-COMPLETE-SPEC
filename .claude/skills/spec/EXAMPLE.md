# Worked Example — The Occam's Protocol App (TOPA)

The gold standard for the loop's text outputs, distilled from this repo's teaching artifact. The **final HTML renders the pitch + scenario, the wireframes, and the detailed spec** (step 3 below). The initial spec (step 2) stays a working scaffold — it is not rendered as its own section.

---

## 1 — Persona & problem

**Personas**

- `WORKOUT APP USER` — a busy person who wants to follow Occam's Protocol without building spreadsheets to calculate weights and track progress.

**Elevator pitch.** The Occam's Protocol App (TOPA) is an iOS and Android application that lets users manage their Occam's Protocol workout regimen, based on Tim Ferriss's *The 4-Hour Body*.

> **Scenario: Jeff (WORKOUT APP USER)**
>
> Jeff recently read *The 4-Hour Body* and wants to build muscle via Occam's Protocol, but he's a busy professional and father of 3 with no time to build spreadsheets. He Googles "occams protocol iphone app," downloads TOPA, and at the gym the app guides him through setup, gathering required info in a few clicks and running all the starting-weight calculations for him. Days later the app notifies him his next workout is tomorrow; he opens it and is told exactly which exercises to do and how much weight to use. He repeats this through the 60-day cycle, gains 20 lbs of muscle, and feels great.

*[add more personas/scenarios here]*

---

## 2 — Initial spec (working scaffold)

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

These behaviors drive the wireframes (step 3) and are the contract for fanning out work. They are not rendered separately in the final doc.

---

## 3 — Detailed persona spec (from the wires)

Phrased identically to the source PDF; only the bullet glyphs differ. Each screen's details nest one level under their `SCREEN:` parent: persona → behavior → `SCREEN:` → that screen's requirements.

**As a `WORKOUT APP USER`, I need to:**

- Download the app from the App Store
- Download the app from Google Play
- Get Started
  - SCREEN: Get Started Screen
    - Single, friendly button
- Create an account
  - SCREEN: Program Details Screen
    - Should require name
    - Should require email
    - Should require start date
    - Should require weight
- See my next workout
  - SCREEN: Home Screen
- Sync to my calendar
  - SCREEN: Home Screen
- Start a workout
  - SCREEN: Home Screen
    - Clicking "Work Out" routes to "Workout Home Screen"
- Perform a workout
  - SCREEN: Workout Home Screen
    - Should show workout title (A or B)
    - Should allow Machine & Freeweight Options
    - Workout A
    - Machine - Pull downs
    - Machine - Shoulder press
    - Freeweight - Yates Row
    - Freeweight - Overhead press
    - Clicking an exercise routes to "Perform Workout Screen"
  - SCREEN: Perform workout
    - Should show exercise title & current weight to attempt
    - Should show lifting rules & cadence
    - Should require # of reps
    - Should show "Done" button
    - If I get 6 or less
    - Routes to "Stop Screen"
    - else
    - Routes to "Perform Workout Screen"
    - Should show cancel button
    - Routes to "Home Screen"
  - SCREEN: Stop screen "The purpose of this screen is stopping the workout and adding another day of rest"
    - Should show the stop alert message
    - Should have "When should I workout again" button
    - Routes to "Home Screen" with updated workout date
- Find my starting weight
  - SCREEN: Weight Selection Screen
    - Should show title
    - Should show "Use a weight you can do 5 times"
    - Should require lbs completed
    - Should show Next button
    - Routes to "Weight Performance Screen"
  - SCREEN: Weight Performance Screen
    - Should tell me how to lift (fast up, 2 seconds down)
    - Should have "I got 5" button
    - Routes to "Weight Performance Screen" with increasing weight
    - Should have "I didn't get 5" button
    - Should route to "Weight Verification Screen" with 70% of last successful weight
  - SCREEN: Weight Verification Screen
    - Should show starting weight
    - Should have "Ok" button
    - Routes to "Perform Workout Screen" for that exercise
