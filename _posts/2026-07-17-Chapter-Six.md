# Chapter 6 – Harmonic Intelligence and Musical Decision Making

> *ReasonTouch Technical Companion*  
> Chapter 6

---

# 6. Harmonic Intelligence and Musical Decision Making

## 6.1 Introduction

Traditional chord software generally answers a simple question:

> *"What chord comes next?"*

ReasonTouch attempts to answer a far more sophisticated question:

> *"Given everything that has happened so far, what is the most musically appropriate direction for this composition?"*

This distinction defines the Harmonic Intelligence layer.

Rather than selecting chords from a static lookup table, ReasonTouch evaluates harmonic context, musical intent, phrase development, functional relationships, cadence behaviour, emotional direction and confidence before proposing new material.

It is therefore not merely a chord suggestion engine—it is a musical reasoning engine.

---

# 6.2 Musical Reasoning Rather than Rule Following

Most educational software is built around fixed rules.

For example:

```
If chord is V

Then suggest I
```

or

```
After ii

Suggest V
```

These rules are correct, but incomplete.

Human composers regularly violate them.

Instead, they evaluate competing musical priorities:

- maintaining momentum
- delaying resolution
- surprising the listener
- reinforcing tonality
- increasing emotional intensity
- preparing modulation

ReasonTouch models this process by allowing multiple musical objectives to compete simultaneously.

---

# 6.3 Layers of Harmonic Intelligence

The harmonic reasoning engine operates as a hierarchy.

```
Musical Context

↓

Harmonic Analysis

↓

Planning

↓

Candidate Generation

↓

Evaluation

↓

Ranking

↓

Presentation
```

Each layer reduces uncertainty before the next stage begins.

This architecture allows reasoning to remain transparent.

---

# 6.4 Understanding Harmonic Function

Every chord fulfils a purpose.

Rather than treating chords as isolated objects, ReasonTouch classifies them by function.

The primary categories are:

```
Tonic

Predominant

Dominant

Passing

Borrowed

Chromatic
```

This abstraction allows identical harmonic behaviour to be recognised in different keys.

For example:

```
C Major

Dm

↓

G

↓

C
```

and

```
G Major

Am

↓

D

↓

G
```

share the same functional movement despite using different chord names.

---

# 6.5 Functional Sequences

Instead of analysing individual chords, the engine analyses sequences.

Example:

```
Tonic

↓

Predominant

↓

Dominant

↓

Tonic
```

This representation allows the software to recognise familiar harmonic shapes regardless of key.

It also enables statistical evaluation of progression quality.

---

# 6.6 Harmonic Stability

Every progression is assigned a stability score.

Conceptually:

```
0.0

Completely unresolved
```

↓

```
1.0

Fully resolved
```

Factors influencing stability include:

- ending function
- cadence strength
- dominant resolution
- tonic reinforcement
- phrase completeness
- borrowed harmony
- chromatic activity

The score provides a numerical estimate of harmonic closure.

---

# 6.7 Musical Tension

Tension is not identical to instability.

For example:

```
Cmaj7
```

may be harmonically stable but emotionally rich.

Similarly,

```
G7
```

creates directional tension despite being functionally expected.

ReasonTouch therefore tracks tension independently from stability.

This distinction enables more expressive planning.

---

# 6.8 Energy Estimation

Energy describes perceived movement.

Typical contributors include:

- harmonic rhythm
- dominant frequency
- root movement
- chromatic density
- borrowed chords
- phrase acceleration

A progression containing repeated tonic harmony may be stable but low in energy.

Conversely, rapidly changing secondary dominants may produce high energy despite remaining tonal.

---

# 6.9 Confidence

Every analytical decision includes confidence.

Confidence measures how strongly the engine believes its interpretation.

Example:

```
Detected Key

G Major

Confidence

0.94
```

versus

```
Detected Key

E Minor

Confidence

0.53
```

Low confidence allows later stages to explore multiple interpretations rather than committing prematurely.

---

# 6.10 Competing Interpretations

Music is often ambiguous.

For example:

```
Am

F

C

G
```

may reasonably belong to

- C Major

or

- A Minor.

Instead of forcing a single answer, ReasonTouch preserves several candidates.

```
1.

C Major

92%
```

```
2.

A Minor

87%
```

```
3.

G Major

61%
```

Later planning stages may evaluate all of them.

