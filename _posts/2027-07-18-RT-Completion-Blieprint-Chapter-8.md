# ReasonTouch Completion Blueprint
## Chapter 8 — The Surprise Me Path

**Version:** 1.0 (Blueprint Draft)

---

# 1. Purpose of the Surprise Me Path

The **Surprise Me** pathway is responsible for introducing controlled musical unpredictability into the composition process.

Unlike the previous planning strategies, its objective is **not** to continue an existing musical idea, resolve it, or increase its tension. Instead, it intentionally explores unexpected yet musically defensible alternatives.

The challenge is therefore one of balance.

A progression that is too predictable fails to surprise.

A progression that is completely random ceases to sound musical.

The planner must therefore generate ideas that listeners would not necessarily expect, but which still sound convincing once heard.

The guiding philosophy is:

> **Unexpected, not incorrect.**

---

# 2. Musical Objectives

When a user selects **Surprise Me**, they are effectively asking:

- "Show me something I wouldn't have thought of."
- "Take this progression somewhere unusual."
- "Break the pattern."
- "Give me a fresh harmonic colour."
- "Challenge my expectations."

The system should therefore favour creativity over familiarity while remaining stylistically appropriate.

---

# 3. Position within the Architecture

The Surprise Me pathway uses the same planning architecture as every other generation strategy.

```
User Intent

↓

Context Acquisition

↓

Progression Analysis

↓

Progression Pairing Engine

↓

Surprise Strategy

↓

Candidate Generation

↓

Evaluation

↓

Ranking

↓

Presentation
```

Only the planning strategy changes.

No architectural modifications are required.

---

# 4. The Principle of Controlled Deviation

One of the key findings of the architectural audit was that "surprise" should never be synonymous with randomness.

Instead, the planner deliberately departs from expectation while preserving musical coherence.

For example:

Expected

```
C

↓

F

↓

G

↓

C
```

Possible Surprise

```
C

↓

Ab

↓

F

↓

G
```

Although unexpected, the borrowed ♭VI chord remains musically convincing.

---

# 5. Sources of Musical Surprise

The planner should understand multiple categories of surprise.

Each becomes another planning tool.

---

## Modal Borrowing

Borrowing harmony from the parallel mode.

Examples:

```
iv

♭VI

♭VII
```

---

## Deceptive Cadences

Rather than resolving:

```
V

↓

I
```

the planner may choose:

```
V

↓

vi
```

creating one of the oldest forms of musical surprise.

---

## Unexpected Modulation

A temporary movement into another key before returning.

Example:

```
C Major

↓

A Minor

↓

E Major

↓

A Minor
```

---

## Chromatic Mediants

Unexpected third-related movement.

Example:

```
C

↓

Ab

↓

E

↓

C
```

Common in cinematic music.

---

## Tritone Substitution

Especially useful in jazz.

```
G7

↓

Db7

↓

C
```

Unexpected but smooth.

---

## Harmonic Colour

Introducing:

- add9
- maj7
- 6 chords
- altered dominants

without changing functional direction.

---

# 6. The Probability Engine

The Surprise planner differs fundamentally from Continue.

Continue chooses the **most likely** option.

Surprise deliberately favours **less likely** candidates.

Illustration:

| Candidate | Normal Probability |
|-----------|------------------:|
| V | 48% |
| ii | 21% |
| IV | 17% |
| ♭VI | 8% |
| bII | 4% |
| Tritone Sub | 2% |

Continue selects V.

Surprise intentionally examines the lower-probability options.

---

# 7. Weighted Creativity

However, low probability alone is insufficient.

The planner introduces a second weighting:

```
Final Score

=

Musical Validity

×

Novelty
```

Thus:

```
Excellent but common

↓

lower novelty

↓

lower surprise score
```

while

```
Unexpected

+

Musically convincing

↓

highest score
```

This prevents random harmonic nonsense.

---

# 8. Candidate Generation

Several surprise pathways should always be explored.

Example A

Borrowed Chords

```
C

↓

Ab

↓

F

↓

G
```

---

Example B

Deceptive Resolution

