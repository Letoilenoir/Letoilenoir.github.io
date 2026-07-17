# ReasonTouch Completion Blueprint
## Chapter 6 — The Resolve Path

Version 1.0 (Draft)

---

# 1. Introduction

If the **Continue Path** is responsible for extending a musical thought, the **Resolve Path** is responsible for bringing that thought to a convincing conclusion.

Resolution is one of the defining characteristics of Western harmony.

Listeners instinctively recognise when music has "come home."

A successful Resolve Path therefore does considerably more than place a tonic chord at the end of a progression.

It creates the **expectation**, **preparation**, and **release** that together produce a satisfying cadence.

The Resolve Path is consequently one of the most musically significant planning modules within ReasonTouch.

---

# 2. Musical Purpose

When the user presses **Resolve**, they are usually communicating one of several intentions:

- Finish this phrase.
- End the section.
- Return home.
- Complete the cadence.
- Close the musical idea.
- Prepare for silence.
- Prepare for a new section.

These intentions all share a common objective:

> Increase harmonic stability.

Unlike Continue, which deliberately preserves momentum, Resolve intentionally reduces uncertainty.

---

# 3. The Philosophy of Resolution

Good resolution is rarely sudden.

Instead, music generally follows a process:

```
Instability

↓

Preparation

↓

Dominant Tension

↓

Release

↓

Rest
```

The planner therefore aims to create a controlled decrease in harmonic tension rather than an abrupt stop.

---

# 4. High-Level Workflow

The Resolve Path follows exactly the same architectural pipeline established in Chapter 5.

```
User presses Resolve

↓

Acquire Context

↓

Analyse Progression

↓

ProgressionAnalysis

↓

Pairing Engine

↓

Determine Resolution Type

↓

Resolve Strategy

↓

Generate Candidate Cadences

↓

Evaluate

↓

Rank

↓

Explain

↓

Present
```

Only the planning strategy changes.

Everything else remains identical.

---

# 5. Resolution Types

The Pairing Engine should determine the most appropriate type of resolution.

Examples include:

---

## Perfect Authentic Cadence

```
V → I
```

Maximum stability.

Suitable for:

- ending songs
- ending choruses
- ending movements

---

## Imperfect Authentic Cadence

```
V → I

(with inversion or alternative voicing)
```

Still stable, but less final.

---

## Plagal Cadence

```
IV → I
```

Gentle.

Often associated with reflective endings.

---

## Deceptive Cadence

```
V → vi
```

Appears to resolve before deliberately avoiding closure.

Useful when postponing an ending.

---

## Half Cadence Completion

```
...

↓

V
```

Useful for ending a verse while encouraging continuation.

---

## Modal Resolution

Examples:

```
♭VII → I

iv → I

bVI → I
```

These provide colour while maintaining musical coherence.

---

# 6. Cadence Planning

Once the resolution type has been selected, the planner constructs a cadence plan.

Example:

```
Goal

Perfect Authentic Cadence

↓

Target

I

↓

Required Function

Dominant

↓

Possible Route

ii → V → I
```

Notice that the destination is planned before any chords are generated.

---

# 7. Harmonic Stability

Unlike Continue, the Resolve Path actively seeks to maximise stability.

Typical stability curve:

```
Current Phrase

0.42

↓

Preparation

0.55

↓

Dominant

0.30

↓

Resolution

0.98
```

The momentary increase in instability before the cadence is intentional.

Without tension there is no satisfying release.

---

# 8. Candidate Generation

Multiple cadential solutions should always be produced.

Example:

Candidate 1

```
Dm

↓

G

↓

C
```

Candidate 2

```
F

↓

G7

↓

Cmaj7
```

Candidate 3

```
Am

↓

Dm

↓

G

↓

C
```

Candidate 4

```
Bb

↓

F

↓

C
```

Each reaches the destination differently.

---

# 9. Resolution Evaluation

Candidates should be evaluated against criteria specific to closure.

---

## Cadential Strength

How convincing is the ending?

---

## Harmonic Stability

Does the final chord genuinely feel resolved?

---

## Voice Leading

Are individual voices resolved smoothly?

---

## Phrase Symmetry

Does the cadence balance the opening phrase?

---

## Stylistic Suitability

Would this cadence sound appropriate in the selected style?

---

## Emotional Character

Examples:

Triumphant

Gentle

Reflective

Suspended

Bittersweet

---

# 10. Ranking Results

The planner ranks cadences according to confidence.

Example:

| Rank | Resolution | Confidence |
|------|-----------|-----------:|
| 1 | ii–V–I | 97% |
| 2 | IV–V–I | 93% |
| 3 | IV–I | 89% |
| 4 | V–vi | 84% |

The user therefore receives several musically valid endings rather than one fixed answer.

---

# 11. Explanation Generation

Each cadence should explain its musical purpose.

Examples:

> Completes a perfect authentic cadence.

---

> Resolves dominant tension onto the tonic.

---

> Uses a plagal cadence for a softer ending.

---

> Delays final resolution through deceptive motion.

Educational explanation remains a defining characteristic of ReasonTouch.

---

# 12. Interaction with Progression Pairing

The Resolve Path never independently determines whether the music should end.

Instead, the Pairing Engine supplies that decision.

Example:

```
Relationship

Resolution

↓

Cadence

Perfect Authentic

↓

Strategy

Resolve
```

This separation keeps planning independent from generation.

---

# 13. Relationship to Song Structure

The planner should eventually recognise where the resolution occurs.

Examples include:

End of Verse

↓

Partial resolution

---

End of Chorus

↓

Strong authentic cadence

---

End of Song

↓

Maximum stability

---

Bridge

↓

Delayed resolution

This allows identical harmonic material to serve different structural purposes.

---

# 14. Future Expansion

Later versions may introduce:

- Jazz cadences
- Gospel endings
- Classical cadences
- Modal endings
- Extended dominant chains
- Tritone substitutions
- Chromatic approaches
- Secondary dominants

These become additional planning strategies rather than architectural changes.

---

# 15. Existing Components

The audit identified several systems already capable of supporting this pathway.

Existing components include:

- KeyDetector
- ProgressionAnalysis
- HarmonicFunction
- CadenceType
- ChordSuggestionEngine
- GeneratedProgression

The Resolve Path primarily integrates these components rather than replacing them.

---

# 16. Success Criteria

The Resolve Path is considered complete when it:

✔ Uses ProgressionAnalysis exclusively.

✔ Plans a cadence before generating chords.

✔ Produces multiple resolution candidates.

✔ Measures harmonic stability.

✔ Explains every cadence.

✔ Ranks candidates by confidence.

✔ Shares infrastructure with the Continue Path.

✔ Requires no duplicated analytical logic.

---

# 17. Architectural Importance

The Resolve Path demonstrates that the architecture can support different musical objectives without changing the underlying framework.

Continue and Resolve differ only in planning philosophy.

Everything else remains identical.

This confirms that the architecture is scalable.

---

# 18. Looking Ahead

Once Continue and Resolve are complete, the architecture has validated two opposing musical objectives:

- continuation
- closure

The remaining pathways operate between these two extremes.

Some extend.

Some intensify.

Some surprise.

Some transform.

Together they form the complete compositional reasoning engine envisioned during the audit.

---

## Next Chapter

**Chapter 7 — The Build Tension Path**

The following chapter examines how ReasonTouch deliberately increases harmonic energy, postpones resolution, and creates anticipation through controlled tension planning, dominant preparation, modal borrowing, and intelligent phrase design.

---

_End of Chapter 6_
