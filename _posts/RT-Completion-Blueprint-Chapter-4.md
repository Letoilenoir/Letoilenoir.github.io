# ReasonTouch Completion Blueprint
## Chapter 4 — The Progression Pairing Engine

Version 1.0 (Draft)

---

# 1. Introduction

The architectural audit identified the **Progression Pairing Engine** as the first major subsystem to be completed following the establishment of the planning architecture.

Although users often think in terms of *individual chord progressions*, composers rarely do.

Instead, they think in **phrases**.

A verse does not exist in isolation.

A chorus follows it.

A bridge prepares the final chorus.

An intro establishes the harmonic language.

An outro provides closure.

The Progression Pairing Engine is responsible for understanding these larger relationships.

It elevates ReasonTouch from generating *the next progression* to constructing *the next musical idea*.

---

# 2. Why Progression Pairing Exists

Current continuation logic assumes that a progression simply continues forward.

For example:

```
C   Am   F   G

↓

Generate another four bars.
```

While this can produce musically valid material, it ignores a fundamental characteristic of composition:

Music is organised into **relationships between phrases**, not merely sequences of chords.

Instead, a composer thinks:

```
Verse

↓

Pre-Chorus

↓

Chorus

↓

Verse

↓

Bridge

↓

Final Chorus
```

Each section has a distinct musical purpose.

The Progression Pairing Engine models these relationships explicitly.

---

# 3. The Concept of a Pair

Within ReasonTouch, a **pair** is defined as two musical phrases that possess a recognised relationship.

Examples include:

```
Question

↓

Answer
```

```
Open

↓

Closed
```

```
Tension

↓

Release
```

```
Statement

↓

Restatement
```

```
Verse

↓

Chorus
```

The engine therefore reasons about complete musical ideas rather than isolated chord sequences.

---

# 4. Musical Relationships

The audit identified several primary relationship types that Version 1 should support.

---

## 4.1 Continuation

The second phrase naturally develops the first.

Example:

```
Phrase A

I  vi  IV  V

↓

Phrase B

vi  ii  V  I
```

No dramatic contrast occurs.

The musical narrative simply continues.

---

## 4.2 Resolution

The second phrase provides closure.

Example:

```
Phrase A

ii  V

↓

Phrase B

I
```

The listener experiences completion.

---

## 4.3 Contrast

The paired phrase deliberately changes mood.

Possible changes include:

- major → minor

- low energy → high energy

- tonic focus → dominant focus

- sparse → dense harmony

Contrast should remain coherent rather than random.

---

## 4.4 Extension

Instead of resolving, the music expands.

For example:

```
Phrase A

↓

Phrase B

↓

Phrase C
```

This relationship becomes particularly important for longer song sections.

---

## 4.5 Preparation

The second phrase prepares something still to come.

Examples include:

Preparing a chorus.

Preparing a bridge.

Preparing a key change.

Preparing an ending.

The paired phrase therefore acts as a transitional structure.

---

# 5. Inputs

The engine receives information from the completed analysis layer.

Typical inputs include:

```
ProgressionAnalysis

Current progression

Detected key

Cadence type

Phrase length

Mood

Energy

Tension

User intent
```

Importantly, the engine does **not** perform its own harmonic analysis.

It consumes the shared analysis already produced elsewhere.

---

# 6. Outputs

Rather than returning chords directly, the engine returns one or more pairing plans.

For example:

```
Pair Type:

Resolution

Destination:

Perfect Authentic Cadence

Preferred Length:

4 bars

Energy:

Decrease

Confidence:

0.91
```

Only later planning layers convert this into actual chords.

---

# 7. Pairing Strategies

Each relationship type should eventually become its own planning strategy.

For Version 1 these include:

```
ContinuePairingStrategy
```

```
ResolvePairingStrategy
```

```
ContrastPairingStrategy
```

```
ExtensionPairingStrategy
```

```
PreparationPairingStrategy
```

This mirrors the architectural philosophy established in previous chapters.

Each planner performs one responsibility exceptionally well.

---

# 8. Pair Quality Evaluation

