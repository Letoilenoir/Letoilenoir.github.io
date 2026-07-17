# Chapter 7 – The Generation Engine

> *ReasonTouch Technical Companion*  
> Chapter 7

---

# 7. The Generation Engine

## 7.1 Introduction

If the Planning Engine decides **where** the music should go, the Generation Engine decides **how it gets there**.

This distinction is one of the most important architectural principles in ReasonTouch.

Planning is abstract.

Generation is concrete.

The planner may decide:

> "Increase tension while remaining inside the current key."

The Generation Engine must convert that instruction into actual harmonic material.

For example:

```
Am

↓

Dm

↓

G7

↓

C
```

or perhaps

```
Am

↓

F

↓

G

↓

Em
```

depending upon the requested strategy.

Generation therefore transforms musical intentions into playable harmonic progressions.

---

# 7.2 Position Within the Architecture

The Generation Engine sits between planning and rendering.

```
User

↓

Analysis

↓

Planning

↓

Generation

↓

Voicing

↓

Playback
```

Its responsibility is deliberately narrow.

It generates harmonic structures.

It does **not** concern itself with:

- fingering
- voicing
- rhythm
- instrumentation
- MIDI timing

Those belong to later stages.

---

# 7.3 Inputs

Generation begins with a planning request.

A typical request contains:

```
Detected key

Planning strategy

Desired phrase length

Cadence objective

Mood bias

Energy target

Tension target

Progression analysis

Source progression
```

Together these describe the musical problem that must be solved.

---

# 7.4 Outputs

Generation returns one or more candidate progressions.

Each candidate contains:

```
GeneratedProgression

├── Chords

├── Confidence

└── Explanation
```

Later revisions may also include:

```
Predicted cadence

Voice-leading score

Difficulty

Borrowed harmony count

Style compatibility

Expected listener tension
```

---

# 7.5 Candidate Generation

Rather than generating a single answer, the engine produces several candidates.

Conceptually:

```
Planning Goal

↓

Candidate A

Candidate B

Candidate C

Candidate D
```

These candidates may differ in:

- harmonic movement
- borrowed harmony
- cadence
- phrase contour
- confidence

The interface can therefore present meaningful alternatives instead of one deterministic result.

---

# 7.6 Incremental Construction

Progressions are generated one chord at a time.

For example:

Current state:

```
C

Am
```

Possible next chords:

```
Dm

F

Em

G
```

Suppose

```
Dm
```

is selected.

The progression becomes:

```
C

Am

Dm
```

The next generation cycle now considers the updated harmonic context.

Generation therefore behaves as a continuously evolving process rather than selecting an entire phrase in one operation.

---

# 7.7 Harmonic Constraints

Every generated chord must satisfy multiple constraints simultaneously.

Examples include:

- key compatibility
- functional movement
- planning objective
- cadence direction
- tension target
- stylistic restrictions

A candidate failing several constraints receives a lower score or may be discarded entirely.

---

# 7.8 Strategy-Driven Generation

Different planning strategies produce different harmonic behaviour.

### Continue

Attempts to preserve flow.

```
ii

↓

V

↓

I
```

---

### Resolve

Moves rapidly toward closure.

```
IV

↓

V

↓

I
```

---

### Build Tension

Extends instability.

```
ii

↓

V

↓

ii

↓

V
```

---

### Surprise

Introduces unexpected but defendable harmony.

```
I

↓

♭VI

↓

IV

↓

V
```

The same harmonic context may therefore produce completely different results depending upon the active strategy.

---

# 7.9 Phrase Length

Generation respects phrase length supplied by the planner.

Examples:

```
2 bars
```

```
4 bars
```

```
8 bars
```

Future versions may permit variable-length phrases that terminate naturally when a cadence objective has been satisfied rather than after a fixed number of bars.

---

# 7.10 Functional Balance

Generated phrases should exhibit balanced harmonic motion.

An ideal phrase generally includes:

```
Tonic

↓

Predominant

↓

Dominant

↓

Tonic
```

The engine therefore attempts to avoid excessive repetition of a single harmonic function.

---

# 7.11 Avoiding Loops

One common weakness of naïve generators is endless looping.

For example:

```
I

V

I

V

I

V
```

ReasonTouch tracks recent history to reduce repetitive behaviour.

Possible mechanisms include:

- repetition penalties
- transition weighting
- phrase memory
- harmonic diversity scoring

