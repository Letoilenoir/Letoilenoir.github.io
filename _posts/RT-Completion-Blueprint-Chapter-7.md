# ReasonTouch Completion Blueprint
## Chapter 7 — The Build Tension Path

Version 1.0 (Draft)

---

# 1. Introduction

The **Build Tension Path** represents the opposite musical objective to the Resolve Path.

Where Resolve deliberately reduces uncertainty, Build Tension intentionally increases it.

Its purpose is not to confuse the listener but to heighten expectation, creating the desire for an eventual release.

Musically, tension is what makes resolution meaningful.

Without tension there is no anticipation.

Without anticipation there is no emotional payoff.

For this reason, the Build Tension Path becomes one of the most expressive planning strategies within the ReasonTouch architecture.

---

# 2. Musical Purpose

When a user presses **Build Tension**, they are rarely asking for "more difficult chords."

Instead, they are usually communicating one of the following intentions:

- Make the music more exciting.
- Delay the ending.
- Increase anticipation.
- Lead towards a climax.
- Prepare the chorus.
- Prepare a solo.
- Keep listeners engaged.

The objective is therefore psychological as much as harmonic.

The listener should increasingly feel that the music is "going somewhere."

---

# 3. Philosophy

The planner follows one guiding principle:

> Tension should always feel intentional.

Random dissonance does not create satisfying music.

Good tension:

- has direction
- has purpose
- increases gradually
- eventually earns its resolution

The planner should therefore avoid sudden, arbitrary harmonic shifts unless specifically requested by another strategy (such as Surprise Me).

---

# 4. High-Level Workflow

The architectural pipeline remains unchanged.

```
User presses Build Tension

↓

Acquire Context

↓

Analyse Progression

↓

ProgressionAnalysis

↓

Pairing Engine

↓

Determine Tension Goal

↓

BuildTensionStrategy

↓

Generate Candidates

↓

Evaluate

↓

Rank

↓

Explain

↓

Present
```

Only the strategy layer differs.

---

# 5. Measuring Existing Tension

Before increasing tension, the planner must understand the current harmonic state.

The existing `ProgressionAnalysis` already provides useful indicators:

- harmonic stability
- energy
- ending function
- cadence type
- confidence

Additional derived values may include:

```
Current Stability

0.71

↓

Current Tension

0.36

↓

Desired Target

0.82
```

The strategy therefore knows both the current and desired emotional state.

---

# 6. Sources of Harmonic Tension

The planner should understand multiple musical mechanisms for increasing tension.

These include:

---

## Dominant Preparation

Moving towards V without immediately resolving.

Example:

```
ii

↓

V

↓

...
```

---

## Extended Dominants

```
V7

V9

V13
```

Increasing colour while maintaining functional direction.

---

## Secondary Dominants

Example:

```
V/V

↓

V

↓

I
```

These temporarily tonicise another harmonic destination.

---

## Suspended Chords

```
Gsus4

↓

G

↓

...
```

The suspended note delays harmonic completion.

---

## Borrowed Chords

Examples:

```
iv

♭VI

♭VII
```

Modal borrowing introduces colour while preserving coherence.

---

## Chromatic Approach

Approaching functional chords by chromatic motion.

Example:

```
F

↓

F#

↓

G
```

---

## Sequential Motion

Repeating harmonic patterns while gradually ascending or descending.

Example:

```
Am

↓

Bm

↓

C#m

↓

...
```

Used carefully, this produces momentum.

---

# 7. Planning Rather Than Selecting

One of the key audit discoveries was that chord selection alone is insufficient.

Instead of asking:

> "Which chord comes next?"

the planner asks:

> "How should harmonic tension evolve?"

Example:

```
Current

Moderate

↓

Increase Slightly

↓

Increase Again

↓

Hold

↓

Maximum

↓

Await Resolution
```

Only after this emotional contour is established are actual chords selected.

---

# 8. Candidate Generation

Several independent tension plans should be generated.

Example:

Candidate A

```
ii

↓

V

↓

V7

↓

...
```

Candidate B

