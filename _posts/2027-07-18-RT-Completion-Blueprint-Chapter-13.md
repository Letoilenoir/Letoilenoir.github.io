# Chapter 13 — Completion Blueprint: The Intelligent Suggestion Ecosystem

> **ReasonTouch Development Blueprint**
>
> Part of the Completion Architecture Series

---

# 13.1 Purpose

With the CONTINUE pathway complete, the remaining suggestion pathways become comparatively straightforward.

This chapter explains how every future pathway becomes a different interpretation of the same underlying harmonic intelligence rather than a separate algorithm.

The objective is therefore **not** to create five independent generators.

Instead we create:

- one analysis engine
- one progression planner
- multiple planning personalities

This dramatically reduces code duplication while greatly increasing musical consistency.

---

# 13.2 The Core Principle

Every suggestion ultimately answers the same question:

> "Given where the music is now, where could it go next?"

Different buttons simply answer this question from different musical perspectives.

Instead of:

```
Continue Engine
Resolve Engine
Tension Engine
Surprise Engine
Modulation Engine
```

ReasonTouch becomes:

```
               Harmonic Analysis
                       │
                       ▼
            Progression Planner
                       │
          ┌────────────┼────────────┐
          │            │            │
          ▼            ▼            ▼
     Continue      Resolve      Surprise
          │            │            │
          └────────────┼────────────┘
                       ▼
                Generated Progression
```

The planning engine stays identical.

Only the planning constraints change.

---

# 13.3 Planning Profiles

The planner should eventually operate from named profiles.

Example:

```kotlin
enum class PlanningIntent {

    CONTINUE,

    RESOLVE,

    BUILD,

    SURPRISE,

    MODULATE,

    DEVELOP,

    CONTRAST

}
```

Each intent simply changes scoring.

Nothing else.

---

# 13.4 Shared Planning Pipeline

Every pathway follows exactly the same stages.

```
Current Progression

↓

Analyse Progression

↓

Determine Key

↓

Determine Harmonic Function

↓

Determine Cadence

↓

Determine Stability

↓

Determine Phrase Position

↓

Select Planning Intent

↓

Generate Candidate Progressions

↓

Score Candidates

↓

Present Best Four
```

Only one stage changes:

```
Planning Intent
```

Everything else is reused.

---

# 13.5 Continue

Continue has already become the reference implementation.

Its priorities are

- maintain momentum

- preserve key

- preserve emotional arc

- avoid unnecessary surprise

Typical weighting:

```
Resolution      Medium

Novelty         Low

Voice Leading   High

Cadence         Medium

Flow            Very High
```

Continue therefore represents the "safe" planner.

---

# 13.6 Resolve

Resolve uses the identical planner.

Different scoring.

Instead of asking

> What comes naturally?

it asks

> What most convincingly reaches home?

Priorities become

```
Authentic cadence

Dominant preparation

Voice leading

Tonic arrival

Phrase closure
```

Likely outputs:

```
ii V I

IV V I

vi ii V I

I64 V I

V7 I
```

Notice:

The planner does not need to know "Resolve."

It only needs to know that tonic arrival scores highest.

---

# 13.7 Build Tension

Build Tension deliberately avoids closure.

Its objective becomes

```
Increase instability

Delay tonic

Increase expectation

Encourage continuation
```

Possible mechanisms

- Secondary dominants

- ii–V chains

- Circle-of-fifths motion

- Suspensions

- Dominant prolongation

- Pedal points

Scoring changes.

Nothing else changes.

---

# 13.8 Surprise

Surprise increases novelty.

Possible scoring additions:

```
Unexpected mediants

Modal borrowing

Chromatic chords

Common-tone modulation

Neapolitan

Augmented sixth

Borrowed iv

Flat VII

Tritone substitution
```

These already exist inside the harmonic vocabulary.

The planner simply allows them higher scores.

---

# 13.9 Develop