---

# 6.11 Weighted Decision Making

Chord selection is not binary.

Every possible continuation receives a weighted score.

Conceptually:

```
Score

=

Harmony

+

Voice Leading

+

Cadence

+

Planning Objective

+

Style

+

Confidence
```

The exact weighting evolves over time but follows this principle.

No single rule dominates every decision.

---

# 6.12 Candidate Evaluation

Each candidate chord is examined across several dimensions.

Examples include:

```
Functional correctness

Resolution quality

Expectedness

Novelty

Voice-leading friendliness

Phrase continuity

Emotional suitability
```

These individual evaluations combine into an overall ranking.

---

# 6.13 Explainable Decisions

One design goal is explainability.

Instead of merely recommending:

```
Am
```

ReasonTouch attempts to explain why.

Examples:

```
Maintains predominant motion.

```

```
Extends dominant preparation.

```

```
Creates deceptive cadence.

```

```
Introduces modal colour without weakening the tonic.
```

This educational aspect differentiates the engine from purely generative systems.

---

# 6.14 Borrowed Harmony

Borrowed harmony expands the harmonic vocabulary while preserving musical coherence.

Examples include:

```
iv

♭VI

♭VII

ii°

Neapolitan

Augmented Sixth
```

Borrowed chords receive additional weighting penalties or bonuses depending upon planning strategy.

For example:

```
Continue

↓

Borrowing discouraged
```

whereas

```
Surprise

↓

Borrowing encouraged
```

The same harmonic object therefore behaves differently depending upon musical intent.

---

# 6.15 Voice-Leading Awareness

Current implementations primarily evaluate harmonic relationships.

Future revisions will additionally score voice-leading quality.

Factors may include:

- common tones
- stepwise movement
- parallel fifth avoidance
- spacing
- inversion suitability
- melodic contour

Voice-leading will become another independent contributor to harmonic intelligence.

---

# 6.16 Context Memory

A single chord has limited meaning.

A progression has history.

ReasonTouch therefore maintains contextual memory including:

- previous harmonic function
- previous cadence
- recent tension
- recent stability
- phrase length
- repeated patterns
- previous suggestions

Future decisions therefore depend upon accumulated musical context rather than isolated events.

---

# 6.17 Predictive Behaviour

The engine does not simply react.

It predicts.

For example:

```
Current progression

↓

Likely destination

↓

Expected cadence

↓

Suggested preparation
```

Planning therefore becomes proactive rather than reactive.

---

# 6.18 Human-Like Reasoning

One long-term objective is to mimic the internal reasoning process of experienced musicians.

Rather than asking:

> "Which chord statistically follows this one?"

the engine attempts to answer:

> "If I were composing this phrase, what musical goal would I currently have?"

This subtle shift dramatically changes generated results.

---

# 6.19 Future Machine Learning Integration

The current reasoning engine is deterministic.

However, future AI systems may influence weighting.

Possible enhancements include:

- learning preferred harmonic movements
- composer-specific models
- style adaptation
- emotional modelling
- personalised composition habits

Importantly, AI should influence decision weighting—not replace musical theory.

This preserves explainability while improving flexibility.

---

# 6.20 Beyond Chord Suggestions

Ultimately Harmonic Intelligence extends beyond progression generation.

Future applications include:

- accompaniment generation
- orchestration advice
- melody harmonisation
- counterpoint assistance
- bass-line planning
- modulation planning
- arrangement guidance

The harmonic reasoning engine therefore becomes a shared service supporting the entire ReasonTouch ecosystem.

---

# 6.21 Design Philosophy

Throughout ReasonTouch, harmonic intelligence follows three guiding principles.

### Musical before mathematical

Mathematics supports musical reasoning but never replaces it.

---

### Explainable before mysterious

Every recommendation should be capable of explanation.

---

### Flexible before rigid

Music contains exceptions.

The engine should recognise them rather than reject them.

---

# 6.22 Summary

The Harmonic Intelligence layer transforms ReasonTouch from a collection of theoretical utilities into a genuine compositional assistant.

Rather than applying isolated rules, it evaluates complete musical context, balances competing objectives, reasons about future harmonic destinations and produces recommendations that are theoretically grounded, musically coherent and educationally transparent.

This layer provides the intellectual foundation upon which future planning engines, AI assistants, orchestration modules and long-form composition systems will be built.