```
Dm

↓

G

↓

Am
```

---

Example C

Secondary Dominants

```
C

↓

E7

↓

Am

↓

F
```

---

Example D

Chromatic Shift

```
C

↓

Db

↓

Fm

↓

G
```

Each surprises in a different musical way.

---

# 9. Evaluation Criteria

The Surprise planner evaluates candidates using criteria unavailable to other pathways.

---

## Novelty

How unexpected is the harmonic movement?

---

## Recoverability

Can the progression return to stable harmony later?

---

## Stylistic Consistency

Would this sound appropriate within the chosen genre?

---

## Voice Leading

Are chord transitions playable and convincing?

---

## Emotional Effect

Does the surprise enhance expression?

---

## Memorability

Would listeners remember the harmonic turn?

---

# 10. Explaining Surprise

The educational philosophy of ReasonTouch remains central.

The planner therefore explains *why* the progression is unusual.

Examples:

> Uses a deceptive cadence to avoid the expected tonic.

---

> Borrows harmony from the parallel minor.

---

> Introduces a chromatic mediant relationship.

---

> Uses an unexpected secondary dominant before returning home.

The explanation should help users learn rather than merely observe.

---

# 11. Genre Awareness

Surprise should always remain stylistically appropriate.

For example:

## Pop

Small harmonic deviations.

---

## Jazz

Large substitutions acceptable.

---

## Classical

Functional surprises preferred.

---

## Film Music

Chromatic mediants encouraged.

---

## Blues

Dominant colour preferred.

The planner should therefore consult future style profiles before selecting candidates.

---

# 12. Interaction with Other Pathways

The Surprise pathway is rarely an ending in itself.

Typical flows include:

```
Continue

↓

Surprise

↓

Resolve
```

or

```
Verse

↓

Surprise

↓

Chorus
```

or

```
Bridge

↓

Surprise

↓

Build Tension
```

It acts as an inflection point within the larger compositional narrative.

---

# 13. Existing Infrastructure

Almost all required infrastructure already exists.

The planner reuses:

- ProgressionAnalysis
- HarmonicFunction
- KeyDetector
- ChordSuggestionEngine
- GeneratedProgression
- Progression Pairing Engine
- confidence scoring
- evaluation framework

Only the candidate-generation heuristics differ.

---

# 14. Implementation Roadmap

Implementation should proceed incrementally.

### Phase 1

Borrowed chords.

### Phase 2

Deceptive cadences.

### Phase 3

Secondary dominants.

### Phase 4

Chromatic mediants.

### Phase 5

Jazz substitutions.

### Phase 6

Adaptive creativity weighting.

This ensures each enhancement remains testable and independent.

---

# 15. Success Criteria

The Surprise pathway is complete when it:

- produces genuinely unexpected harmonic ideas
- avoids random chord selection
- remains stylistically coherent
- explains every surprise
- integrates with existing planning architecture
- supports multiple creative mechanisms
- shares evaluation infrastructure with other pathways

---

# 16. Architectural Importance

With the completion of the Surprise pathway, the ReasonTouch planning engine now supports four fundamentally different compositional intentions:

- **Continue** — preserve direction.
- **Resolve** — reduce instability.
- **Build Tension** — increase expectation.
- **Surprise Me** — introduce controlled novelty.

These four strategies form the core of the intelligent progression planning architecture.

---

# 17. Looking Beyond Surprise

Although Surprise introduces creative deviation, many composers eventually seek something even more expressive.

Rather than simply changing harmony, they wish to alter the emotional character of the music itself.

This leads naturally to the next family of planning strategies:

- darker
- brighter
- more emotional
- more energetic
- calmer
- more dramatic

These strategies manipulate musical emotion directly rather than harmonic expectation.

---

## Next Chapter

**Chapter 9 — Emotion-Driven Progression Planning**

The next chapter explores emotional intent as a first-class planning objective, showing how ReasonTouch can translate concepts such as *hopeful*, *melancholic*, *triumphant*, or *mysterious* into coherent harmonic decisions using the same planning architecture established throughout this blueprint.

---

**End of Chapter 8**