```
IV

↓

ii

↓

V

↓

...
```

Candidate C

```
♭VI

↓

V

↓

...
```

Candidate D

```
I

↓

iii

↓

vi

↓

ii

↓

...
```

Each increases expectation differently.

---

# 9. Evaluation Criteria

Candidate phrases should be evaluated against criteria specific to tension.

---

## Energy Growth

Does musical intensity genuinely increase?

---

## Harmonic Direction

Is there a clear destination?

---

## Voice Leading

Does increased tension remain playable?

---

## Functional Logic

Do borrowed or chromatic chords remain convincing?

---

## Emotional Consistency

Does the phrase become increasingly expectant?

---

## Avoiding Premature Resolution

Any candidate resolving too early receives a lower score.

---

# 10. Ranking

Example ranking:

| Rank | Strategy | Confidence |
|------|----------|-----------:|
| 1 | Dominant Expansion | 96% |
| 2 | Modal Borrowing | 92% |
| 3 | Secondary Dominant Chain | 89% |
| 4 | Sequential Rise | 84% |

The highest-ranked candidate represents the most convincing increase in tension.

---

# 11. Explanation Generation

Explanations should describe why the planner increased tension in a particular way.

Examples include:

> Extends dominant preparation before resolution.

---

> Uses modal borrowing to increase emotional colour.

---

> Delays tonic arrival through secondary dominants.

---

> Builds harmonic energy without sacrificing stability.

These explanations reinforce the educational objectives of ReasonTouch.

---

# 12. Interaction with Other Pathways

The Build Tension Path is rarely the final stage of a composition.

Instead, it commonly precedes:

```
Continue

↓

Build Tension

↓

Resolve
```

or

```
Verse

↓

Build Tension

↓

Chorus
```

It therefore functions as a bridge between stable musical regions.

---

# 13. Structural Awareness

Future versions should allow tension planning to recognise song structure.

Examples:

Verse

↓

Moderate tension

---

Pre-Chorus

↓

Rapid increase

---

Chorus

↓

Peak intensity

---

Bridge

↓

Alternative tension profile

This enables the same harmonic vocabulary to serve different structural purposes.

---

# 14. Existing Infrastructure

Much of the required infrastructure already exists.

Examples include:

- ProgressionAnalysis
- HarmonicFunction
- CadenceType
- ChordSuggestionEngine
- GeneratedProgression
- Confidence calculations

The Build Tension Path primarily introduces a new planning philosophy rather than new low-level theory components.

---

# 15. Success Criteria

The pathway is considered complete when it:

✔ Measures existing harmonic tension.

✔ Plans an increasing tension curve.

✔ Generates multiple tension-building phrases.

✔ Avoids accidental resolution.

✔ Produces educational explanations.

✔ Shares infrastructure with Continue and Resolve.

✔ Requires no duplicated analytical logic.

---

# 16. Architectural Importance

The first three planning strategies now demonstrate three distinct musical objectives.

Continue

→ Preserve momentum.

Resolve

→ Increase stability.

Build Tension

→ Increase expectation.

This confirms that the planning architecture is flexible enough to support fundamentally different compositional goals without modification to the surrounding pipeline.

---

# 17. Long-Term Expansion

Future enhancements may include:

- Jazz dominant chains
- Tritone substitutions
- Altered dominant harmony
- Diminished passing chords
- Whole-tone colour
- Octatonic approaches
- Film-score tension models
- Genre-specific tension curves

Each becomes an alternative implementation within the same architectural framework.

---

# 18. Looking Ahead

With Continue, Resolve, and Build Tension complete, the architecture now supports three of the most common compositional intentions.

The next logical step is to introduce controlled unpredictability.

Rather than extending, ending, or intensifying musical ideas, the next pathway deliberately explores unexpected yet musically defensible directions.

---

## Next Chapter

**Chapter 8 — The Surprise Me Path**

The following chapter examines controlled musical unpredictability, intelligent harmonic deviation, stylistic awareness, probability weighting, and the techniques required to produce genuinely surprising—but still musical—progressions.

---

_End of Chapter 7_