These encourage more interesting musical development.

---

# 7.12 Borrowed Harmony

When permitted by the planner, borrowed harmony becomes part of candidate generation.

Examples include:

```
iv

♭VI

♭VII
```

Borrowing is never random.

It must satisfy:

- tonal compatibility
- stylistic appropriateness
- phrase objective
- confidence threshold

---

# 7.13 Cadence Awareness

Generation is cadence-aware.

If the planner requests:

```
Perfect Authentic Cadence
```

the final portion of the phrase is biased toward:

```
V

↓

I
```

If the planner requests an unresolved ending, generation intentionally avoids complete resolution.

Cadence therefore becomes an explicit design parameter rather than an accidental outcome.

---

# 7.14 Confidence Accumulation

Every chosen chord contributes to the confidence of the finished phrase.

For example:

```
Chord 1

0.93
```

```
Chord 2

0.91
```

```
Chord 3

0.86
```

```
Chord 4

0.97
```

Overall confidence may be calculated as an average or weighted aggregate.

This value helps rank competing generated phrases.

---

# 7.15 Explanations

Each generated progression attempts to include a concise explanation.

Examples include:

```
Maintains descending fifth motion.

```

```
Resolves dominant tension naturally.

```

```
Uses modal borrowing to introduce colour.

```

```
Delays tonic resolution until the final bar.
```

These explanations reinforce the educational purpose of ReasonTouch.

---

# 7.16 Deterministic Behaviour

Current implementations are intentionally deterministic.

Given identical inputs:

```
Key

Planning strategy

Mood

Analysis
```

the engine should produce identical outputs.

This predictability simplifies:

- debugging
- testing
- educational demonstrations
- regression validation

Future AI layers may introduce controlled variation while preserving reproducibility where required.

---

# 7.17 Extensibility

The generation architecture is intentionally modular.

New generators can be introduced without modifying existing ones.

Future examples include:

```
JazzGenerator

FilmScoreGenerator

BluesGenerator

ModalGenerator

NeoSoulGenerator

ClassicalGenerator
```

Each implements the same generation interface while applying different harmonic languages.

---

# 7.18 Multi-Candidate Ranking

After candidate generation, phrases are ranked.

Possible scoring criteria include:

- harmonic correctness
- planning satisfaction
- cadence quality
- tension profile
- voice-leading potential
- stylistic suitability
- novelty

Only the highest-ranking candidates are presented to the user.

---

# 7.19 Interaction with Voice Leading

The current generator primarily reasons harmonically.

Future versions will collaborate closely with the Voice-Leading Engine.

For example:

```
Candidate A

Excellent harmony

Poor voice-leading
```

versus

```
Candidate B

Excellent harmony

Excellent voice-leading
```

Candidate B should receive the higher overall score.

Generation therefore becomes increasingly integrated with later musical layers.

---

# 7.20 Long-Term Evolution

The current engine focuses primarily on phrase generation.

Future developments include:

### Multi-phrase generation

Creating complete sections rather than isolated continuations.

---

### Section planning

Generating:

- verses
- choruses
- bridges
- introductions
- codas

---

### Motivic development

Maintaining recognisable harmonic identity across an entire composition.

---

### Adaptive complexity

Producing harmonically richer phrases as user expertise increases.

---

### Composer modelling

Learning stylistic preferences from previous compositions.

---

# 7.21 Relationship to Artificial Intelligence

The Generation Engine is designed so that future AI systems enhance rather than replace it.

The intended architecture becomes:

```
Natural Language

↓

AI Interpreter

↓

Planning Engine

↓

Generation Engine

↓

Voice Leading

↓

Performance
```

AI determines intent.

The deterministic generator transforms that intent into musically valid harmonic structures.

This preserves theoretical integrity while allowing conversational composition.

---

# 7.22 Summary

The Generation Engine is the component that transforms musical intentions into actual harmonic progressions.

By separating planning from generation, ReasonTouch gains remarkable flexibility:

- strategies remain interchangeable,
- harmonic reasoning remains explainable,
- generated phrases remain deterministic,
- future AI integration becomes straightforward,
- and increasingly sophisticated compositional techniques can be introduced without redesigning the underlying architecture.

As the project evolves, the Generation Engine will expand from producing four-bar continuations into constructing complete musical forms while remaining faithful to the planning objectives established by the Harmonic Intelligence layer.