Development is neither continuation nor surprise.

Instead it asks:

> "How can I evolve the existing idea?"

Possible transformations

- inversion

- rhythmic displacement

- harmonic expansion

- sequence

- fragmentation

- extension

Instead of replacing ideas,

it grows them.

---

# 13.10 Contrast

Contrast deliberately changes one musical dimension.

Possible dimensions

```
Energy

Density

Cadence

Mode

Register

Rhythmic activity

Bass movement
```

Example:

Current progression

```
I
vi
IV
V
```

Contrast might become

```
i
VI
III
VII
```

Same architecture.

Different emotional colour.

---

# 13.11 Modulate

Modulation is simply another planning objective.

Planner asks

```
Target key?
```

Then constructs

```
Pivot chord

↓

Secondary dominant

↓

Arrival cadence
```

The planner remains identical.

Only destination changes.

---

# 13.12 Emotional Planning

Eventually every planner should incorporate emotional targets.

Instead of

```
Continue
```

the planner could receive

```
Continue

Energy +20%

Brightness +10%

Resolution −15%

Confidence +30%
```

The planner then searches for harmonic movement matching these emotional vectors.

This is considerably more powerful than simple chord prediction.

---

# 13.13 Scoring Architecture

Every candidate progression receives weighted scores.

Example:

```
Resolution

Voice Leading

Novelty

Cadence

Emotional Match

Energy Match

Phrase Balance

Stylistic Match

Functional Correctness

Predictability
```

Each planning intent adjusts these weights.

Example:

Continue

```
Flow 40%

Voice Leading 30%

Novelty 10%

Cadence 20%
```

Surprise

```
Novelty 45%

Voice Leading 20%

Resolution 10%

Emotion 25%
```

Same engine.

Different weights.

---

# 13.14 Strategy Objects

Each intent becomes a small strategy.

```kotlin
interface PlanningStrategy {

    fun score(
        candidate: PlannedProgression,
        analysis: ProgressionAnalysis
    ): Float

}
```

Implementations:

```
ContinueStrategy

ResolveStrategy

BuildStrategy

SurpriseStrategy

DevelopStrategy

ContrastStrategy

ModulationStrategy
```

Tiny.

Independent.

Highly testable.

---

# 13.15 UI Integration

Eventually the workspace simply exposes planning intents.

```
CONTINUE

RESOLVE

BUILD

SURPRISE

DEVELOP

MODULATE

CONTRAST
```

Each button calls

```
ProgressionPlanner.generate()

↓

PlanningIntent
```

Nothing else changes.

---

# 13.16 Future Expansion

This architecture naturally supports:

Jazz

Film

Pop

Rock

Blues

Classical

Celtic

Gospel

Neo Soul

because style simply becomes another scoring modifier.

```
Planning Intent

+

Style Profile

+

Emotional Target

↓

Planner
```

No rewrite required.

---

# 13.17 Why This Matters

Many music applications accumulate separate generators for every feature.

ReasonTouch deliberately avoids that trap.

By treating every pathway as a different interpretation of the same harmonic planner, the system gains:

- dramatically less duplicated code

- consistent musical behaviour

- easier testing

- easier extension

- richer future possibilities

The planning engine becomes the musical heart of the application.

Every new feature strengthens the same engine rather than replacing it.

---

# Chapter Summary

This chapter defines the long-term architecture for every future suggestion pathway.

Rather than building isolated generators, ReasonTouch should evolve a single reusable planning engine driven by interchangeable planning intents and scoring strategies.

The completed CONTINUE pathway serves as the reference implementation. RESOLVE, BUILD TENSION, SURPRISE, DEVELOP, CONTRAST, and MODULATE become progressively richer views of the same underlying harmonic intelligence.

This design provides a scalable foundation capable of supporting future styles, emotional targets, adaptive learning, and increasingly sophisticated compositional assistance without architectural redesign.