Not every pairing is equally convincing.

The engine therefore evaluates candidate relationships.

Suggested evaluation criteria include:

## Harmonic Compatibility

Does the second phrase naturally follow the first?

---

## Functional Continuity

Do harmonic functions progress logically?

---

## Cadential Strength

Does the pairing create the intended sense of arrival?

---

## Emotional Flow

Does energy change appropriately?

Examples:

```
Verse

↓

Higher energy chorus
```

or

```
Bridge

↓

Quiet breakdown
```

---

## Structural Suitability

Does the pairing make sense within the current song structure?

---

# 9. Relationship Metadata

Every generated pair should carry descriptive metadata.

Example:

```
Relationship

Continuation

Destination

Open Phrase

Energy

+0.20

Expected Cadence

Half Cadence

Confidence

0.87
```

This metadata later supports:

- explanation generation

- educational feedback

- filtering

- ranking

- adaptive planning

---

# 10. Interaction with Continue

One important discovery during the audit was that the Continue pathway should not generate chords immediately.

Instead, it should first consult the Pairing Engine.

The flow becomes:

```
Continue Selected

↓

Analyse progression

↓

Determine relationship

↓

Create pairing plan

↓

Generate paired phrase

↓

Evaluate

↓

Display
```

Notice that "Continue" becomes only one consumer of the pairing engine.

---

# 11. Future Consumers

Although initially created for Continue, the Pairing Engine is intended to become reusable.

Future consumers include:

Resolve

Build Tension

Surprise Me

Song Builder

AI Composer

Automatic Arrangement

Style Templates

This reinforces the architectural goal of avoiding duplicated planning logic.

---

# 12. Educational Value

The Pairing Engine provides educational opportunities unavailable in conventional DAWs.

The application can explain relationships such as:

> "This phrase answers the previous phrase."

> "This continuation delays the final cadence."

> "This progression intentionally avoids tonic resolution."

> "This bridge increases dominant tension before the chorus."

Such explanations reinforce musical understanding rather than simply presenting results.

---

# 13. Implementation Roadmap

The audit recommends implementing the engine incrementally.

---

## Phase 1

Support only:

- Continue

- Resolve

These provide immediate value while establishing the architecture.

---

## Phase 2

Introduce:

- Contrast

- Extension

- Preparation

---

## Phase 3

Allow user-adjustable pairing preferences.

Examples:

- conservative

- adventurous

- jazz

- pop

- cinematic

---

## Phase 4

Support automatic song-form planning.

Example:

```
Verse

↓

Verse

↓

Pre-Chorus

↓

Chorus

↓

Verse

↓

Bridge

↓

Final Chorus
```

At this stage the Pairing Engine becomes one of the principal architectural components of ReasonTouch.

---

# 14. Architectural Benefits

Completing the Pairing Engine provides several immediate advantages.

✔ Eliminates duplicated continuation logic.

✔ Separates planning from generation.

✔ Allows multiple reasoning paths to reuse the same infrastructure.

✔ Supports future song-level planning.

✔ Enables meaningful musical explanations.

✔ Provides a scalable foundation for intelligent composition.

Perhaps most importantly, it changes the application's perspective.

Instead of asking:

> "What chords should come next?"

ReasonTouch begins asking:

> "What musical relationship should exist next?"

That single shift transforms chord generation into phrase composition.

---

# 15. Relationship to Subsequent Chapters

The Progression Pairing Engine defines *where* the music should go.

The following chapters define *how* each destination is achieved.

The Continue Path, Resolve Path, Build Tension Path, and Surprise Path all become specialised clients of the Pairing Engine.

This ensures that every future planning subsystem shares a common understanding of phrase relationships.

---

## Next Chapter

**Chapter 5 — The Continue Path**

The next chapter describes the first complete reasoning pipeline to be implemented using the architecture defined thus far.

Rather than generating another chord, the Continue Path will analyse the current musical context, determine the desired phrase relationship through the Pairing Engine, and produce a coherent continuation complete with confidence scoring and musical explanation.

---

_End of Chapter 4_
